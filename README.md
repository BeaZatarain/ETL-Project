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

1. Explorar que información contiene cada CSV entregado por el cliente de cara a, posteriormente, facilitarnos las futuras relaciones que se crearán en el momento de crear la base de datos. 

2. Limpieza de información que no aportaba valor a la base de datos (columnas constantes, duplicados, nulos...)

Finalmente, tras todo este proceso, hemos importado los CSVs a Mysql para crear la base de datos. Cabe remarcar que, tras este proceso:

 - El CSV de old_HDD, ha sido dividido en dos "tablas puente". Por un lado, old_HDD1.csv con el fin de ser tabla intermedia entre films y actors y por otro, old_HDD2.csv, que relacionado con la tabla de films, nos proporcionará la informaición necesaria para consultar las categorías de todas las películas. 

 - El CSV de category, no ha sido importado ya que tras el proceso de limpieza en Python, la información que contenía se ha incluido en old_HDD2.csv como tabla puente de conexión.
 
 En definitiva, los CSVs que se han importado son los siguientes:
 
 ![imports](https://github.com/BeaZatarain/Data-Base-Project/blob/main/images/csvsimport.png)
 

## Creación de la Base de Datos 'Vidieoclub'


Una vez finalizado el proceso de exploración y limpieza de los datos recopilados y transformados, se ha llevado a cabo un proceso de análisis para establecer las relaciones entre las tablas de la nueva base de datos. 

También, se ha analizado cuidadosamente, el tipo de dato que contiene cada columna de las identidades de la base de datos para evitar errores a la hora de la creación. 

Con ello, el resultado final, se puede apreciar en la siguiente imagen:

 ![Relaciones](https://github.com/BeaZatarain/ETL-Project/blob/main/images/relacion.png)



