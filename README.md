# ETL-Project


![cabecera](https://github.com/BeaZatarain/ETL-Project/blob/main/images/cabecera.png)

## Descripción general del proyecto

Este proyecto consiste en  realizar un proceso completo de ETL (extraer información, transformarla y cargarla en una base de datos).Concretamente, el lenguaje de programación que se utilizará será Python y para la creación de la base de datos, MySQL Workbench.

Además, como restricciones este proyecto presenta los dos siguientes requisitos:

 1. Extraer información de, al menos, tres fuentes distintas. 
 2. Utilizar como mínimo dos métodos diferentes de extracción de datos. 
 
Por último, este proyecto, tiene como objetivo recopilar datos de los servicios sociales que se ofrecen en la Comunidad de Madrid e información relacionada para poder realizar futuros análisis como la población por cada código postal y la obtención de todos los códigos postales de la Comunidad de Madrid. 

## 1. Extracción de datos. 

### 1.1 Importación CSV de Base de datos de Registro de Servicios Sociales de la Comunidad de Madrid

**Fuente**: 'https://datos.comunidad.madrid/catalogo/dataset/servicios_sociales_registro_centros'

**Método de extracción**: descarga CSV de la página web oficial.

### 1.2 Scraping codigos postales de la comunidad de Madrid

**Fuente**: 'https://www.worldpostalcodes.org/es/espana/comunidad-autonoma/lista-de-codigos-postales-en-community-of-madrid'

**Método**: scraping utilizando la herramienta **Selenium** de Python.

### 1.3 Población por cada código postal de la Comunidad de Madrid de 2022

**Fuente**: INE = 'https://www.ine.es/jaxiT3/Tabla.htm?t=2881'

**Método**: configuración de la selección de datos (población por cada CP de la Comunidad de Madrid del año 2022, por género y número total de personas)


## **2. Exploración y limpieza de los datos**


Para la limpieza y la exploración de los datos, hemos utilizado Python y concretamente Pandas para llevar a cabo nuestro objetivo. 

Con ello, este proceso ha consistido básicament en: 

1. Unificar en un sólo dataframe tanto la tabla de códigos postales de Madrid, como la tabla de población por código postal al tratarse de dos tablas muy relacionadas. Cabe destacar, que la tabla de población por código postal tenía una estructura inicial que impedía la unificación con la otra tabla por lo que se ha utilizado el método de pivot table antes de hacer merge. 

2. Limpieza de tabla de servicios sociales de Madrid, en la que hemos eliminado ciertas columnas que no aportaban valor a futuros posibles análisis y limpieza de nulos en las columnas de coordenadas (rellenados con 'unknown'). Por último, cabe destacar que en algunas ocasiones el servicio social aparecía con un código postal y dirección 'reservado', por tanto, al no tener otro dato con el que relacionar los datos, se han eliminado dichas filas. 



## **3. Carga de datos a MySQL Workbench**

Una vez finalizado el proceso de exploración y limpieza de los datos recopilados y transformados, se ha llevado a cabo un proceso de análisis para establecer las relaciones entre las tablas de la nueva base de datos. Cabe remarcar que, tras este proceso:

 - Aunque partíamos de tres tablas diferentes, tras la unificación de la tabla de población y la de códigos postales, únicamente se han importado dos tablas. 

 - La relación principal entre las tablas es por el código postal.
 
 
 En definitiva, los CSVs y la relación de nuestra base de datosson los siguientes:
 
 ![relaciones](https://github.com/BeaZatarain/ETL-Project/blob/main/images/relacion.png)
 




