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


### DATASETS Y FUENTES ALTERNATIVAS DE DATOS

*df_google* es un dataset publicado por Google que se puede descargar del siguiente enlace: [www.google.com/covid19/mobility/data_documentation](https://www.google.com/covid19/mobility/data_documentation.html?hl=es) <br>
*df_covd19* es un dataset publicado por el [Instituto de Salud Carlos III (ISCIII)](https://www.isciii.es) y que puede encontrar en el siguiente enlace: [casos_hosp_uci_def_sexo_edad_provres.csv](https://cnecovid.isciii.es/covid19/resources/casos_hosp_uci_def_sexo_edad_provres.csv)

-  Tras cargar *df_google* prescindimos de las columnas *metro_area y census_fips_code* ya que no aportan información. <br> 
    Posteriormente rellenamos la columna *sub_region_1* por faltar nombres de las provincias de las comunidades con una sola provincia. Comprobamos que están todas las provincias. <br>
    Creamos una nueva columna a partir de *sub_region_1*, *provincia_id_g* para cruzarla con la otra tabla.

- En *df_covid19* encontramos que hay datos que no están asociados a provincias concretas, prescindimos de ellos ya que queremos solo los datos asociados a una provincia.

Una vez que tenemos los dos dataset preparados que vamos a usar en este EDA toca unirlos, para ello se hace un *merge* de df_google sobre df_covid19 por las columnas fecha y provincia. Columnas estas previamente armonizadas. 

### LIMPIEZA

- Borramos la columna *Unnamed: 0*.
- Recortamos el dataframe por las primeras fechas ya que no hay datos de google antes del 15-02-2020. 
- Tratamos varios nulos en las columnas de las provincias que tiene como resultado prescindir de los datos sobre Ceuta y Melilla. 
- Además observamos una serie de nulos que corresponden a situaciónes en las que google ha considerado que no tenían sufiente calidad los datos que había recogido. <br>
    Son casos puntuales, por lo que los rellenamos con la media de los valores del día anterior y posterior.
- Dropeamos entonces las columnas *['date', 'provincia_iso_g', 'country_region_code', 'iso_3166_2_code']*.
- Renombramos y reordenamos las columnas.

Y ya tenemos el dataset limpio y listo para el estudio.

### ESTUDIO

- Cambio de las fechas a *type datetime*.

Comienzo del Análisis univariante:
- Contrucción de la tabla resumen de análisis de los datos de las diferentes columnas con *nombre, type, prio, card, card%, class y mode*.
- Gráficas sobre la distribución de los datos. Primero las Categóricas y luego las numéricas.

Creamos nuevos subdataframes, agrupando por *fechas* y por *fechas y provincias*. Trabajaremos principalmente con la agrupación por *fechas*. 
- Primero volvemos hacer el análizar el análisis univariante de las columnas numéricas.

Aquí comienza el análisis bivariante:
- Lo primero es hacer un análisis de los datos de la incidencia del covid en función del tiempo. Además suavizamos la curva para asumir fallas semanales en la recogida de datos. Ventana de 7 días. Usamos gráfica de líneas.
- Realizamos diferentes gráficas para comprar las diferentes métricas de incidencia. Usaremos *num_casos* y *num_hosp* para lo siguiente.
- Seguimos con un análsis temporal de los datos de afluencia de gente. También suavizamos con ventana de 7 días. Le superponemos la línea de *num_casos* para ver posibles correlaciones. Usamos gráfica de líneas.
- Comparamos ahora directamente mediante mapas de calor cada una de las categorías de lugares de Google, primero con *num_casos*, y luego con también con el resto de métricas de incidencia. 
- Así mismo hacemos una comparación de los mapas de calor anteriores con otro con un desfase de 15 días atendiendo al periodo de desactivación del contagio del covid.
- Se observa, 
    - primero que podría existir cierta correspondencia entre las métricas, 
    - segundo se duda de la fiabildad de *num_casos*, 
    - tercero parece haber más corresondencia con el desfase de 15 días.
- Para tratar de aclarar esto buscamos una representación algo más clarificadora, y hacemos lo mismo con diagramas de puntos. Y nos aclaran dos cosas: <br>
    - *num_casos* no es un buen dato ya que no parece reflejar bien la intensidad real de la epidemia por la imposibilidad de registrar todos los casos. Optamos por trabajar con *num_hosp*. <br>
    - se confirma la correspondencia con el desfase.
- Volvemos a hacer la comparación temporal de cada categoría de lugar esta vez con *num_hosp* y el análisis visual muestra mayor correspondencia.
- Para terminar comprobamos la correlación de Pearson entre las columnas que no sale nada llamativo. Pero al hacer la correlación cruzada observamos correlaciones de en torno a 0.7 en la mayoría de ellas a 10 días. 

###  CONCLUSIONES

- El mejor indicador epidemiológico parece ser el número de hospitalizaciones.
- No podemos afirmar a ciencia cierta que haya causalidad, pero sí podemos hablar de correspondencia. 
- En ese sentido podríamos concluir que en general hay una correspondencia moderada-fuerte entre la incidencia del covid y la afluencia de público a lugares de comercio_ocio, estaciones y lugares de trabajo inversamente proporcional y una relación directa con las zonas residenciales.
- No pasa así con los supermercados_farmacias y parques cuya afluencia de público parece ser independiente del número de hospitalizaciones.
- En los primeros, la tendencia es a la normalización con la baseline. En los segundos tienen una tendencia alcista. Si bien, en las zonas de trabajo la afluencia de público parece constante y menor a la baseline sin vistas de movimiento. Algo parecido pasa con las zonas de comercio_ocio que aún al final no han recuperado su afluencia.
- En general este comportamiento se corresponde con lo anteriormente citado, si bien se ve relajado con el tiempo.
- Esta correlación moderada-fuerte se da con 10 días de antelación. Es decir, la correspondencia se da entre los datos de afluencia de 10 días anteriores con respecto al número de hospitalizados.

