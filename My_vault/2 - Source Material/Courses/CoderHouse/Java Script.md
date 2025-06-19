2025-06-18 22:41

**Tags:** 
###### **References:** 

**JavaScript** es un lenguaje de programación que se utiliza principalmente para hacer páginas web interactivas. Junto con **HTML** y **CSS**, forma la base del desarrollo web en el navegador.

Es un lenguaje levemente tipado y no necesariamente orientado a objetos

No necesita ser **compilado** [[Java Script#**Diferencia entre un lenguaje interpretado y un lenguaje compilado**]] , es interpretado directamente con el navegador, o sea que lo único que necesito para programar en JS es un archivo de extensión .js y cualquier navegador lo entiende.

### ¿Para qué se usa JavaScript?

- **Interactividad**: botones que responden al hacer clic, menús desplegables, formularios que validan datos sin recargar la página, etc.
    
- **Manipulación del DOM**: cambiar el contenido de una página web mientras se visualiza.
    
- **Animaciones**: mover elementos, mostrar u ocultar cosas, transiciones visuales.
    
- **Comunicación con servidores**: enviar y recibir datos sin recargar la página (AJAX o Fetch API).
    
- **Aplicaciones completas**: JavaScript permite crear aplicaciones web completas, incluso juegos o editores de texto, directamente en el navegador.
    

### ¿Dónde se ejecuta?

- Principalmente en el **navegador web** (Chrome, Firefox, Safari, etc.).
    
- También en el **servidor** gracias a tecnologías como **Node.js**.
    

### ¿Es lo mismo que Java?

No. A pesar del nombre, **JavaScript y Java no son lo mismo**. Tienen sintaxis parecida en algunos aspectos, pero son lenguajes distintos.

### Ejemplo básico en JavaScript:

```javascript
alert("Hola, mundo!");
```

Este código muestra una ventana emergente en el navegador con el mensaje “Hola, mundo!”.


#### **Diferencia entre un lenguaje interpretado y un lenguaje compilado**
La diferencia está en **cómo se ejecuta el código que escribes**.
### 🔹 **Lenguaje Compilado**

Un **lenguaje compilado** necesita ser **traducido completamente** a lenguaje máquina (binario) **antes de ejecutarse**. Esta traducción la hace un programa llamado **compilador**.
#### Ejemplos:
- C
- C++
- Go
- Rust
#### Características:

- ✅ **Más rápido en ejecución** (porque ya está traducido).   
- ❌ **No puedes probar el código directamente**; tienes que compilarlo primero.    
- ✅ **Menos errores en tiempo de ejecución**, ya que muchos se detectan durante la compilación.
    
### 🔹 **Lenguaje Interpretado**

Un **lenguaje interpretado** se **ejecuta línea por línea**, sin necesidad de compilar todo el código antes. Usa un programa llamado **intérprete**.

#### Ejemplos:
- JavaScript
- Python
- PHP
- Ruby
#### Características:

- ✅ **Fácil de probar y modificar**, ideal para desarrollo rápido.
- ❌ **Más lento** que uno compilado, porque se traduce en el momento de ejecutarse.
- ❌ Puede tener **más errores en tiempo de ejecución**.

---
### 🔸 ¿Y Java?

Java es un **caso mixto**: el código se **compila** a un formato intermedio llamado **bytecode**, y luego se **interpreta o se ejecuta** por una máquina virtual (JVM).

### Resumen en una tabla:

| Característica         | Lenguaje Compilado | Lenguaje Interpretado    |
| ---------------------- | ------------------ | ------------------------ |
| Traducción             | Antes de ejecutar  | Mientras se ejecuta      |
| Velocidad de ejecución | Más rápido         | Más lento                |
| Ejemplo                | C, C++, Go         | JavaScript, Python, Ruby |
| Facilidad para probar  | Menor              | Mayor                    |
| Detección de errores   | En compilación     | En tiempo de ejecución   |
#### **Ejemplo simple** hecho en:
1. 🔹 Un **lenguaje compilado** (C)
2. 🔹 Un **lenguaje interpretado** (Python)
---
### ✅ Ejemplo: Mostrar “Hola, mundo”

---
#### 🔹 **Lenguaje Compilado: C**

```c
#include <stdio.h>

int main() {
    printf("Hola, mundo\n");
    return 0;
}
```

**¿Cómo se ejecuta?**

1. Guardas el archivo como `hola.c`
2. Lo **compilas**:
    ```bash
    gcc hola.c -o hola
    ```    
3. Ejecutas el archivo compilado:
    ```bash
    ./hola
    ```    

---
#### 🔹 **Lenguaje Interpretado: Python**

```python
print("Hola, mundo")
```

**¿Cómo se ejecuta?**

1. Guardas el archivo como `hola.py`    
2. Lo ejecutas directamente:

    ```bash
    python hola.py
    ```

---
### 🔄 Diferencia clave:

- En C necesitas **compilar primero**, y eso genera un **archivo ejecutable**.
- En Python **no compilas**, el intérprete lee y ejecuta el código **línea por línea**.

---
