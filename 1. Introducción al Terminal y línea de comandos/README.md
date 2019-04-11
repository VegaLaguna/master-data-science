# Ejercicios de introducción al terminal y línea de comandos

## Parte 1 - Manejo de ficheros

##### 1. Create a directory “first_dir” in you home folder
    Creamos el directorio: mkdir first_dir
    
##### 2. Create an empty file “text_file.txt” inside “first_dir” directory. 

    Primero nos situamos en el directorio donde queremos crear el archivo: cd first_dir
    Creamos el archivo: touch text_file.txt

##### 3. Add execute permissions to group users, and write permissions to other users to “text_file.txt”

    Primero miramos qué permisos tiene nuestro archivo: ls -l text_file.txt
    Los permisos tienen el formato user/group/other y read/write/execute
    Añadimos los permisos: chmod g+x, ugo+w text_file.txt

##### 4. Create 3 subdirectories inside “first_dir”: “sub1”, “sub2”, “text_file” 

    Se pueden crear los 3 subdirectorios a la vez: mkdir sub1 sub2 text_file

##### 5. Copy the “text_file.txt” file into “sub1” directory.
    
    Copiamos al directorio sub1: cp -r text_file.txt sub1
    Si queremos comprobar si está en sub1: cd sub1 y luego ls (para ver los ficheros que contiene el directorio)

##### 6. Move the “text_file.txt” into sub2 under name “text_file.txt.2” . 

    Primero volvemos al directorio inicial: cd -
    Luego movemos el archivo y le cambiamos el nombre: mv text_file.txt sub2/text_file.txt.2

##### 7. Copy the whole directory “sub1” to “sub3” directory. 

    Copiamos el directorio: cp -r sub1 sub3

##### 8. Change file name of “first_dir /sub2/text_file.txt.2” to “first_dir /sub2/text_file.txt.backup”

    Para cambiar el nombre usamos el mismo comando que para mover archivos: 
    mv sub2/text_file.txt.2 sub2/text_file.txt.backup

##### 9. Move “first_dir /sub2/text_file.txt.backup” to “first_dir” directory as hidden file

    Hay que tener en cuenta dos conceptos:
        - Para llamar al directorio en el que estamos se usa un punto "./"
        - Los archivos ocultos llevan un punto "." delante del nombre
    Por tanto para mover el archivo al directorio donde estamos y ponerlo como archivo oculto: 
    mv sub2/text_file.txt.backup ./.text_file.txt.backup
    

##### 10. Delete the “sub2” subdirectory

    Para borrar se usa el comando: rm -r sub2
    


## Parte 2 - Manejo del contenido

##### 1. Go to data/shell/ directory and use less to open Finn.txt

    Primero nos colocamos en el directorio que nos piden: cd data/shell/
    Abrimos el archivo Finn.txt usando less en lugar de cat 
    (porque queremos trabajar de manera interactiva con él): less Finn.txt
    
###### a) Locate the lines starting with “The”

    Usamos el siguiente comando para localizar palabras que estén al principio de lineas: ^The
    Para movernos sobre las distintas palabras que hemos localizado: n (si queremos la siguiente) 
    y N (si queremos ver la anterior)
    
###### b) Locate the lines ending with “works”

    Usamos el siguiente comando: works$


##### 2. Open ~/Data/opentraveldata/optd_aircraft.csv with less command. Search for “Canada” and then search for “Puma”

    Como en la primera parte del punto anterior: cd ../opentraveldata
    Abrimos el archivo: less optd_aircraft.csv
    Buscamos Canada: /Canada (/si buscamos hacia delante o ? si buscamos hacia atrás)
    Volvemos al inicio y buscamos Puma: g y luego /Puma


##### 3. Use help to find out how to get the list of subdirectories limited to 2 sublevels by using “tree” command

    Si no tenemos instalado el comando tree, primero hay que poner: sudo apt-get install tree
    La ayuda se despliega con el comando man (de manual): man tree
    Vemos que el comando para desplegar los subdirectorios es: tree -L 2

  