# Tutorial SvelteKit 

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

Acá vemos el componente NavLink, que expone (_export let ..._) algunas variables para recibir datos desde su componente padre (**SiteNavigation**), como el texto a mostrar, y la información sobre la ruta actual desde el **Store** (contexto) que brinda **SvelteKit**.

[SCREENSHOT NavLINK]

## Subir repositorio a GitHub

Para guardar nuestro trabajo y mantener un control seguro sobre las versiones del mismo, lo más recomendable es utilizar servicios como GitHub o GitLab, basados en GIT. Hay muchos métodos y formas de lograr el mismo objetivo, siendo la más sencilla "arrastrar" el contenido del proyecto a un repositorio en GitHub.

Para familiarizarnos con el uso de GIT y la consola, recomiendo hacer unos pasos extra:

1. Luego de haber completado todo el tutorial hasta acá, o siemplemente después de haber creado el proyecto, creamos un repositorio en GitHub.
2. Luego volvemos a nuestra consola y tipeamos los siguientes comandos:
   - git init (inicia un repositorio git)
   - git remote add origin git@github.com:&lt;tu usuario&gt;/&lt;nombre-del-repositorio&gt; (conecta el repositorio local con el repositorio remoto en GitHub)
   - git add . (prepara todos los archivos para ser enviados a github)
   - git commit -m "first commit" (crea un commit con mensaje "first commit" para identificar la subida, se puede cambiar el mensaje)
   - git push ("empuja" los cambios y los sube a GitHub)

Luego de esto, si volvemos a GitHub y abrimos nuestro nuevo repositorio, tendríamos que ver subidos todos los archivos. Los comandos "git add .", "git commit -m '..' " y "git push" podemos utilizarlos de ahora en adelante para enviar a GitHub los cambios que vayamos haciendo.

## Publicar proyecto en Vercel.app

Desde hace unos años, varias compañias comenzaron a brindar servicios de hosting gratuito para proyectos pequeños, que no requieran de un servicio de backend personalizado. Son ideales para hostear portfolios, landing pages, SPAs simples, etc. 
Entre estas compañias están Vercel, Netlify, GitHub (GitHub Pages) y Cloudflare (Cloudflare Pages).
Cada una tiene sus beneficios y particularidades, por lo que es ideal leer las características de los servicios que ofrecen.

En este tutorial vamos a utilizar los servicios de Vercel, compañía que incorporó recientemente en su equipo a Richard Harris, el creador de Svelte y SvelteKit. Desde esta incorporación, se hicieron algunos cambios en SvelteKit para lograr que la integración con Vercel sea automática.

Tenemos que crearnos una cuenta en [Vercel.app](https://vercel.app), es recomendable hacerlo mediante la cuenta de GitHub, para hacerlo más sencillo aún. Luego, cuando ya ingresamos a nuestro dashboard de Vercel, clickeamos en New Project e importamos un Repositorio Git. Configuramos un nombre, hacemos click en Deploy, y en apenas unos segundos, ya vamos a tener disponible una versión en vivo de nuestro proyecto, hosteado en vercel. 

Si tenemos un dominio personalizado (.com / .com.ar , etc) es muy sencillo de configurar. Abrimos el proyecto en vercel, y vamos a su configuración. Desde ahí buscamos la sección "Domains" y podremos agregar nuestro dominio. El siguiente paso será conectar el dominio con los servidores DNS de vercel (este paso depende de dónde se haya comprado el dominio, podés contactarme si necesitás ayuda.)

Eso fue todo, espero que haya sido útil!


