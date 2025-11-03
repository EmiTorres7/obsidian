2025-10-15 16:53

**Status:** #In_progress 
**Tags:** #base_datos  #data_warehouse 

---
###### **References:** 
**Índice**:
- Qué es una base de datos -> [[#**Base de datos** base_datos]]
- Identificar los diferentes tipos de #base_datos: #bd_relacionales que sería #SQL y #BDD_NoSQL, y su relevancia en el mundo actual -> [[#Tipos de base de datos]]
- Sentencias del sub lenguaje de SL y cuándo es apropiado usarlas
- Tablas y claves [[#Tablas y claves]]
- Identificaremos un #data_warehouse (almacén de datos), sus componentes y el rol que juegan en el análisis de datos
- Operadores en SQL
- Sentencias del sub lenguaje ddl
- DER (Diagrama de Entidad de Relación) **CTRL + R**

**Link:** [Unidad 1 - Google Docs](https://docs.google.com/document/d/1qKsI2OVHUVyRjiDXxQjBgwMah3Hi9O_o8EtYFQH-Cd8/edit?tab=t.0#heading=h.ebzixumzggus)

---
##### **Base de datos** #base_datos 
Es un conjunto de información, usualmente perteneciente a un mismo contexto, que es almacenado sistemáticamente para su posterior uso.

Se compone de una o muchas tablas que, a su vez están compuesta por filas y columnas.
Las tablas guardan información específica de algo.
- Cada **fila** se corresponde a un **Registro** único.
- Cada **columna** será un **atributo o propiedad** 

>Las **tablas** organizan los datos en filas y columnas. Cada tabla se enfoca en un tema o entidad específica, como clientes o productos

>El **esquema de una tabla** define su estructura y especifica qué columnas contiene y qué tipo de datos se pueden almacenar.

- En una **base de datos plana**, podríamos tener una única tabla donde cada fila contiene toda la información del cliente y los detalles de la compra, repitiendo así la información del cliente para cada compra. Sin embargo, esto no es eficiente ya que genera redundancia de datos. Por ejemplo, una tabla en Excel, donde tenemos mucha redundancia

- En una **base de datos relacional**, la información se normaliza y se divide en múltiples tablas, como una tabla para clientes y otra para compras. Cada tabla tiene un propósito específico, y las relaciones entre estas tablas se establecen a través de claves primarias y foráneas.
Aquí se hace una normalización porque tenemos muchas tablas que se relacionan y por ejemplo tendremos una tabla de comprar y otra de proveedores, entonces en la tabla de compras tendremos una columna proveedores y las filas estarán dados por valores que serían los id_provedor que con una clave foránea nos la va a relacionar con la tabla proveedores donde por el id_provedor podremos ver en detalle los datos de esos proveedores, pero en otra tabla; de esta manera tenemos todo más organizado. Así con estos identificadores accedemos a la información de ese proveedor pero en otra tabla.

>Las bases de datos continúan evolucionando, adaptándose a nuevas tecnologías y necesidades, como el análisis de grandes volúmenes de datos **(big data)**, el aprendizaje automático **( #machine_learning)**, y el **Internet de las Cosas (IoT)**.

---
##### Tipos de base de datos

Las #base_datos pueden ser:
- #SQL (Relacionales): se llama así porque cada registro o columna son datos relacionados.
- #NoSQL : tienen tecnologías diferentes entre sí, por lo tanto encontramos gran cantidad de lenguajes para interactuar con estas BDD. Ej: **Mongo DB** ideal para datos no estructurados

**2- SQL** #SQL
**S**tructured **Q**uery **L**anguage. Es un lenguaje de consulta estructurado #bd_relacionales 

>Las bases de datos relacionales utilizan SQL (Structured Query Language) para realizar consultas complejas y obtener reportes de manera eficiente. SQL es un lenguaje poderoso que permite recuperar, insertar, actualizar y eliminar datos de manera eficaz.

Este lenguaje utilizamos para realizar acciones en BDD SQL.
Diseñado para administrar y recuperar información de sistemas de gestión de #bd_relacionales (SGBD)

Las #base_datos #SQL más conocidas son:
- PostgressSQL
- MySQL

Estas son #base_datos que utilizan #SQL (lenguaje) para realizar consultas a una BDD. Acá creamos las BDD y hacemos las consultas con #SQL 

#SQL es el lenguaje con el que nos comunicaremos con el SGBD (software para administrar la bd). Existen distintos gestores como Oracle, PostgressSQL, MySQL.

**3-SGBD (Sistema de Gestión de #base_datos )**
Es un software que permite administrar una #base_datos 
Mediante este programa podemos utilizar, configurar y extraer información almacenada.
Los usuarios pueden acceder a la información usando herramientas específicas de consulta

>Las **bases de datos relacionales** #bd_relacionales se basa en tablas para representar y gestionar los datos. 
>Este enfoque se fundamenta en el **modelo relacional**, desarrollado por E.F. Codd en 1970, el cual utiliza la lógica matemática para estructurar datos y relaciones.

---
##### Tablas y claves

Las **Tablas** son el núcleo de las #bd_relacionales. 
Su nombre es por la capacidad de definir **relaciones entre tablas**.
Las relaciones se establecen utilizando claves:

- **Clave Primaria (PK)**: La **llave primaria** o _primary key_ es un identificador único para cada registro dentro de una tabla. Este campo o conjunto de campos garantiza que cada fila de la tabla pueda ser identificada de manera unívoca, evitando duplicados y asegurando que los datos sean únicos y no nulos. La clave primaria es fundamental para la estructura de las #bd_relacionales, ya que permite mantener la integridad de los datos.

Se utiliza una **clave primaria (PK)** para identificar cada registro de manera única. Es un campo con valores únicos para cada registro, asegurando que cada fila sea individualmente identificable.

Una **clave primaria (PK)** debe ser **única y no nula**, garantizando que cada registro tenga un identificador exclusivo.

Por ejemplo, en una tabla de clientes, el número de identificación o DNI podría servir como **llave primaria**, ya que no existen dos clientes con el mismo número. Esta llave no solo facilita la búsqueda y clasificación de los datos, sino que también permite la relación entre tablas al servir como punto de referencia.


- **Clave Foránea (FK)**: La **llave foránea** o _foreign key_ es un campo o conjunto de campos en una tabla que se utiliza para establecer y reforzar un vínculo entre los datos de dos tablas. Este tipo de llave apunta a una llave primaria en otra tabla, permitiendo que las bases de datos se conecten y compartan información de manera lógica y ordenada.

La **llave foránea (FK)** garantiza que la relación entre las tablas mantenga la integridad referencial.

Esto significa que, por ejemplo, si una tabla de "Pedidos" tiene una llave foránea que apunta a una llave primaria en una tabla de "Clientes", cada pedido debe estar asociado a un cliente existente. Si un cliente es eliminado de la base de datos, las restricciones de integridad referencial evitarán que existan pedidos huérfanos sin un cliente asociado.

>Asegura que las relaciones entre tablas permanezcan consistentes. Por ejemplo, una clave foránea debe corresponder siempre a una clave primaria válida en la tabla relacionada, evitando así enlaces rotos y datos huérfanos


- **Clave Única (UK)**: La **llave única** o _unique key_ es un campo o un conjunto de campos cuyos valores son únicos para cada registro dentro de una tabla, pero que no identifica a la misma ante las demás tablas. Ejemplo de esto podría ser el mail en una tabla de usuarios, cuya clave primaria es el Id de Usuario pero en el modelo se determina que el mail no se puede repetir.

<--------------->
##### Tipos de Relaciones en Bases de Datos Relacionales

- **Uno a Uno (1:1)**: Cada fila en una tabla se relaciona con una única fila en otra tabla. Por ejemplo, un empleado puede tener un único número de identificación.
   
- **Uno a Muchos (1:n)**: Una fila en una tabla se puede relacionar con muchas filas en otra tabla. Por ejemplo, un departamento puede tener muchos empleados.

- **Muchos a Muchos (n:m)**: Muchas filas en una tabla pueden relacionarse con muchas filas en otra tabla, generalmente implementado mediante una tabla intermedia. Por ejemplo, estudiantes y cursos donde un estudiante puede inscribirse en múltiples cursos y un curso puede tener múltiples estudiantes.


---
##### **Proyecto Final**

Tener en cuenta 4 puntos claves:
- Definir la temática de tu proyecto y decide el modelo de negocio que aplicarás
- Presentar el diagrama de entidad de relación de tu bdd, esto ayuda a organizar y visualizar las tablas y relaciones dentro de tu proyecto
- Organizar tu repositorio script SQL, aquí almacenarás todos los scripts SQL que utilizaste durante el desarrollo de tu proyecto, sirve para mejorar la habilidad de gestionar y documentar tu trabajo.
- Ejecutar tu proyecto en MySQL mostrando cómo interactúan tus consultas SQL con tu Base de Datos y los resultados obtenidos
---













