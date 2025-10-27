

# Uso de información de [GBIF](https://www.gbif.org/) para generar mapas de área de distribución de especies en Sierra Nevada

> + **_Tipo de material_**: <span style="display: inline-block; font-size: 12px; color: white; background-color: #4caf50; border-radius: 5px; padding: 5px; font-weight: bold;"> Prácticas</span> 
> + **_Versión_**: 2025-2026
> + **_Asignatura (grado)_**: Ecología (CCAA)
> + **_Autor_**: Curro Bonet-García (fjbonet@uco.es)
> + **_Duración_**: Dos sesiones de 2 horas cada una. Alguna hora más en casa. 

![portada](https://raw.githubusercontent.com/aprendiendo-cosas/P_estructura_pobs_ecologia_CCAA/refs/tags/2024-2025/imagenes/portada.png)



Concretamente, tendrás que incluir en este trabajo, mapas de distribución de las siguientes especies en función del ecosistema con el que estés trabajando:

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

Además de incluir los mapas de las especies que te correspondan, deberás de incluir en el documento una discusión ecológica sobre la distribución de las especies estudiadas. Analiza, por ejemplo, cómo se distribuyen en función del clima, la orientación, la geología o cualquier otra variable que consideres relevantes. 



## Objetivos

- Aprender qué es GBIF. Curro o Jorge.
- Representar una tabla en csv con coordenadas en QGIS. Jorge
- Consultar la tabla de atributos del csv. Jorge.
- Extraer shapefiles de puntos con la distribución de las especies clave de un ecosistema concreto. Jorge puede hacer algún ejemplo en clase. Los alumnos hacen esto para el ecosistema que tienen asignado.
- Entender el concepto de área de distribución de especies. Curro.
- Entender el concepto de distribución de ecosistemas. Curro.



## Pasos a dar

Aquí describo lo que he hecho yo para preparar los datos. Jorge usa de aquí lo que le resulte útil para su práctica.

- Partimos de `csv_gbif_sierra_nevada.zip`  que contiene todos los datos de presencia de especies que hay en GBIF para un rectángulo que ocupa toda Sierra Nevada. 

- Tras cargar el csv anterior en QGIS hacemos lo siguiente:

  - Reproyecto la capa (que viene en WGS84) al EPSG 23030.
  - Añado campos *coord_x* y *coord_y* con las coordenadas correspondientes en EPSG 20300. Uso la calculadora de campos con *$X* y *$Y*.
  - Selecciono los puntos de GBIF que caen dentro de esta capa (*parque_sierra_nevada.shp*) que representa el espacio protegido de Sierra Nevada. 
  - Guardo la capa solo con los campos: *scientific, decimalLat, decimalLong, coord_x, coord_y*
  - Obtenemos `datos_presencia_GBIF_23030_snev.shp`

- A la capa anterior se le aplican las siguientes consultas para obtener puntos de presencia de especies clave en distintos ecosistemas. Esto es lo que tendrían que hacer los estudiantes en sus casas. Quizás en la práctica de SIG pueden hacer un ejemplo. Yo les daré instrucciones sobre qué especies elegir para cada tipo de ecosistema.

- **Encina (para estudiantes que trabajan con encinares):**

  - Consulta: 

  ```sql
  "scientific" LIKE 'Quercus ilex%' OR "scientific" LIKE 'Quercus rotundifolia%'
  ```

  - Resultado: *[encina.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/encina.zip)*

- **Pinus halepensis (para estudiantes que trabajan con pinares de repoblación):**

  - Consulta: 

  ```sql
  "scientific" LIKE 'Pinus halepensis%'
  ```

  - Resultado: *[pinus_halepensis.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pinus_halepensis.zip)*

- **Pinus pinaster (para estudiantes que trabajan con pinares de repoblación) :**

    - Consulta: 

    ```sql
    "scientific" LIKE 'Pinus pinaster%'
    ```

    - Resultado: *[pinus_pinaster.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pinus_pinaster.zip)*

- **Pinus nigra (para estudiantes que trabajan con pinares de repoblación):**

    - Consulta: 

    ```sql
    "scientific" LIKE 'Pinus nigra%'
    ```

    - Resultado: *[pinus_nigra.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pinus_nigra.zip)*

- **Pinus sylvestris (para estudiantes que trabajan con pinares de repoblación):**

    - Consulta: 

    ```sql
    "scientific" LIKE 'Pinus sylvestris%'
    ```

    - Resultado: *[pinus_sylvestris.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pinus_sylvestris.zip)*


  - **Roble (para estudiantes que trabajan con robledales):**

    - Consulta: 

    ```sql
     "scientific" IS 'Quercus pyrenaica Willd.'
    ```

    - Resultado: *[roble.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/roble.zip)*
    
  - **Romero (para estudiantes que trabajan con matorrales de media montaña):**
  
    - Consulta: 
    
    ```sql
      "scientific" LIKE 'Rosmarinus%' 
    ```
  
    - Resultado: *[romero.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/romero.zip)*

 - **Tomillos comunes (para estudiantes que trabajan con matorrales de media montaña):**
  
    - Consulta: 
    
    ```sql
      "scientific" LIKE 'Thymus mastichina%' OR "scientific" LIKE 'Thymus vulgaris%' OR "scientific" LIKE 'Thymus zygis%'
    ```
  
    - Resultado: *[thymus.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/thymus.zip)*

 - **Jaras (para estudiantes que trabajan con matorrales de media montaña):**
  
    - Consulta: 
    
    ```sql
      "scientific" LIKE 'Cistus%'
    ```
  
    - Resultado: *[cistus.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/cistus.zip)*
  
  - **Enebros y sabinas de alta montaña (para estudiantes que trabajan con enebrales y piornales):**
  
    - Consulta: 
    
    ```sql
      "scientific" IS 'Juniperus hemisphaerica Jacq. & C.Presl' OR  "scientific" IS 'Juniperus communis subsp. nana (Willd.) Syme'  OR"scientific" IS  'Juniperus nana Willd.' OR  "scientific" LIKE  'Juniperus sabina%'  
    ```
    - Resultado: *[juniperus.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/juniperus.zip)*

  - **Piornos de alta montaña (para estudiantes que trabajan con enebrales y piornales):**
  
    - Consulta: 
    
    ```sql
      "scientific" LIKE  'Genista versicolor%' 
    ```
    - Resultado: *[genista.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/genista.zip)*
    
  - **Festucas de alta montaña (para estudiantes que trabajan con pastizales de alta montaña):**
  
    - Consulta: 
    ```sql
    "scientific" IS  'Festuca glacialis Miégev.' OR  "scientific" LIKE  'Festuca      indigesta Boiss%'  
    ```
    - Resultado: *[festuca.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/festuca.zip)*

 - **Arenaria de alta montaña (para estudiantes que trabajan con pastizales de alta montaña):**
  
    - Consulta: 
    ```sql
     "scientific" LIKE 'Arenaria pungens%' 
    ```
    - Resultado: *[arenaria.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/arenaria.zip)*

  

 - **Chopos  (para estudiantes que trabajan con bosques de ribera):**
   
      - Consulta: 
        
      ```sql
        "scientific" LIKE 'Populus%''
      ```
   - Resultado: *[populus.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/populus.zip)*

 - **Sauces  (para estudiantes que trabajan con bosques de ribera):**
   
      - Consulta: 
        
      ```sql
        "scientific" LIKE 'Salix%''
      ```
   - Resultado: *[salix.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/salix.zip)*

 - **Cárices  (para estudiantes que trabajan con borreguiles):**
   
      - Consulta: 
        
      ```sql
        "scientific" LIKE 'Carex%''
      ```
   - Resultado: *[salix.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/carex_nigra.zip)*







