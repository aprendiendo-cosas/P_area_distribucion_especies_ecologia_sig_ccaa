

# Uso de información de [GBIF](https://www.gbif.org/) para generar mapas de área de distribución de especies en Sierra Nevada

> + **_Tipo de material_**: <span style="display: inline-block; font-size: 12px; color: white; background-color: #4caf50; border-radius: 5px; padding: 5px; font-weight: bold;"> Prácticas</span> 
> + **_Versión_**: 2025-2026
> + **_Asignatura (grado)_**: Ecología (CCAA)
> + **_Autor_**: Curro Bonet-García (fjbonet@uco.es)
> + **_Duración_**: Lo que haya durado esta sesión en la asignatura de SIG más una hora en casa 

![portada](https://raw.githubusercontent.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/refs/heads/main/imagenes/portada.png)



## Objetivos

- Disciplinares para la asignatura de ecología:
  - Familiarizarse con GBIF como infraestructura que provee datos a escala mundial sobre diversidad y distribución de especies. 
  - Entender bien la diferencia entre área de distribución de una especie y distribución de un ecosistema en el que esa especie es dominante.

- Competenciales: Relacionados con la adquisición de competencias genéricas (SIG y R en este caso):
  - Entrenar la capacidad de representar datos georreferenciados en tablas `csv` usando QGIS.
  - Consultar la tabla de atributos de dicha capa usando QGIS.
  - Generar ficheros de formas (shapefile) de puntos con la distribución de las especies clave de un ecosistema concreto. 


Los objetivos de aprendizaje anteriores se materializan en el siguiente objetivo operativo. Es decir, tienes que hacer esto:

> Generar un mapa que muestre la distribución de las especies dominantes del ecosistema con el que estás trabajando y otro con la distribución de dicho ecosistema. 



## Contextualización ecológica: áreas de distribución de especies (nicho ecológico) y distribución de ecosistemas.

Los ecosistemas terrestres están dominados por plantas. Ellas son las que suelen dar la forma y también el nombre a dichos ecosistemas. Un pinar, por ejemplo, es un bosque en el que dominan los pinos. Pero no todos los sitios en los que hay pinos son pinares. Puede haber pinos en mitad de un encinar y no pasa nada. Si en un lugar concreto hay muchos individuos de una especie, es porque en esa zona se dan las condiciones adecuadas para su supervivencia. Si en una zona hay pocos individuos de una especie, es porque las condiciones no son tan adecuadas. La combinación de todas las condiciones ambientales que determinan la presencia de especies en el territorio es lo que denominamos "nicho ecológico". La idoneidad del territorio para que en él vivan las distintas especies cambia de manera gradual al hacerlo las condiciones ambientales. 

Los lugares en los que una especie es muy abundante son los que reciben un nombre que alude a dicha especie. Esta abstracción y generalización nos permite crear el concepto de "tipo de ecosistema". Así, un encinar, por ejemplo, es un lugar en el que hay muchas encinas. Esta abundancia de una o varias especies en concreto condiciona la estructura y también el funcionamiento del sistema en su conjunto.

El siguiente esquema muestra esta idea.





![gradientes](https://raw.githubusercontent.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/refs/heads/main/imagenes/gradientes_nicho.png)

En nuestro caso hemos trabajado por ahora tanto con la distribución de las especies concretas (en la práctica de SIG y en la de ecología sobre el mapa de biodiversidad) y también con la idea de distribución de tipos de ecosistemas. En este ejercicio combinaremos ambas ideas para entenderlo todo mejor. Generaremos un mapa que muestre por un lado la distribución de las especies dominantes de nuestro ecosistema y por otro la distribución de dicho ecosistema. 

La interpretación ecológica de los resultados obtenidos nos ayudará a entender mejor cómo se distribuyen las especies y los ecosistemas en Sierra Nevada. Así, por ejemplo, el mapa de distribución de ecosistemas se ha generado a partir de las zonas de máxima abundancia de las especies dominantes. Un lugar que esté fuera del área de distribución de un ecosistema, pero que tenga puntos de presencia de una especie de otro ecosistema se interpreta como que en esa zona pueden vivir pocos individuos de esa especie. Sin embargo, un polígono del mapa de ecosistemas que no tenga puntos de presencia de la especie dominante, sería interpretada como un error de muestreo. 



## Flujo de trabajo

A continuación se describen los pasos que hay que dar para generar mapas de distribución de las especies de interés. Describiré con menos detalle las cuestiones que ya habéis visto en la asignatura de SIG:

### 1. Cargar en QGIS los datos de presencia y consultar por especie

+ **1.1** Descarga el archivo `csv` que contiene los datos de presencia de especies según GBIF. Lo tienes [aquí](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/csv_gbif_sierra_nevada.zip). 

+ **1.2.** Como os enseñó Jorge, carga el archivo `csv` indicando que los campos `UTM_X`  y `UTM_Y` tienen las coordenadas de los puntos.

+ **1.3** También como te enseñó Jorge, selecciona los puntos que tengan las distintas especies que son importantes en tu ecosistema. Una vez tengas hecha la selección, guarda los puntos en un fichero de formas de puntos asignándole un nombre característico de la especie. Si tu ecosistema tiene dos especies clave, por ejemplo, tendrás dos ficheros de formas (shapefiles) con los resultados de las consultas. A continuación tienes una lista con las especies que tendrás que caracterizar en función de cuál sea tu ecosistema:

  - **Encinar**: Mapa de distribución de *Quercus ilex*. Recuerda que también tiene como sinónimo *Quercus rotundifolia*.

  - **Pinares de repoblación:**

    - Mapa de *Pinus halepensis*
    - Mapa de *Pinus pinaster*
    - Mapa de *Pinus nigra*

    - Mapa de *Pinus sylvestris*

  - **Robledales**: Mapa de distribución de *Quercus pyrenaica*

  - **Matorrales mediterráneos**:
    - Mapa de *Rosmarinus*
    - Mapa de los tomillos más comunes (*Thymus mastichina, Thymus vulgaris* y *Thymus zygis*)
    - Mapa de las jaras más comunes (*Cistus*)

  - **Piornales y enebrales de alta montaña**:
    - Mapa de *Juniperus hemisphaerica, Juniperus communis subsp. nana, Juniperus nana* y *Juniperus sabina*
    - Mapa de *Genista versicolor*

  - **Pastizales de alta montaña**:
    - Mapa de *Arenaria pungens*

  - **Bosques de ribera**:
    - Mapa de *Populus*
    - Mapa de *Salix*

  - **Borreguiles**
    - Mapa de *Carex nigra*

+ **1.4** Una vez que tengas los mapas de las especies que te interesan, despliega las capas en QGIS y ponles unos colores que te gusten.



### 2. Carga en QGIS el mapa de ecosistemas

+ **2.1** En [este](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/ecosistemas_snev_dissolve.zip) enlace puedes descargar el mapa de ecosistemas. 
+ **2.2** Una vez descargado, despliégalo en QGIS y ponle unos colores que te gusten y que permitan ver bien los puntos de presencia de las especies.



## Resultados esperados e interpretación ecológica

Si sigues correctamente los pasos anteriores, deberás obtener un mapa parecido al que se muestra a continuación. 

![encina_encinar](https://raw.githubusercontent.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/refs/heads/main/imagenes/encina_encinar.png)

Los puntos naranjas se corresponden con el área de distribución de la especie del ejemplo. Los polígonos verdes corresponden con el área de distribución del ecosistema en el que es dominante esta especie.

Para interpretar ecológicamente el resultado, intenta contestar a estas preguntas. Te darán información relevante:

+ ¿Cómo explicamos que los puntos en los que hay individuos de la especie estudiada que no están en lugares clasificados como el ecosistema en cuestión?
+ ¿Hay algún polígono en el que no aparezca ningún punto de presencia de la especie estudiada? En caso afirmativo, ¿a qué crees que se debe esto?



****

[Aquí](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/archive/refs/tags/2025_2026.zip) puedes descargar un archivo .zip que contiene este guión en formato html y todo el material que incluye.

****
Haz click [aquí](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/releases) para ver cómo ha cambiado este guión en los distintos cursos académicos.

****
 <p xmlns:cc="http://creativecommons.org/ns#" >El contenido de este repositorio se puede utilizar bajo la siguiente licencia:  <a  href="https://creativecommons.org/licenses/by-nc-sa/4.0/?ref=chooser-v1"  target="_blank" rel="license noopener noreferrer"  style="display:inline-block;">CC BY-NC-SA 4.0<img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1"  alt=""></a></p> 

<p>Esta licencia no aplica a enlaces a artículos, libros o imágenes no originales. Estos productos tienen su licencia correspondiente.</p>





