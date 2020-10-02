# Deploy a Heroku

## Objeto del documento

Describir el proceso para deplegar a producción en [Heroku](https://www.heroku.com/) + [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) una SPA con cliente [`create-react-app`](https://create-react-app.dev/docs/getting-started/) y servidor [ExpressJS](https://expressjs.com/).

## Especificaciones

El deploy se realizará en base a los siguientes objetivos:

- Disponer de los entornos de desarrollo y producción **activos de forma paralela**.
- Consumir la base de datos desde MongoDB Atlas.
- Disponer del cliente y servidor alojados en dos aplicaciones independientes de Heroku.


## Fases de paso a producción

1. [Registro y configuración base en MongoDB Atlas](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage1.md)
2. [Registro y creación de aplicaciones para cliente y servidor en Heroku](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage2.md)
3. [Paso a producción: base de datos](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage3.md)
4. [Paso a producción: servidor](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage4.md)
5. Paso a producción: cliente
