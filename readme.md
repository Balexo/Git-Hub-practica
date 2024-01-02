* 10)	Deshacer el último commit (perdiendo los cambios realizados en el working copy) *
Git reset –hard HEAD~1
**Razonamiento:** con esto vuelvo al commit anterior perdiendo los cambios en el working copy

* 12)	Rehacer el último commit (el que acabamos de deshacer) *
Git reflog
Git reset –hard <commit id> "c4e3845"
**Razonamiento:** Con ello pongo HEAD y la rama styled a ese commit que ahora está inaccesible. Además recupera la rama styled y el archivo git-nuestro con las modificaciones de styled, de otra forma sería un detached HEAD. Con un git status compruebo que el HEAD está en la rama styled

* 13)	Hacer un merge con ‘main’ (styled absorbe a main) *
Git merge main
**Razonamiento:** En la rama styled para que esta abosorva a mian. Como en main no ha habido cambios y solo en styled va a indicar Already up to date  ya que styled tiene acceso a todos los commits de main y no incorpora ninguna modificación de main.

* 19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify) *
Git checkout styled. Git merge htmlify.
**Razonamiento:** movemos el HEAD a styled para que absorva a htmlify. El archivo git-nuestro tendría la información que aparece en la rama htmlify pero al haber un conflicto al estar el mismo archivo, en las mismas líneas y con diferente código, nos vamos a quedar con el código de la rama styled como indicado en el paso 20.

* 21) Desde “main”, hacer un merge con “styled” *
Git checkout main. Git merge styled. 
**Razonamiento:** El archivo git-nuestro incorpora los cambios de styled. 

* 25) Dibujar el diagrama *
git log --graph
**Dibujo**
PS C:\Users\oscar\Git-Hub-practica> git log --graph
*   commit 8f88a7613e0941150d07cc49f657959e1023d6e5 (HEAD -> main, styled)
|\  Merge: c4e3845 b0a5719
| | Author: Oscar Vallejo <oscar.vallejo@outlook.com>
| | Date:   Mon Jan 1 16:45:18 2024 +0100
| |
| |     Mergeadas las ramas htmlify y styled. Se mantiene contenido de styled debido a conflictos
| |
| * commit b0a5719358ee05fb1f70692e4c042f98ec2cf4c2 (htmlify)
| | Author: Oscar Vallejo <oscar.vallejo@outlook.com>
| | Date:   Mon Jan 1 16:43:26 2024 +0100
| |
| |     Modifico el archivo git-nuestro en la rama htmlify
| |
* | commit c4e38458ad8efe0344a26acdf6261170e5727ca8
|/  Author: Oscar Vallejo <oscar.vallejo@outlook.com>
|   Date:   Mon Jan 1 16:40:39 2024 +0100
|   
|       Modificamos el archivo git-nuestro en la rama styled
|
* commit a1066fb29fa7359c6334c6b24a68e20846cf179c
| Author: Oscar Vallejo <oscar.vallejo@outlook.com>
| Date:   Mon Jan 1 16:38:52 2024 +0100
|
|     Creo el archivo git-nuestro
|
* commit 735b8b00d0e8e5816b30773cd335a1552225e2c6
  Author: Oscar Vallejo <oscar.vallejo@outlook.com>
  Date:   Mon Jan 1 16:37:50 2024 +0100

      Añado el archivo readme

* 26) Hacer un merge “no fast-forward” de “title” en “main” (main absorbe a title) *
Ya estoy en la rama main así que Git merge –no-ff title. 
**Razonamiento:** Para que no sea fast forward hay que añadir --no-ff Ahora main tiene el archivo git nuestro con el título.

* 27) Deshacer el merge (sin perder los cambios del working copy)*
Git reset HEAD~1
**Razonamiento:** muevo el HEAD por el grafo y mantengo la working copy

* 28) Descartar los cambios *
Git restore git-nuestro.md
**Razonamiento:** deshacemos los cambios en el working copy de git-nuestro.md

* 29) Eliminar la rama “title” *
Git branch -D title
**Razonamiento:** Tengo que estar situado fuera de esa rama. Indica que no está fully mergue por este razón tengo que hacerlo con la D mayúscula.

30) Rehacer el merge que hemos deshecho
Git reflog. Git reset –hard HEAD~1 "c6a4ec0"
**Razonamiento:** Con ello pongo HEAD y la rama main a ese commit anterior. Recupero el merge y el archivo git-nuestro con las modificaciones de title. Con un git status compruebo que el HEAD está en la rama main.

32) Volver al commit inicial cuando se creó el poema
Git reflog
Git checkout <commit id> "a1066fb"
**Razonamiento**: busco el commit con el texto “Creo el archivo git-nuestro”

33) Volver al estado final, cuando pusimos título al poema
Git checkout main
**Razonamiento**: ya que es la única rama que nos queda y que contiene el último merge que hicimos.












