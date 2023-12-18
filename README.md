El archivo "eda.csv" es un dataset que contiene inforación de varios datasets diferentes. 

Por un lado incorporamos la información sobre movilidad de los datos que publicó google agrupados por diferentes categorías de lugares, 
en los que se representa la variación de concurrencia de personas a esos lugares. Por otro lado recopilaos la información sobre la incidencia del coronavirus en España.
Todo ello agrupado por fechas y provincias. 

El fin del EDA es obervar cómo la incidencia del coronavirus influyó a lo largo del tiempo y en los diferentes territorios sobre el comportamiento y la movilidad de la gente.
¿Varía el comportamiento según las incidencia en cada provincia?
¿Varía el comportamiento según la incidencia en el tiempo?
¿Por qué?

Aquí dejo una relación de las columnas y una descripción de las mismas:

**provincia_iso** 
Código ISO de la provincia de residencia. NC (no consta)
**fecha**
Casos: En los casos anteriores al 11 de mayo, se utiliza la fecha de diagnóstico, en su
ausencia la fecha de declaración a la comunidad y, en su ausencia, la fecha clave (fecha
usada para estadística por las CCAA). En los casos posteriores al 10 de mayo, en ausencia
de fecha de diagnóstico se utiliza la fecha clave1.
Hospitalizaciones, ingresos en UCI, defunciones: los casos hospitalizados están
representados por fecha de hospitalización (en su defecto, la fecha de diagnóstico, y en
su defecto la fecha clave, los casos UCI por fecha de admisión en UCI (en su defecto, la
fecha de diagnóstico, y en su defecto la fecha clave) y las defunciones por fecha de
defunción (en su defecto, la fecha de diagnóstico, y en su defecto la fecha clave).
**sexo** Sexo de los casos: H (hombre), M (mujer), NC (no consta)
**grupo_edad** 
Grupo de edad al que pertenece el caso: 0-9, 10-19, 20-29, 30-39, 40-49, 50-59, 60-69,
70-79, ≥80 años. NC: no consta. Después del 28 de Marzo solo grupos de más de 60 años
**num_casos**
Número de casos notificados confirmados con una prueba diagnóstica positiva de
infección activa (PDIA) tal como se establece en la Estrategia de detección precoz,
vigilancia y control de COVID-19 y además los casos notificados antes del 11 de mayo que
requirieron hospitalización, ingreso en UCI o fallecieron con diagnóstico clínico de COVID19, de acuerdo a las definiciones de caso vigentes en cada momento.
**num_hosp** 
Número de casos hospitalizados
**num_uci**
Número de casosingresados en UCI
**num_def** 
Número de defunciones
