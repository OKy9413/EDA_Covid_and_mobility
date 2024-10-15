<div>
<img src="portada.jpg " width="700"/>
</div>

### TEMA

Cruce de datos de incidencia de la covid_19 en España proporcionados por el Ministerio de Sanidad con datos de movilidad sobre la afluencia de personas a determinadas lugares agrupados en diferentes categorías proporcionados por Google. <br>
Todo ello agrupado por fechas y provincias.

Veremos la correspondencia entre la incidencia del covid y las métricas de afluencia de público a según qué sitios.

### HIPÓTESIS

##### La principal hipótesis es que la incidencia del Covid influyó sobre los lugares que mas se frecuentaron durante la pandemia.

De ahí salen varias preguntas: <br>
- ¿Existen cambios significativos en los patrones de conducta durante este periodo? <br>
- ¿Existe correspondencia entre las diferentes métricas temporales? <br>
- ¿Podemos con estos datos afirmar que existe causalidad o mera correspondencia entre ellos? <br>
- ¿Qué efectos tiene para cada categoría de estudio? <br>
- ¿Cuánto duran los efectos de esos cambios? <br>


##### Por otro lado, podríamos verlo al revés, ¿influye los lugares frecuentados con el crecimiento de los datos de incidencia del covid?

## OBTENCIÓN DE LOS DATOS

### DATASETS Y FUENTES ALTERNATIVAS DE DATOS

*df_google* es un dataset publicado por Google que se puede descargar del siguiente enlace: [www.google.com/covid19/mobility/data_documentation](https://www.google.com/covid19/mobility/data_documentation.html?hl=es) <br>
*df_covd19* es un dataset publicado por el [Instituto de Salud Carlos III (ISCIII)](https://www.isciii.es) y que puede encontrar en el siguiente enlace: [casos_hosp_uci_def_sexo_edad_provres.csv](https://cnecovid.isciii.es/covid19/resources/casos_hosp_uci_def_sexo_edad_provres.csv)

Incluye aquí una vista del dataset o datasets de los que partirás para poder evaluar tu hipótesis. <br>
También incluye el origen de estos datos y su fuente.

-  Tras cargar *df_google* prescindimos de las columnas *metro_area y census_fips_code* ya que no aportan información. <br> 
    Posteriormente rellenamos la columna *sub_region_1* por faltar nombres de las provincias de las comunidades con una sola provincia. Comprobamos que están todas las provincias. <br>
    Creamos una nueva columna a partir de *sub_region_1*, *provincia_id_g* para cruzarla con la otra tabla.

- En *df_covid19* encontramos que hay datos que no están asociados a provincias concretas, prescindimos de ellos ya que queremos solo los datos asociados a una provincia.

Una vez que tenemos los dos dataset preparados que vamos a usar en este EDA toca unirlos, para ello se hace un *merge* de df_google sobre df_covid19 por las columnas fecha y provincia. Columnas estas previamente armonizadas. 

###  CONCLUSIONES

- El mejor indicador epidemiológico parece ser el número de hospitalizaciones.
- No podemos afirmar a ciencia cierta que haya causalidad, pero sí podemos hablar de correspondencia. 
- En ese sentido podríamos concluir que en general hay una correspondencia moderada-fuerte entre la incidencia del covid y la afluencia de público a lugares de comercio_ocio, estaciones y lugares de trabajo inversamente proporcional y una relación directa con las zonas residenciales.
- No pasa así con los supermercados_farmacias y parques cuya afluencia de público parece ser independiente del número de hospitalizaciones.
- En los primeros, la tendencia es a la normalización con la baseline. En los segundos tienen una tendencia alcista. Si bien, en las zonas de trabajo la afluencia de público parece constante y menor a la baseline sin vistas de movimiento. Algo parecido pasa con las zonas de comercio_ocio que aún al final no han recuperado su afluencia.
- En general este comportamiento se corresponde con lo anteriormente citado, si bien se ve relajado con el tiempo.
- Esta correlación moderada-fuerte se da con 10 días de antelación. Es decir, la correspondencia se da entre los datos de afluencia de 10 días anteriores con respecto al número de hospitalizados.

