# Configuración normal: Node.js y Angular CLI global

## 1. Instalar Node.js

1. Descargue la versión **LTS** más reciente desde [nodejs.org](https://nodejs.org/).
2. Ejecute el instalador y permita que agregue Node.js al `PATH`.
3. Cierre y abra una nueva terminal. Verifique la instalación:

```powershell
node --version
npm --version
```

## 2. Instalar Angular CLI globalmente

Instale la versión de Angular CLI usada por el proyecto:

```powershell
npm install --global @angular/cli@22
ng version
```

Para crear otro proyecto con esta versión:

```powershell
ng new mi-proyecto
```

## 3. Instalar dependencias del proyecto

Abra una terminal en la raíz del repositorio y ejecute:

```powershell
npm install
```

## 4. Ejecutar la aplicación

Ejecución habitual:

```powershell
ng serve
```

Con host y puerto específicos:

```powershell
ng serve --host=127.0.0.1 --port=4200
```

Para pruebas desde la red local:

```powershell
ng serve --host=0.0.0.0 --port=4200 --allowed-hosts=true
```

Alternativamente, puede utilizar los scripts del proyecto:

```powershell
npm start
npm start -- --host=127.0.0.1 --port=4200
```

Abra la aplicación en `http://127.0.0.1:4200`. Para detener el servidor use `Ctrl + C`.
