# Despliegue de aplicación PokeDex en Vercel

## 🖥️ Descripción

En este documento, explico cómo realice el desplegué de la aplicación **PokeDex** en la plataforma **Vercel**. Desde la conexión de mi repositorio [Pokedex](https://github.com/LuisDTech/Pokedex) de GitHub hasta la publicación final de la aplicación [Pokedex](https://pokedex-chi-ashen.vercel.app/), todo el proceso lo realicé paso a paso, asegurándome de que todo estuviera funcionando correctamente. Aquí te dejo los detalles completos de mi experiencia y cómo realice el despliegue.

---

## 📅 Pasos para pesplegar la aplicación PokeDex en Vercel

### 1. Conecté mi proyecto con Vercel

1. Una vez que accedí a mi cuenta de **Vercel**, desde el panel principal hice clic en el botón **"New Project"** para crear un nuevo despliegue.
2. En la siguiente pantalla, me pidió conectar mi cuenta de **GitHub**. Como ya había vinculado mi cuenta de GitHub en la creación de la cuenta, simplemente seleccioné **GitHub**.
3. Vercel escaneó automáticamente mis repositorios de GitHub y me presentó una lista de todos ellos. Seleccioné el repositorio [Pokedex](https://github.com/LuisDTech/Pokedex).

### 2. Configuración del proyecto en Vercel

1. Después de seleccionar el repositorio, Vercel intentó detectar automáticamente el marco de trabajo de la aplicación. Como la aplicación se encuentra creada en el framework **Angular**, Vercel lo reconoció inmediatamente.
2. Me pidió confirmar algunas configuraciones predeterminadas. Aquí opté por lo siguiente:
   - **Framework**: Angular (Vercel lo detectó correctamente).
   - **Root Directory**: Dejé la opción predeterminada, ya que mi proyecto se encontraba en la raíz del repositorio.
3. No necesité cambiar ninguna configuración adicional en este paso, ya que no requería configuraciones específicas para la aplicación. Solo hice clic en **"Deploy"** para iniciar el despliegue.

### 3. Despliegue automático

1. Vercel comenzó a compilar y desplegar la aplicación. Este proceso tardó solo unos minutos y consistió en los siguientes pasos:
   - **Instalación de dependencias**: Vercel ejecutó el comando `npm install` para instalar todas las dependencias que tenía en el archivo `package.json`.
   - **Construcción de la aplicación**: Usó el comando `ng build --prod` para construir la versión optimizada de mi aplicación Angular.
   - **Despliegue de archivos estáticos**: Los archivos generados fueron enviados a la red global de distribución de contenido (CDN) de Vercel, lo que asegura tiempos de carga rápidos desde cualquier lugar del mundo.
2. Una vez completado el proceso, Vercel me proporcionó una URL única para acceder a mi aplicación desplegada. Esta URL es: `https://pokedex-chi-ashen.vercel.app/`, y ya podía ver la aplicación en línea [Pokedex](https://pokedex-chi-ashen.vercel.app/).

---

## 🔄 Despliegue automático y actualización continua

Uno de los aspectos más convenientes de usar **Vercel** es que configuró el **despliegue automático** para mi repositorio. Esto significa que cada vez que hago un **push** a la rama `main` de mi repositorio de GitHub, Vercel automáticamente despliega los cambios sin que tenga que hacer nada manualmente.

---

## 🛠 Configuración de Archivos Específicos para Vercel

Durante el proceso de despliegue, tuve que realizar varias modificaciones importantes para asegurarme de que la aplicación funcionara correctamente, especialmente en lo que respecta a la correcta referencia de las imágenes y el tamaño de los archivos.

### 1. Modificación en las Rutas de las Imágenes

Al momento de crear el build de mi aplicación con `ng build --prod`, las rutas de las imágenes no se resolvían correctamente. Esto ocurrió porque las rutas generadas en el archivo de build no correspondían a la estructura del servidor de Vercel. Así que, tuve que actualizar la ruta `path` de las imágenes para asegurarlas en la correcta ubicación.

- En lugar de usar rutas relativas como `../assets/imagen.png`, cambié las rutas para que fueran absolutas a partir de la raíz del proyecto, como `assets/imagen.png`.
- Esto permitió que las imágenes se cargaran correctamente en el entorno de producción.

### 2. Modificación en el archivo `angular.json`

Al momento de generar el build de la aplicación, noté que el tamaño de las imágenes causaba algunos problemas de rendimiento. Así que realicé una modificación en el archivo **`angular.json`** para optimizar cómo se gestionan los activos estáticos, especialmente las imágenes. Esto ayudó a reducir los tiempos de carga de las imágenes y asegurar un mejor rendimiento general.

- Modifiqué las configuraciones dentro de la sección `assets` de `angular.json` para incluir un proceso de optimización adicional para los recursos estáticos.
- Aumenté el tamaño del límite de imágenes en la propiedad `fileReplacements` para manejar correctamente los archivos de gran tamaño.

---

## 🌍 Acceso

Una vez que el despliegue fue exitoso, pude ingresar a la URL proporcionada por Vercel (`https://pokedex-chi-ashen.vercel.app/`) para verificar que la aplicación estuviera funcionando correctamente. Navegué por varias pantallas de la app, revisé el funcionamiento de las funcionalidades principales  y confirmé que todo estaba operativo.

---


Este proceso de despliegue fue rápido y sencillo gracias a las herramientas que Vercel ofrece. Ahora la aplicación está disponible de forma pública y se actualiza automáticamente con cada cambio que realizo en GitHub.
