# Buscando cartógrafos

Usamos el editor SPARQL de Wikipedia https://query.wikidata.org/

https://wdqs-tutorial.toolforge.org/
https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples
https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples/advanced
https://www.wikidata.org/wiki/Wikidata:Request_a_query
https://js.histropedia.com/apps/query-timeline/
https://en.wikibooks.org/wiki/SPARQL
https://davidsbatista.net/blog/2023/01/19/SPARQL_WikiData/

Nuestro resultset van a ser personas, que vamos a escoger por su ocupación. Esto hace que el atributo que nos interesa para filtrar es `wdt:P106`. En Wikidata no todas las enidades tienen todos sus atributos rellenos. Hay catalogaciones incompletas, bien por errores o por desconocimiento, que hacen que a muchas entidades les falten ciertos atributos. Por eso al hacer nuestra consulta SPARQL seleccionamos registros que tienen este atributo relleno, para poder filtrar por el.

* Utilizamos el servicio **wikibase:label** para poder convertir entidades Wikidata en texto legible.
* `?person` hace referencia a la entidad y `?personLabel` a la entidad legible.
* Al comienxo es mejor limirtar siempre los resultados, para evitar colapsar los servicios
* Establecemos cláusula restrictiva, que obligue a que los registros listados tengan el atributo `wdt:P106` relleno
* A este atributo, lo llamamos `?empleo`, que es el nombre que ponemos en el **SELECT**.
* Después ponemos un filtro, `person wdt:P106 wd:Q1734662`, en donde establecemos que uno de sus atributo empleo `wdt:P106` debe ser cartógrafo `wd:Q1734662`

La cláusula de consulta resultante es 👇

```sql
SELECT ?person ?personLabel ?empleo ?empleoLabel 
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, este campo debe estar relleno
    ?person wdt:P106 ?empleo.
    
    # FILTROS
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662)
    ?person wdt:P106 wd:Q1734662
    
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en"
    }
  }
 limit 10
```

Y los datos obtenidos

![](img/01result.png)

Si no establecemos orden, los resultados se ordenan por relevancia, en este caso del personaje. **George Washington** fue un cartógrafo coco conocido, pero se lista el primero porque su relevancia por sus otras ocupaciones es enorme. Aparace varias veces porque se listan una a una todas sus ocupaciones asignadas.
Vemos que `?person` y `?empleo` muestran las entidades Wikidata. Pinchando en ella accedemos al elemento resultante. Pero para que aparezcan en los resultados, hacemos uso del servicio **wikibase:label**, que nos permite enlazar las entidades con sus denominaciones. Las denominacione pueden cambiar según el idioma, así que podemos definir el idioma de retorno o dejar que el servicio lo estableca por nosotros

```js
// Así 👇 lo establece por defecto, poniendo si primero el termino español y depués el inglés
bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en". 
// De esta manera 👇 devolvería los textos Label en alemán
bd:serviceParam wikibase:language "de". 
```

Vamos a poner los dato un poco mejpor, agrupando el empleo en una línea: de esta forma utilizamos una función de agregación **group_concat** para concatenar los valores, y el resultado obtenido es mucho más llevadero.

```sql
SELECT ?person ?personLabel (group_concat(?empleoLabel;separator=",") as ?lstempleos)
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, el campo debe estar relleno
    ?person wdt:P106 ?empleo.
    
    # FILTROS
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662)
    ?person wdt:P106 wd:Q1734662
    
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en".
      ?empleo rdfs:label ?empleoLabel .
      ?person rdfs:label ?personLabel .
    }
  }
group by ?person ?personLabel
limit 10
```

![](img/02result.png)

Ahora los resultados nos muestran todas las profesiones de los personajes en una línea. Y seguimos ordenando por relevancia. La lista cuadra.

En esta investigación nos puede ser útil que si hay foto, que la muestre, pero que si no la hay, no omita el registro. Por tanto, queremos que siempre que sea posible aparezca la foto. Para ello introducimos la cláusula `OPTIONAL{ ?person wdt:P18 ?foto }`

```sql
SELECT ?person ?personLabel (group_concat(?empleoLabel;separator=",") as ?lstempleos) ?foto
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, el campo debe estar relleno
    ?person wdt:P106 ?empleo.
    
    # FILTROS
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662)
    ?person wdt:P106 wd:Q1734662
            
    # Aquí ponemos las opcionales (puede haber valores de ese campo o no)
    # Queremos que salgan los registros que tengan campo imagen. Además hacemos un alias ?foto y lo ponemos en el select 👆
    OPTIONAL{ ?person wdt:P18 ?foto }
      
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en".
      ?empleo rdfs:label ?empleoLabel .
      ?person rdfs:label ?personLabel .
    }
  }
group by ?person ?personLabel ?foto
limit 10
```

Podemos ver en la vista **Image Grid** que el resultado obtenido encuentra fotos para 9 de los 10 personajes.

![](img/03result.png)

Sin embargo, si volvemos al modo tabla, si lista los 10, uno de ellos sin imagen, Arno Peters.

![](img/04result.png)

Ahora vamos a filtrar un poco más. No sólo nos valen los cartógrafos, también los geógrafos, así que podemos añadir una segunda profesión a nuestro filtro.

```sql
SELECT ?person ?personLabel (group_concat(?empleoLabel;separator=",") as ?lstempleos) ?foto
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, el campo debe estar relleno
    ?person wdt:P106 ?empleo.
    
    # FILTROS
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662)
    #?person wdt:P106 wd:Q1734662
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662) y geógrafo (wd:Q901402), ambas incluidas (usamos ;) (puede tener más)
    ?person wdt:P106 wd:Q1734662;wdt:P106 wd:Q901402


    # Aquí ponemos las opcionales (puede haber valores de ese campo o no)
    OPTIONAL{ ?person wdt:P18 ?foto }  #Queremos que salgan los registros con campo imagen. Y hacemos un alias ?foto y lo ponemos en el select
      
    
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en".
      ?empleo rdfs:label ?empleoLabel .
      ?person rdfs:label ?personLabel .
    }
  }
group by ?person ?personLabel ?foto
limit 10
```

Ahora en los resultados vemos que desaparece, entre otros, Washington, porque en Wikidata era cartógrafo, pero no geógrafo.

* Sentencias equivalentes, que buscan las ocupaciones cartógrafo(wd:Q1734662) y geógrafo (wd:Q901402). Ambas deben estar presentes
  * `#?person wdt:P106 wd:Q901402,wd:Q1734662.`
  * `#?person wdt:P106 wd:Q1734662,wd:Q901402.`
  * `?person wdt:P106 wd:Q1734662,wd:Q901402.`
* Si queremos que los personajes tengan asigndas las dos propiedades, o sólo una de ellas, podemos usar la opción filter
  * `FILTER ( ?empleo in ( wd:Q901402,wd:Q1734662 ) )`


Por último, podemos extender la consulta para sacar los cartógrafos y/o geógrafos que nacieron o murieron en un determinado periodo, para sacar efemérides

```sql
SELECT ?person ?personLabel (group_concat(?empleoLabel;separator=",") as ?lstempleos) ?birthDate ?birthPlace ?deathDate ?deathPlace ?foto
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, el campo debe estar relleno
    ?person wdt:P106 ?empleo.
    ?person wdt:P569 ?birthDate.
    ?person wdt:P19 ?birthPlace.  # Con esto sacamos el Lugar de Nacimiento, pero no vienen coordenadas
    ?person wdt:P570 ?deathDate.  # Con  esto sacamos la fecha de la muerte
    ?person wdt:P20 ?deathPlace.  # Con esto sacamos el Lugar de fallecimiento

    OPTIONAL{ ?person wdt:P18 ?foto }  
       
    # Aquí ponemos las opcionales (puede haber valores de ese campo o no)
    FILTER ( ?empleo in ( wd:Q901402,wd:Q1734662 ) )

    # Filtramos personas nacidas o fallecidas entre el 17 y el 21 de junio
    FILTER(
     (month(?birthDate) = 6 && day(?birthDate) >= 17) && (month(?birthDate) = 6 && day(?birthDate) <= 21) ||
     (month(?deathDate) = 6 && day(?deathDate) >= 17) && (month(?deathDate) = 6 && day(?deathDate) <= 21)
    )

    
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en".
      ?empleo rdfs:label ?empleoLabel .
      ?person rdfs:label ?personLabel .
    }
  }
group by ?person ?personLabel ?birthDate ?birthPlace ?deathDate ?deathPlace ?foto
limit 100

```

Vemos que salen más resultados de los que deberían salir, porque muchis personajes tienen asociadas varias fotos, y por cada una de ellas se repite el registro. Si no tenemos predilección por ninguna de ellas, podemos usar la función de agregación **SAMPLE** para que agrupe y seleccione al azar una de ellas. Si a eto ordenamos por nombre

```sql
SELECT ?person ?personLabel (group_concat(?empleoLabel;separator=",") as ?lstempleos) ?birthDate ?birthPlaceLabel ?deathDate ?deathPlaceLabel (SAMPLE(?foto) AS ?single)
  WHERE {
    # Aquí ponemos las restrictivas. Para que salga registro, el campo debe estar relleno
    ?person wdt:P106 ?empleo.
    ?person wdt:P569 ?birthDate.
    ?person wdt:P19 ?birthPlace.  # Con esto sacamos el Lugar de Nacimiento, pero no vienen coordenadas
    ?person wdt:P570 ?deathDate.  # Con  esto sacamos la fecha de la muerte
    ?person wdt:P20 ?deathPlace.  # Con esto sacamos el Lugar de fallecimiento

    OPTIONAL{ ?person wdt:P18 ?foto }  #Queremos que salgan los registros que tengan campo imagen. Además hacemos un alias ?foto y lo ponemos en el select para que los liste
    
    # FILTROS
    # Filtramos personas cuya ocupación (P106) es surveyor o agrimensor(wd:Q294126)
    #?person wdt:P106 wd:Q1734662    
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662)
    #?person wdt:P106 wd:Q1734662
    # Filtramos personas cuya ocupación (P106) es cartógrafo(wd:Q1734662) y geógrafo (wd:Q901402), ambas incluidas (usamos ;) (puede tener más)
    #?person wdt:P106 wd:Q901402;wdt:P106 wd:Q1734662.
    #?person wdt:P106 wd:Q901402,wd:Q1734662.
    #?person wdt:P106 wd:Q1734662,wd:Q901402.
    
    # Aquí ponemos las opcionales (puede haber valores de ese campo o no)
    
    
    FILTER ( ?empleo in ( wd:Q901402,wd:Q1734662,wd:Q294126 ) )

      # Filtramos personas nacidas o fallecidas entre el 17 y el 21 de junio
    FILTER(
     (month(?birthDate) = 6 && day(?birthDate) >= 17) && (month(?birthDate) = 6 && day(?birthDate) <= 21) ||
     (month(?deathDate) = 6 && day(?deathDate) >= 17) && (month(?deathDate) = 6 && day(?deathDate) <= 21)
    )

    # Como hacemos una función de agregación, la asociación con el Label de los campos se establece aquí.
    SERVICE wikibase:label { 
      bd:serviceParam wikibase:language "[AUTO_LANGUAGE],es,en".
      ?empleo rdfs:label ?empleoLabel .
      ?person rdfs:label ?personLabel .
      ?birthPlace rdfs:label ?birthPlaceLabel .
      ?deathPlace rdfs:label ?deathPlaceLabel .
    }
  }
group by ?person ?personLabel ?birthDate ?birthPlaceLabel ?deathDate ?deathPlaceLabel 
order by ?personLabel
limit 100
```

http://www.ign.es/web/biblioteca_cartoteca/abnetcl.cgi?TITN=63667