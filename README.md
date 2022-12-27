# Architectura de Linux: Carpetas / luego etc dev home usr var
## Abro Terminal Windows: luego flechita abajo y selecciono Ubuntu
## Dentro de Ubuntu le doy a code . y me abre Visual Studio
## Ctrl + l equivale a darle clear
cd clear
## Para listar los archivos de donde estoy
ls
## Para listar los archivos de donde estoy con detalles
ls -l
## Para listar los archivos de donde estoy con detalles para humanos
ls -h
## Para listar los archivos de donde estoy con maximo detalle para humanos
ls -lh
## cd nos lleva al directorio donde estoy
cd
## Este nos lleva al directorio Home de una sola vez
cd ../..
## Este nos lleva al directorio que deseo
cd Directorioquedeseo
## Este me da la informacion del path working directory
pwd (path working directory)
## Este me lleva al directorio especifico que deseo dentro de otro
cd ./Documents/Dev
## Este me lleva a un directorio mas arriba del que me encuentro
cd .. (me regreso un directorio atras)
## Este comando file me 
file principios_de_usabilidad.md 
## Este a continuacion me da la ruta y detalles
file ./Picturesscreenshot.png
## Para listarlos incluyendo los archivos ocultos
ls -la
## Para ordenarlos por mayor a menor tamano
ls -lS
## Para mostrarlos en orden reverso
ls -lr
## Para ver los directorios y archivos como arbol
tree
## Para ver menos directorios en detalle y mas manejable en dos niveles
tree -L 2
## Para crear directorio (se aconseja no colocar espacios en el nobmre)
mkdir miDirectorio
## Si tengo que poner espacio aparecera como 'Mi Directorio
mkdir "Mi Directorio"'
## Para crear archivo
touch miArchivo
## Para crear varios directorios de una manera rapida
mkdir dir1 dir2 dir3
## Para crear varios archivos dentro del directorio dir1 voy a el y luego
cd dir1
touch file1 file2 file3
## Para copiar archivo como nuevo archivo file_bk
cp file1 file_bk
## Para moverlo a un directorio hacia atras
mv file_bk ..
## Para renombrar el archivo mientrs lo muevo
mv file_bk fileCopy
## Para borrar archivo
rm fileCopy
## Para borrar de modo interactivo que es mas seguro que con -rf
## -rf es recursive forzed. Aqui utilizamos -i interactive
rm -i miArchivo
## Y me continuara preguntando para hacerlo uno por uno hasta borrar
## todos los archivos y finalmente para borrar tambien el directorio donde estaban
## Para decirle que continue haciendo le escribo y (de YES)
## Para mover el directorio 1 dentro del cirectorio 2
mv dir1 dir2
## Verifico
ls dir1
## Para remover un directorio
rm -ri dir1
## Me preguntara por ser interactive para ir borrando uno por uno hsta el directiorio incluso
## Antes de remover un archivo verificar primero con ls donde estoy ubicado
## Para que muestre las primeras 10 lineas
head principios_de_usabilidad.md
## Para que muestre el numero de lienas que yo deseo (15)
head principios_de_usabilidad.md -n 15
## Para mostrar las ultimas 10 lineas del texto
tail
## Para mostrar las ultimas 20 lineas del texto
tail principios_de_usabilidad.md -n 20
## Para 
less principios _de_usabilidad.md
## Si le doy /Flexibilidad me busca la palabra Flexibilidad dentro del texto
## Luego para salir de less presionar la letra q
## En mac existe el comando open pero en linux usamos xdg-open
xdg-open principios_de_usabilidad.md
## Ahora estoy viendo la informacion con mi editor de texto predeterminado que es Visual Studio Code
## Se ha creado un proceso y para salir debo presionar Ctrl + c ( y asi matamos el proceso)
## Para que abra la carpeta en la que estamos o deseemos en Explorer
nautilus  Documents/Dev
## Para matarlo debo darle Ctrl + c
## Un comando puede ser: 1. un programa ejecutable 2. Un comando de utilidad shell
## 3. Una funcion de shell 4. un alias (que es temporal)
## Para determinar que clase de comando es
type cd
type mkdir
type ls
## Aparece 'ls --color=auto'
## Las opciones pueden escribirse con palabrs completas precedidas de -- y luego a continuacion puede ponerseles =auto (el signo igual y a continuacion un parametro)
## Para crear un alias
l="ls -lh"
## Ahora lo ejecuto asi
l
## Tras salir del terminal y volver ya los alias no estan disponibles
## Para help de cd (una utilidad de shell)
help cd
## En general para cualquier comando obtengo el help asi
ls --help
## Otra opcion para obtener informacion del comando
info cd
## Luego le doy a la letra q para salir de info
## Para ver el manual de usuario de un comando utilizo este a continuacion
man ls
## Para conocer la naturaleza del comando
whatis ls
whatis alias
## Para el uso de Wildcards coloco ? para un solo caracter o * para multiples
## Para crear multiples archivos
touch file.txt dot.txt dot2.txt index.html datos1 datos123 abc
ls *.txt
ls
ls datos*
ls datos?
ls datos???
ls *.html
ls *.*
## Para mostrar todos los archivos y directorios que comienzen or mayuscula
ls -d [[:upper:]] *
ls -d [[:lower:]] *
## Muestra los archivos que comienzen por letra a o d
ls [ad]*
ls [ai]*
## Redirecciones como funciona la shell
## En la shell entramos infor como stdin (Standard Input; file descriptors)
## Puede salir un error o el output (stdout ; o stderr)
## Redirecciones
ls Pictures > archivo.txt
less misarchivos.txt
ls Downloads > misArchivos.txt
less misarchivos.txt
## Para concatenar debemos utilizar dos veces el mayor que
ls Downloads >> misarchivos.txt
less misarchivos.txt
## Para redirigir el standard output
head error.txt
## Si escribo algo que no existe
ls ljkasdklj
## Pero no tiene nada
ls ljkasdklj > error.txt
## Si le doy head no me muestra el error
head
## Para redirigir el standard error, debo poner el numero por donde pasa esa informacion en este caso el 2 (su file descriptor)
ls ljkasdklj 2> error.txt
head error.txt
## Lo redirigjo a un error y luego tambien al Standard Output
ls asdasdas > output.txt 2>&1
head output.txt
ls Documents/ > output.txt 2>&1
less output.txt
## De este modo hemos podido almacenar los errores en archivos para verlos
## El pipe operator. Permite ejecutar un comando que pase como Standard output a otro comando
## Genera un standard output
echo "Hola Platzi!"
less error.txt
less output.txt
## Para concatenar los dos archivos de error
cat error.txt output.txt
## Todos redirigen a un Standard output
## Para el standard input lo hacemos asi a continuacion
cat < error.txt
## El pipe operator | permite que el standard output de un comando se conviert
## en el standard input de otro comando
ls -lh
ls -lh | less
## Lo hemos redirigido al comando less
## No necesito forzosamente crear un archivo pero para hacerlo puedo usar tee
ls - lh | less | tee output.txt
## Pero aqui he utilizaod el tee mal
cat output.txt
## Lo que en realidad quiero con el tee es generar el archivo primero y luego verlo con less
ls -lh | tee output.txt | less
cat output.txt
ls -lh Pictures | sort | tee pictures.txt | less
## A continuacion le doy a la letra q para salir
cowsay
sudo apt install cowsay
sudo apt install lolcat
cowsay "Hola"
echo "Hola Platzi"| lolcat
cowsay "Hola amigos" | lolcat
cowsay "Hola amigos" | lolcat | tee vaca.txt
## En este ultimo aparece todo en blanco en vez de color como antes
## Encadenando comandos : operadores de control
ls; mkdir holi; cal
## Asi he listado, creado un directorio llamado holi y un calendario.
ls & date & cal
## Asi me dice en que orden los ha procesado
## Como correr comandos de manera condicional (solo si el primero se ejecuto)
mkdir text && cd test
pwd
cd ajknmsdklnmasdn && touch archivo.txt && echo "Archivo creado"
## Ese directorio no existe y no avanza al siguiente paso
## El poperador or si lo permite
cd ajknmsdklnmasdn || touch archivo.txt || echo "Archivo creado"
ls
cd asdkjasdj || echo "Cambio de directorio"
## Tipos de archivos; Archivo normal -; d un directorio; l un link simbolico; b un archivo de bloque especial (se manejan la informacion de los bloques de datos como una USB)
## Tipos de modo (rws dueno; r-x grupo; r-x World)
## rwx 1 1 1; grupo r-x 1 0 1; World 1 0  1
## El modo octal da ponderacion de base de 2
## 4 2 1 = 7; En grupo 4+0+1=5; en World 4 +0+1=5
## Octales de 0 a 7 corresponden a binario 000,001,010,011,100,101,110,111
## y permisos ---, --x,-w-,-wx,r--,r-x,rw-,rwx
## El modo simbolico: u solo para el usuario; g solo para el grupo'o solo para otros (el World); a para todos
## Modificando permisos en la terminal
## root tiene privilegios para hacer de todo
mkdir sandbox
cd sandbox
mitexto.txt
## Asi he creado el archi o mitexto.txt
cat > mitexto.txt
ls -l
## Con permisos solo de read y ejecucion
chmod 755 mitexto.txt
ls -l
## Ahora me muestra los permisos que tiene
## Quitando permisos de lectura
chmod u-r mitexto.txt
ls -l
cat mitexto.txt
chmod u+r mitexto.txt
ls -l
cat mitexto.txt
## Ya nos deja visualizar el permiso
chmod u-x,go=w mitexto.txt
ls -l
whoami
id
su root
whoami
pwd
cd
touch rootfile
ls -l
rm rootfile
sudo rm rootfile
ls
passwd
## VARIABLES DE ENTORNO
ln -s Documents/Dev
cd Desarrollo
printenv
echo $HOME
cd Documents/Dev/
cd $HOME
echo $PATH
## Al instalar nuevos binarios hay manejadores de paquetes
## Estos manejadores de paquetes traen un repositorio instalan un binario
## Normalmente nos piden de donde se entregan los binarios agregandolos a la variable path
ls -la
code .bashrc
## Se abre Visual Studio Code y aparece el archivo con todas las variables y lo que puedo modificar. Vemos aqui el alias ls
alias l='ls -lh'
PlatzI_MESSAGE="Hola amigos"
bash
echo $PlatzI_MESSAGE
echo $PATH
mkdir bin
ls
pwd
PATH=$PATH:/home/codevars/bin
bash
echo $PATH
## COMANDOS DE BUSQUEDA
which cd
type cd
which code
which obs
find ./ -name file
## Busco todos los archivos que se llamen file en todos los idrectorios que tenga
find ./ -name *.txt | less
find ./ -type fd
## Que solo busque files o directorios
find ./ -type d -name Documents
find ./ -type f -name *.log
find ./ -size 20M
## Encuentra todos los archivos mayores a 20 mega bytes
find ./ -size -20M
## Encuentra todos los archivos menores a 20 mega bytes
## Exec permite que despues de realizar la busqueda ejecuta un comando
## Despues de find puedo darle rm para borrar
find ./ -type d -empty
## Asi ha buscado los achivos menores de 4 kb
## GREP permite encontrar coincidencias en una busqueda
## Tras bajar el archivo movies.csv y pegarlo en c/armyc/personalProjects/CursoTerminalyLineadeComandos
grep Towers movies.csv
## TOMAR CURSO DE EXPRESION DE REGULARES
grep the movies.csv
## ME dice cuantas veces encuentra the en el archivo movies.csv
grep -i the movies.csv
grep -i the movies.csv | less
## Recordarle darle q para salir
grep -c the movies.csv
grep -vi towers movies.csv
## Con al agregar la i en vi busca sin importar si es mayuscula o minuscula
wc movies.csv
## Esto nos cuenta cuantas palabras letras y numero de bits
wc -l movies.csv
wc -w movies.csv
wc -c movies.csv
## En un archivo de codigo podemos encontrarlo con grep
## UTILIDADES DE RED
ifconfig
ping www.google.com
## Extrae un archivo a traves de la red
curl www.google.com
curl www.google.com > index.html
less index.html
rm index.html
wget www.google.com
rm index.html
traceroute www.google.com
netstat -i
ifconfig
## MAS DE ESTO EN CURSO DE REDES DE PLATZI
## Comprimiendo archivos
mkdir ToCompress
cd ToCompress
touch file file2 file3
cd ..
tree ToCompress/
tar -cvf ToCompress.tar ToCompress/
ls
## Mejor compresor es el siguiente
tar -cvzf ToCompress.tar ToCompress
## Para descomprimir
rm -r ToCompress
tar -xzvf ToCompress.tar
tar -xzvf ToCompress.tar.gz
zip -r ToCompressInZip.zip ToCompress
unzip ToCompressInZip.zip
## Luego le pongo A para todo
rar -r ToCompressInRAR.rar ToCompress
unrar ToCompressInRAR.rar
## MANEJO DE PROCESOS (Ctrl Alt Suprimir)
ps
## PID Process ID
cat & ls
## Se ejecuto de manera asincrona
## Para terminar esos procesos
kill 20425
top
## Muestra los procesos que estan utilizando mas recursos
## Si presiono h me muestra la ayuda
## Escribo mi usuario Armyubuntu
kill 20167
## Asi se cierra mi terminal
## Comando htop
cat > mi_nota.txt
## Nuestra terminal se vera con el prompt esperando a que ingresemos texto
## Podemos escribir algo y despues terminar el input del texto con CTRL + D,
## Para suspender el proceso, le damos Ctrl + Z.
## EDITORES DE TEXTO EN LA TERMINAL
vim
## Para salir luego de vim le damos :q
vim index.html
## PERSONALIZAR LA TERMINAL DE COMANDOS
## Vamos a instalar un emulador de terminal
## Getting Tilix pacman es el manejador de paquetes de arch Linux
sudo pacman -S tilix
## Para Ubuntu
sudo apt install tilix
## Para instalar ZSH para cambiar de Shell
apt install zsh
zsh --version
## Y me muestra la version que instale
## Para cambiar una shell
## Ahora va a buscar la ruta de zsh instlado
chsh -s $(which zsh)
## A continuacion me pide mi contrasena
## Darle a la opcion 0 para salir creando el zsh como Shell
## Luego instalas un enhancer con oh-my-zsh now
install oh-my-zsh now
sudo rm -r /home/codevars/.oh-my-zsh
## Esto solo le paso al profesor
## A continuacion para bajar el powerlevel10k tras instalar el shell zsh
$ ZSH_THEME="powerlevel10k/powerlevel10k"
## Para instalar un tema llamado powerlevel10k
## Para cambiar el HOME/Ubuntu a la raiz que quiero que seria
## /mnt/c/users/armyc
## Y para ello le digo que ahora HOME sea donde estoy actualmente, y
## actualmente estoy (y tengo que estar) en /mnt/c/users/armyc
## Aqui el $(pwd) se lo asigno como valor a la variable
HOME=$(pwd)
## echo es para imprimir el valor de las variables de entorno
echo $HOME
## Para ver todas las variables de entorno, chequeo asi todas las variables de entorno, utilizo el comando env environment
env
## Para que dentro de env me busque cual es el HOME
env | grep HOME
env | grep OLDPWD
cat README.md | grep "##"
cat README.md | grep Para
## Para consulta url de google lo formatee y me muestre el titulo html
## xq para html, jq y yq (html, json (java script object notation), yaml)
curl www.google.com  -s | xq | grep title
## Mas especifica la linea
curl www.google.com  -s | xq | grep "<title"
## Para silencio es s minuscula y la I para mostrar la metadata info de cabecera header
curl www.google.com -Is
## Para
curl www.google.com -ISs
