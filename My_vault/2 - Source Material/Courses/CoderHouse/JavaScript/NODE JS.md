2025-06-18 22:54

**Status:** #In_progress 
**Tags:** #JS #JavaScript #NodeJS 
##### **References**
[[Java Script]], [[GitHub]]

--------------
**Índice:**
[[#🚀 ¿Qué es Node.js?]]
[[#📦 ¿Qué es npm?]]
[[#Framework vs Librería]]
[[#Librerías Descarga de Archivos o CDN]]

---
## 🚀 ¿Qué es Node.js?

>**Node.js** es un **entorno de ejecución** que permite correr código JavaScript **fuera del navegador**, es decir, en el **servidor**.

🔧 Fue creado sobre el motor **V8** de Google Chrome (el mismo que interpreta JavaScript en el navegador), pero adaptado para usarse en computadoras o servidores.

>**Es JavaScript pero para Backend**, o sea es una versión de JS que no necesita tener un navegador para ser interpretado, sino que lo vana  interpretar directamente los servidores de Backend.

Necesito esta herramienta para ejecutar código de React por ejemplo.

>De Node JS usamos **npm (Node Manager Package)**, administrador de paquetes de Node, esta herramienta lo que hace es descargar paquetes de internet e instalarlo en mi proyecto. Así me permite instalar y administrar los paquetes de Node.

 **🧠 ¿Para qué se usa?**

Node.js se utiliza para construir aplicaciones del lado del servidor, como:

- 🌐 **Servidores web**
- 🛒 **APIs para sitios o apps**
- 📡 Aplicaciones en tiempo real (como chats o juegos)
- ⚙️ Automatización de tareas (scripts de backend)    

#### ✅ Características principales

| Característica                     | Descripción                                                                                                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 🧵 **Asincrónico y no bloqueante** | Node puede manejar muchas tareas al mismo tiempo sin "congelarse", gracias a su modelo basado en eventos. Ideal para apps rápidas. |
| ⚡ **Muy rápido**                   | Usa el motor V8 de Chrome, que es altamente optimizado.                                                                            |
| 📦 **Gran ecosistema**             | Usa **npm** (Node Package Manager), el mayor repositorio de paquetes de software del mundo.                                        |
| 🌐 **Usa JavaScript**              | Los desarrolladores web pueden usar el mismo lenguaje en el cliente (navegador) y en el servidor.                                  |
**🧪 Ejemplo básico con Node.js**
Un pequeño **servidor web** que responde “Hola, mundo”:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hola, mundo');
});

server.listen(3000, () => {
    console.log('Servidor corriendo en http://localhost:3000');
});
```

Para ejecutarlo:

1. Guarda este código en un archivo, por ejemplo `app.js`
2. Abre tu terminal y escribe:

    ```bash
    node app.js
    ```
    
3. Abre tu navegador y ve a: [http://localhost:3000](http://localhost:3000/)


---
### 📦 ¿Qué es npm?
**Node Package Manager**
`npm` es el **gestor de paquetes** de Node.js. Te permite instalar librerías o frameworks fácilmente.

- Es básicamente un repositorio de paquetes.
- Es una herramienta que tiene Node JS #NodeJS que sirve como administrador o gestor de paquetes/librerías
- Me permite instalar y administrar los paquetes de #NodeJS. Descarga paquetes de internet y lo instala en mi proyecto. 

Ejemplo:

```bash
npm install express
```

Esto instala **Express**, un popular framework para construir servidores con Node.js.

---
#### 🎯 ¿Cuándo deberías usar Node.js?

- Cuando necesitas manejar **muchas conexiones al mismo tiempo** (como en un chat en tiempo real).
- Para construir APIs REST rápidas y ligeras.
- Si ya sabes JavaScript y quieres trabajar también en el **backend**.

---
### Framework vs Librería

**Framework**: es un marco de trabajo donde tenemos todas las herramientas necesarias para hacer un trabajo. Es conjunto de herramientas, bibliotecas y convenciones que proporcionan una estructura predefinida para el desarrollo de software
Ej: Bootstrap

**Librería**: es una herramienta particular que utilizo para hacer determinada actividad o acción
Ej: React

---
### Librerías: Descarga de Archivos o CDN

Las librerías se incorporan al proyecto como **archivos**
Se vinculan a nuestra aplicación en el HTML como cualquier otro script de #JavaScript 

- Para incorporar estas librerías a nuestro **HTML** lo podemos hacer de 2 maneras:

**1. Descarga de los archivos de la librería**
```html
<script src="js/libreria.js"></script>
```

**2. A través de un CDN**:
Sería como el url que nos trae la librería
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
```


- En la **terminal** al inicializar **npm** con *npm init* y luego *npm install <librería>*
**3. A través de npm**:
```bash
npm install bootstrap@5.3.7
````


