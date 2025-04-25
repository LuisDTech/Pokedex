# 📦 PokeDex Angular - Instalación, ejecución y despliegue en Vercel

Hola, soy Luis Avila Barrera, y este documento explicare detalladamente cómo instalé, ejecuté, versioné y desplegué la aplicación web **PokeDex**, desarrollada con **Angular**, utilizando **GitHub** para el control de versiones y **Vercel** como plataforma gratuita para el despliegue.

---

## 🛠️ Requisitos previos a tomar en cuenta

Antes de comenzar, me aseguré de tener instaladas las siguientes herramientas:

- **Node.js** (versión LTS) y **npm**  
  👉 [https://nodejs.org/](https://nodejs.org/)  
- **Angular CLI**  
  ```bash
  npm install -g @angular/cli
  ```
- **Git**  
  👉 [https://git-scm.com/](https://git-scm.com/)
- Cuenta en **GitHub** y **Vercel**

Verifiqué cada instalación con los comandos:
```bash
node -v
npm -v
ng version
git --version
```

---

## 📥 Instalación y ejecución en local

### 1. Descargué y descomprimí el proyecto original

- Ruta original del archivo ZIP:  
`sistemas-distribuidos/poke-dex-lab/source/pokedex-angular.zip`

Extraje el contenido en una carpeta de trabajo la cual se encuentra en Github y navegué hasta la ruta del proyecto y lo descargue:

```bash
"sistemas-distribuidos/poke-dex-lab/source/pokedex-angular"
```

### 2. Instalé las dependencias del proyecto

- Comando:
```bash
npm install
```

Este comando descargó todos los paquetes que se encuentran definidos en el archivo `package.json`.

### 3. Ejecuté el servidor de desarrollo en local

- Comando:
```bash
npm start
```

Esto levantó el servidor en el enlace `http://localhost:4200`, donde pude visualizar y probar la aplicación localmente.

---

## 🏗️ Compilación para producción

Para generar el build de producción, ejecuté el siguiente comando:

```bash
npm run build
```

Esto generó una carpeta optimizada en la ruta:

```
dist/pokedex-angular
```

Los archivos en esta carpeta son los que se encuentran listos para ser desplegados en cualquier servidor estático, en este caso fue desplegado en `Vercel`.

---

## 🧩 Subida del proyecto a GitHub

### 1. Inicialicé un repositorio Git en la ruta del proyecto

```bash
git init
```

### 2. Agregué todos los archivos al área de staging

```bash
git add .
```

### 3. Realicé el primer commit

```bash
git commit -m "Versión inicial de la PokeDex en Angular"
```

### 4. Creé la rama principal

```bash
git branch -M main
```

### 5. Conecté el repositorio local con GitHub

Primero, creé un nuevo repositorio vacío en [https://github.com](https://github.com).  
Luego, lo vinculé desde la terminal:

```bash
git remote add origin https://github.com/LuisDTech/Pokedex.git
```

### 6. Subí los archivos a GitHub

```bash
git push -u origin main
```

---

## 🚀 Despliegue del proyecto en la nube publica Vercel.

### 1. Realice la vinculacion del repositorio con Vercel

- Ingresé a [https://vercel.com](https://vercel.com) y e ingrese con mi cuenta de GitHub.
- Hice clic en **"New Project"**.
- Seleccioné el repositorio `Pokedex`.

### 2. Configuré las opciones de despliegue

Vercel detectó automáticamente el framework Angular. Verifiqué y confirmé lo siguiente:

- **Framework Preset**: Angular
- **Build Command**: `ng build`
- **Output Directory**: `dist/pokedex-angular`

Hice clic en **Deploy**.

### 3. Proceso automático de despliegue

- Vercel realizo la instalacion de las dependencias (`npm install`)
- Compiló la app (`ng build --prod`)
- Subió los archivos estáticos a su CDN global

Al finalizar, recibí la URL de producción:

📎 [https://pokedex-chi-ashen.vercel.app/](https://pokedex-chi-ashen.vercel.app/)

---

## 🛠️ Ajustes tomados en cuenta para producción

### ✔️ Rutas de imágenes

Corregí rutas relativas de imágenes a absolutas en el archivo que se encuentra en la ruta `src/environments/environment.prod.ts`, linea `imagesPath: '/pokedex-angular/assets/images`, esto con el fin de lograr asegurar la carga correcta en producción:

```html
<!-- Antes -->
<export const environment = {
  production: true,
  pokeApi: 'https://pokeapi.co/api/v2',
  pokeApiGraphQL: 'https://beta.pokeapi.co/graphql/v1beta',
  homeAngular: 'https://angular.io/',
  homePokeApi: 'https://pokeapi.co/',
  keilerLinkedin: 'https://www.linkedin.com/in/keilermora/',
  pokedexGithub: 'https://github.com/keilermora/pokedex-angular',
  imagesPath: '/pokedex-angular/assets/images',
  language: 'en',
  languageId: 9,
};>

<!-- Después -->
<export const environment = {
  production: true,
  pokeApi: 'https://pokeapi.co/api/v2',
  pokeApiGraphQL: 'https://beta.pokeapi.co/graphql/v1beta',
  homeAngular: 'https://angular.io/',
  homePokeApi: 'https://pokeapi.co/',
  keilerLinkedin: 'https://www.linkedin.com/in/keilermora/',
  pokedexGithub: 'https://github.com/keilermora/pokedex-angular',
  imagesPath: '/assets/images',
  language: 'en',
  languageId: 9,
};>
```

### ✔️ Optimización en `angular.json`

Tuve que modificar los límites de advertencia en `angular.json` para evitar errores al compilar:

```angular.json

<!-- Antes -->
"type": "initial",
"maximumWarning": "500kb",
"maximumError": "1mb"
},
{
  "type": "anyComponentStyle",
  "maximumWarning": "2kb",
  "maximumError": "12kb"

<!-- Después -->
"type": "initial",
"maximumWarning": "700kb",
"maximumError": "1mb"
},
{
  "type": "anyComponentStyle",
"maximumWarning": "8kb",
"maximumError": "12kb"
```


---

## 🔁 Despliegue automático con GitHub

Cada vez que realizo un `git push` a la rama `main`, Vercel detecta los cambios y realiza automáticamente un nuevo despliegue.

### Ejemplo practico:

```bash
git add .
git commit -m "Agregado nuevo componente de búsqueda"
git push origin main
```



---

## 📌 Resumen de los comandos clave 

|                  Acción                   |                        Comando                       |                                         Descripción                                                     |
|-------------------------------------------|------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Instalar Angular CLI                      | `npm install -g @angular/cli`                        | Instala Angular CLI de forma global para usarlo en cualquier proyecto Angular desde la terminal.        |
| Crear nuevo proyecto Angular              | `ng new nombre-proyecto`                             | Crea un nuevo proyecto Angular con la estructura básica.                                                |
| Ingresar a la carpeta del proyecto        | `cd nombre-proyecto`                                 | Entra al directorio raíz del proyecto para trabajar desde allí.                                         |
| Instalar dependencias                     | `npm install`                                        | Instala todas las dependencias necesarias definidas en `package.json`.                                  |
| Ejecutar servidor de desarrollo           | `npm start`                                          | Inicia el servidor de desarrollo en `http://localhost:4200/`.                                           |
| Compilar la aplicación para producción    | `npm run build`                                      | Genera una versión optimizada del proyecto en la carpeta `dist/`.                                       |
| Ejecutar pruebas unitarias                | `ng test`                                            | Ejecuta las pruebas unitarias definidas en el proyecto con Karma.                                       |
| Ejecutar pruebas end-to-end               | `ng e2e`                                             | Corre pruebas end-to-end usando Protractor.                                                             |
| Verificar versión de Angular              | `ng version`                                         | Muestra la versión actual del CLI de Angular y de los paquetes instalados.                              |
| Crear un componente                       | `ng generate component nombre-componente`            | Crea un nuevo componente con sus archivos asociados (`.ts`, `.html`, `.scss`, `.spec.ts`).              |
| Crear un servicio                         | `ng generate service nombre-servicio`                | Genera un nuevo servicio Angular.                                                                       |
| Inicializar repositorio Git               | `git init`                                           | Crea un repositorio Git local en la carpeta actual.                                                     |
| Agregar archivos al área de staging       | `git add .`                                          | Añade todos los archivos del proyecto al área de preparación.                                           |
| Realizar commit con mensaje               | `git commit -m "mensaje"`                            | Guarda los cambios en el repositorio local con un mensaje descriptivo.                                  |
| Cambiar nombre a la rama principal        | `git branch -M main`                                 | Renombra la rama actual a `main`, como estándar moderno.                                                |
| Crear repositorio remoto (GitHub)         | Desde GitHub                                         | Ve a GitHub y crea un nuevo repositorio vacío.                                                          |
| Agregar repositorio remoto a Git          | `git remote add origin https://github.com/usuario/repositorio.git` | Conecta tu repositorio local con el remoto en GitHub.                                     |
| Subir código al repositorio remoto        | `git push -u origin main`                            | Envía tu proyecto a GitHub y deja la rama `main` como principal.                                        |
| Clonar repositorio desde GitHub           | `git clone https://github.com/usuario/repositorio.git` | Descarga un proyecto completo desde GitHub a tu equipo local.                                         |
| Ver estado actual del repositorio         | `git status`                                         | Muestra los archivos modificados, sin seguimiento o pendientes de commit.                               |
| Ver historial de commits                  | `git log`                                            | Muestra el historial de commits del repositorio.                                                        |
| Crear una nueva rama                      | `git checkout -b nombre-rama`                        | Crea y se mueve a una nueva rama en Git.                                                                |
| Cambiar a otra rama existente             | `git checkout nombre-rama`                           | Cambia de rama en el repositorio local.                                                                 |
| Fusionar rama con `main`                  | `git merge nombre-rama`                              | Fusiona los cambios de una rama con la rama `main`.                                                     |
| Descargar últimos cambios del remoto      | `git pull`                                           | Actualiza tu proyecto local con los últimos cambios del repositorio remoto.                             |
| Subir cambios al repositorio remoto       | `git push`                                           | Sube los cambios que has hecho localmente al repositorio remoto.                                        |


