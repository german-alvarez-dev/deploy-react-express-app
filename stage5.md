

# Paso a producción: cliente

Transferir tu aplicación de React a producción supone compilarla para desplegar los archivos que la componen a un servidor externo, permitiendo así que las peticiones que ahora se emiten desde `http://localhost:3000` pasen a realizarse desde `https://myclient.herokuapp.com`.

## Variable de entorno remoto

Debido a que las peticiones que se realizan desde tus servicios deben ir dirigidas hacia `http://localhost:6000/api` cuando se encuentre en el entorno local, y hacia  `https://myserver.herokuapp.com/api` en un entorno remoto, es necesario crear las variables de entorno en ambos contextos.
 
1. Accede mediante la terminal al directorio raíz de tu cliente y declara una variable de entorno remoto en tu aplicación de Heroku:

       heroku config:set REACT_APP_API_URL="https://yourserver.herokuapp.com/api"

   Es importante que su nombre comience con `REACT_APP_`, de lo contrario create-react-app no la reconocerá en el siguiente paso. 
   
2.  Modifica **todos** tus servicios de Axios que ahora apuntan a `http://localhost:5000/api` para que, una vez subido el cliente a la aplicación de Heroku, tomen como `baseURL` el valor de la variable de entorno remoto que acabas de crear. 

        `baseURL: env.process.REACT_APP_API_URL

## Variable de entorno local

Tu aplicación local ha dejado de funcionar. El paquete create-react-app no dispone de una dependencia como `dotenv` que propague las variables de entorno local, pero manipulando el script de inicio de su `package.json`podemos alcanzar el mismo objetivo:

    "start": "REACT_APP_API_URL=http://localhost:5000/api react-scripts start",  

De esta forma `env.dev.REACT_APP_API_URL` tomará dos valores: el del script en un entorno local, y el de Heroku en el entorno remoto. Tendremos pues el cliente funcionando de manera paralela en ambos entornos.

## Paso a producción

Transferir los archivos a la aplicación de Heroku permitirá acceder tu cliente de React desde cualquier navegador, a la vez que mantendrá todas sus funcionalidades en el entorno local, donde puedes seguir desarrollando.

1. Accede mediante la terminal a la raíz de tu cliente, donde se encuentra el archivo `package.json`
2. Agrega los cambios y realiza un primer commit:
       git add .
       git commit -m "first client deploy on heroku app"  
       git push heroku master
3. Procede a la subida mediante el comando `git push heroku master`
4. Una vez finalizado, comprueba la ausencia de errores en los logs mediante el comando `heroku logs --tail`
5. Abre tu aplicación en el navegador mediante `heroku open`, o tecleando la URL de la misma. Podrás navegar a través de ella como lo haces en en entorno local.

## Interfaz de usuario de Heroku

Puedes acceder a [tu cuenta de Heroku](https://dashboard.heroku.com/apps) mediante el navegador para comprobar detalles de tus aplicaciones: commits (pestaña *Activity*), variables de entorno (pestaña *Settings*), o incluso trabajar con la consola de Heroku en la esquina superior derecha *More => Console*.
