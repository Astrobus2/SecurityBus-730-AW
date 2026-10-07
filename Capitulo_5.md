## Capítulo V: Product Implementation, Validation & Deployment

### 5.1. Software Configuration Management

#### 5.1.1. Software Development Environment Configuration

Para establecer el entorno de desarrollo del software, se han seleccionado diferentes herramientas, plataformas y guías de trabajo. La siguiente tabla muestra cada recurso utilizado, junto con la finalidad que cumple dentro del proyecto y el medio mediante el cual se puede acceder a este.

| Proceso | Recurso o plataforma | Finalidad | Medio de acceso o Enlace |
|---------|----------------------|-----------|--------------------------|
|Especificación de requisitos|Convenciones Gherkin|Definir condiciones de aceptación y criterios funcionales de manera clara y precisa| [Guía Gherkin](https://cucumber.io/docs/gherkin/)
|Desarrollo Landing Page| Visual Studio Code | Desarrollar, modificar y optimizar el código fuente de la aplicación web|[Visual Studio Code](https://code.visualstudio.com/)|
|Administrador de versiones| Git | Controlar las modificaciones realizadas y administrar las diferentes versiones del proyecto|[Git](https://git-scm.com/)|
|Diseño de experiencia e interfaz| Figma | Elaborar prototipos y organizar visualmente la interfaz de usuario|[Figma](https://figma.com)|
|Publicación y despliegue| Github Pages | Publicar y alojar la página web para permitir su acceso en línea|[Github Pages](https://pages.github.com/)|
|Planificación y gestión del proyecto| Jira Software | Administrar el Product Backlog, planificar los Sprints y realizar el seguimiento de las actividades mediante una metodología ágil|[Jira](https://www.atlassian.com/es/software/jira)|
|Diagramas| PlantUML | Crear representaciones UML relacionadas con la estructura y funcionamiento del sistema|[PlantUML](https://plantuml.com/)|
|Modelado de procesos| UXPressia | Desarrollar herramientas de análisis UX enfocadas en las necesidades y experiencia del usuario|[UXPressia](https://uxpressia.com/)|

#### 5.1.2. Source Code Management

El control del código fuente se realizará mediante GitHub, utilizado como repositorio central para almacenar el proyecto y facilitar el trabajo colaborativo. Además de permitir que los integrantes trabajen sobre una misma base de código, esta plataforma proporciona un historial de las modificaciones realizadas, lo que permite identificar los cambios efectuados durante el desarrollo y mantener su trazabilidad.

Para organizar el proceso de desarrollo, el equipo ha establecido un flujo de trabajo que combina elementos de Git Flow con prácticas de GitHub Flow. Esta organización busca separar adecuadamente el desarrollo de nuevas funcionalidades, la integración de cambios y la gestión de versiones estables, permitiendo que el proyecto pueda incorporar progresivamente nuevas características sin perder el control sobre el código existente.

La estrategia de ramas definida para el proyecto se distribuye de la siguiente manera:

**main:** mantiene la versión estable del sistema que está preparada para ser desplegada.<br>
**develop:** funciona como rama de integración de los avances antes de incorporarlos a la versión estable.<br>
**feature/:** se emplea para desarrollar funcionalidades nuevas o realizar mejoras específicas.<br>
**hotfix/:** se utiliza para solucionar problemas urgentes encontrados en la versión desplegada.

El desarrollo de una nueva funcionalidad comienza creando una rama independiente a partir de develop. Esta forma de trabajo permite que cada modificación sea desarrollada de manera aislada, reduciendo la posibilidad de afectar otras partes del proyecto mientras se encuentra en proceso de implementación.

Una vez que la funcionalidad o corrección ha sido completada, el resultado se incorpora mediante un Pull Request. Antes de realizar la fusión, los demás integrantes pueden revisar los cambios efectuados. De esta manera, la integración no depende únicamente del desarrollador que realizó la modificación, sino que también incorpora una instancia de revisión colaborativa.

**Convención para los commits**

Como complemento al manejo de ramas, se utilizará Conventional Commits para mantener una estructura uniforme en los mensajes de confirmación. Esto permite reconocer rápidamente qué tipo de modificación se realizó y facilita la consulta posterior del historial del proyecto.

Los prefijos considerados son:

| Prefijo | Uso |
|---------|-----|
| **feat** | Incorporación de una nueva funcionalidad. |
| **fix** | Corrección de un error existente. |
| **docs** | Actualización o modificación de documentación. |
| **refactor** | Reorganización o mejora interna del código sin modificar su funcionalidad. |
| **style** | Cambios relacionados con el formato o estilo del código. |
| **test** | Creación o modificación de pruebas. |

**Esquema de versionado**

El proyecto también empleará Semantic Versioning, representado mediante el formato MAJOR.MINOR.PATCH. Este mecanismo permitirá identificar de forma ordenada la evolución de las versiones y diferenciar los cambios realizados según su impacto sobre el sistema.

En conjunto, el uso de GitHub, la estrategia de ramas, los Pull Requests, Conventional Commits y Semantic Versioning proporciona una estructura de trabajo que facilita el control de las modificaciones y la colaboración entre los integrantes. Asimismo, estas prácticas contribuyen a que el código pueda mantenerse y ampliarse de forma organizada durante las siguientes iteraciones del proyecto.

#### 5.1.3. Source Code Style Guide & Conventions
Para evitar diferencias innecesarias en la forma de desarrollar los distintos componentes del sistema, se establecen criterios comunes de programación. Estas reglas serán aplicadas a los lenguajes empleados en el proyecto: HTML, CSS, JavaScript y C#.

Una de las reglas generales consiste en utilizar el inglés para nombrar variables, clases, archivos, comentarios técnicos y elementos de la documentación interna. Con ello se busca mantener una nomenclatura uniforme y facilitar la comprensión del código independientemente del integrante que lo revise o modifique.

Las convenciones adoptadas toman como referencia buenas prácticas provenientes de Google Style Guides, MDN JavaScript, MDN JavaScript Guidelines y Microsoft C# Coding Conventions. También se consideran criterios relacionados con la accesibilidad y la legibilidad del código.

**HTML**

La construcción de la interfaz se realizará mediante HTML5 semántico, buscando que los elementos del documento tengan una organización lógica y que el contenido sea accesible.

Para ello, se tendrán en cuenta las siguientes reglas:

+ Las secciones principales utilizarán etiquetas semánticas como &lt;header&gt;, &lt;nav&gt;, &lt;main&gt;, &lt;section&gt;, &lt;article&gt; y &lt;footer&gt;.
+ Las etiquetas y atributos HTML se escribirán en minúsculas.
+ Todas las etiquetas deberán cerrarse correctamente.
+ Las imágenes incluirán el atributo alt para proporcionar información alternativa y favorecer la accesibilidad.
+ Cuando corresponda, las imágenes definirán sus dimensiones mediante width y height.
+ El documento HTML establecerá lang="en" en la etiqueta &lt;html&gt;.
+ Se incluirán elementos básicos de metadatos, entre ellos &lt;title&gt; y &lt;meta name="descripcion"&gt;.
+ Se evitará incorporar estilos y scripts directamente dentro del HTML cuando no sea necesario.

Ejemplo:
```HTML
<section class="hero-banner">
    <img src="banner.jpg" alt="Main promotional banner" width="1200" height="600">
</section>
```

**CSS**

Los estilos estarán organizados de manera modular, procurando que puedan reutilizarse y mantenerse con facilidad. Para la nomenclatura de las clases se utilizará kebab-case y se aplicará la metodología BEM (Block Element Modifier) para establecer una estructura coherente.

También se seguirán estos criterios:

+ Utilizar nombres de clases descriptivos.
+ Organizar las propiedades CSS siguiendo una secuencia lógica relacionada con el layout, box model, tipografía y apariencia visual.
+ Priorizar unidades relativas como rem, %, vh y vw.
+ No especificar unidades cuando el valor establecido sea cero.
+ Diseñar bajo un enfoque mobile-first para facilitar la adaptación a diferentes tamaños de pantalla.
+ Centralizar las variables reutilizables dentro de :root.

Ejemplo: 

```CSS
:root{ 
--primary-color: #2563eb; 
--secondary-color: #64748b; 
} 
.main-header{ 
    padding: 1rem; 
    background-color: var(--primary-color); 
}
```

**JavaScript**

En el caso de JavaScript, las convenciones estarán orientadas a mantener una estructura clara y facilitar la reutilización y modificación del código.

Se aplicarán las siguientes reglas:

+ Las variables y funciones utilizarán camelCase.
+ Las clases y constructores utilizarán PascalCase.
+ Para declarar variables se emplearán const y let, evitando var.
+ Las funcionalidades se distribuirán en archivos independientes de acuerdo con su responsabilidad.
+ Los eventos se gestionarán mediante addEventListener() en lugar de utilizar eventos directamente en el HTML.
+ Los comentarios se reservarán principalmente para explicar fragmentos cuya lógica sea compleja o poco evidente.
+ Los nombres de las funciones deberán describir la acción que realizan.

Ejemplo:

```JavaScript
const submitButton = document.querySelector("#submit-button"); 
function validateForm(){ 
    return true; 
}
```

**C#**

Para los componentes relacionados con el backend y la lógica de negocio se seguirán las convenciones recomendadas para C# por Microsoft.

Entre los principales criterios se encuentran:

+ Aplicar PascalCase a clases, métodos y propiedades.
+ Utilizar camelCase para variables locales y parámetros.
+ Nombrar los métodos mediante expresiones descriptivas que representen acciones.
+ Considerar el principio Single Responsibility Principle (SRP) para distribuir adecuadamente las responsabilidades.
+ Evitar líneas excesivamente extensas para facilitar la lectura.
+ Incorporar comentarios breves en métodos críticos cuando sea necesario.
+ Organizar los componentes utilizando las capas controllers, services, repositories y models.

Ejemplo:
```C#
public class UserService { 
    public bool ValidateCredentials(string userEmail, string password) { 
        return true; 
        } 
    }
```

**Gherkin**

Para expresar los criterios de aceptación y estructurar las pruebas funcionales se empleará Gherkin. Su utilización permitirá describir el comportamiento esperado del sistema mediante una estructura comprensible tanto para los integrantes técnicos como para los stakeholders.

Los escenarios deberán cumplir con las siguientes condiciones:

Seguir la estructura Given-When-Then.
Utilizar un lenguaje comprensible para personas sin conocimientos técnicos.
Contar con títulos específicos que permitan identificar fácilmente el escenario.
Emplear Scenario Outline cuando sea necesario representar diferentes casos que mantengan una estructura similar.

Ejemplo:

```gherkin
Feature: User Login 
Scenario: Sucessful login 
    Given the user is on the login page 
    When the user enters valid credential 
    Then the system should redirect to the dashboard
```

**Principios generales de codificación**

Además de las reglas específicas para cada lenguaje, el desarrollo se orientará mediante cinco principios generales:

+ Readability First: priorizar que el código pueda entenderse fácilmente.
+ Consistency: conservar criterios de desarrollo uniformes en toda la solución.
+ Modularity: separar las responsabilidades en módulos claramente definidos.
+ Scalability: mantener una estructura que pueda soportar el crecimiento futuro del sistema.
+ Maintainability: facilitar la corrección, modificación y evolución del código.

#### 5.1.4. Software Deployment Configuration

**Despliegue de la Landing Page**

La Landing Page será desarrollada utilizando HTML, CSS y JavaScript y posteriormente publicada mediante GitHub Pages. Para ello, primero será necesario mantener correctamente organizados los archivos dentro del repositorio remoto.

**Organización del repositorio**

El archivo index.html deberá encontrarse directamente en la raíz del repositorio, debido a que será utilizado como archivo inicial durante el proceso de publicación. Los recursos complementarios se distribuirán en carpetas independientes según su función, permitiendo diferenciar los estilos, scripts e imágenes y facilitando el mantenimiento posterior.

La estructura prevista será la siguiente:

```
/ 
|---index.html 
|---css/ 
|   |__ styles.css 
|---js/ 
|  |__ main.js 
|---assets/ 
|       |__ images/
```
**Configuración de GitHub Pages**

Una vez que los archivos se encuentren disponibles en el repositorio, se configurará GitHub Pages como servicio de publicación de la Landing Page.

La configuración contempla las siguientes acciones:

1. Acceder al repositorio del proyecto en GitHub.
2. Ingresar a Settings.
3. Seleccionar la sección Pages.
4. Establecer la rama main como fuente de publicación.
5. Seleccionar la carpeta raíz /root como directorio de despliegue.
6. Guardar la configuración.

Después de completar la configuración, GitHub realizará automáticamente el proceso necesario para generar y publicar el sitio.

**Acceso a la versión publicada**

Cuando el despliegue haya finalizado, GitHub proporcionará una dirección pública desde la cual será posible acceder a la Landing Page.

La estructura esperada de la dirección será:

```
https://<usernanme>.github.io/<repository-name>/
```

Esta dirección corresponderá al acceso público de la versión oficial del producto.

**Actualización del sitio**

El proceso de despliegue también contempla las futuras modificaciones realizadas por el equipo. Cada cambio efectuado en la Landing Page deberá registrarse mediante un nuevo commit y enviarse al repositorio.

Cuando los cambios sean incorporados a la rama principal, GitHub Pages actualizará automáticamente el contenido publicado. Así, la versión disponible en línea podrá mantenerse sincronizada con la versión estable más reciente del código fuente.


### 5.2. Landing Page, Services & Applications Implementation

#### 5.2.1. Sprint 1

##### 5.2.1.1. Spring Planning 1
Para este primer Sprint, el equipo estableció como objetivo principal la implementación y despliegue de la primera versión de la Landing Page.

| Campo | Detalle |
|-------|---------|
| Sprint # | Sprint 1 |
| Date | 2026-09-06 |
| Time | 05:00 PM |
| Location | Reunión virtual vía Google Meet |
| Prepared By | Pillaca Gonzales, Andy Saúl |
| Attendees | Justo Yauricasa, Alexander Paolo / Pillaca Gonzales, Andy Saúl /Alvarado Millan, Boris / Martinez Ramos, Bryan Felix / Nawrocki Loureiro, Ian Andre |
| Sprint N-1 Review Summary | Dado que este es el Sprint inicial del proyecto, no se cuenta con un ciclo anterior para revisión. En consecuencia, la implementación del producto comienza formalmente desde sus cimientos. |
| Sprint N-1 Retrospective Summary | Al tratarse de la iteración inicial, no se cuenta con un proceso de retrospectiva previo. No obstante, el equipo estableció el compromiso de asegurar una comunicación fluida y acatar los plazos previstos. |
| Sprint 1 Goal | Nos enfocamos en el desarrollo y lanzamiento de la primera versión de la Landing Page, orientada a comunicar nuestra propuesta de valor: mejorar la seguridad y monitorieo en el transporte público. Consideramos que transmite con claridad los beneficios del sistema a potenciales clientes, lo cual se validará cuando el sitio esté en línea, cuente con todas las secciones clave y permita una navegación fluida. |
| Sprint N Velocity | 09 |
| Sum of Story Points | 09 |

##### 5.2.1.2. Aspect Leaders and Collaborators

| Team Member | GitHub Username | Configuración del Repositorio y CI/CD (L/C) | Estructura Base del Landing Page (L/C) | Funcionalidades Interactivas (L/C) | Corrección de Contenido (L/C) |
|------------|-----------------|---------------------------------------------|----------------------------------------|-----------------------------------|-------------------------------|
| Alvarado Millan, Boris | borisalvaradomillanPE | L | C | C | C |
| Justo Yauricasa, Alexander Paolo | AlexanderrJusto | C | C | C | L |
| Martinez Ramos, Bryan Felix | BryanMR1 | C | L | L | C |
| Pillaca Gonzales, Andy Saúl | apillacag | C | C | C | L |
| Nawrocki Loureiro, Ian Andre | IanNaw | C | C | C | L |

##### 5.2.1.3. Sprint Backlog 1
Se presenta el desglose tecnico de las historias seleccionadas para esta iteracion inicial. El proposito prioritario del Sprint abarca el despliegue de la pagina de aterrizaje y el cimiento de la arquitectura tecnologica del proyecto. Seguidamente, se incluye la imagen del tablero de Trello y la tabla de estados correspondiente a los elementos de trabajo.

<img src="docs/assets/Cap5/EvidenciaTrello.png">

link: https://trello.com/invite/b/6aada76451c89821aa1c576d/ATTI9ede0c7d6fa24ae911466aeadaa1cec5C94715BC/sprint-1-astrobusteam 

| Sprint # | Sprint 1 | | | | | | |
|----------|----------|-|-|-|-|-|-|
| **User Story** | | **Work-item / Task** | | | | | |
| Story Id | Story Title | Task Id | Task Title | Task Description | Estimation (Hours) | Assigned To | Status (To-do / In-Process / To-Review / Done) |
| US29 | Segmento al que apunta la solución | T-01 | Segmento al que apunta | Mostramos a como y andonde apunta nuestro sistema. | 2 | Alvarado Millan, Boris | Done |
| US37 | Problemática del transporte en la landing page | T-02 | Problematica | Mostrar la desbentajas del traspodte publico sin nuestro aplicacativo. | 2 | Justo Yauricasa, Alexander Paolo | Done |
| US38 | Propuesta de valor en la landing page | T-03 | Propuesta de valor | Mostrar los valores que tiene nuestra aplicativo en el trasporte publico. | 1 | Martinez Ramos, Bryan Felix | Done |
| US45 | Beneficios del sistema en la landing page | T-04 | Beneficios | Mostrar los beneficios que tiene nuestra aplicativo en el trasporte publico. | 1 | Pillaca Gonzales, Andy Saúl | Done |
| US46 | Equipo detrás de la solución | T-05 | Equipo | Mostramos las soluciones que tene nuestro aplicatico en el traspote publico | 2 | Nawrocki Loureiro, Ian Andre | Done |
| US30 | Mision y vision de la startup | T-06 | Mision y vision | Mostromos la vision y mision en la Landing Page. | 1 | Pillaca Gonzales, Andy Saúl | Done |


##### 5.2.1.4. Development Evidence for Sprint Review

En este primer Sprint el equipo implementó la landing page. Todo el trabajo se desarrolló sobre ramas feature/* que se integraron a develop mediante Pull Requests revisados. A continuación se listan los commits más representativos del sprint.

| Repository | Branch | Commit Id | Commit Message | Commit Message Body | Commited on (Date) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| SecurityBus-730-AW | feature/00-chapter-01 | ce1b67ea7c64e009aa307b91b9498b2e4d3211fd | docs: Merge chapter 1 | Merge branch 'feature/00-chapter-01' of https://github.com/AstroBusTeam/SecurityBus-730-AW into feature/00-chapter-01 | 10/09/2026 |
| SecurityBus-730-AW | feature/10-chapter-02 | e4c0da51c90fd37c8a59aa353c58aa894d881e12 | fix: fix a litle problem in the document | - | 11/09/2026 |
| SecurityBus-730-AW | feature/chapter-3 | 0e8fbc867149f98f4a5e1b9058293ccb81b53b93 | docs: Merge chapter 3 | Merge branch 'feature/chapter-3' into develop| 10/09/2026 |
| SecurityBus-730-AW | feature/chapter-04 | 9063bdf2ee33ae22be820af08c69f8ebb2443b58 | Docs: Create Event Storming | -| 10/09/2026 |
| SecurityBus-730-AW | feature/chapter-05 | 8d75682360fd891997329ce480af8349b238b4a8 | Docs:Event Storming folder created | -| 11/09/2026 |

##### 5.2.1.5. Execution Evidence for Sprint Review

Durante el primer Sprint, la prioridad del equipo fue la implementación y el lanzamiento de la primera versión de la página. El propósito central fue posicionar la propuesta de valor en materia de seguridad para el transporte público mediante una estructura que abarca desde la presentación general y los beneficios, hasta testimonios, funcionalidades clave y canales de contacto. 

La Landing Page incluye las siguientes secciones:

- **Hero:** Sección inicial que presenta el mensaje principal "Protege tu ruta, asegura tu futuro" e incorpora los accesos "Empezar ahora" y "Ver características" para orientar al usuario hacia las principales opciones de la plataforma.

![Hero](docs/assets/Cap5/LP_Evidencia/Hero2.png)

- **Caracteristicas:** Presenta las funciones principales de SecurityBus, como la validación del conductor mediante código QR, el botón de pánico para situaciones de emergencia, el control de pasajeros a bordo y el seguimiento de la unidad durante el recorrido.

![Hero](docs/assets/Cap5/LP_Evidencia/Caracteristicas.png)

- **Funcionalidad** Expone de forma resumida el funcionamiento de SecurityBus, abarcando desde la verificación del conductor hasta las acciones previstas ante una situación de emergencia.

![Hero](docs/assets/Cap5/LP_Evidencia/Funcionalidad.png)

- **Navegacion:** Barra de navegación que facilita el acceso a las distintas secciones disponibles en la Landing Page de SecurityBus.

![Hero](docs/assets/Cap5/LP_Evidencia/Navegacion.png)

- **Estadistica:** Muestra datos relevantes que permiten contextualizar los principales problemas relacionados con la seguridad en el transporte público.

![Hero](docs/assets/Cap5/LP_Evidencia/Estadistica.png)

- **Interfaz:** Utiliza una apariencia moderna en modo oscuro, acompañada de elementos visuales y tonalidades contrastantes que refuerzan la identidad de SecurityBus.

![Hero](docs/assets/Cap5/LP_Evidencia/Interfaz.png)

Link a la Landing Page: [SecurityBus Landing Page](https://astrobusteam.github.io/SecurityBus-landing-page-aw/)

##### 5.2.1.6. Services Documentation Evidence for Sprint Review

En el Sprint 1 de SecurityBus, el desarrollo estuvo centrado únicamente en la construcción de la Landing Page estática. Durante esta etapa no se implementaron servicios web, por lo que aún no se dispone de endpoints que requieran documentación. El desarrollo y la documentación de estos servicios se abordarán en los siguientes Sprints.

##### 5.2.1.7. Software Deployment Evidence for Sprint Review

Las funcionalidades desarrolladas durante este Sprint comprenden tanto la estructura principal de navegación como distintos elementos destinados a mejorar la experiencia del usuario en la Landing Page de SecurityBus. Para su construcción se estableció una organización basada en componentes reutilizables, un sistema de enrutamiento y estilos globales alineados con la identidad visual definida previamente para el proyecto.

El proceso de desarrollo se gestionó mediante Git Flow, utilizando ramas específicas para trabajar las diferentes funcionalidades antes de incorporarlas al proyecto mediante pull requests. Esta metodología permitió mantener una adecuada organización del código y facilitar el trabajo colaborativo entre los integrantes del equipo de AstroBus, quienes participaron en las distintas actividades relacionadas con el desarrollo front-end.

Asimismo, se realizaron ajustes orientados al diseño responsive, buscando que la Landing Page pueda visualizarse correctamente en distintos tamaños de pantalla. También se consideraron aspectos relacionados con el rendimiento y la accesibilidad web, tomando como referencia los estándares WCAG para ofrecer una interfaz más accesible a los diferentes usuarios vinculados con la propuesta de SecurityBus.

- 1: Primera funcionalidad: Implementación de la sección Hero, encargada de presentar el propósito principal de SecurityBus, acompañada de indicadores relacionados con el impacto de la propuesta y botones de llamada a la acción.
- 2: Segunda funcionalidad: Desarrollo de la sección de Características, donde se presentan las seis funcionalidades principales del sistema: Verificación QR, Botón de Pánico, Conteo de Pasajeros, Monitoreo Real, Alertas Inteligentes y Soporte 24/7.
- 3: Tercera funcionalidad: Incorporación de la sección ¿Cómo funciona SecurityBus?, en la que se explica el funcionamiento general de la propuesta mediante cuatro etapas: Inicio de Turno, Monitoreo Constante, Alerta Inmediata e Intervención.

---

### Despliegue en GitHub Pages

1. Se creó el repositorio público en la organización de GitHub del equipo SecurityBus y se subió el código fuente de la landing page construida con React + Vite.
   
2. En el repositorio. Dentro de **Pages**, como origen de publicación, se guardaron los cambios para activar la publicación automática.
   
3. Se configuraron los archivos necesarios para que los assets funcionen correctamente bajo el subdominio de GitHub Pages.
   
4. Se creó el archivo de workflow para automatizar el build y despliegue mediante GitHub Actions cada vez que se realice un push a la rama
   
5. Una vez activado el despliegue, GitHub Pages generó la URL pública del sitio desde donde cualquier usuario puede acceder a la landing page de SecurityBus sin necesidad de credenciales.
    
---

##### 5.2.1.8. Team Collaboration Insights during Sprint

Durante el Sprint 1, los integrantes del equipo AstroBus participaron de manera conjunta en el desarrollo de la Landing Page de SecurityBus, quedando sus aportes registrados mediante los commits realizados en el repositorio del proyecto. Las actividades fueron distribuidas entre los miembros del equipo, permitiendo avanzar de forma organizada en la implementación de las diferentes secciones, funcionalidades, contenido y aspectos visuales de la página.

Para administrar los cambios realizados durante el desarrollo, el equipo utilizó GitFlow como estrategia de control de versiones. El trabajo se realizó principalmente sobre la rama develop, utilizando ramas específicas para cada capitulo. 
Posteriormente, los cambios fueron integrados mediante Pull Requests, permitiendo revisar las modificaciones antes de incorporarlas a las ramas principales del proyecto.

![Contribuciones](docs/assets/Cap5/Contributions.png)


#### 5.2.2. Sprint 2

##### 5.2.2.1. Sprint Planning 2

| Sprint # | Sprint 2 |
| :--- | :--- |
| **Sprint Planning Background** | |
| Date | 29/09/2026 |
| Time | 5:20 PM |
| Location | Virtual |
| Prepared By | Martinez Ramos, Bryan Felix |
| Attendees (to planning meeting) | Alvarado Millan, Boris<br>Nawrocki Loureiro, Ian Andre |
| **Sprint 2 Review Summary** | Durante este sprint, el equipo desarrolló la primera versión funcional de la aplicación web de SecurityBus con Vue 3, Vite y TypeScript. El código se organizó bajo una arquitectura DDD, con tres bounded contexts (conductor, tracking y administration) y un núcleo compartido, cada uno con sus capas de dominio, aplicación, infraestructura y presentación. Se implementó el flujo del conductor (verificación con código de empleado, inicio y cierre del servicio, mapa de la unidad, conteo de pasajeros y botón de pánico) y el panel de administración (centro de control con el mapa de la flota y la gestión de alertas, además de las vistas de conductores, unidades, notificaciones, historial de turnos e impacto en números). La aplicación consume una Fake API REST con json-server y conserva la sesión, el turno en curso y las alertas en localStorage, de modo que no se pierden al recargar la página. Además, se dejó configurado su despliegue en Cloudflare. |
| **Sprint 2 Retrospective Summary** | El equipo logró avanzar de forma ordenada gracias a la separación por bounded contexts y capas, que permitió repartir el trabajo sin que unos módulos interfirieran con otros, y al uso de componentes reutilizables, que agilizó la construcción de las vistas. La Fake API permitió desarrollar la interfaz sin depender del backend. Como puntos de mejora, identificamos que para los próximos sprints debemos coordinar mejor la distribución de tareas, acordar desde el inicio el contrato de la API (nombres de recursos y campos), incorporar pruebas automatizadas y reemplazar los comportamientos simulados (escáner QR, movimiento de las unidades y conteo de pasajeros) por datos reales. |
| **Sprint Goal & User Stories** | |
| **Sprint 2 Goal** | Implementar la primera versión funcional de la aplicación web de SecurityBus, cubriendo el flujo del conductor (verificación, servicio y botón de pánico) y el panel de administración (centro de control, conductores, unidades, notificaciones e historial), con una arquitectura DDD, datos servidos por una Fake API y despliegue en Cloudflare, de modo que luego pueda reemplazarse la Fake API por los servicios reales del backend. |
| **Sprint 2 Velocity** | 109 |
| **Sum of Story Points** | 109 |

##### 5.2.2.2. Aspect Leaders and Collaborators

Durante el desarrollo del Sprint 2, se han identificado distintos aspectos funcionales relacionados al diseño y construcción de la aplicación web de SecurityBus. Con el objetivo de organizar el trabajo del equipo de manera eficiente, se ha elaborado una matriz de Liderazgo y Colaboración (LACX), donde se asigna a cada integrante el rol de líder (L) en los módulos clave del desarrollo que se le han asignado, y el rol de colaborador (C) en otros aspectos.

Los aspectos definidos para este Sprint, son:

1. **Apartado de Login:** Verificación del conductor mediante su código de empleado (o el escáner de código QR), validación contra la API y conservación de la sesión en localStorage.
2. **Apartado de Dashboard:** Monitoreo de distancia, tiempo, pasajeros, recaudación y ruta operada, conteo de pasajeros a bordo, protocolo de cierre y botón de finalizar servicio, con el resumen del turno.
3. **Gestión de flota:** Panel de administración para consultar conductores y unidades con su estado y ruta, y revisar el historial de turnos y el impacto en números.
4. **Botón de alarma:** Botón de pánico que envía la alerta de un conductor con la ubicación de su unidad y muestra la confirmación con el estado de la central.
5. **Registros de alarma:** Visualización de las alertas con su nivel, tipo, hora, coordenadas y estado, y su resolución desde el centro de control.
6. **Mapa:** Visualización de la posición de la unidad del conductor y, en el centro de control, de toda la flota con sus alertas, sobre OpenStreetMap.
7. **Sistema de notificaciones:** Consulta de los destinatarios de las alertas y del registro de entregas de notificaciones.

A continuación, se presenta la matriz de responsabilidades del equipo:

| Team Member (Last Name, First Name) | GitHub Username | Login | Dashboard | Fleet management | Alarm button | Alarm logs | Map | Notification system |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Martinez Ramos, Bryan Felix | Bryan Martinez | L | L | L | C | C | C | C |
| 	Alvarado Millan, Boris | Boris Alvarado | C | C | C | L | L | L | L |
| 	Nawrocki Loureiro, Ian Andre | Ian | L | C | C | C | C | C | L |

**Nota:** Distribución de responsabilidades de los integrantes del equipo durante el Sprint 2, indicando el liderazgo (L) y la colaboración (C) en cada funcionalidad desarrollada.

##### 5.2.2.3. Sprint Backlog 2

| User Story Id | User Story Title | Work Item/Task Id | Work Item/Task Title | Description | Estimation | Assigned To | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-01 | Autenticación del conductor al iniciar la jornada | T01 | UI Autenticación Conductor | Pantalla de login con código de empleado y escáner QR (simulado). | 3h | Bryan Martinez | Done |
| US-14 | Verificación de habilitación del conductor | T08 | Caso de uso Iniciar Sesión | Validación del código de empleado contra la API antes de abrir la sesión. | 8h | Ian Nawrocki | Done |
| US-15 | Vínculo entre conductor y unidad | T09 | UI Asignación de Unidades | Vista de las unidades con su conductor, ruta y estado. | 3h | Bryan Martinez | Done |
| US-02 | Apertura del registro de servicio | T02 | Inicio de Turno | Apertura automática del turno al autorizar el acceso del conductor. | 5h | Boris Alvarado | Done |
| US-03 | Envío de alerta desde la unidad | T03 | UI Botón de Pánico | Botón de pánico en el menú lateral y pantalla de confirmación de la alerta. | 3h | Bryan Martinez | Done |
| US-04 | Notificación de la alerta a la central | T04 | Caso de uso Levantar Alerta | Envío de la alerta a la API para que aparezca en el centro de control. | 4h | Bryan Martinez | Done |
| US-42 | Ubicación asociada al evento | T20 | Ubicación en Alerta | Registro de las coordenadas de la unidad (simuladas) al emitir la alerta. | 3h | Boris Alvarado | Done |
| US-05 | Persistencia del evento de emergencia | T05 | Persistencia de Alertas | Guardado de la alerta en la API y en localStorage. | 3h | Ian Nawrocki | Done |
| US-40 | Clasificación de alertas por gravedad | T19 | Niveles de Gravedad | Asignación del nivel (crítico, alto, medio o bajo) según el tipo de alerta. | 5h | Boris Alvarado | Done |
| US-33 | Difusión de la alerta a varios destinatarios | T17 | UI Notificaciones | Vista de destinatarios activos y registro de entregas (datos de muestra). | 4h | Bryan Martinez | Done |
| US-43 | Seguimiento de la unidad asignada | T21 | UI Mapa y Seguimiento | Mapa con la posición de la unidad, actualizada en tiempo real. | 5h | Bryan Martinez | Done |
| US-06 | Conteo automático de ocupantes | T06 | UI Conteo de Pasajeros | Conteo simulado de pasajeros a bordo, con nivel de ocupación y aviso de anomalía. | 4h | Boris Alvarado | Done |
| US-07 | Disponibilidad del conteo para reportes | T07 | Consulta de Registros de Pasajeros | Consulta a la API de los últimos registros de pasajeros. | 2h | Ian Nawrocki | Done |
| US-25 | Cierre del registro de servicio | T13 | UI Cierre de Servicio | Botón para finalizar el servicio y archivar el turno en localStorage. | 4h | Boris Alvarado | Done |
| US-26 | Consulta del estado del propio servicio | T14 | UI Estado de Servicio | Dashboard con distancia, tiempo, pasajeros, recaudación y resumen del turno. | 3h | Ian Nawrocki | Done |
| US-27 | Tablero de estado de la flota | T15 | Dashboard Flota | Centro de control con indicadores, mapa de la flota y lista de unidades. | 5h | Boris Alvarado | Done |
| US-16 | Revisión del historial de emergencias | T10 | UI Registro de Alertas | Listado de alertas con nivel, tipo, hora, coordenadas y estado. | 4h | Bryan Martinez | Done |
| US-28 | Seguimiento de la ocupación en operación | T16 | Indicador de Ocupación | Pasajeros a bordo de la flota en el centro de control y por unidad. | 4h | Ian Nawrocki | Done |

**Nota:** Relación entre las historias de usuario del Sprint 2 y las tareas implementadas, incluyendo su estimación, responsable asignado y estado de ejecución. Las historias US-23, US-24 y US-35 no se implementaron en este Sprint y pasan al siguiente.

##### 5.2.2.4. Development Evidence for Sprint Review

En este segundo Sprint se implementó el frontend de la aplicación web de SecurityBus. El trabajo se organizó en ramas feature/* creadas a partir de develop, una por cada bounded context (iam, fleet, operations, alerts y shared), y los cambios se integraron mediante Pull Requests. En la siguiente tabla se muestran los commits más representativos del Sprint.

| Repository | Branch | Commit Id | Commit Message | Commit Message Body | Commited on (Date) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AstroBusTeam-FrontEnd | feature/iam | 2317a3abf7b753f4b52e65aed1632721b0c10258 | feature: add iam | -- | 05/10/2026 |
| AstroBusTeam-FrontEnd | feature/fleet | b4b01276395f339487e1b7b3fdb1e36e9536ef05 | feature: create the fleet component and functions | -- | 06/10/2026 |
| AstroBusTeam-FrontEnd | feature/operations | 830f93a480adb5f957ff975f007e2058a0b2fd88 | Merge pull request #3 from AstroBusTeam/feature/operations | -- | 06/10/2026 |
| AstroBusTeam-FrontEnd | feature/alerts | 5c51e4912c9308f6e14fa750d7a1e1316efe779d | Merge pull request #2 from AstroBusTeam/feature/alerts | -- | 06/10/2026 |
| AstroBusTeam-FrontEnd | feature/shared | 0a53309b6b74c59fb78f26beb44be9cb3cff9339 | Merge pull request #1 from AstroBusTeam/feature/shared | -- | 06/10/2026 |

##### 5.2.2.5. Execution Evidence for Sprint Review

En este Sprint se logró la primera versión funcional de la Web Application de SecurityBus. La aplicación permite que el conductor ingrese con su código de empleado, inicie y cierre su servicio, vea el mapa de su unidad, consulte el conteo de pasajeros y emita una alerta de emergencia con un solo botón. Del lado de la empresa, permite supervisar la flota desde el centro de control, revisar y resolver las alertas, consultar conductores y unidades, ver los destinatarios de las notificaciones, y revisar el historial de turnos y los indicadores de impacto. Los datos se obtienen de una Fake API REST, y la sesión, el turno en curso y las alertas se conservan en localStorage para que no se pierdan al recargar la página.

Verificación de identidad del conductor. El conductor ingresa su código de empleado (por ejemplo, EMP-001) o utiliza el escáner de código QR, que en esta versión simula la lectura. El sistema consulta la Fake API para validar que el código exista; si es válido, abre la sesión y muestra la pantalla de acceso autorizado, desde la cual el conductor pasa al dashboard con su turno iniciado. Si el código no existe, se muestran los mensajes de error correspondientes. La sesión queda guardada en localStorage.

![verificación de identidad del conductor](docs/assets/Cap5/evidenciaWeb/1.png)

Dashboard e inicio de servicio. El turno comienza al autorizarse el acceso. El dashboard muestra los indicadores del turno en curso (distancia, tiempo, pasajeros y recaudación), la ruta operada con acceso al mapa, el estado del sistema y el protocolo de cierre. Al finalizar el servicio, el conductor confirma el cierre y se presenta el resumen del turno, que queda archivado en el historial.

![dashboard](docs/assets/Cap5/evidenciaWeb/2.1.png)
![dashboard](docs/assets/Cap5/evidenciaWeb/2.2.png)

Conteo de pasajeros. Muestra los pasajeros a bordo, el total de los que abordaron y bajaron, la capacidad máxima y el nivel de ocupación, con un aviso de anomalía cuando se supera el 90 % de la capacidad. En esta versión el conteo es simulado y el historial de registros se consulta a la Fake API.

![passenger-count](docs/assets/Cap5/evidenciaWeb/3.png)

Mapa del servicio y centro de control. El mapa dibuja la posición de las unidades sobre los tiles de OpenStreetMap. El conductor ve su unidad y la empresa ve toda la flota en el centro de control, junto con los indicadores de unidades activas, alertas activas y pasajeros a bordo. El movimiento de las unidades es simulado y su posición se actualiza periódicamente en la Fake API.

![control-center](docs/assets/Cap5/evidenciaWeb/4.png)

Botón de pánico. Disponible en el menú lateral del conductor, registra una alerta crítica con la ubicación de la unidad, la envía a la Fake API y la guarda en localStorage. Luego muestra una pantalla de confirmación con las coordenadas y el estado de la central. El botón de cancelar se habilita a los 5 segundos y devuelve al conductor al dashboard.

![panic-signal](docs/assets/Cap5/evidenciaWeb/5.png)

Registro de alertas. En el módulo del conductor, el registro lista las alertas emitidas por su unidad con su nivel, tipo, hora, coordenadas y estado. En el centro de control, la empresa ve las alertas recientes de toda la flota, puede ubicar la unidad en el mapa y marcar las alertas como resueltas.

![alert-details](docs/assets/Cap5/evidenciaWeb/6.png)

Notificaciones. Presenta los destinatarios activos con su tipo y estado, y el registro de entregas de las notificaciones. En esta versión los datos son de muestra.

![notifications](docs/assets/Cap5/evidenciaWeb/7.png)

Gestión de conductores y unidades. La vista de conductores presenta una tabla con búsqueda por nombre, apellido o DNI, y la de unidades muestra cada bus con su conductor, ruta, pasajeros, velocidad y estado. Las acciones de edición, bloqueo y reasignación están dispuestas en la interfaz, pero su funcionamiento queda para el siguiente Sprint.

![vehicles](docs/assets/Cap5/evidenciaWeb/8.png)

![drivers](docs/assets/Cap5/evidenciaWeb/9.png)

Historial de turnos e impacto en números. El historial lista los turnos con su conductor, bus, ruta, fecha, distancia, pasajeros, recaudación y estado; incluye los turnos finalizados en el navegador (guardados en localStorage) y datos de muestra. La vista de impacto resume los indicadores principales del servicio y la tendencia semanal de alertas.

![shift-history](docs/assets/Cap5/evidenciaWeb/10.png)

Para evidenciar las funcionalidades implementadas, se adjunta un video donde se muestra la navegación entre las vistas, la interacción con el botón de pánico y la comunicación con la Fake API desplegada.

URL del video de ejecución de la Web Application: [https://upcedupe-my.sharepoint.com/:v:/g/personal/u202418823_upc_edu_pe/IQC9xqrLUfGBTKetm5mY0sOrAQ1vPREJ-m9pPR_8LgcypCI?e=u1aGF4&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202418823_upc_edu_pe/IQC9xqrLUfGBTKetm5mY0sOrAQ1vPREJ-m9pPR_8LgcypCI?e=u1aGF4&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D) 

##### 5.2.2.6. Services Documentation Evidence for Sprint Review

Durante el Sprint 2, el equipo implementó una Fake API RESTful con json-server, que simula el comportamiento del backend de SecurityBus mientras se desarrollan los servicios reales. La API expone cinco recursos (conductores, turnos, alertas, pasajeros y unidades), definidos en el archivo db.json, y soporta operaciones CRUD con los verbos GET, POST, PUT, PATCH y DELETE. Su configuración de rutas (routes.json) redirige el prefijo /api/v1 a los recursos de la base de datos, de forma que la aplicación consume la misma estructura de URL que tendrá el servicio definitivo.

La Web Application accede a la API mediante adaptadores de la capa de infraestructura de cada bounded context, que implementan los repositorios definidos en el dominio. La URL base se configura con las variables de entorno VITE_API_MODE y VITE_API_BASE_URL, por lo que reemplazar la Fake API por los servicios reales solo requiere cambiar el adaptador, sin modificar el dominio ni los casos de uso. Esto permitió desacoplar la aplicación web de datos locales y realizar pruebas colaborativas sobre una API pública.

URL base del servicio: [https://astro-bus-team-fake-api-aw-730.vercel.app](https://security-bus-fake-api.vercel.app/)

Dado que json-server no genera documentación OpenAPI automáticamente, en este Sprint los endpoints se documentan en las siguientes tablas. La especificación OpenAPI formal se elaborará con los Web Services definitivos en los siguientes Sprints.

**Recursos expuestos**

| Endpoint | Acciones soportadas | Acciones que usa la Web Application | Descripción |
| :--- | :--- | :--- | :--- |
| /conductores | GET, POST, PUT, PATCH, DELETE | GET | Datos de los conductores; se usa para verificar el código de empleado al iniciar sesión. |
| /unidades | GET, POST, PUT, PATCH, DELETE | GET, PATCH | Unidades de la flota con su posición, ruta y estado; se usa en el mapa y el centro de control. |
| /alertas | GET, POST, PUT, PATCH, DELETE | POST, PATCH | Emisión y resolución de alertas de emergencia. |
| /pasajeros | GET, POST, PUT, PATCH, DELETE | GET | Registros del conteo de pasajeros por unidad. |
| /turnos | GET, POST, PUT, PATCH, DELETE | Ninguna | Registro de turnos de servicio. En esta versión el turno en curso y los turnos finalizados se guardan en localStorage. |

**Modelo de datos**

| Recurso | Campos |
| :--- | :--- |
| conductores | id, nombre, apellido, dni, codigoEmpleado, codigoQr, placa, estado, foto |
| unidades | id, placa, conductor, ruta, estado, lat, lng, pasajeros, velocidad |
| alertas | id, conductorId, turnoId, tipo, nivelRiesgo, latitud, longitud, timestamp, descripcion, resuelta |
| pasajeros | id, turnoId, busId, totalAbordaron, totalBajaron, totalAbordo, timestamp, anomalia |
| turnos | id, conductorId, busId, rutaNombre, rutaOrigen, rutaDestino, distanciaKm, tiempoSegundos, pasajeros, recaudacion, estado, fechaInicio, fechaFin |

Valores de los campos de estado: en unidades, estado es ACTIVO, INACTIVO o ALERTA; en alertas, tipo es PANICO, VELOCIDAD, PASAJEROS o DESVIO (sin tilde) y nivelRiesgo es CRITICO, ALTO, MEDIO o BAJO.

**Acciones sobre los recursos**

| Acción | Verbo HTTP | Sintaxis de llamada | Parámetros | Response |
| :--- | :--- | :--- | :--- | :--- |
| Listar recursos | GET | /api/v1/{recurso} | Opcionales: filtros por campo, por ejemplo ?codigoEmpleado=EMP-001, ?estado=ALERTA o ?resuelta=false | 200 OK con un arreglo JSON. Si ningún registro coincide con el filtro, devuelve 200 con un arreglo vacío. |
| Obtener por id | GET | /api/v1/{recurso}/{id} | id en la ruta | 200 OK con el recurso. 404 si no existe. |
| Crear | POST | /api/v1/{recurso} | Cuerpo JSON con los campos del recurso | 201 Created con el recurso y su id generado. |
| Reemplazar | PUT | /api/v1/{recurso}/{id} | id en la ruta y cuerpo JSON completo | 200 OK con el recurso reemplazado. |
| Actualizar parcialmente | PATCH | /api/v1/{recurso}/{id} | id en la ruta y cuerpo JSON solo con los campos a modificar | 200 OK con el recurso actualizado. |
| Eliminar | DELETE | /api/v1/{recurso}/{id} | id en la ruta | 200 OK con un objeto vacío. |

Se adjuntan las siguientes capturas de la interacción con la API usando los datos de muestra:

![evidencia1](docs/assets/Cap5/sprint02/ev1.png)

<br>

![evidencia2](docs/assets/Cap5/sprint02/ev2.png)


Repositorio de la Fake API: [https://github.com/AstroBusTeam/AstroBusTeam-fake-api-aw-730](https://github.com/Astrobus2/SecurityBus-fake-api)

##### 5.2.2.7. Software Deployment Evidence for Sprint Review

Durante el Sprint 2, el equipo realizó el despliegue de la Web Application y de la Fake API. A diferencia del Sprint 1, donde solo se publicó la Landing Page en GitHub Pages, en esta iteración se consolidó una arquitectura de dos servicios: la aplicación web, publicada con Firebase Hosting, y la Fake API, publicada en Vercel. La aplicación web se configura mediante variables de entorno (modo de la API y URL base), de modo que la dirección del servicio no queda escrita en el código fuente y puede cambiarse entre desarrollo y producción sin modificarlo.

La arquitectura de despliegue se compone de los siguientes elementos:

Web Application: aplicación Vue 3 con TypeScript, compilada con Vite y organizada en bounded contexts bajo una arquitectura DDD. Su resultado (carpeta dist) se publica en Firebase Hosting.
Fake API: servicio RESTful basado en json-server (archivos db.json y routes.json), ejecutado mediante un servidor Express y publicado en Vercel.
Variables de entorno: archivos .env.development y .env.production con VITE_API_MODE (json-server) y VITE_API_BASE_URL (URL base de la API). En desarrollo apuntan a la API local (http://localhost:3000/api/v1), que se inicia con npm run api; en producción apuntan a la Fake API publicada en Vercel.
Persistencia en el navegador: la sesión del conductor, el turno en curso, los turnos finalizados y las alertas se guardan en localStorage, por lo que no requieren un servicio de almacenamiento adicional.

**Despliegue de la Fake API en Vercel**

- Se creó la cuenta en Vercel y se importó el repositorio de la Fake API desde GitHub.
- Se configuró json-server con el archivo db.json, que contiene los recursos conductores, turnos, alertas, pasajeros y unidades, y se definió en routes.json la redirección del prefijo /api/v1/* hacia dichos recursos.
- Se agregó un punto de entrada con Express para que Vercel detecte y ejecute la aplicación.
- Se publicó el proyecto y Vercel generó la URL pública del servicio.
- Se verificó el funcionamiento consultando los recursos desde el navegador (por ejemplo, /api/v1/conductores) y desde la Web Application.

![evidence-fake-api](docs/assets/Cap5/sprint02/evAPI1.png)

**Despliegue de la Web Application en Firebase Hosting**

- Se creó el proyecto en Firebase y se habilitó Hosting.
- Se configuró firebase.json con la carpeta dist como directorio público y una regla de reescritura de todas las rutas hacia index.html, necesaria para que Vue Router funcione al recargar la página o abrir un enlace directo.
- Se definió en .env.production el modo json-server y la URL base de la Fake API desplegada en Vercel.
- Se generó la versión de producción con npm run build, que verifica los tipos con vue-tsc y luego compila con Vite, y se publicó con firebase deploy --only hosting.
<br>

![evidence-frontend-firebase](docs/assets/Cap5/sprint02/evWEB1.png)

La Web Application desplegada está disponible en: [https://securitybus-730-aw-front-7bf31.web.app/](https://securitybus-ab878.web.app)

Repositorio de la Web Application: [https://github.com/AstroBusTeam/AstroBusTeam-FrontEnd](https://github.com/Astrobus2/SecurityBus-frontend)


##### 5.2.2.8. Team Collaboration Insights during Sprint

Durante el Sprint 2, el equipo trabajó de forma colaborativa en la implementación de la Web Application y de la Fake API. Se mantuvo la estrategia GitFlow definida en la configuración del proyecto: cada funcionalidad se desarrolló en una rama feature/* creada a partir de develop, y los cambios se integraron mediante Pull Requests revisados por otro integrante antes de incorporarse. Los mensajes de commit buscaron seguir la convención Conventional Commits definida en la sección 5.1.2, lo que permitió mantener la trazabilidad de cada cambio.

El trabajo se distribuyó según la matriz de líderes y colaboradores de la sección 5.2.2.2. Alexander Justo lideró los aspectos de login, dashboard y gestión de flota, y Andy Pillaca lideró el botón de alarma, los registros de alarma, el mapa y el sistema de notificaciones, colaborando ambos en los aspectos del otro. La Fake API y el despliegue se trabajaron de forma conjunta. Esta organización permitió que la interfaz, los datos de prueba y el despliegue avanzaran en paralelo. El seguimiento de las tareas se realizó en el tablero de Trello del Sprint.

A continuación se presentan las evidencias extraídas de los repositorios del proyecto, que reflejan la participación de los integrantes durante el Sprint.

**Evidencia 1: Gráfico de contribuciones por integrante**

![contributors](docs/assets/Cap5/sprint02/contributors.png)

**Evidencia 2: Resumen de actividad del Sprint mediante GitHub Pulse**

![pulse](docs/assets/Cap5/sprint02/pulse.png)

<br>

**Evidencia 3: Gestión de cambios mediante Pull Requests**

![pull-requests](docs/assets/Cap5/sprint02/pull-requests.png)

<br>

**Evidencia 4: Organización de ramas bajo GitFlow**

![gitflow](docs/assets/Cap5/sprint02/git-flow.png)

<br>

Las evidencias muestran la participación de los integrantes en la implementación, con commits distribuidos durante el Sprint e integraciones frecuentes hacia la rama develop. Entre las actividades colaborativas más relevantes destacan:

- Implementación de las vistas del conductor: verificación de identidad con código de empleado, dashboard con el resumen del turno, mapa de la unidad, conteo de pasajeros, botón de pánico y registro de alertas.
- Desarrollo del panel de administración: centro de control con el mapa de la flota, conductores, unidades, notificaciones, historial de turnos e impacto en números.
- Organización del frontend por bounded contexts con capas de dominio, aplicación, infraestructura y presentación, y persistencia de la sesión, el turno y las alertas en localStorage.
- Configuración de la Fake API con json-server y conexión de la aplicación mediante adaptadores y variables de entorno.
- Despliegue de la Web Application en Firebase Hosting y de la Fake API en Vercel.

Repositorio de la Web Application: [https://github.com/AstroBusTeam/AstroBusTeam-FrontEnd](https://github.com/AstroBusTeam/AstroBusTeam-FrontEnd)

Repositorio de la Fake API: [https://github.com/AstroBusTeam/AstroBusTeam-fake-api-aw-730](https://github.com/AstroBusTeam/AstroBusTeam-fake-api-aw-730)


## Conclusiones

### Conclusiones y Recomendaciones

SecurityBus plantea una solución tecnológica orientada a mejorar la seguridad en el transporte público, considerando las necesidades tanto de las empresas de transporte como de los conductores durante la operación de las unidades.

La propuesta integra funcionalidades como la verificación del conductor mediante código de empleado y código QR, botón de pánico, conteo de pasajeros y monitoreo de las unidades, permitiendo abordar diferentes situaciones relacionadas con el control y la seguridad durante los recorridos.

El proyecto busca facilitar una respuesta más rápida ante situaciones de riesgo y proporcionar a las empresas información que les permita tener un mayor conocimiento de lo que ocurre durante la operación de sus unidades.

Asimismo, SecurityBus busca complementar las medidas tradicionales de seguridad mediante herramientas digitales que permitan mejorar la comunicación y supervisión entre conductores y empresas de transporte.

Primera versión funcional lograda. Con el Sprint 2 la propuesta pasó de la Landing Page a una Web Application que cubre el flujo del conductor (verificación de identidad, inicio y cierre del servicio, conteo de pasajeros y botón de pánico) y el de la empresa (centro de control con el mapa de la flota, alertas, conductores, unidades, notificaciones e historial de turnos).

Función crítica ya demostrable. El botón de pánico registra una alerta crítica con la ubicación de la unidad, la envía a la API y la guarda en localStorage, y de inmediato muestra al conductor una pantalla de confirmación. Esto responde a la recomendación de mantener las acciones de emergencia simples y rápidas.

Arquitectura modular. Organizar el frontend por bounded contexts (conductor, tracking y administration), con capas de dominio, aplicación, infraestructura y presentación, facilita que el trabajo se reparta y que el sistema crezca. La lógica de negocio queda en el dominio y en los casos de uso, sin depender del framework ni de la fuente de datos.

Desacople mediante la Fake API. Consumir una API con la misma estructura de URL que tendrá el servicio real permitió desarrollar la interfaz sin esperar al backend. Como el acceso a los datos se realiza mediante adaptadores que implementan los repositorios del dominio, reemplazar la Fake API por los servicios reales solo requerirá cambiar el adaptador, lo que reducirá el trabajo de integración.

Persistencia en el navegador. El uso de localStorage permite que la sesión del conductor, el turno en curso, los turnos finalizados y las alertas se conserven al recargar la página. Si el conductor la recarga durante un turno, el cronómetro continúa donde iba y los turnos finalizados aparecen en el historial.

Trabajo colaborativo. GitFlow, Pull Requests y la matriz de líderes y colaboradores permitieron avanzar en paralelo en interfaz, datos de prueba y despliegue.

Despliegue continuo del producto. Ahora hay dos servicios publicados (la aplicación web en Firebase Hosting y la API en Vercel), y la aplicación se configura mediante variables de entorno para apuntar a cada API según el ambiente.

Experiencia de uso. El tema oscuro y la identidad visual mantienen lo definido en las Style Guidelines.

Alcance actual. Algunas funciones de esta versión son simuladas y quedan para los siguientes Sprints: la lectura del código QR, la ubicación y el movimiento de las unidades, el conteo de pasajeros y los datos de las notificaciones. Asimismo, las acciones de edición, bloqueo y reasignación de las vistas de administración, el acuse de recibo y reenvío de alertas, y el cálculo del promedio de pasajeros por viaje aún no están implementados.

**Recomendaciones**

Se recomienda priorizar una experiencia de uso sencilla y rápida, especialmente en funcionalidades destinadas a situaciones de emergencia, evitando procesos complejos que puedan dificultar su utilización por parte del conductor.

Es importante continuar validando las necesidades de conductores y empresas de transporte, con el propósito de asegurar que las funcionalidades desarrolladas respondan a situaciones reales presentes durante los recorridos.

También se recomienda garantizar la confiabilidad de funciones críticas como el botón de pánico, la verificación del conductor y el monitoreo, debido a que su correcto funcionamiento resulta fundamental dentro de la propuesta de seguridad de SecurityBus.

Finalmente, se recomienda desarrollar SecurityBus de manera progresiva, evaluando los resultados obtenidos con los usuarios y utilizando esta información para mejorar las funcionalidades y adaptar la plataforma a las necesidades del transporte público.

Reemplazar las funciones simuladas por datos reales. Se recomienda incorporar la lectura del código QR con la cámara del dispositivo, la ubicación real de las unidades mediante GPS y la integración con sensores para el conteo de pasajeros, de modo que la información que ve la central corresponda a lo que ocurre en la unidad.

Comunicación en tiempo real. La posición de las unidades y las alertas se generan en el cliente y se envían a la Fake API, pero los demás usuarios no las reciben de inmediato. Para que la central reaccione a tiempo, se necesitaría un mecanismo como WebSockets o una actualización periódica de los datos desde el servidor.

Reemplazar la Fake API por los Web Services reales y documentarlos con OpenAPI, ya que json-server no valida datos ni ofrece seguridad, y su persistencia depende de un archivo. Con la arquitectura actual, el cambio se concentra en los adaptadores de infraestructura.

Autenticación real. Hoy el ingreso se valida solo con el código de empleado y no se verifica el estado del conductor ni se protegen las rutas; conviene usar tokens, control de permisos por rol (conductor y empresa) y guardas de navegación. Asimismo, localStorage es propio de cada navegador y no es un medio seguro, por lo que la información sensible y el historial definitivo deben almacenarse en el servidor.

Completar las funcionalidades pendientes. Quedan por implementar las acciones de administración (crear, editar y bloquear conductores, y reasignar unidades), el acuse de recibo y reenvío de las alertas, y el promedio de pasajeros por viaje.

Incorporar pruebas automatizadas. La separación en dominio y casos de uso facilita probar la lógica de negocio sin depender de la interfaz ni de la red. Se recomienda sumar pruebas unitarias de estos componentes y automatizar la compilación y el despliegue.

Validar la accesibilidad y el diseño responsive. Se recomienda comprobar la interfaz en dispositivos reales y con los estándares WCAG, especialmente en las pantallas que usa el conductor durante el recorrido.


---

## Bibliografía

Brandolini, A. (2021). Introducing EventStorming: An act of deliberate collective learning. Leanpub. https://leanpub.com/introducing_eventstorming

Brown, S. (2020). The C4 model for visualising software architecture. C4 Model. https://c4model.com/

Cucumber. (s.f.). Gherkin Reference: Syntax and Keywords. https://cucumber.io/docs/gherkin/

EmailJS. (2024). EmailJS Official Documentation. https://www.emailjs.com/docs/

Evans, E. (2003). Domain-Driven Design: Tackling Complexity in the Heart of Software. Addison-Wesley Professional. https://www.oreilly.com/library/view/domain-driven-design-tackling/0321125215/

GitHub. (2024). GitHub Actions and GitHub Pages Documentation. https://docs.github.com/

Gothelf, J., & Seiden, J. (2021). Lean UX: Designing Great Products with Agile Teams (3.ª ed.). O'Reilly Media. https://www.oreilly.com/library/view/lean-ux-3rd/9781492048596/

---

## Anexos

**<center>Anexo A: Guía de entrevistas por segmentos</center>**<br>

Segmento 1: Empresas y organizaciones de transporte publico

|#|Preguntas de Entrevista|
|-|-----------------------|
|1|¿Cómo gestionan actualmente las emergencias que ocurren durante el recorrido de sus unidades?|
|2|¿Cuándo ocurre un asalto, extorsión o incidente, ¿cuál es el procedimiento que siguen para atenderlo?|
|3|¿Qué dificultades encuentran para conocer en tiempo real lo que sucede dentro de una unidad?|
|4|¿Cuáles son los riesgos de seguridad que más afectan a su empresa y a sus conductores?|
|5|¿Cuánto tiempo suele transcurrir entre el incidente y que la empresa sea informada?|
|6|¿Qué herramientas tecnológicas utilizan actualmente para monitorear sus vehículos y conductores?|
|7|¿Considera útil que el conductor pueda activar un botón de pánico con envío automático de ubicación GPS? ¿Por qué?|
|8|¿Qué información sería indispensable que reciba la central al momento de una alerta de emergencia?|
|9|¿Qué factores influirían en la decisión de implementar este sistema en su organización?|
|10|¿Qué beneficios esperaría obtener de una plataforma de seguridad y monitoreo de transporte publico?|

Segmento 2: Conductores de transporte público

|#|Preguntas de Entrevista|
|-|-----------------------|
|1|¿Qué situaciones de inseguridad has vivido o presenciado durante tu jornada laboral?|
|2|¿Qué tipo de apoyo o asistencia esperas recibir por parte de tu empresa después de reportar una emergencia?|
|3|¿En qué momentos del recorrido sientes que existe mayor riesgo de sufrir un asalto o una amenaza?|
|4|¿Cuando ocurre una emergencia, ¿cómo solicitas ayuda actualmente?|
|5|¿Qué tan seguro te sentirías utilizando un botón de pánico que envíe una alerta de forma silenciosa?|
|6|¿Qué tan importante consideras que la empresa conozca tu ubicación en tiempo real durante una emergencia?|
|7|¿Qué dificultades enfrentas para comunicarte con tu empresa mientras estás conduciendo?|
|8|¿Qué información te gustaría que recibiera la central al activar una alerta de emergencia?|
|9|¿Crees que un sistema de seguridad y seguimiento podría ayudarte a reaccionar mejor ante situaciones de riesgo? ¿Por qué?|
|10|¿Qué características considerarías indispensables en una aplicación de seguridad para conductores?|

**<center>Anexo B: Gestión del Product Backlog en Trello</center><br>

**Referencia:** AstroBus. (2026). Product Backlog de SecurityBus. Trello.
<a href="https://trello.com/invite/b/6aada76451c89821aa1c576d/ATTI9ede0c7d6fa24ae911466aeadaa1cec5C94715BC/sprint-1-astrobusteam">https://trello.com/invite/b/6aada76451c89821aa1c576d/ATTI9ede0c7d6fa24ae911466aeadaa1cec5C94715BC/sprint-1-astrobusteam</a>

Se presenta el desglose tecnico de las historias seleccionadas para esta iteracion inicial. El proposito prioritario del Sprint abarca el despliegue de la pagina de aterrizaje y el cimiento de la arquitectura tecnologica del proyecto. Seguidamente, se incluye la imagen del tablero de Trello y la tabla de estados correspondiente a los elementos de trabajo.

![Trello](/docs/assets/Cap5/EvidenciaTrello.png)


**<center>Anexo C: Prototipado y Diseño de Interfaces en Figma</center><br>
**Referencia:** AstroBus. (2026). Design System & Mockups de SecurityBus. Figma.
<a href="https://www.figma.com/design/dZGVlWuEfGy76GBO9a8nmO/SecurityBus?node-id=194-17020&t=qkGb9pUHIXJa9Tu6-0">https://www.figma.com/design/dZGVlWuEfGy76GBO9a8nmO/SecurityBus?node-id=194-17020&t=qkGb9pUHIXJa9Tu6-0</a>

<center>Captura o Evidencia del Diseño de Interfaces - Figma</center><br>

![Diseño UX/UI](/docs/assets/Cap5/figmaWireframesMockups.png)



