# Práctica Guiada



## Creación del directorio prueba_git

Creamos un directorio llamado **prueba_git** y accedemos a él:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada (main)
$ mkdir prueba_git

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada (main)
$ cd prueba_git
```
Ahora creas el archivo **texto.txt** y añadimos unas palabras:

```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ echo "uno" > texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ echo "dos" >> texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ echo "tres" >> texto.txt
```

Y el archivo **script.sh**

```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ echo "Listado completo" > script.sh

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ echo "ls -l" >> script.sh
```

##  1. Inicialización (init y status)

Ahora creamos un nuevo repositorio para poder añadir archivos y que nos debería devolver la ruta que estamos usando:

```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ git init
Initialized empty Git repository in C:/Users/usuario/Practica-Guiada/prueba_git/.git/
```
Pero los archivos antes creados(**texto.txt** y **script.sh**) no los toma en cuenta para ser parte del repositorio.Esto se puede ver con el comando <u>git status</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```
Ahora queremos cambiar el nombre de branch de "master" a "main" asi que usaremos el comando <u>git branch -m</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git branch -m main

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$

```
Y como se muestra al final del identificador se mostrará "main". Pero lo volvemos a dejar como estaba
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (main)
$ git branch -m master

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$
```

## 2. Añadiendo archivos (add y commit)
Ahora añadimos mediante <u>git add</u> el archivo **script.sh** para que lo tome en cuenta el repositorio
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git add script.sh
```
y nos devolvería:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   script.sh

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt
```
Pero este cambio no está confirmado hasta que usemos un <u>commit</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -m "Confirmación inicial"
[master (root-commit) 145ebaf] Confirmación inicial
 1 file changed, 2 insertions(+)
 create mode 100644 script.sh
```
Y ahora nos mostrará:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Hacemos ahora lo mismo con **texto.txt**:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git add texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -m "Añadido archivo texto.txt"
[master 4c6aae3] Añadido archivo texto.txt
 1 file changed, 3 insertions(+)
 create mode 100644 texto.txt
```
Y al mostrar el estado nos pondrá este mensaje:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
nothing to commit, working tree clean
```

## 3. Modificando archivos

Ahora añadimos la palabra "cuatro" al archivo **texto.txt** y hacemos un <u>status</u> que nos mostrará que el archivo ha sido modificado:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ echo "cuatro" >> texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
Para poder guardarlo antes necesitamos prepararlo usando el <u>add</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git add texto.txt
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt
```
Si ahora modificas otra vez **texto.txt**  y miras el estado de git saldrá esto:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ echo "cinco" >> texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt
```
Esta esperando a que hagamos un <u>add</u> para poder prepararlo para guardarlo pero si queremos guardarlo todo volvemos a escribir:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the next time Git touches it

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -m "Ampliada la explicación del texto"
[master fa153df] Ampliada la explicación del texto
 1 file changed, 2 insertions(+)

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
nothing to commit, working tree clean
```
Ya no habrá nada mas para guardar.

## 4. Información (git show y git log)
Si no quieres estar todo el rato para modificar un archivo poner <u>add</u> y luego <u>commit</u> se puede resumir mediante <u>git commit -a -m "Nueva versión"</u>.

Esto funciona siempre y cuando tengas solo un archivo que modificar, si tienes mas por modificar/actualizar debes usar <u>add</u>.

Mediante el comando <u>show</u> puedes ver la última versión del git que has trabaja.
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git show
commit fa153df75aac38d824be050f1bc6a16170f8e390 (HEAD -> master)
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 22:53:00 2025 +0100

    Ampliada la explicación del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuatro
+cinco
```
 Si quieres ver como han sido los cambios en formato historial es mediante el comando <u>log</u> donde se mostrarán los <u>commit</u> que usaste:
 ```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git log
commit fa153df75aac38d824be050f1bc6a16170f8e390 (HEAD -> master)
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 22:53:00 2025 +0100

    Ampliada la explicación del texto

commit 4c6aae3cfb03ebf198c900d0c439c817af75751d
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 22:31:46 2025 +0100

    Añadido archivo texto.txt

commit 145ebafd3d5fc65f311c5cdb3854db4037b3cbbd
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 22:24:03 2025 +0100

    Confirmación inicial
 ```
Y si usas <u>git cat-file 145e -p</u> te mostrará más a detalle(ojo,el "145e" depende de tu commit, en mi caso es este):
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git cat-file 145e -p
tree 89b5b5a72473e7e60d405f45b1fe9c1e5f3b1f00
author Borja <borjafer06@gmail.com> 1761773043 +0100
committer Borja <borjafer06@gmail.com> 1761773043 +0100

Confirmación inicial
```
## 5. Diferencias (git diff)
Ahora añadiremos "seis" al archivo **texto.txt** y eliminaremos "tres" manualmente mediante <u>nano</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ echo "seis" >> texto.txt

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ nano texto.txt
```
Y ahora mediante el comando <u>diff</u> podemos ver las diferencias entre la última versión de un archivo confirmada y uno modifico:
```bash
diff --git a/texto.txt b/texto.txt
index 23c83ff..bf98941 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,5 +1,5 @@
 uno
 dos
-tres
 cuatro
 cinco
+seis
```
Ejecutando <u>git commit -a -m "Probando diff"</u> muestra información sobre lo añadido y eliminado:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -a -m "Probando diff"
[master 87cbaf7] Probando diff
 1 file changed, 1 insertion(+), 1 deletion(-)
```
Nos da que hubo una iserción y una eliminación.
Ahora añadimos la "siete" a **texto.txt** y volvemos a usar <u>diff</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ echo "siete" >> texto.txt
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git diff
diff --git a/texto.txt b/texto.txt
index bf98941..430cdae 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,3 +3,4 @@ dos
 cuatro
 cinco
 seis
+siete
```
## 6. Ignorar archivos (.gitignore)

Cuando ya tenemos una gran cantidad de archivos y algunos no queremos gestionarlos con git usamos el archivo **.gitignore**.Primero lo creamos y añadimos estas líneas mediante <u>nano</u> dentro de prueba_git:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ nano .gitignore
```
Y dentro escribes:
```bash
# ignora los archivos terminados en .class
*.class
# ignora los archivos terminados en ~
*~
# pero no importante~, aun cuando había ignorado los archivos terminados en ~
!importante~
```
Ahora creas el archivo **Hola.java**:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ nano Hola.java
```
Y dentro escribes:
```bash
class Hola {
    public static void main(String[] args){
        System.out.println("Welcome to the Java World");
    }
 }
```
Y por último creamos los archivos temporales:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ touch temporal~ importante~
```
Si has hecho todos los pasos anteriores, mediante <u>ls</u> te debería salir algo como esto:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ ls -a
./   .git/       Hola.java    script.sh  texto.txt
../  .gitignore  importante~  temporal~
```
Ahora compilamos el **Hola.java** para que nos aparezca su .class:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ javac Hola.java

```
Mostramos todo y nos dará esto:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Hola.java
        importante~
```
Ahora para añadir todo lo que esta pendiente tenemos que usar este comando <u>add .</u> y luego un <u>commit</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git add .
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'Hola.java', LF will be replaced by CRLF the next time Git touches it

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -m "Añadidos fuentes en java y archivos importantes"
[master 463ef01] Añadidos fuentes en java y archivos importantes
 4 files changed, 12 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
 create mode 100644 importante~
```
Para ver los archivos que hay en el directorio tras el último commit en la rama principal pon este comando:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git ls-tree --name-only -r HEAD
.gitignore
Hola.java
importante~
script.sh
texto.txt
```
## 7. Tags y gestión de versiones (git tag y git checkout)

Ahora usaremos el comando <u>show</u> y el código del commit que prefieras para verlo más a fondo (usa <u>log</u> para ver los commit):
```bash
  usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git show 463ef01aad5d159adfa93876a493f203d246249f
commit 463ef01aad5d159adfa93876a493f203d246249f (HEAD -> master)
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 23:49:31 2025 +0100

    Añadidos fuentes en java y archivos importantes

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..c6f5000
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,6 @@
+# ignora los archivos terminados en .class
+*.class
+# ignora los archivos terminados en ~
+*~
+#pero no importante~, aun cuando había ignorado los archivos terminados en ~
+!importante~
diff --git a/Hola.java b/Hola.java
new file mode 100644
index 0000000..94dcbfd
--- /dev/null
+++ b/Hola.java
@@ -0,0 +1,5 @@
+class Hola {
+       public static void main(String[] args){
+               System.out.println("Welcome to the Java world");
+       }
+}
diff --git a/importante~ b/importante~
new file mode 100644
index 0000000..e69de29
diff --git a/texto.txt b/texto.txt
index bf98941..430cdae 100644
--- a/texto.txt

```
La salida del comando dependerá del commit que elijamos.

Para que no sea tan tedioso escribir el código del commit se usan los <u>tag</u> seguido del código y luego <u>git log --oneline</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git tag  v0.3 ^M

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git log --oneline
463ef01 (HEAD -> master, tag: v0.3) Añadidos fuentes en java y archivos importantes
87cbaf7 Probando diff
fa153df Ampliada la explicación del texto
4c6aae3 Añadido archivo texto.txt
145ebaf Confirmación inicial
```
Nos mostrará los commit resumidos y en una linea(^M es q es un copia pega del código del commit).

También puedes hacer una versión más simple con el comando <u> git show v0.3</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git show v0.3
commit 463ef01aad5d159adfa93876a493f203d246249f (HEAD -> master, tag: v0.3)
Author: Borja <borjafer06@gmail.com>
Date:   Wed Oct 29 23:49:31 2025 +0100

    Añadidos fuentes en java y archivos importantes

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..c6f5000
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,6 @@
+# ignora los archivos terminados en .class
+*.class
+# ignora los archivos terminados en ~
+*~
+#pero no importante~, aun cuando había ignorado los archivos terminados en ~
+!importante~
diff --git a/Hola.java b/Hola.java
new file mode 100644
index 0000000..94dcbfd
--- /dev/null
+++ b/Hola.java
@@ -0,0 +1,5 @@
+class Hola {
+       public static void main(String[] args){
+               System.out.println("Welcome to the Java world");
+       }
+}
diff --git a/importante~ b/importante~
new file mode 100644
index 0000000..e69de29
diff --git a/texto.txt b/texto.txt
index bf98941..430cdae 100644
--- a/texto.txt
:
```
Puedes ver además versiones antiguas con <u>git checkout v0.3
</u> y para volver a la actual escribe <u>git checkout master</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git checkout v0.3
Note: switching to 'v0.3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 463ef01 Añadidos fuentes en java y archivos importantes

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git ((v0.3))
$ git checkout master
Switched to branch 'master'
```

## 8. Ramas
En todo momento en la consola nos aparece la rama en la que estamos (master), si queremos crear otra tenemos que escribir <u> git branch Prueba</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git branch Prueba
```
Y si queremos verla escribimos <u> git log --oneline</u> y se muestran las ramas en la primera línea
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git log --oneline
463ef01 (HEAD -> master, tag: v0.3, Prueba) Añadidos fuentes en java y archivos importantes
87cbaf7 Probando diff
fa153df Ampliada la explicación del texto
4c6aae3 Añadido archivo texto.txt
145ebaf Confirmación inicial
```
Ahora para ver el listado de ramas tenemos que escribir:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git branch
  Prueba
* master
```
Si quieres cambiar la rama escribe <u>git switch Prueba</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git switch Prueba
Switched to branch 'Prueba'

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$
```
Aparecerá que ahora estamos en la rama Prueba, también hace lo mismo <u>git checkout Prueba</u>.

Volvemos a usar <u>git brach</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git branch
* Prueba
  master
```
Y ahora nos sale que estamos en Prueba con el asterisco.
Si usamos <u>git log --oneline</u> nos marca que estamos en Prueba:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git log --oneline
463ef01 (HEAD -> Prueba, tag: v0.3, master) Añadidos fuentes en java y archivos importantes
87cbaf7 Probando diff
fa153df Ampliada la explicación del texto
4c6aae3 Añadido archivo texto.txt
145ebaf Confirmación inicial
```

Ahora estando en Prueba vamos a añadir una línea a **Hola.java**:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ nano Hola.java
```
Y escribimos dentro:
```bash
System.out.println("I have no more branches to commit, said the Ent");
```
ahora añadimos un <u>commit</u> y luego <u>git tag v0.7-Ent-Release</u>
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git commit -a -m "Llegan los Ents a Java"
warning: in the working copy of 'Hola.java', LF will be replaced by CRLF the next time Git touches it
[Prueba 2980b84] Llegan los Ents a Java
 1 file changed, 1 insertion(+)

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git tag v0.7-Ent-Release
```
Para que luego al usar un <u>log</u> se muestre algo asi:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git log --oneline
2980b84 (HEAD -> Prueba, tag: v0.7-Ent-Release) Llegan los Ents a Java
463ef01 (tag: v0.3, master) Añadidos fuentes en java y archivos importantes
87cbaf7 Probando diff
fa153df Ampliada la explicación del texto
4c6aae3 Añadido archivo texto.txt
145ebaf Confirmación inicial
```
Volvemos a rama master y mostramos **Hola.java** que deberiá ser así:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (Prueba)
$ git switch master
Switched to branch 'master'

usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ cat Hola.java
class Hola {
        public static void main(String[] args){
                System.out.println("Welcome to the Java world");
        }
}
```
También se puede unir con la rama principal mediante <u>merge</u>:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git merge Prueba
Updating 463ef01..2980b84
Fast-forward
 Hola.java | 1 +
 1 file changed, 1 insertion(+)
```

## 9. Eliminar y quitar seguimiento
Si deseas eliminar un archivo del repositorio sería así:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git commit -m "Eliminar importante~ del repositorio"
On branch master
nothing to commit, working tree clean
```
Y luego un commit. Aunque si ya lo has eliminado previamente git se pondrá a buscarlo sin encontrarlo, si sucede eso tienes que escribir:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git reset HEAD *.class
```
## 10. Repositorios remotos: GitHub
Si deseas clonar un proyecto remoto, GitHub permite esto con un solo comando:
```bash
usuario@DESKTOP-2P747RT MINGW64 ~/Practica-Guiada/prueba_git (master)
$ git clone https://github.com/ColegioVivasCurro/HolaED
Cloning into 'HolaED'...
remote: Enumerating objects: 20, done.
remote: Total 20 (delta 0), reused 0 (delta 0), pack-reused 20 (from 1)
Receiving objects: 100% (20/20), 4.26 KiB | 101.00 KiB/s, done.
Resolving deltas: 100% (8/8), done.
```
Aquí he clonado un proyecto remoto.

