| **Español** | **English** |
|-------------|-------------|
| Los archivos "eda_parte_X.csv" forman un dataset que contiene información cruzada de varios datasets diferentes. | The files "eda_parte_X.csv" form a dataset that contains cross-referenced information from several different datasets. |
| Por un lado, incorporamos la información sobre movilidad de los datos que publicó Google, agrupados por diferentes categorías de lugares, en los que se representa la variación de concurrencia de personas a esos lugares. | On one hand, we include mobility data published by Google, grouped by different categories of places, representing the variation in foot traffic to those locations. |
| Por otro lado, recopilamos la información sobre la incidencia del coronavirus en España. Todo ello agrupado por fechas y provincias. | On the other hand, we collect information on the incidence of the coronavirus in Spain. All of this is organized by dates and provinces. |
| El fin del EDA es observar cómo la incidencia del coronavirus influyó a lo largo del tiempo y en los diferentes territorios sobre el comportamiento y la movilidad de la gente. ¿Varía el comportamiento según la incidencia en cada provincia? ¿Varía el comportamiento según la incidencia en el tiempo? ¿Por qué? | The goal of the EDA is to observe how the incidence of the coronavirus influenced people's behavior and mobility over time and across different regions. Does behavior change based on the incidence in each province? Does behavior change based on the incidence over time? Why? |
| Aquí dejo una relación de las columnas y una descripción de las mismas: | Here is a list of the columns and their descriptions: |
| **provincia_iso** | **provincia_iso** |
| Código ISO de la provincia de residencia. NC (no consta) | ISO code of the province of residence. NC (not available) |
| **fecha** | **fecha** |
| Casos: En los casos anteriores al 11 de mayo, se utiliza la fecha de diagnóstico, en su ausencia la fecha de declaración a la comunidad y, en su ausencia, la fecha clave (fecha usada para estadística por las CCAA). En los casos posteriores al 10 de mayo, en ausencia de fecha de diagnóstico se utiliza la fecha clave1. | Cases: For cases before May 11, the diagnosis date is used; if unavailable, the date of reporting to the community; if unavailable, the key date (used for statistical purposes by the CCAA). For cases after May 10, if no diagnosis date is available, the key date is used. |
| Hospitalizaciones, ingresos en UCI, defunciones: los casos hospitalizados están representados por fecha de hospitalización (en su defecto, la fecha de diagnóstico, y en su defecto la fecha clave). Los casos UCI por fecha de admisión en UCI (en su defecto, la fecha de diagnóstico, y en su defecto la fecha clave). Las defunciones por fecha de defunción (en su defecto, la fecha de diagnóstico, y en su defecto la fecha clave). | Hospitalizations, ICU admissions, deaths: Hospitalized cases are recorded by the date of hospitalization (if unavailable, by diagnosis date, and if unavailable, the key date). ICU cases are recorded by ICU admission date (if unavailable, by diagnosis date, and if unavailable, the key date). Deaths are recorded by the date of death (if unavailable, by diagnosis date, and if unavailable, the key date). |
| **sexo** | **sexo** |
| Sexo de los casos: H (hombre), M (mujer), NC (no consta) | Sex of the cases: H (male), M (female), NC (not available) |
| **grupo_edad** | **grupo_edad** |
| Grupo de edad al que pertenece el caso: 0-9, 10-19, 20-29, 30-39, 40-49, 50-59, 60-69, 70-79, ≥80 años. NC: no consta. Después del 28 de marzo, solo grupos de más de 60 años. | Age group of the case: 0-9, 10-19, 20-29, 30-39, 40-49, 50-59, 60-69, 70-79, ≥80 years. NC: not available. After March 28, only groups older than 60 years. |
| **num_casos** | **num_casos** |
| Número de casos notificados confirmados con una prueba diagnóstica positiva de infección activa (PDIA), tal como se establece en la Estrategia de detección precoz, vigilancia y control de COVID-19 y además los casos notificados antes del 11 de mayo que requirieron hospitalización, ingreso en UCI o fallecieron con diagnóstico clínico de COVID-19, de acuerdo a las definiciones de caso vigentes en cada momento. | Number of confirmed cases reported with a positive diagnostic test for active infection (PDIA), as established in the Early Detection, Surveillance, and Control Strategy for COVID-19, as well as cases reported before May 11 that required hospitalization, ICU admission, or resulted in death with a clinical diagnosis of COVID-19, according to the case definitions in effect at that time. |
| **num_hosp** | **num_hosp** |
| Número de casos hospitalizados | Number of hospitalized cases |
| **num_uci** | **num_uci** |
| Número de casos ingresados en UCI | Number of ICU admissions |
| **num_def** | **num_def** |
| Número de defunciones | Number of deaths |
| **country_region_code** | **country_region_code** |
| Código de España para Google | Spain's code for Google |
| **country_region** | **country_region** |
| Indica que el país es España | Indicates that the country is Spain |
| **sub_region_1** | **sub_region_1** |
| Nombre de la Comunidad Autónoma | Name of the Autonomous Community |
| **sub_region_2** | **sub_region_2** |
| Nombre de la Provincia | Name of the Province |
| **iso_3166_2_code** | **iso_3166_2_code** |
| Código ISO de la provincia | ISO code of the province |
| **place_id** | **place_id** |
| ID del lugar | Place ID |
| **date** | **date** |
| Columna duplicada de fecha | Duplicated date column |
| **retail_and_recreation_percent_change_from_baseline** | **retail_and_recreation_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a lugares de comercio y ocio | Percentage change compared to a baseline reference in foot traffic to retail and recreation places |
| **grocery_and_pharmacy_percent_change_from_baseline** | **grocery_and_pharmacy_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a supermercados y farmacias | Percentage change compared to a baseline reference in foot traffic to grocery stores and pharmacies |
| **parks_percent_change_from_baseline** | **parks_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a parques | Percentage change compared to a baseline reference in foot traffic to parks |
| **transit_stations_percent_change_from_baseline** | **transit_stations_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a estaciones de transporte | Percentage change compared to a baseline reference in foot traffic to transit stations |
| **workplaces_percent_change_from_baseline** | **workplaces_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a lugares de trabajo | Percentage change compared to a baseline reference in foot traffic to workplaces |
| **residential_percent_change_from_baseline** | **residential_percent_change_from_baseline** |
| Porcentaje de cambio con respecto a una medida de referencia base en la afluencia de público a lugares de residencia | Percentage change compared to a baseline reference in foot traffic to residential areas |
