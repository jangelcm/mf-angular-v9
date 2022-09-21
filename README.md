[![Build Status](https://travis-ci.org/joeldenning/coexisting-angular-microfrontends.svg?branch=master)](https://travis-ci.org/joeldenning/coexisting-angular-microfrontends)

# Coexisting Angular Microfrontends
Demo: https://github.com/jangelcm/mf-angular-v9.git


Este es un kit de inicio/repositorio de ejemplo para trabajar con múltiples microfrontends angulares coexistiendo dentro de una sola página. 
Cada de las aplicaciones angulares fue creada y administrada por Angular CLI.

Utiliza [single-spa](https://single-spa.js.org) para lograr esto, lo que significa que incluso puede agregar React, Vue u otros marcos como
microfrontends adicionales.

Para mapear rutas a aplicaciones, utiliza [single-spa-layout](https://single-spa.github.io/single-spa.js.org/docs/layout-overview/).

## An important note

Este repositorio de github tiene cuatro proyectos, todo en un solo repositorio. Pero cuando haces esto tú mismo, ** querrás tener un repositorio de git por
aplicación angular**. El proyecto del archivo root-html también debe estar en su propio repositorio. Esto es lo que permite que diferentes equipos y desarrolladores estén en
cargo de diferentes microfrontends.

## Local development -- one app at a time
[Tutorial video](https://www.youtube.com/watch?v=vjjcuIxqIzY&list=PLLUD8RtHvsAOhtHnyGx57EYXoaNsxGrTU&index=4)

Con single-spa, se prefiere ejecutar `ng serve` en una sola aplicación de un single-spa a la vez, mientras se usa un
versión de las otras aplicaciones. Esto lo convierte en una experiencia de desarrollador increíble en la que puede iniciar solo uno
microfrontend a la vez, sin siquiera tener que clonar, instalar npm o iniciar todos los demás.

Para probar esto, clone el repositorio y ejecute los siguientes comandos:
```sh
cd app1
npm i
npm start
```

Now go to http://coexisting-angular-microfrontends.surge.sh in a browser. Click on the yellowish rectangle at the bottom right. Then click on `app1`. Change the module url to http://localhost:4201/main.js. Then apply the override and reload the page. This will have change app1 to load from your localhost instead of from surge.sh. As you modify the code locally, it will
reload the page on coexisting-angular-microfrontends.surge.sh. See https://github.com/joeldenning/import-map-overrides for more info on this.

## Local development -- all at once
It is preferred to only run one app at a time. But if you need to run them all locally, you can do so with the following instructions

```sh
# First terminal tab
cd root-html-file
npm install
npm start
```
```sh
# Second terminal tab
cd app1
npm install
npm start
```

```sh
# Third terminal tab
cd app2
npm install
npm start
```

```sh
# Fourth terminal tab
cd navbar
npm install
npm start
```

Now go to http://localhost:4200 in a browser. Note that you can change any of the ports for the projects by modifying the Import Map inside of
root-html-file/index.html.

If you get serious about deploying your code, you'll want to make it no longer necessary to boot up all of the apps in order to do anything.
When you get to that point, check out [import-map-overrides](https://github.com/joeldenning/import-map-overrides/), which lets you go to
a deployed environment and override the [Import Map](https://github.com/WICG/import-maps) for just one microfrontend at a time. The
import-map-overrides library is already loaded in the index.html of root-html-file, so you can start using it immediately. You can make your
deployed environment overridable, just like you can do overrides on http://coexisting-angular-microfrontends.surge.sh

## More documentation
Go to https://github.com/CanopyTax/single-spa-angular to learn how all of this works.
