
# Registro y creación de aplicaciones para cliente y servidor en Heroku

El objetivo del deploy es disponer de dos aplicaciones independientes para el cliente y el servidor que conectaremos de la siguiente forma:

- Tu cliente de React se alojará en `https://myclient.herokuapp.com/` emitiendo las peticiones que procedan para consumir tu API.
- Tu API de Express responderá desde `https://myserver.herokuapp.com/`a cada petición con el JSON que proceda.

Heroku ofrece un servicio gratuito de alojamiento para aplicaciones basadas en NodeJS, pudiendo desplegar a sus servidores los archivos tanto de tu cliente como de tu servidor, obteniendo así una URL para cada uno que permitirá accederlos.

Tú elegirás qué nombre deseas para tus aplicaciones, pero en adelante usaremos para esta documentación las URLs `https://myclient.herokuapp.com/`y `https://myserver.herokuapp.com/` como ejemplo de cliente y  servidor, respectivamente. 

## Registro 
Accede a [Heroku](https://www.heroku.com/) y realiza el proceso de registro con los datos personales.

Todos los demás pasos los realizaremos desde la terminal, por lo que no es necesario continuar ningún proceso en la página web.

## Instalación de Heroku CLI
Para hacer uso de los comandos de Heroku en un dispositivo, es necesario realizar la instalación de la Interfaz de Línea de Comandos (CLI) de Heroku, accediendo a [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) y siguiendo las instrucciones de instalación. 
Esto habilitará el uso de [todos los comandos de Heroku](https://devcenter.heroku.com/articles/heroku-cli-commands) en nuestra terminal.

## Inicio de sesión Heroku CLI
Para identificarnos en Heroku CLI acceder a nuestra cuenta desde la terminal, usaremos el comando `heroku login` y siguiendo los pasos. 

Podremos cerrar la sesión cuando necesitemos mediante el comando `heroku logout`.

## Creación de aplicación cliente en Heroku

Alojaremos nuestro cliente de `create-react-app` en una aplicación de Heroku. Para ello debemos crearla mediante el comando `heroku create <appname>`. Ejemplo:

    heroku create myclient

Elige un buen nombre en este punto, ya que este será el que Heroku incluya en la URL pública con la que se podrá acceder a tu aplicación desde cualquier navegador. Es por ello que, según el anterior ejemplo, la URL final de tu producto sería:

    https://myclient.herokuapp.com/

Una vez que hayas procedido, podrás acceder a esa URL. Recuerda que el número máximo de aplicaciones que podrás crear en una cuenta de Heroku sin indicar los datos de tu tarjeta de crédito es de 5 aplicaciones.

## Creación de aplicación servidor en Heroku

Usaremos de nuevo el comando `create` para crear nuestra aplicación donde alojaremos tu API de Express: 

    heroku create myserver
