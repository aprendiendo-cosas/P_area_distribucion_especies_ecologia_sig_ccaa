

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

- Partimos de este archivo csv que contiene todos los datos de presencia de especies que hay en GBIF para un rectángulo que ocupa toda Sierra Nevada. 



 "scientific" LIKE 'Pinus%' 





 "scientific" IS 'Quercus pyrenaica Willd.'



 "scientific" LIKE 'Rosmarinus%' 







 "scientific" IS 'Juniperus hemisphaerica Jacq. & C.Presl' OR  "scientific" IS 'Juniperus communis subsp. nana (Willd.) Syme'  OR"scientific" IS  'Juniperus nana Willd.' OR  "scientific" LIKE  'Juniperus sabina%' OR  "scientific" LIKE  'Genista versicolor%' 





 "scientific" LIKE 'Populus%' OR  "scientific" LIKE 'Salix%'





 "scientific" IS  'Festuca glacialis Miégev.' OR  "scientific" LIKE  'Festuca indigesta Boiss%' OR  "scientific" LIKE 'Agrostis%' OR  "scientific" LIKE 'Arenaria%'



