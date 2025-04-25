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

## 📌 Resumen de Comandos Clave

|           Acción             |                Comandos                     |
|------------------------------|---------------------------------------------|
| Instalar Angular CLI         | `npm install -g @angular/cli`               |
| Instalar dependencias        | `npm install`                               |
| Ejecutar servidor local      | `npm start`                                 |
| Compilar para producción     | `npm run build`                             |

