# Tutorial SvelteKit - Parte 1

Con este tutorial, vas a aprender a construir una [Web SPA](https://desarrolloweb.com/articulos/que-es-una-spa.html) utilizando [SvelteKit](https://kit.svelte.com), el framework que está ganando cada vez más popularidad por su facilidad de uso y aprendizaje, y todas sus prestaciones.
Podés descargar el proyecto desde [GitHub](https://github.com/ucielsola/sveltekit-tutorial) y seguir esta misma guía desde el README del repositorio.

En la **Parte 2** de este tutorial (_próximamente_), podrás publicar tu proyecto SvelteKit (y también de React/Next/Vue/Nuxt) al servicio de hosting gratuito de [Vercel](https://vercel.app), directamente desde GitHub.

## Configuración inicial

Para poder seguir paso a paso este tutorial, vas a necesitar tener instalado Node y NPM (su gestor de paquetes). [Acá podés aprender a hacerlo.](https://desarrolloweb.com/articulos/instalar-node-js.html)

Una vez que tengamos Node y NPM instalados en nuestro sistema, podemos visitar la [web de SvelteKit](https://kit.svelte.com) para leer la documentación (es excelente) y copiar los comandos necesarios para su instalación.

Abrimos la terminal de comandos de nuestro sistema, y escribimos lo siguiente:

    npm init svelte@next <nombre-del-proyecto>
    cd <nombre-del-proyecto>
    npm install
    npm run dev

### ¿Qué hacen estos comandos?

1. Inicia un proyecto de SvelteKit y le asigna el nombre que le pasemos. Luego pregunta:

   a) si queremos iniciar un Demo o un proyecto en blanco (**yo elegí esta opción**)

   b) si queremos usar TypeScript (**yo elegí que no**)

   c) si queremos usar ESLint (**yo elegí que sí**)

   d) si queremos usar Prettier (**yo elegí que sí**)

   d) si queremos usar Playwright (**yo elegí que no**)

2. Posiciona el directorio de trabajo de la terminal en la carpeta creada por el comando anterior
3. Instala las dependencias necesarias para utilizar SvelteKit
4. Lanza un servidor local, normalmente en la dirección [http://localhost:3000](http://localhost:3000). Acá podemos ver en vivo los cambios que vamos haciendo en nuestro código.

## Estructura de un proyecto SvelteKit

La estructura de SvelteKit es a la vez muy **sencilla** y muy **poderosa**. Lo más importante, por el momento, es comprender que contamos con un sistema [Server-Side-Rendering](https://lemoncode.net/lemoncode-blog/2018/5/13/server-side-rendering-i-conceptos) con [Client-Side-Routing](https://codigofacilito.com/articulos/router-client-spa).

Adentro de la carpeta "**src**", vamos a encontrar la carpeta **routes**, donde podemos ubicar todas las rutas de nuestra web/app ( _Inicio | Acerca de | Galería | Portfolio_ ). SvelteKit se encarga de organizar y configurar el ruteo automáticamente, y sólo basta con que nosotros creemos los archivos **.svelte** con el nombre de cada ruta adentro de esta carpeta.

[SCREENSHOT ROUTES]

Además de las rutas, es conveniente que creemos una carpeta llamada **lib**, donde podemos guardar componentes y otras utilidades para nuestra web/app. Normalmente, suelo crear la siguiente estructura: _lib > components > componente1.svelte, componente2.svelte, componente3.svelte_

[SCREENSHOT LIB]

 SvelteKit nos brinda una herramienta súper útil, llamada **layout**. Creando un archivo llamado **\_\_layout.svelte** (dos guiones bajos antes de "layout") podemos crear una estructura general para "rodear" a nuestras páginas. Por ejemplo, si queremos que el **header** y el **footer** de nuestra web se mantenga estático al cambiar de página, tenemos que ubicarlo adentro del **layout**, que se encargará de montar y desmontar las páginas de nuestra web en el espacio que asignemos usando la etiqueta **&lt;slot/&gt;**

[SCREENSHOT LAYOUT]

Finalmente, tenemos la carpeta **static** (hermana de **src**). Acá podemos guardar todos los recursos estáticos, para facilitar el acceso a ellos desde cualquier ruta y componente:

    <img src="/images/screenshot_static.png" alt"Screenshot carpeta Static">
    
    <style>
    @font-face {
        font-family: 'Nunito Sans';
        font-style: normal;
        font-weight: 400;
        src: local('Nunito Sans'),
        url('/fonts/nunito-sans-v11-latin-regular.woff2') format ('woff2'),
        url('/fonts/nunito-sans-v11-latin-regular.woff') format  ('woff');
    }
    </style>

[SCREENSHOT STATIC]


## Estructura de un archivo .svelte

SvelteKit reconocerá los archivos con extensión **.svelte** y los tomará como rutas y/o componentes. Cada uno de estos archivos puede alojar codigo **HTML**, **CSS**, y **JavaScript/TypeScript**. Esto hace que sea extremadamente fácil construir web/apps modulares, separando las funcionalidades de cada componente, y también sus estilos. Veamos como ejemplo la barra de navegación de este proyecto, que incorpora al componente **NavLink**:

[SCREENSHOT NAVBAR]

Y el componente NavLink, que exporta algunas variables para recibir datos desde su componente padre (**SiteNavigation**), e importa la información sobre la ruta actual desde el **Store** (contexto) que brinda **SvelteKit**.


