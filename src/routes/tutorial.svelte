<script>
	import CodeBlock from '$lib/components/codeBlock.svelte';
	import { text } from 'svelte/internal';
</script>

<section>
	<h1>Tutorial SvelteKit</h1>

	<p>
		Con este tutorial, vas a aprender a construir una <a
			href="https://desarrolloweb.com/articulos/que-es-una-spa.html"
			class="highlight"
			target="_blank">Web SPA</a
		>
		utilizando
		<a href="https://kit.svelte.com" target="_blank" class="highlight">SvelteKit</a>, el framework
		que está ganando cada vez más popularidad por su facilidad de uso y aprendizaje, y todas sus
		prestaciones.
	</p>

	<p>
		También, podrás publicar tu proyecto SvelteKit (y también de React/Next/Vue/Nuxt) al servicio de
		hosting gratuito de
		<a href="https://vercel.app" class="highlight" target="_blank">Vercel</a> , directamente desde GitHub.
	</p>

	<p>
		Podés descargar el proyecto desde
		<a href="https://github.com/ucielsola/sveltekit-tutorial" class="highlight" target="_blank"
			>GitHub</a
		> y seguir esta misma guía desde el README del repositorio.
	</p>
</section>

<section>
	<h2>Configuración Inicial</h2>

	<p>
		Para poder seguir paso a paso este tutorial, vas a necesitar tener instalado Node y NPM (su
		gestor de paquetes). <a
			href="https://desarrolloweb.com/articulos/instalar-node-js.html"
			class="highlight"
			target="_blank">Acá podés aprender a hacerlo.</a
		>
	</p>
	<p>
		Una vez que tengamos Node y NPM instalados en nuestro sistema, podemos visitar la <a
			href="https://kit.svelte.com"
			class="highlight"
			target="_blank">web oficial de SvelteKit</a
		> para leer la documentación (es excelente) y copiar los comandos necesarios para su instalación.
	</p>

	<p>Abrimos la terminal de comandos de nuestro sistema, y escribimos lo siguiente:</p>
	<CodeBlock
		text="
    npm init svelte@next &lt;nombre-del-proyecto&gt;
    cd &lt;nombre-del-proyecto&gt;
    npm install
    npm run dev"
	/>
	<h3>¿Qué hacen estos comandos?</h3>
	<ol class="indent-1">
		<li>
			Inicia un proyecto de SvelteKit y le asigna el nombre que le pasemos. Luego pregunta:
			<ol type="a" class="indent-2">
				<li>si queremos iniciar un Demo o un proyecto en blanco (yo elegí esta opción)</li>
				<li>si queremos usar TypeScript (yo elegí que no)</li>
				<li>si queremos usar ESLint (yo elegí que sí)</li>
				<li>si queremos usar Prettier (yo elegí que sí)</li>
				<li>si queremos usar Playwright (yo elegí que no)</li>
			</ol>
		</li>
		<li>
			Posiciona el directorio de trabajo de la terminal en la carpeta creada por el comando anterior
		</li>
		<li>Instala las dependencias necesarias para utilizar SvelteKit</li>
		<li>
			Lanza un servidor local, normalmente en la dirección http://localhost:3000. Acá podemos ver en
			vivo los cambios que vamos haciendo en nuestro código.
		</li>
	</ol>
</section>

<section>
	<h2>Estructura de un Proyecto SvelteKit</h2>
	<p>
		La estructura de SvelteKit es a la vez muy sencilla y muy poderosa. Lo más importante, por el
		momento, es comprender que contamos con un sistema
		<a
			href="https://lemoncode.net/lemoncode-blog/2018/5/13/server-side-rendering-i-conceptos"
			class="highlight"
			target="_blank">Server-Side-Rendering</a
		>
		con
		<a
			href="https://codigofacilito.com/articulos/router-client-spa"
			class="highlight"
			target="_blank">Client-Side-Routing</a
		>.
	</p>

	<p>
		Adentro de la carpeta <span class="highlight">src</span>, vamos a encontrar la carpeta
		<span class="highlight">routes</span>, donde podemos ubicar todas las rutas de nuestra web/app (
		Inicio | Acerca de | Galería | Portfolio ). SvelteKit se encarga de organizar y configurar el
		ruteo automáticamente, y sólo basta con que nosotros creemos los archivos
		<span class="highligh">.svelte</span> con el nombre de cada ruta adentro de esta carpeta.
	</p>

	<img src="/images/routes.png" alt="Screenshot Routes" class="center" />

	<p>
		Además de las rutas, es conveniente que creemos una carpeta llamada <span class="highlight"
			>lib</span
		>, donde podemos guardar componentes y otras utilidades para nuestra web/app. Normalmente, suelo
		crear la siguiente estructura: <br />
		lib > components > componente1.svelte, componente2.svelte, componente3.svelte
	</p>

	<img src="/images/lib.png" alt="Screenshot Lib folder" class="center" />

	<p>
		SvelteKit nos brinda una herramienta súper útil, llamada <span class="highlight">layout</span>.
		Creando un archivo llamado
		<span class="highlight">__layout.svelte</span> (dos guiones bajos antes de "layout") podemos
		crear una estructura general para "rodear" a nuestras páginas. Por ejemplo, si queremos que el
		header y el footer de nuestra web se mantenga estático al cambiar de página, tenemos que
		ubicarlo adentro del layout, que se encargará de montar y desmontar las páginas de nuestra web
		en el espacio que asignemos usando la etiqueta <span class="highlight">&lt;slot/&gt;</span>
	</p>

	<img src="/images/layout.png" alt="Screenshot Layout" class="center" />

	<p>
		Finalmente, tenemos la carpeta <span class="highlight">static</span> (hermana de
		<span class="highlight">src</span>). Acá podemos guardar todos los recursos estáticos, para
		facilitar el acceso a ellos desde cualquier ruta y componente:
	</p>
	<CodeBlock
		text="
    <img src='/images/screenshot_static.png' alt'Screenshot carpeta Static'>
    <img src='/images/screenshot_lib.png' alt'Screenshot carpeta Lib'>
    "
	/>
</section>

<section>
	<h2>Estructura de un archivo .svelte</h2>
	<p>
		SvelteKit reconocerá los archivos con extensión <span class="highligh">.svelte</span> y los
		tomará como rutas y/o componentes. Cada uno de estos archivos puede alojar codigo
		<span class="highlight">HTML</span>, <span class="highlight">CSS</span>, y
		<span class="highlight">JavaScript/TypeScript</span>. Esto hace que sea extremadamente fácil
		construir web/apps modulares, separando las funcionalidades de cada componente, y también sus
		estilos. Veamos como ejemplo la barra de navegación de este proyecto, que incorpora al
		componente <span class="highlight">NavLink</span>:
	</p>
	<img src="/images/navigation.png" alt="Screenshot Navigation" class="center" />
	<p>
		Acá vemos el componente NavLink, que expone ("export let ...") algunas variables para recibir
		datos desde su componente padre (SiteNavigation), como el texto a mostrar, y la información
		sobre la ruta actual desde el <a
			href="https://kit.svelte.dev/docs/modules#$app-stores"
			class="highlight"
			target="_blank">Store</a
		> (contexto) que brinda SvelteKit.
	</p>
	<img src="/images/link.png" alt="Screenshot link" class="center" />
</section>

<section>
	<h2>Subir repositorio a GitHub</h2>
	<p>
		Para guardar nuestro trabajo y mantener un control seguro sobre las versiones del mismo, lo más
		recomendable es utilizar servicios como GitHub o GitLab, basados en GIT. Hay muchos métodos y
		formas de lograr el mismo objetivo, siendo la más sencilla "arrastrar" el contenido del proyecto
		a un repositorio en GitHub.
	</p>
	<p>Para familiarizarnos con el uso de GIT y la consola, recomiendo hacer unos pasos extra:</p>
	<ol class="indent-1">
		<li>
			Luego de haber completado todo el tutorial hasta acá, o siemplemente después de haber creado
			el proyecto, creamos un repositorio en GitHub.
		</li>
		<li>
			Luego volvemos a nuestra consola y tipeamos los siguientes comandos:
			<ul class="indent-2">
				<li>git init (inicia un repositorio git)</li>
				<li>
					git remote add origin git@github.com:&lt;tu usuario&gt;/&lt;nombre-del-repositorio&gt;
					(conecta el repositorio local con el repositorio remoto en GitHub)
				</li>
				<li>git add . (prepara todos los archivos para ser enviados a github)</li>
				<li>
					git commit -m "first commit" (crea un commit con mensaje "first commit" para identificar
					la subida, se puede cambiar el mensaje)
				</li>
				<li>git push ("empuja" los cambios y los sube a GitHub)</li>
			</ul>
		</li>
	</ol>
	<p>
		Luego de esto, si volvemos a GitHub y abrimos nuestro nuevo repositorio, tendríamos que ver
		subidos todos los archivos. Los comandos "git add .", "git commit -m '..' " y "git push" podemos
		utilizarlos de ahora en adelante para enviar a GitHub los cambios que vayamos haciendo.
	</p>
</section>

<section>
	<h2>Publicar proyecto en Vercel.app</h2>
	<p>
		Desde hace unos años, varias compañias comenzaron a brindar servicios de hosting gratuito para
		proyectos pequeños, que no requieran de un servicio de backend personalizado. Son ideales para
		hostear portfolios, landing pages, SPAs simples, etc. Entre estas compañias están Vercel,
		Netlify, GitHub (GitHub Pages) y Cloudflare (Cloudflare Pages). Cada una tiene sus beneficios y
		particularidades, por lo que es ideal leer las características de los servicios que ofrecen.
	</p>
	<p>
		En este tutorial vamos a utilizar los servicios de Vercel, compañía que incorporó recientemente
		en su equipo a Richard Harris, el creador de Svelte y SvelteKit. Desde esta incorporación, se
		hicieron algunos cambios en SvelteKit para lograr que la integración con Vercel sea automática.
	</p>
	<p>
		Tenemos que crearnos una cuenta en <a
			href="https://vercel.app"
			class="highlight"
			target="_blank">Vercel.app</a
		>, es recomendable hacerlo mediante la cuenta de GitHub, para hacerlo más sencillo aún. Luego,
		cuando ya ingresamos a nuestro dashboard de Vercel, clickeamos en New Project e importamos un
		Repositorio Git. Configuramos un nombre, hacemos click en Deploy, y en apenas unos segundos, ya
		vamos a tener disponible una versión en vivo de nuestro proyecto, hosteado en vercel.
	</p>
	<p>
		Si tenemos un dominio personalizado (.com / .com.ar , etc) es muy sencillo de configurar.
		Abrimos el proyecto en vercel, y vamos a su configuración. Desde ahí buscamos la sección
		"Domains" y podremos agregar nuestro dominio. El siguiente paso será conectar el dominio con los
		servidores DNS de vercel (este paso depende de dónde se haya comprado el dominio, podés
		contactarme si necesitás ayuda.)
	</p>
</section>

<section>
	<p>Eso fue todo, espero que haya sido útil!</p>
</section>

<style>
	.indent-1 {
		padding-inline-start: 1rem;
	}

	.indent-2 {
		padding-inline-start: 1.5rem;
	}

	li {
		font-size: 1rem !important;
	}
</style>
