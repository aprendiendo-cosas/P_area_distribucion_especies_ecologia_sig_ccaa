

# Uso de información de [GBIF](https://www.gbif.org/) (Global Biodiversity Information Facility) para generar mapas de área de distribución de especies en Sierra Nevada



## Objetivos

- Aprender qué es GBIF. Curro o Jorge.
- Representar una tabla en csv con coordenadas en QGIS. Jorge
- Consultar la tabla de atributos del csv. Jorge.
- Extraer shapefiles de puntos con la distribución de las especies clave de un ecosistema concreto. Jorge puede hacer algún ejemplo en clase. Los alumnos hacen esto para el ecosistema que tienen asignado.
- Entender el concepto de área de distribución de especies. Curro.
- Entender el concepto de distribución de ecosistemas. Curro.



## Pasos a dar

Aquí describo lo que he hecho yo para preparar los datos. Jorge usa de aquí lo que le resulte útil para su práctica.

- Partimos de [este](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/csv_gbif_sierra_nevada.zip) archivo csv que contiene todos los datos de presencia de especies que hay en GBIF para un rectángulo que ocupa toda Sierra Nevada. 

- Tras cargar el csv anterior en QGIS hacemos lo siguiente:

  - Reproyecto la capa (que viene en WGS84) al EPSG 23030.
  - Añado campos *coord_x* y *coord_y* con las coordenadas correspondientes en EPSG 20300. Uso la calculadora de campos con *$X* y *$Y*.
  - Selecciono los puntos de GBIF que caen dentro de [esta](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/parque_sierra_nevada.zip) (*parque_sierra_nevada.shp*) capa que representa el espacio protegido de Sierra Nevada. 
  - Guardo la capa solo con los campos: *scientific, decimalLat, decimalLong, coord_x, coord_y*
  - Obtenemos [esta](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/datos_presencia_GBIF_23030_snev.zip) capa (*datos_presencia_GBIF_23030_snev.shp*)

- A la capa anterior se le aplican las siguientes consultas para obtener puntos de presencia de especies clave en distintos ecosistemas. Esto es lo que tendrían que hacer los estudiantes en sus casas. Quizás en la práctica de SIG pueden hacer un ejemplo. Yo les daré instrucciones sobre qué especies elegir para cada tipo de ecosistema.

  - **Encina:**

    - Consulta: 

    ```sql
    "scientific" LIKE 'Quercus ilex%' OR "scientific" LIKE 'Quercus rotundifolia%'
    ```

    - Resultado: *[encina.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/encina.zip)*

  - **Pinos:**

    - Consulta: 

    ```sql
    "scientific" LIKE 'Pinus%'
    ```

    - Resultado: *[pinus.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pinus.zip)*

  - **Roble:**

    - Consulta: 

    ```sql
     "scientific" IS 'Quercus pyrenaica Willd.'
    ```

    - Resultado: *[roble.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/roble.zip)*
    
  - **Romero:**
  
    - Consulta: 
  
    ```sql
      "scientific" LIKE 'Rosmarinus%' 
    ```
  
    - Resultado: *[romero.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/romero.zip)*
  
  - **Enebrales y piornales:**
  
    - Consulta: 
  
    ```sql
      "scientific" IS 'Juniperus hemisphaerica Jacq. & C.Presl' OR  "scientific" IS 'Juniperus communis subsp. nana (Willd.) Syme'  OR"scientific" IS  'Juniperus nana Willd.' OR  "scientific" LIKE  'Juniperus sabina%' OR  "scientific" LIKE  'Genista versicolor%' 
    ```
    - Resultado: *[enebrales.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/enebrales.zip)*
  
    
  
  - **Pastizales de alta montaña:**
  
    - Consulta: 
    ```sql
    "scientific" IS  'Festuca glacialis Miégev.' OR  "scientific" LIKE  'Festuca      indigesta Boiss%' OR  "scientific" LIKE 'Agrostis%' OR  "scientific" LIKE 'Arenaria%' 
    ```
    - Resultado: *[pastizales_alta_montania.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/pastizales_alta_montania.zip)*
  
  
  
  
    - **Chopos y sauces (Bosques de ribera):**
  
      - Consulta: 
        
      ```sql
        "scientific" LIKE 'Populus%' OR  "scientific" LIKE 'Salix%'
      ```
  
  
      - Resultado: *[bosques_ribera.shp](https://github.com/aprendiendo-cosas/P_area_distribucion_especies_ecologia_sig_ccaa/raw/refs/heads/main/geoinfo/bosques_ribera.zip)*
  





