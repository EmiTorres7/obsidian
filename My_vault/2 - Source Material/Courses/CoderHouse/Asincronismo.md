2025-08-20 19:59

**Tags:** #JS #NodeJS #single-threaded #event_loop #call_stack #Callback_queue 

## Asincronismo, Errores y Peticiones

###### **References:** 
**Link:** [Funcionamiento del código en JavaScript](latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)
**Link:** [JSON API]([JSONPlaceholder - Free Fake REST API](https://jsonplaceholder.typicode.com/))
**Link:** [AJAX (JavaScript Asíncrono y XML)]([Primeros Pasos](https://developer.mozilla.org/es/docs/conflicting/Web/Guide/AJAX_21419c7dfa67c94789f037a33c4e4e3e)) 
**Link:**[Loupe Event Loop](http://latentflip.com/loupe/?code=Y29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)
**Clase:** [Clase Asincronismo y Errores]([Unidad 8- Asincronismo y errores - Google Slides](https://docs.google.com/presentation/d/1xKJyUcNJ53RU81T9CW5XqlqqAjTSJMjaWuPql0mOcEQ/edit?slide=id.p1#slide=id.p1))

---

#JavaScript es un lenguaje #single-threaded (de un solo hilo)**, maneja la asincronía a través del **Event Loop**, el cual permite que las tareas no bloqueantes sean manejadas en 2do plano y sus resultados procesados cuando estén disponibles.

- El **asincronismo** se maneja principalmente a través de **callbacks**, promesas y las más recientes **async/await**

>Al ser #single-threaded sólo puede realizar una tarea a la vez dentro de su hilo principal de ejecución.

>Para gestionar la ejecución de múltiples tareas, #JavaScript utiliza una estructura llamada **Call Stack** y un mecanismo conocido como **Event Loop**, estos son fundamentales para entender cómo se maneja tanto la ejecución sincrónica como asincrónica en #JavaScript  

##### **Call Stack:** 
O pila de llamadas, es una estructura de datos en la que se registran las funciones que están siendo ejecutadas.
Cada vez que se invoca una función, esta se apila en el #call_stack
Cuando una función se termina de ejecutar, se desapila del #call_stack, y el control se devuelve a la función en la pila.

##### **Event Loop:**
Permite a #JavaScript manejar operaciones asincrónicas a pesar de que este sea #single-threaded 
Mientras que el #call_stack  maneja funciones sincrónicas, el #event_loop supervisa la cola de tareas (también llamada #Callback_queue) donde se van colocando las operaciones asincrónicas una vez que están listas para ser ejecutadas.

![[Pasted image 20250820224323.png]]

Cuando el #call_stack está vacío, el #event_loop toma la primera tarea del #Callback_queue y la coloca en el #call_stack para su ejecución (WebAPIs)
Así este proceso continúa asegurando que las tareas asincrónicas se ejecuten cuando el hilo principal esté libre.

El #event_loop es una herramienta que permite que #JavaScript pueda manejar tareas asincrónicas como temporizadores (setTimeout o setInterval) o promesas (Promise) sin bloquear el código. Así estas operaciones que tardan más no detienen el flujo del programa.

>Mientras que el #call_stack maneja las funciones sincrónicas, El #event_loop supervisa la cola de tareas #Callback_queue que es donde se colocan las operaciones asincrónicas una vez que están lista para ejecutarse

>Cuando el #call_stack está vacío, el #event_loop toma la primera tarea del #Callback_queue y la coloca en el #call_stack para su ejecución. Así continúa este proceso asegurando que las tareas asincrónicas se ejecuten cuando el hilo o pila en el #call_stack esté libre 

>Todas las funciones van al #Callback_queue y el #event_loop es la herramienta que va a determinar de mandar eso que está en el #Callback_queue al #call_stack si es que esta se encuentra vacía 
---
















