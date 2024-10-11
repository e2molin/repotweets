## ⌛️ 2024-10-11

### 🧵 Nociones de caligrafía [Enlace en Twitter](https://x.com/bne_biblioteca/status/1821876681293914427?s=48)
### ⚗️ Desarrollo de mapas interactivos con Quarto [Enlace al tutorial](https://neocarto.github.io/geounivr2024/VEN1_geoviz_TP/docs/index.html)
### 😎 Artículo: The Way to Mecca [Revista de LOC](https://loc.gov/lcm/pdf/LCM_2024_0708.pdf)
### 📰 Disponible nueva versión de Natural Earth [Version 6](https://shadedrelief.com/ne-draft/)
### 🧰 drawDB. Esquemas de base de datos [🔗 Enlace](https://www.drawdb.app/)
### 🧰 Swapy. Librería para hacer dragdrop en JS [🔗 Enlace](https://swapy.tahazsh.com/)
### 🧰 Two-Up-Element. Librería de comparación de dos imágenes [🔗 Enlace](https://github.com/GoogleChromeLabs/two-up)
### 😎 Artículo: Las Guias Freytag & Berndt [🔗 Enlace](https://www.geografiainfinita.com/2017/06/freytag-berndt-los-mejores-mapas-de-carreteras-del-mundo) 

### 🌐 Carte Topographique De La France de l'Etat-Major, Levee et Publi

Creada entre 1832 y 1876 a escala 1:80.000. [🔗 Mosaico de 267 imágenes](https://www.davidrumsey.com/luna/servlet/s/1fn8qy)

Tenemos artículo seobre esto `2022 - La cartografia de Francia 1832-1876 - Jean-Luc Arnaud.pdf` [🔗 Enlace](https://shs.hal.science/halshs-03688084v1/document)

### 🐳 Docker del Catálogo de la Cartoteca

Ya me he logado y actualizado la contraseña a la habitual italiana



---
## ⌛️ 2024-10-10

Comienzo los contactos con TAYSA para el Catálogo

> https://meet.google.com/jxf-hehs-ofb

Me crean una máquina de desarrollo con Docker

10.67.33.46
esteban.emolin // Cnig.2024

Tienes que entrar con por SSH ( putty ) y la primera vez pedirá un cambio de contraseña.
Tu directorio de trabajo en /docker/cartoteca puedes dejar ahí los ficheros.

---
## ⌛️ 2024-10-09

Documentación de SIDDAE preparada para el CdD

* 1322 documentos nuevos (25Gb)
* 297 documentos modificados (4Gb)

💿 `D:\volcadosCDD`

### 🔍 Averiguar sobre el Planisferio de Vesconte Maggiolo de 1531

[Este mapa de La biblioteca de Macao](http://lunamap.must.edu.mo/luna/servlet/view/search/when/1527?q=maggiolo&sort=identifier%2Ctitle%2Ccontributor%2Ctype) es de 1527

Echar un vistazo a estos [catálogos de Daniel Crouch](https://crouchrarebooks.com/catalogues-rare-maps-atlases-books/)

España dividida segun acostumbran los geografos - El mapa regional 1456-1850 - Jesus Burqueño

### 😎 Lecturas

* La historia de Europa de Péres-Reverte [Artículos 🔗](https://www.zendalibros.com/tag/una-historia-de-europa/)
* Mapas italianos Guerra Civil [Artículo 🔗](https://www.geografiainfinita.com/2021/05/los-mapas-italianos-de-espana-para-la-guerra-civil/)


### 💻 Desarrollo

¡TRUCAZO para liberar GIGAS de tu disco duro! Si eres programador y usas NPM...

Ejecuta el comando: `npx npkill`

Muestra las carpetas node_modules y lo que ocupan. Dale [Espacio] para eliminar las que no uses ↓


## ⌛️ 2024-10-08

🍉 Cargando datos de Colmenares

```sql
select * from bdsidschema.archivodocmtn where sellado in
(
503691,503692,503693,503750,504173,504174,504175,504176,504177,504178,504179,504180,504181,504182,504183,504184,504185,504186,504187,504188,504189,504190,504191,504192,504231,504232,504233,504234,506204,506205,506206,506207,506208,506209,506210,506211,506212,506213,506343,506344,506345,503647
);
```

💿 `D:\WorkLocal\Archivo Topografico\20231024 - Escaneado masivo de cuadernos interiores `

20241007 - Suma de datos - Duplicados Segunda revision - Colmenares.xlsx
Lo último actulziado han sido el campo zona_num


🍉 Analizo los históricos

\\sbdignmad801.ign.fomento.es\DELIMITACIONES_TERRITORIALES\Historicos\Historico\Shape-1995\SHP


🍉 Añadimos etiquetas a los eventos de efemérides:

* **HistoCarto**: evento relacionado con la historia de la cartografía o vida de un cartógrafo, geógrafo, matemático, grabador, impresor, editor de mapas...
* **CartoEvent**: evento relacionado directamente con un mapa o conjunto de mapas.
* **HistoEvent**: evento histórico que hemos conectado con algún mapa de la cartografía.
* **HistoIGN**: evento o personaje relacionado con el IGN



## ⌛️ 2024-10-04

### Mapas de España siglo XIX y om,ienzos siglo XX

El mapa de España de 1884, tengo [una ficha interesante 🔗](http://guiadigital.uam.es:90/SCUAM/documentacion/1884Mapa.php)
En EL ICGC tienen un mapa de España que creo nosotros no tenemos [Enlace 🔗](https://cartotecadigital.icgc.cat/digital/collection/espanya/id/2492/rec/1)



### 👨 James Renell

* Considerado el padre del levantamiento geodésico de la India
* Exposición en la Universidad e Michigan [🔗 Enlace](https://apps.lib.umich.edu/online-exhibits/exhibits/show/india-maps) sobre metodologías, instrumentos y mapas relacionados

### 🕌 Busco mapas relacionados con la cartografía Safávida

Tengo material para hablar de los otomanos y del periodo Mughai en la India con los mapas Jainistas con [un podcast 🎧 de William Dalrymple en Oculi Mundi](https://oculi-mundi.com/william-dalrymple). Incluso pàra la época post Mughai con el levantamiento geodésico de la India. Pero me falta la parte safávida.

Me gustaría encontrar algo relacionado con los mapas de la *qibla*, y entender el trazado de esos mapas en los astrolabios.

* Material: 
  * [A sine on the road to Mecca](https://www.islamicity.org/5434/a-sine-on-the-road-to-mecca/))
  * [Muslim Mathematicians on the Road to Makkah](https://www.islamicity.org/2363/muslim-mathematicians-on-the-road-to-makkah/)

Hay un libro, [ 📚 World-maps for Finding the Direction and Distance to Mecca](https://brill.com/display/title/1073) de David King, que trata sobre dos mapamundis dafávidas encontrados en 1989 y 1995.  Ambos están hechos de latón y datan del siglo XVII en Irán. La Meca está en el centro y una sofisticada cuadrícula de longitud y latitud permite al usuario determinar la dirección y la distancia a la Meca desde cualquier lugar del mundo entre Andalucía y China. Antes del descubrimiento de estos mapas, se creía que dichas cuadrículas cartográficas se habían concebido en Europa alrededor de 1910. Este libro profusamente ilustrado presenta una descripción general de las formas en que los musulmanes a lo largo de los siglos han determinado la dirección sagrada hacia la Meca ( qibla ) y luego describe los dos mapamundis en detalle. El autor muestra que los datos geográficos derivan de una fuente de Asia Central del siglo XV y que las matemáticas subyacentes a la cuadrícula se desarrollaron en Bagdad en el siglo IX.

<section style="display:flex; text-align: center; justify-content: center; align-items:center;">
  <figure>
    <img src="img/preserving-distances-to-mecca.jpg" alt="Offset de cuatro cuerpos" width="100%"/>
    <figcaption>Mapa deformado conservando las distancias a La Meca, situada en el centro</figcaption>
  </figure>
</section> 

Hay un documento e imágenes en mi Cartoteca sobre este tema: `1600-1700 - Safavid Mecca-centered World Map.md`

### Efemérides Encontradas

Facundo Cañada López, del que no hay fechas en Wiki, es jubilado del servicio activo del ejercito en la primera quincena de junio de 1903. Esto se firma el 11 de julio de 1903 y se publica en la Gaceta del 13 de julio de 1903.

Su plano de Madrid datado en 1902 y en cuya ejecución se invirtieron cuatro años, es un plano realizado a escala 1:7.500, y consta de seis hojas que al unirlas forman un mapa continuo de gran detalle (ver figura 1). Este plano fue realizado a partir de tomas de datos topográficos de campo y de información de los trabajos catastrales que hasta la fecha obraban en poder del Instituto Geográfico Nacional (en ese tiempo denominado Instituto Geográfico y Estadístico) y otros parcelarios inéditos cedidos por Corporaciones o particulares.

Por este plano le concedieron a Facundo Cañada el “Premio de Honor de la Cámara Internacional de Industria, Comercio y Ciencias de Madrid de 1902” 

En noviembre de 1854, llega a
Madrid y es instalado el Circulo Meridiano Repsold. Fue construido en Hamburgo y comprado por 22.000 francos,
siendo el instrumental que durante un
siglo ha permitido más horas de observación, considerándose el elemento fundamental del Observatorio, ya que en
combinación con un reloj de péndulo,
es utilizado para determinar la posición
absoluta de los astros en la esfera celeste.


* Johan Georg Justus Perthes (Rudolstadt, Turingia, 11 de septiembre de 1749 - Gotha, Turingia, 2 de mayo de 1816) 
* Adolf Stieler (26 February 1775 – 13 March 1836) 
* Heinrich Karl Wilhelm Berghaus (3 May 1797 – 17 February 1884)
* Christian Gottlieb Reichard (26 June 1758 – 11 September 1837)
* Augustus Heinrich Petermann (18 April 1822 – 25 September 1878)
* Joan Blaeu (Alkmaar, 23 de septiembre de 1596-Ámsterdam, 28 de mayo de 1673) 
* Jodocus Hondius (versión latinizada de Joost de Hondt) (Wakken, 17 de octubre de 1563-Ámsterdam, 12 de febrero de 1612)
* Gerardus Mercator (Rupelmundo, Flandes; 5 de marzo de 1512-Duisburgo, Sacro Imperio Romano Germánico; 2 de diciembre de 1594),
* Regnier Gemma Frisius (Dokkum, Frisia, 9 de diciembre de 1508 - Lovaina, Brabante, 25 de mayo de 1555) f
* Abraham Ortelius (Amberes, 14 de abril de 1527 - Amberes, 28 de junio de 1598),
* Benito Arias Montano (Fregenal de la Sierra, 1527 - Sevilla, 6 de julio de 1598)
* Georg Braun (también Brunus, Bruin; Colonia, 1541-10 de marzo de 1622) 
* Sebastian Muenster— (Nieder-Ingelheim, 20 de enero de 1488-Basilea, 26 de mayo de 1552)
* Nicolás de Fer (1646 – 25 de octubre de 1720)
* Johann Baptist Homann (Kammlach, Baviera, 20 de marzo de 1664 - Núremberg, 1 de julio de 1724) 
* Jan Huyghen van Linschoten (o Huijgen) (Haarlem, ca. 1563 - Enkhuizen, 8 de febrero de 1611)
* Matthäus Merian der Ältere (Matthäus Merian, el Viejo, Basilea, 22 de septiembre de 1593-Bad Schwalbach, 19 de junio de 1650)
* John Speed (1552 – 28 de julio de 1629)
* Alexis-Hubert Jaillot (1632 – 2 November 1712)
* Guillaume de l'Isle, or Guillelmo Delille (French pronunciation: [ˌɡi:yom ˈthe:líl]; 28 February 1675, Paris – 25 January 1726, Paris[1])
* Nicolas Sanson (20 December 1600 – 7 July 1667) 
* Jacques Nicolas Bellin (1703 – 21 March 1772)
* Michel-Étienne Turgot (/tʊərˈɡoʊ/; French: [tyʁgo]; 9 June 1690 in Paris – 1 February 1751 in Paris) 
* Charles-François Delamarche (August 1740 – 31 October 1817)
* Jean-Baptiste Bourguignon d'Anville (French pronunciation: [ʒɑ̃ batist buʁgiɲɔ̃ dɑ̃vil]; born in Paris 11 July 1697 – 28 January 1782)
* Mary Ann Rocque (c. 1725 - 8 May 1774)  
* Adam Friedrich Zürner (15 August 1679 – 18 December 1742)
* John Ogilby, Ogelby, or Oglivie (17 November 1600 – 4 September 1676) 
* Nicolaes Visscher I (25 January 1618, Amsterdam – buried 11 September 1679, Amsterdam)
* Claes Janszoon Visscher (1587 – 19 June 1652) 
* Gerard de Jode (also known as Petrus de Jode; c. 1511 – 5 February 1591)
* Willem Barentsz (Dutch pronunciation: [ˈʋɪləm ˈbaːrənts]; c. 1550 – 20 June 1597),
* Vincenzo Maria Coronelli (August 16, 1650 – December 9, 1718)
* Stefano Bonsignori or Buonsignori (died 21 September 1589, in Florence)
* Ignazio (or Egnazio) Danti, O.P. (April 1536 – 10 October 1586)
* Urbano Monti (16 August 1544 – 15 May 1613)
* Matteo Ricci (6 October 1552 – 11 May 1610)
* Conrad Malte-Brun (Thisted, Dinamarca, 12 de agosto de 1755 - París, Francia, 14 de diciembre de 1826) 
* Pascual Madoz e Ibáñez (Pamplona, 17 de mayo de 1806-Génova, 11 de diciembre de 1870)
* López de Vargas Machuca, Tomás. Madrid, 1730 – 19.VII.1802.
* Adolf Repsold (* 31. August 1806 in Hamburg; † 13. März 1871 ebenda)
* Jerónimo Pedro Mathet Rodríguez (Madrid, 7 de abril de 1878-Madrid, 28 de noviembre de 1936)
* Rigobert Bonne (Raucourt, 6 de octubre de 1727 - 2 de noviembre de 1795)

