
# Registro y creación de aplicaciones para cliente y servidor en Heroku

El objetivo final que perseguimos con el proceso de pasar a producción (despliegue, _deploy_, etc) es disponer de dos aplicaciones independientes para el cliente y el servidor que conectaremos de la siguiente forma:

- Tu cliente de React se alojará en `https://myclient.herokuapp.com/` emitiendo las peticiones que procedan para consumir tu API.
- Tu API de Express responderá desde `https://myserver.herokuapp.com/`a cada petición con el JSON que proceda.

Heroku ofrece un servicio gratuito de alojamiento para aplicaciones basadas en NodeJS, pudiendo desplegar a sus servidores los archivos tanto de tu cliente como de tu servidor y obteniendo así una URL para cada uno que permitirá accederlos.

## Elige los nombres de tus aplicaciones 

Tú elegirás qué nombre deseas para tus aplicaciones, aunque en adelante usaremos para esta documentación las URLs `https://myclient.herokuapp.com/`y `https://myserver.herokuapp.com/` como ejemplo de cliente y servidor, respectivamente. 

Si tu proyecto se llama, por ejemplo, _Donuts Planet_, sería ideal elegir un nombre como `donuts-planet` para la aplicación de cliente y `donuts-planet-api` para la de servidor.

## Registro 
Accede a [Heroku](https://www.heroku.com/) y realiza el proceso de registro con los datos personales.

Todos los demás pasos los realizaremos desde la terminal, por lo que no es necesario continuar ningún proceso en la página web.

## Instalación de Heroku CLI
Para hacer uso de los comandos de Heroku en tu terminal, es necesario realizar la instalación de la Interfaz de Línea de Comandos (CLI) de Heroku, accediendo a [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) y siguiendo las instrucciones de instalación. 
Esto habilitará el uso de [todos los comandos de Heroku](https://devcenter.heroku.com/articles/heroku-cli-commands) en nuestra terminal.

## Inicio de sesión Heroku CLI
Para identificarnos en Heroku CLI y acceder a nuestra cuenta de Heroku desde la terminal, usaremos el comando `heroku login` siguiendo los pasos. 

Podremos cerrar la sesión cuando necesitemos mediante el comando `heroku logout`.

## Creación de aplicación cliente en Heroku

Alojaremos nuestro cliente de React en una aplicación de Heroku. Elige un buen nombre en este punto, ya que este será el que Heroku incluya en la URL pública con la que se podrá acceder a tu aplicación desde cualquier navegador. Es por ello que, si creases una aplicación de nombre `myclient`, la URL final de tu producto sería:

    https://myclient.herokuapp.com/
    
1. Accede mediante la terminal a la raíz de tu aplicación cliente `/client`, donde se encuentra su `package.json`, e introduce el comando `heroku create <appname>`. Ejemplo:

  ````
  heroku create myclient
  ````

2. Ahora enlaza el directorio `/client` en el que te encuentras al Git de la aplicación de Heroku mediante el comando 

  ````
  heroku git:remote -a myclient
  ````

3. Puedes comprobar en cualquier momento la aplicación de Heroku asociada a un Git mediante el comando

  ````
  heroku apps:info
  ````
 
Una vez que hayas procedido, podrás acceder a esa URL. Recuerda que el número máximo de aplicaciones que podrás crear en una cuenta de Heroku sin indicar los datos de tu tarjeta de crédito es de 5 aplicaciones.

## Creación de aplicación servidor en Heroku

Usaremos de nuevo el comando `create` para crear nuestra aplicación donde alojaremos tu API de Express, pero esta vez lo haremos accediendo mediante la terminal al directorio raíz de la aplicación de servidor `/server`, donde se encuentra su `package.json`: 

    heroku create myserver
    heroku git:remote -a myserver

