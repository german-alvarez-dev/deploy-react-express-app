
# Registro y configuración base en MongoDB Atlas + Heroku

Proceso de resgistro en Heroku y MongoDB Atlas y configuración base para desplegar a producción.

## MongoDB Atlas

Este servicio permitirá alojar la base de datos en remoto, pudiendo conectarte a ella a través de un string de conexión que sustituirá a tu actual `mongodb://localhost/db_local`

### Registro y configuración de Cluster

- Acceder a [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) y comenzar el proceso de registro con los datos personales.
- En la siguiente pantalla, seleccionar *Skip*: 
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601658684/Captura_de_pantalla_2020-10-02_a_las_19.09.26.png)
- En la siguiente pantalla, seleccionar *Shared Cluster* (compartido y gratuito):
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601658764/Captura_de_pantalla_2020-10-02_a_las_19.12.07.png)
- En la siguiente pantalla, mantener AWS y seleccionar un servidor europeo. Seleccionar *Create Cluster*:
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601659031/Captura_de_pantalla_2020-10-02_a_las_19.17.01.png)
- Una vez creado el Cluster, seleccionar *Connect*.

### Obtención del string de conexión

- En la sección *Add a connection IP address* de la ventana modal, seleccionar  *Allow Access from Anywhere*. 
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601659526/Captura_de_pantalla_2020-10-02_a_las_19.22.34.png)
  Veremos que el campo *IP Address* toma el valor `0.0.0.0/0` permitiendo asi el acceso a la base de datos desde cualquier IP.  
![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601659536/Captura_de_pantalla_2020-10-02_a_las_19.25.28.png)
  Seleccionar *Add IP Address.*
- En la sección *Create a database user* de la ventana modal, rellenar el nombre de usuario para acceder a la base de datos y una contraseña. Seleccionar *Create database user*:
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601659726/Captura_de_pantalla_2020-10-02_a_las_19.27.33.png) 
- A continuación, seleccionar *Choose a connection method*.
- Entre los métodos de conexión, seleccionar *Connect using MongoDB Compass*:
  ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601659855/Captura_de_pantalla_2020-10-02_a_las_19.30.13.png)
- Copiar el string de conexión y modificarlo de la siguiente forma:
    - Sustituir `<password>` por la contraseña de conexión.
    - Sustituir `/test` por el nombre deseado para la base de datos.
 ![x](https://res.cloudinary.com/ironhack-german/image/upload/v1601660110/Captura_de_pantalla_2020-10-02_a_las_19.31.39.png)
