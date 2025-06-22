**References:**
[[NODE JS]] [[Java Script]] [[GitHub]]
### **"Diccionario"**:
Es simplemente un **objeto** que almacena pares clave-valor. Aquí tienes ejemplos básicos de cómo crear y usar un diccionario en JavaScript:
#### 🟢 **1. Crear un diccionario**

```javascript
let diccionario = {
  nombre: "Carlos",
  edad: 30,
  ciudad: "Madrid"
};
```
#### 🟢 **2. Acceder a valores**

```javascript
console.log(diccionario["nombre"]);  // Carlos
console.log(diccionario.edad);       // 30
```
#### 🟢 **3. Agregar o modificar elementos**

```javascript
diccionario["profesion"] = "Ingeniero";
diccionario.edad = 31;
```
#### 🟢 **4. Eliminar una clave**

```javascript
delete diccionario.ciudad;
```
#### 🟢 **5. Recorrer un diccionario**

```javascript
for (let clave in diccionario) {
  console.log(clave + ": " + diccionario[clave]);
}
```
#### 🟢 **6. Verificar si una clave existe**

```javascript
if ("nombre" in diccionario) {
  console.log("Existe la clave 'nombre'");
}
```

Si quieres algo más parecido a un diccionario con funciones adicionales (como en Python), puedes usar el objeto `Map`:

```javascript
let mapa = new Map();
mapa.set("nombre", "Ana");
mapa.set("edad", 25);

console.log(mapa.get("nombre")); // Ana
```

------------


























