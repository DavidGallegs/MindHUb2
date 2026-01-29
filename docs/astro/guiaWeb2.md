# WEB ASTRO

## UNIDAD 3

### COMPONENTES

Los componentes estarán en la carpeta de `src/components`
**Creamos un componente:**

~~~astro
<!-- src/components/Navigation.astro -->
---
---
<a href="/">Inicio</a>
<a href="/about/">Sobre mi</a>
<a href="/blog/">Blog</a>
~~~

**Llamamos a un componente:**

~~~astro
---
import Navigation from '../components/navigation.astro';
import "../styles/global.css";
const titulo = "Astro"
---
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width" />
        <meta name="generator" content={Astro.generator} />
        <title>{titulo}</title>
    </head>
        <h1>Astro Web Prueba</h1>
        <Navigation/>
    </body>
</html>
~~~

Podemos crear componentes que se usen en otros componentes.
Los componentes pueden recibir variables:

**Componente Hijo:**

~~~astro
---
const { platform, username } = Astro.props;
---
<!-- social.astro -->

<a href={`https://www.${platform}.com/${username}`}>{platform}</a>
~~~

**Componente Padre:**

~~~astro
---
import Social from './social.astro';
---
<!-- footer.astro -->
<footer>
    <Social platform="twitter" username="astrodotbuild" />
    <Social platform="github" username="withastro" />
    <Social platform="youtube" username="astrodotbuild" />
</footer>
~~~

Los componentes pueden estilizarse

~~~astro
---
const { platform, username } = Astro.props;
---
<!-- social.astro -->
<a href={`https://www.${platform}.com/${username}`}>{platform}</a>

<style>
  a {
    padding: 0.5rem 1rem;
    color: white;
    background-color: #4c1d95;
    text-decoration: none;
  }
</style>
~~~

Los componentes se pueden reutilizar.
Es recomendable que los componentes tengan sus style propios
Y en la página principal donde se usen reciban el style del archivo css
Evitando importar para cada compoenente un estilo del archivo css.

### SCRIPTS CON ASTRO

En el propio archivo astro podemos insertar javaScript con la etiqueta `<script>`
Otra forma es con una importación de un archivo js

~~~astro
<body>
      <Footer/>
  <script>import "../scripts/menu.js";</script>
</body>
~~~

~~~js
    const menu = document.querySelector('.menu');

    menu?.addEventListener('click', () => {
    const isExpanded = menu.getAttribute('aria-expanded') === 'true';
    menu.setAttribute('aria-expanded', `${!isExpanded}`);
    });
~~~

## UNIDAD 4

### CONSTRUIR PLANTILLAS

Las plantillas se crean en `src/layouts` y contienen estructuras y componentes
Para poder editar estos layouts tenemos que colocar la etiqueta `<slot/>`
que permite que a partir de esa ubicación, el codigo inyeacto se escriba ahí.

**Layout:**

~~~astro
---
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
import '../styles/global.css';
const pageTitle = "Página de inicio";
---
<html lang="es">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content={Astro.generator} />
    <title>{pageTitle}</title>
  </head>
  <body>
    <Header />
    <h1>{pageTitle}</h1>
    <slot />
    <Footer />
    <script>
      import "../scripts/menu.js";
    </script>
  </body>
</html>
~~~

**Index.astro + Layout:**

~~~astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
const pageTitle = "Página de inicio";
---
<BaseLayout>
  <h2>Mi impresionante subtítulo del blog</h2>
</BaseLayout>
~~~

### PASAR VALORES ESPECÍFICOS

Podemos modificar al layout para recibir parámetros

~~~astro
---
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
import '../styles/global.css';
const { pageTitle } = Astro.props;
---
~~~

~~~astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
const pageTitle = "Página de inicio";
---
<BaseLayout pageTitle={pageTitle}>
  <h2>Mi impresionante subtítulo del blog</h2>
</BaseLayout>
~~~

### CREAR Y PASAR DATOS DE UNA PLANTILLA DE BLOG PERSONALIZADA

Mirar el recurso de Introducción a YAML y ver que es eso.
