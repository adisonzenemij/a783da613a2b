# Configuración con Node Version Manager (NVM)

NVM permite instalar y alternar entre varias versiones de Node.js. En Windows puede instalar **nvm-windows** desde [sus publicaciones oficiales](https://github.com/coreybutler/nvm-windows/releases).

## Configurar variables de entorno y PATH

### Windows: NVM for Windows

Durante la instalación elija las carpetas que prefiera para NVM y para el enlace de Node.js. Por ejemplo:

```text
NVM_HOME    = C:\Software\NodeVersionManager
NVM_SYMLINK = C:\Program Files\nodejs
```

En **Variables de entorno** de Windows, compruebe que existan las variables de usuario o del sistema `NVM_HOME` y `NVM_SYMLINK` con las rutas elegidas. Después, en la variable `Path`, agregue estas dos entradas:

```text
%NVM_HOME%
%NVM_SYMLINK%
```

No instale Node.js manualmente dentro de la carpeta definida como `NVM_SYMLINK`; NVM administra ese enlace al ejecutar `nvm use`. Si anteriormente instaló Node.js de forma directa y utiliza la misma carpeta, desinstálelo o defina otro directorio para evitar conflictos.

Al terminar, cierre todas las terminales abiertas y abra una nueva para que Windows reconozca las variables.

### Linux y macOS: NVM

En Linux/macOS, NVM se configura con la variable `NVM_DIR`, que define la carpeta donde se instalará. La ubicación usual es `~/.nvm`, pero puede elegir otra ruta según sus preferencias. Agregue esta configuración al archivo de inicio de su terminal, por ejemplo `~/.bashrc` o `~/.zshrc`:

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
```

Si eligió otra carpeta, reemplace `"$HOME/.nvm"` por la ruta deseada. Abra una terminal nueva o ejecute `source ~/.bashrc` (o el archivo que corresponda) antes de utilizar `nvm`.

## 1. Instalar y seleccionar Node.js con NVM

Después de instalar NVM, abra una nueva terminal y ejecute:

```powershell
nvm install lts
nvm use lts
node --version
npm --version
```

También puede instalar y seleccionar una versión concreta de Node.js:

```powershell
nvm install 22.17.0
nvm use 22.17.0
```

> Si el alias `lts` no está disponible en la versión de NVM instalada, seleccione una versión específica de Node.js compatible con Angular 22.

## 2. Usar Angular sin instalación global

No es necesario instalar Angular CLI globalmente. Para generar un nuevo proyecto con la versión requerida use `npx`:

```powershell
npx @angular/cli@22 new mi-proyecto
```

Este repositorio ya incluye Angular CLI como dependencia local.

## 3. Instalar dependencias del proyecto

Abra una terminal en la raíz del repositorio y ejecute:

```powershell
npm install
```

## 4. Ejecutar la aplicación con la CLI local

Ejecución habitual:

```powershell
node node_modules/@angular/cli/bin/ng serve
```

Con host y puerto específicos:

```powershell
node node_modules/@angular/cli/bin/ng serve --host=127.0.0.1 --port=4200
```

Para una prueba local usando la configuración de producción:

```powershell
node node_modules/@angular/cli/bin/ng serve --host=0.0.0.0 --port=4200 --configuration=production --allowed-hosts=true
```

Abra la aplicación en `http://127.0.0.1:4200`. Para detener el servidor use `Ctrl + C`.
