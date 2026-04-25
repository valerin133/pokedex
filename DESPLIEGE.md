Paso 1 — Clonar el Repositorio y Enlazarlo con Visual Studio Code

Dentro del repositorio en GitHub se copió el enlace del repositorio.
Se abrió la terminal del computador y se ejecutó el comando para descargarlo.

Se abrió Visual Studio Code.
Se fue a Archivo, luego Abrir carpeta y se seleccionó la carpeta pokedex clonada.
Visual Studio Code detectó automáticamente que era un repositorio Git.
Se copiaron todos los archivos del proyecto PokeDex dentro de la carpeta pokedex.


Paso 2 — Subir el Código a GitHub

Se abrió la terminal integrada de Visual Studio Code desde Terminal, luego Nueva terminal.
Se ejecutaron los siguientes comandos:

git add .
git commit -m "feat: initial commit - PokeDex web app"
git push origin main

Se verificó en GitHub que todos los archivos aparecieron correctamente en el repositorio pokedex.


Paso 3 — Creación del Recurso en Azure

Se ingresó al portal de Azure en https://portal.azure.com con la cuenta personal.
En la barra de búsqueda se escribió Static Web Apps y se seleccionó el servicio.
Se hizo clic en Crear.
Se completó el formulario con los datos del proyecto, asignando el nombre poquedexvc al recurso.
Se seleccionó GitHub como origen del código.
Se inició sesión con GitHub y se autorizó el acceso de Azure.
Se seleccionó el repositorio pokedex y la rama main.
Se dejó la ubicación de la aplicación como / y los demás campos vacíos.
Se hizo clic en Revisar y crear, luego en Crear.
Azure tardó aproximadamente 2 minutos en desplegar el recurso poquedexvc.
Se copió la URL pública generada desde la sección Información general del recurso.


Paso 4 — Configuración de los Encabezados de Seguridad HTTP

Dentro de la carpeta pokedex en Visual Studio Code se creó un archivo llamado staticwebapp.config.json.

Se guardó el archivo y se ejecutaron los siguientes comandos para subir el cambio:

git add staticwebapp.config.json
git commit -m "security: add HTTP security headers"
git push origin main

GitHub Actions desplegó automáticamente los cambios en Azure en aproximadamente 2 minutos.


Paso 5 — Verificación del Despliegue

Se abrió la URL pública en el navegador y se confirmó que la aplicación cargaba correctamente.
Se verificó que el navegador mostrara el candado de HTTPS activo.
Se abrieron las DevTools con F12 y se confirmó que no había errores en la consola.
Se ingresó a https://securityheaders.com, se escribió la URL de la aplicación y se hizo clic en Scan.
Se obtuvo una calificación A+ y se tomó captura de pantalla del resultado.


Errores Encontrados y Soluciones

Error 1 — Las imágenes de los Pokémon no cargaban

En la consola del navegador aparecía un error de Content-Security-Policy bloqueando imágenes externas.
Se actualizó la directiva img-src en staticwebapp.config.json agregando los dominios de las imágenes.
Se subió el cambio con git push y el problema se resolvió.

Error 2 — La calificación en securityheaders.com era C

El escaneo retornaba calificación C con advertencias sobre encabezados faltantes.
Se agregaron los encabezados Permissions-Policy y Referrer-Policy al archivo staticwebapp.config.json.
Se volvió a hacer push y la calificación mejoró a A+.