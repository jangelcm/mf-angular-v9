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

Ahora vaya a http://coexisting-angular-microfrontends.surge.sh en un navegador. Haga clic en el rectángulo amarillento en la parte inferior derecha. Luego haga clic en `app1`. Cambie la URL del módulo a http://localhost:4201/main.js. Luego aplique la anulación y vuelva a cargar la página. Esto tendrá el cambio app1 para cargar desde su host local en lugar de surge.sh. A medida que modifica el código localmente, se
Vuelva a cargar la página en coexisting-angular-microfrontends.surge.sh. Consulte https://github.com/joeldenning/import-map-overrides para obtener más información al respecto.

## Local development -- all at once

Es preferible ejecutar solo una aplicación a la vez. Pero si necesita ejecutarlos todos localmente, puede hacerlo con las siguientes instrucciones.

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

Ahora vaya a http://localhost:4200 en un navegador. Tenga en cuenta que puede cambiar cualquiera de los puertos para los proyectos modificando el mapa de importación dentro de
root-html-file/index.html.

If you get serious about deploying your code, you'll want to make it no longer necessary to boot up all of the apps in order to do anything.
When you get to that point, check out [import-map-overrides](https://github.com/joeldenning/import-map-overrides/), which lets you go to
a deployed environment and override the [Import Map](https://github.com/WICG/import-maps) for just one microfrontend at a time. The
import-map-overrides library is already loaded in the index.html of root-html-file, so you can start using it immediately. You can make your
deployed environment overridable, just like you can do overrides on http://coexisting-angular-microfrontends.surge.sh

## More documentation
Go to https://github.com/CanopyTax/single-spa-angular to learn how all of this works.
