

# Paso a producción: base de datos

En este punto tu aplicación está conectada a una base de datos local que es accedida a través del método `connect()`de Mongoose y el string de conexión `mongodb://localhost/yourdatabase`. Esto es apto para un entorno local de desarrollo, pero no sería posible accederla desde un entorno de producción ya que, valga la redundancia, es *local*. Tu equipo no cumple ninguno de los requisitos de accesibilidad, capacidad o concurrencia de un servidor, [entre otros](https://preview.my.ironhack.com/lms/courses/course-v1:IRONHACK+WDFT+202008_MAD/units/ironhack-course-chapter_3-sequential_1-vertical#Introduction-to-Databases). 

Realizaremos aquí las operaciones necesarias para transferir tu base de datos a un servidor de producción contra el que trabajarás en adelante, exportando las colecciones en tu equipo e importándolas en MongoDB Atlas.

## Exportación de base de datos local

MongoDB permite exportar colecciones de una BBDD local como archivos JSON que después pueden importarse en la BBDD remota. 

1. Accede mediante la terminal al directorio donde deseas crear los archivos JSON de tus colecciones.
2. Haz uso del comando `mongoexport` de MongoDB para exportarte la primera colección, siguiendo esta sintaxis:

   `mongoexport --collection=<collection> --db=<database> --out=<file>`
    
    - Sustituye &lt;collection> por el nombre de la colección
    - Sustituye &lt;database> por el nombre de la base de datos
    - Sustituye &lt;file> por el nombre del archivo de salida.

   Ejemplo:
 
     `mongoexport --collection=students --db=school --out=students-collection.json`

3. Comprueba cómo se ha creado el archivo con los datos y repite el proceso para colección, cambiando el nombre de la colección y el nombre del archivo en cada una.



## Importación de base de datos remota

MongoDB Atlas permite alojar y gestionar bases de datos en sus servidores a través del string de conexión obtenido tras el registro.

1. Abre Mongo Compass y en el menú superior selecciona *Connect => Connect to...*
2. Pega tu string de conexión de MongoDB Atlas y selecciona Connect. Estarás visualizando asi tu Cluster donde a continuación importaremos tus datos. 
3. Accede mediante la terminal al directorio donde se encuentran los archivos JSON de tus colecciones.
4. Haz uso del comando `mongoimport` de MongoDB para importarte la primera colección, siguiendo esta sintaxis:

   `mongoimport --uri="<connectionstring>" --collection=<collection> --out=<file>`
    
    - Sustituye &lt;connectionstring> por el string de conexión de MongoDB Atlas 
    - Sustituye &lt;collection> por el nombre de la colección que se creará
    - Sustituye &lt;file> por el nombre del archivo donde se encuentran los datos de la colección

   Ejemplo:
 
     `mongoimport --uri="mongodb+srv://your_user:your_pwd.ooyyy.mongodb.net/school" --collection=students --out=students-collection.json`
     
     Si ya habías importado antes esta colección, incluye el flag `--drop` para vaciarla previo a re-importarla y evitar que se acumulen los registros.

5. En Mongo Compass, actualiza la vista y comprueba que se ha creado tanto tu colección como los documentos que la conforman.
6. Repite el proceso para cada colección, cambiando el nombre de la colección y el nombre del archivo en cada comando.


## Conexión de la API local con la base de datos remota

Despídete de tu base de datos local porque en adelante trabajarás contra la base de datos remota, tal y como hacías con la base de datos local. Todas las operaciones pueden realizarse de igual manera en una y otra, así como ambas pueden ser gestionadas a través de Mongo Compass como ya has visto.

1. Accede al archivo `.env` de tu aplicación de Express, y crea la variable de entorno `DB_REMOTE` con el string de conexión de MongoDB Atlas como valor. 

    `DB_REMOTE=mongodb+srv://your_user:your_pwd.ooyyy.mongodb.net/school`

2. Modifica el método `connect()` de tu aplicación, tomando como valor de conexión esta variable de entorno:

    ````javascript
    mongoose
       .connect(process.env.DB_REMOTE, ...
    ````

3. Reinicia el servidor y comprueba cómo sigue funcionando con normalidad, ahora contra MongoDB Atlas.
