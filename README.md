# <h1 align=center>**PROYECTO DATA-ANALYTICS**

# <h1 align=center>**`EDA-POWER BI`**</h1>  

Este proyecto hace énfasis en la resolución de un problema en el campo de Data-Analytics, más específicamente en un análisis de mercado de los denominados MOOCs (Cursos en línea masivos y abiertos). Para ello se pone a disposición una serie de conjuntos de datos que brinda información sobre la situación de mercado de los cursos online. Se hará uso de técnicas para análisis exploratorio de datos (EDA) en Python y métodos de visualización (Dashboards) en Power BI. Adicional a ello, se hace la formulación de (KPIs) que permitan analizar y sacar conclusiones de los datos recolectados.

# <h2> **Objetivos**</h1>
- Realizar labores de Análisis Exploratorio de Datos (EDA)
- Generar visualizaciones y análisis de Datos con la herramienta POWER BI
- Presentación de la información usando estrategias de (Storytelling)

## **Tareas a Ejecutar**

1.Las Tareas de Análisis Exploratorio de datos en este proyecto se pueden resumir en:
- Eliminación de duplicados
- Eliminación de datos atípicos
- Imputación de valores Nulos
- Generación de Nubes de Palabras (Word-Cloud)
- Generar archivos de formato (csv) para su posterior uso en POWER BI
  
2.Las tareas en la generación de métricas y KPIs para el análisis de datos, se pueden resumir en:
- Selección de tipo de visualizaciones para los Datos
- Selección de métricas y KPIs que ayuden al análisis de Datos y den respuesta al problema de negocio
  
3.Formulación de un ,,Storytelling"
- Contextualización del problema y creación de historia alrededor del mismo


## **Archivos del repositorio**
- **`Scripts`**: (EDA.ipynb) Se generó un archivo de análisis Exploratorio por cada conjunto de datos por separado (EDA_udemy, EDA_edx, EDA_cour, EDA_cour_rev). Los últimos son los datos correspondientes a coursera y coursera reviews. Además, hay un script llamado join_coursera que unifica los archivos csv para la plataforma coursera y que fueron producto del análisis exploratorio 

- **`Nubes de Palabras`**: (./.png/) Archivo tipo .png que contienen las nubes de palabras para diferentes campos de texto de interés.

- **`.CSV`**: (./.csv/) Archivos tipo CSV que serán usados para su análisis en POWER BI. Los archvos .csv se encuentran en el siguiente link
https://drive.google.com/drive/folders/16tQO2x5NkRwdz3DhWoq2l3-Gz-MeAQhS

- **`Dashboards`**: (/.pbix) Archivo con el contenido del Dashboard o visualizaciones para el análisis de datos

## `1.EDA (Análisis Exploratorio de Datos)`
Con el archivo EDA.py se realizaron las tareas de análisis exploratorio de datos. Haciendo uso de pandas se realizaron las siguientes tareas: 

+ Eliminación de valores duplicados: Se eliminaron valores duplicados en cada uno de los conjuntos de datos

+ Limpieza de datos: normalización de columnas tipo texto (uso de minúsculas y eliminación de caracteres especiales)

+ Normalización de los campos fecha en los diferentes dataset, dejándolos de la forma year-day-month

+ Imputación de nulos para el conjunto de datos (**`edx`**) en el campo (**`nr_enrolled`**), usando para ello los valores máximos (75%) por (**`subject`**)

+ Para los campos de precio se hace una division en 3 categorias (I**`low-medium-high`**) garantizando un numero equitativo de observaciones por cada categoria

+ Para el para el conjunto de datos (**`edx`**) campo (**`language`**), se decide agrupar los idiomas con observaciones no representativas dentro de una nueva categoria (**`other`**)

+ Imputación de nulos para el conjunto de datos (**`udemy`**) en el campo (**`subscribers`**), usando para ello los valores máximos (75%) por (**`subject`**)

+ Para el conjunto de datos (**`udemy`**) se genera un nuevo campo ventas (**`ventas`**), y un nuevo KPI (**`engage_index`**)

+ Para los campos de texto (course_id,reviews,name ó title)  en cada uno de los conjuntos de datos se genera una nube de palabras usando el siguiente código:

```
text = " ".join(course_id for course_id in df_cour_co.course_id)

stopwords = set(STOPWORDS)

stopwords.update(["basic", "learn", "fundamental", "international", "wharton","fundamentals","introduction","intro","uva darden","uva","darden","principles","foundation","foundations","learning","big","everyday","tools"])

# Generar una imagen de nube de palabras

wordcloud = WordCloud(stopwords=stopwords,max_font_size=80, max_words=100,background_color="white").generate(text)

# Visualizar la imagen generada

plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.show()

#Exportar la imágen a archio .png
wordcloud.to_file("./img_coursera.png")
```

## `2.Selección de KPIs y métricas para el análisis de Datos`

Usando los datos disponibles se formularon KPIs como (**`ventas totales anuales`**) y el (**`engage index/índice de participación`**). Adicionalmente se usaron métricas para analizar el comportamiento del mercado de los cursos on-line como por ejemplo (**`nro subscriptores/nro cursos/nro reviews`**)

## `3.Realización de Dashboard`
El Dashboard y las visualizaciones para análisis de datos se encuentran en el siguiente enlace

-  https://drive.google.com/file/d/1YID7QPIFdjmprdy5YekX3VIiLjqbS5ss/view?usp=share_link

