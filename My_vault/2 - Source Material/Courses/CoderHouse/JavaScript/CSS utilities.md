2025-08-11 20:10

**Status:** #In_progress 
**Tags:** #coderHouse #NodeJS 
##### **References**
- [[#border-box]]
- [[#🧱 ¿Qué es `.wrap`?]]
- [[#🔍 ¿Qué hace `display block;`?]]

---
## border-box
[[#**References**]]

```css
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
```


Esa línea de CSS que estás viendo:

```css
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
```

Sirve para **establecer cómo se calcula el tamaño de un elemento HTML** (ancho y alto), y es muy importante para el diseño y la maquetación web.

#### 📦 ¿Qué hace `box-sizing: border-box`?

Por defecto, cuando defines un `width` o `height` en CSS, **solo se aplica al contenido** del elemento. Los `padding` y `border` se suman al tamaño total, lo que puede desajustar tu diseño.

Con `box-sizing: border-box`, **el ancho y alto incluyen el contenido + padding + borde**, lo que hace mucho más fácil controlar el tamaño total del elemento.
#### 🧱 Ejemplo práctico

#### Sin `border-box` (comportamiento por defecto):

```css
box-sizing: content-box;
width: 200px;
padding: 20px;
border: 5px solid black;
```

🔹 Tamaño total real: **200 + 40 (padding) + 10 (border) = 250px**

#### Con `border-box`:

```css
box-sizing: border-box;
width: 200px;
padding: 20px;
border: 5px solid black;
```

🔹 Tamaño total real: **200px** (el padding y borde ya están incluidos)
##### 🔧 ¿Y los prefijos `-webkit-` y `-moz-`?

- `-webkit-`: Para navegadores basados en WebKit (como Safari antiguos o versiones antiguas de Chrome).
    
- `-moz-`: Para versiones antiguas de Firefox.
    

Hoy en día, la mayoría de los navegadores modernos ya reconocen `box-sizing` sin prefijos, pero se ponen por compatibilidad retroactiva.

##### ✅ Conclusión

Este bloque de CSS:

```css
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
```

✔️ Hace que los elementos **calculen su tamaño total incluyendo borde y padding**  
✔️ Ayuda a que el diseño sea **más predecible y fácil de controlar**  
✔️ Incluye prefijos para compatibilidad con navegadores antiguos

---
### 🧱 ¿Qué es `.wrap`?
[[#**References**]]

```css
.wrap {
	margin: auto;
	max-width: 800px;
	width: 90%;
}
```


`.wrap` es una **clase CSS**, normalmente usada como **contenedor envolvente** ("wrapper") para centrar contenido y limitar su ancho en una página web.

#### `margin: auto;`

- Centra horizontalmente el elemento dentro de su contenedor **siempre y cuando tenga un ancho definido**.
    
- Es equivalente a: `margin-left: auto; margin-right: auto;`
    
- Muy común para centrar bloques como `<div>` en el medio de la pantalla o del contenedor padre.
    

#### `max-width: 800px;`

- Define un **ancho máximo** para el elemento: nunca será mayor a 800px, incluso si `width` le da un valor mayor.
    
- Es útil para asegurar que el contenido **no se estire demasiado** en pantallas grandes (lo cual mejora la legibilidad).
    

#### `width: 90%;`

- Define que el ancho del elemento será el **90% del ancho del contenedor padre**.
    
- Es útil para que el diseño sea **responsive**: el ancho se adapta a diferentes tamaños de pantalla.
    

> ⚠️ Pero como hay también un `max-width: 800px`, este 90% solo se aplicará **hasta que llegue a 800px**. Luego de eso, se queda fijo.

##### 📱 ¿Qué resultado da esto?

Imagina que estás en una pantalla de 1200px de ancho:

- `width: 90%` ⇒ 90% de 1200px = 1080px
    
- Pero el `max-width: 800px` **limita** eso ⇒ se queda en **800px**


Ahora en una pantalla de 600px:

- 90% de 600px = 540px ⇒ como está por debajo de 800px, se aplica ese valor
    

Además, `margin: auto` lo centra horizontalmente en ambos casos.

##### ✅ ¿Para qué se usa esto normalmente?

Este tipo de clase `.wrap` se usa muchísimo como:

```html
<div class="wrap">
  <!-- contenido principal aquí -->
</div>
```

Sirve para:

- Centrar el contenido en la página
    
- Limitar el ancho para evitar que se vea demasiado extendido
    
- Hacer que se adapte a pantallas más pequeñas (diseño responsive)
    

---

Perfecto, vamos a explicar esta línea dentro del selector:

```css
.tareas .lista li a {
	color: #212121;
	display: block;
}
```

La parte clave de tu duda es:

```css
display: block;
```

---
### 🔍 ¿Qué hace `display: block;`?
[[#**References**]]

Le dice al navegador que el enlace (`<a>`) debe comportarse como un **elemento de bloque**, en lugar de su comportamiento por defecto que es **en línea (inline)**.

#### ✅ ¿Qué cambia al usar `display: block` en un `<a>`?

Por defecto, un enlace (`<a>`) es **inline**, lo que significa:

- Solo ocupa el **ancho necesario para su contenido**
    
- No se puede aplicar `width`, `height`, `margin` o `padding` vertical de forma completa
    
- No salta a una nueva línea
    

Cuando le pones `display: block`, entonces:

- El enlace ocupa **todo el ancho disponible del contenedor**
    
- Puedes aplicar `width`, `height`, `padding`, `margin`, etc. sin restricciones
    
- El elemento aparece en **una nueva línea** (como un `<div>` o `<p>`)
    
#### 📌 ¿Por qué es útil en este caso?

En este selector:

```css
.tareas .lista li a {
	color: #212121;
	display: block;
}
```

Estás diciendo que **todos los enlaces dentro de ítems de una lista (`li`) dentro de `.lista` dentro de `.tareas`** deben:

1. Tener color de texto oscuro `#212121`
    
2. Comportarse como bloques
    

Esto es común cuando se quiere que **todo el área del ítem sea clickeable**, no solo el texto del enlace.

##### 📱 Ejemplo visual:

#### Sin `display: block`:

```html
<li><a href="#">Tarea 1</a></li>
```

🔹 Solo el texto "Tarea 1" es clickeable

##### Con `display: block` + padding:

```html
<li><a href="#">Tarea 1</a></li>
```

```css
li a {
  display: block;
  padding: 10px;
}
```

🔹 **Todo el área con padding es clickeable**, no solo el texto.  
🔹 Esto mejora la **usabilidad en móviles** y la **experiencia de usuario**.

---

