2025-06-20 16:25

**Tags:** #JS 
[[NODE JS]] [[Java Script]]

Nuestro **repositorio** será un espacio de trabajo, en este caso estará de forma remota pero también lo podemos clonar y tenerlo en nuestra computadora de forma local.

Si creamos un **nuevo repositorio desde github** y luego queremos **clonarlo** para tenerlo en nuestra compu de forma local (o sea replicar estos archivos y tenerlos en nuestra compu)…, una vez que creamos el repositorio copiamos el link (url).  

Luego en nuestra pc, vamos a ir a una **terminal** (sea powershel, gitbash, la que sea) y ahí en la consola vamos a ejecutar el comando de clonado que es:
  
```bash
Git clone + url que copiamos
```
  
Le damos enter y empieza a clonar los archivos, voy a la carpeta esa con: 

 > cd + nombre_carpeta

Y si quiero abrirlo con el **Visual Studio Code**: 

>code .

  
- Cuando en el VSC vemos por ejemplo algún archivo que creamos (como un index) aparece una **U** al costado, quiere decir que no lo reconoce, desde su último registro no lo tiene ubicado

- Si modifico un archivo que ya tenía en el repo, nos aparecerá una **M** al costado que nos dice que lo modificamos.
  
Si quiero **subir estos cambios nuevamente a mi plataforma remota a Github**, tengo que hacer un **commit** (que es como un punto de guardado o una foto que le sacamos en ese momento al proyecto) y así vamos a almacenar esos cambios. 

**Para hacer esto**:

1. Usamos el comando: 
> git add .
   
Con esto estoy tomando todos los archivos de esa carpeta y preparándolos para el nuevo commmit

2. Para confirmar este nuevo punto de guardado: 
>git commit -m “mensaje“
   
Una vez hecho esto ya tengo mi punto de guardado, pero estos cambios se efectuaron en mi computadora local, si quiero que **se actualice a la plataforma remota de github** tenemos que usar el comando:

>Git push / git push -u origin main

Con esto mis cambios se van a pasar a la web

---------
**En terminal**: (para ver si lo tengo instalado)
>git -v

https://git-scm.com/downloads 
Para instalarlo para Windows

#### Diferencias Git - GitHub

- **Git** es la **herramienta con la que vamos a mover toda la data**, trayendo, guardando versiones de nuestro software, etc, mientras que, 

- **GitHub** es el **Google drive de todas esas versiones que mueve git**. Sería un almacenamiento remoto en la nube donde voy a poder guardar todas esas cosas.. xq antes Git guardaba todas las versiones de forma local y luego empezaron a surgir todos los repositorios de software.

>**Git**: es la herramienta que uso para mover archivos, data y todas las versiones.
   **GitHub:** sería la nube o repositorio, como el Google drive de todas las versiones de datos que mueve git.

Lo **ideal es manejar todo desde la TERMINAL:** esto no es más que una interfaz de cómo voy a ingresar a la computadora.
Puedo usar **CMD, Powershell o GitBash.. todas son terminales** que nos sirven para ingresar a la computadora. Son emulaciones de una terminal conectada a mi propia computadora.

Lo que está dentro del **Visual Studio Code** es tb una terminal hacia nuestra computadora para poder operar por medio de comandos nuestra misma computadora, utilizo GitBash o Powershell dentro del Visual Studio Code. 

1. git init

2. cd repos

3. git add nombre_archivo o git add --all

4. git commit -m "nombre"

5. git branch -M (nombre_branch:main)

6. Para cambiar la branch: git remote rm origin (elimino la dirección/ruta)

7. Para agregar nueva dirección/ruta: git remote add origin https://github...

8. git push -u origin nombre_branch/proyecto

Creo una carpeta en mi escritorio o puedo inciarlizar el repositorio desde alguna carpeta que ya tengo creada.
**Por ejemplo,** ya tengo mi carpeta obsidian my_vault.. entonces ceo el repsotorio en GitHub que se llame Obsidian, después me voy a la terminal abriendo powershell desde la caprtea donde quiero incializar mi repositorio que acabo de crear y ahí pongo gi init, git comit, git add, git remote.. y todo el resto que me aparece cuando en github ponemos Create Reposotroy.

- En GitHub ceo un nuevo repositorio, al poner create repository me sale para poner todo los pasos desde git init, git commit, git add, etc.

- Voy a la terminal de powershell en la carpeta que cree en mi escritorio

**Terminal PowerShell**
```
PS C:\GitHub\js_project> git init
Initialized empty Git repository in C:/GitHub/js_project/.git/
PS C:\GitHub\js_project> code .  (con esto se me abre el visual para crear algún archivo de código)

PS C:\GitHub\js_project> git add .
PS C:\GitHub\js_project> git commit -m "first commit"
[master (root-commit) 0e21c69] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 main.js

PS C:\GitHub\js_project> git config --global user.email "emi.mtorresbq@gmail.com"
PS C:\GitHub\js_project> git config --global user.name "EmiTorres7"
PS C:\GitHub\js_project> git branch -M main
PS C:\GitHub\js_project> git remote add origin https://github.com/EmiTorres7/js_project.git
PS C:\GitHub\js_project> git push -u origin main
```

Con el **git remote** conecto mi repositorio que acabo de crear con la carpeta que hice en mi escritorio.

Con esto hago que por defecto mi branch sea main y ya no es necesario poner git branch -M main:
>PS C:\GitHub\js_project> git config --global init.defaultBranch main


- Esto es lo que me aparece en **GitHub** cuando pongo para crear un nuevo repositorio
```
git init
git add .
git commit -m "first commit"
git Branch -M main
git remote add origin https://github.com/EmiTorres7/js_project.git
```

Y todo eso lo tengo que ir poniendo en la terminal desde la carpeta que quiero inicializar mi repositorio. 

Y **cada vez que hago algún cambio en mis archivos de mi repositorio ya creado** poner en la terminal si estoy desde el Visual:
```
git init
git add .
git commit -m "commit…"
git push -u origin main
```

#### Getting Started First Time
https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

INGRESAR LAS CREDENCIALES

You can view all of your settings and where they are coming from using:

```bash
$ git config --list --show-origin
```

 Luego me va a pedir que ingrese la clave o el token, para eso vamos a Git, a Settings, Developer Settings y ahí generamos el token.
 
 Lo copiamos y vamos a la terminal e ingresamos el token