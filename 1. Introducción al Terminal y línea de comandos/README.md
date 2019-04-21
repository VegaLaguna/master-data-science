# Ejercicios de introducción al terminal y línea de comandos

* **Parte 1 - Manejo de ficheros**
* **Parte 2 - Manejo del contenido**
* **Parte 3 - Manejo del fichero y su contenido**
* **Parte 4 - Búsqueda de ficheros**


                            
                                 
## Parte 1 - Manejo de ficheros

**1. Create a directory “first_dir” in you home folder**
    Creamos el directorio: mkdir first_dir
    
**2. Create an empty file “text_file.txt” inside “first_dir” directory. **

    Primero nos situamos en el directorio donde queremos crear el archivo: cd first_dir
    Creamos el archivo: touch text_file.txt

**3. Add execute permissions to group users, and write permissions to other users to “text_file.txt”**

    Primero miramos qué permisos tiene nuestro archivo: ls -l text_file.txt
    Los permisos tienen el formato user/group/other y read/write/execute
    Añadimos los permisos: chmod g+x, ugo+w text_file.txt

**4. Create 3 subdirectories inside “first_dir”: “sub1”, “sub2”, “text_file”**

    Se pueden crear los 3 subdirectorios a la vez: mkdir sub1 sub2 text_file

**5. Copy the “text_file.txt” file into “sub1” directory.**
    
    Copiamos al directorio sub1: cp -r text_file.txt sub1
    Si queremos comprobar si está en sub1: cd sub1 y luego ls (para ver los ficheros que contiene el directorio)

**6. Move the “text_file.txt” into sub2 under name “text_file.txt.2”.**

    Primero volvemos al directorio inicial: cd -
    Luego movemos el archivo y le cambiamos el nombre: mv text_file.txt sub2/text_file.txt.2

**7. Copy the whole directory “sub1” to “sub3” directory.** 

    Copiamos el directorio: cp -r sub1 sub3

**8. Change file name of “first_dir /sub2/text_file.txt.2” to “first_dir /sub2/text_file.txt.backup”**

    Para cambiar el nombre usamos el mismo comando que para mover archivos: 
    mv sub2/text_file.txt.2 sub2/text_file.txt.backup

**9. Move “first_dir /sub2/text_file.txt.backup” to “first_dir” directory as hidden file.**

    Hay que tener en cuenta dos conceptos:
        - Para llamar al directorio en el que estamos se usa un punto "./"
        - Los archivos ocultos llevan un punto "." delante del nombre
    Por tanto para mover el archivo al directorio donde estamos y ponerlo como archivo oculto: 
    mv sub2/text_file.txt.backup ./.text_file.txt.backup
    

**10. Delete the “sub2” subdirectory**

    Para borrar se usa el comando: rm -r sub2
    



## Parte 2 - Manejo del contenido

##### 1. Go to data/shell/ directory and use less to open Finn.txt

    Primero nos colocamos en el directorio que nos piden: cd data/shell/
    Abrimos el archivo Finn.txt usando less en lugar de cat 
    (porque queremos trabajar de manera interactiva con él): less Finn.txt
    
######    a) Locate the lines starting with “The”

    Usamos el siguiente comando para localizar palabras que estén al principio de lineas: /^The
    Para movernos sobre las distintas palabras que hemos localizado: n (si queremos la siguiente) 
    y N (si queremos ver la anterior)
    
######    b) Locate the lines ending with “works”

    Usamos el siguiente comando: /works$


##### 2. Open ~/Data/opentraveldata/optd_aircraft.csv with less command. Search for “Canada” and then search for “Puma”

    Como en la primera parte del punto anterior: cd ../opentraveldata
    Abrimos el archivo: less optd_aircraft.csv
    Buscamos Canada: /Canada (/si buscamos hacia delante o ? si buscamos hacia atrás)
    Volvemos al inicio y buscamos Puma: g y luego /Puma


##### 3. Use help to find out how to get the list of subdirectories limited to 2 sublevels by using “tree” command

    Si no tenemos instalado el comando tree, primero hay que poner: sudo apt-get install tree
    La ayuda se despliega con el comando man (de manual): man tree
    Vemos que el comando para desplegar los subdirectorios es: tree -L 2




## Parte 3 - Manejo del fichero y su contenido

##### 1. Go to ~/Data/Shell/ and use Text_example.txt to generate a new file with the same content but with line number at the beginning of each line.

    Cambiamos de directorio: cd ~/Data/Shell
    Para ver los números de líneas en un archivo usamos el comando: cat -n Text_example.txt
    Como queremos crear un nuevo archivo donde vayan directamente escritas las líneas sin tener que poner nosotros el -n:
    cat -n Text_example.txt > Text_example_lineas.txt
    Al abrir este último archivo con cat Text_example_lineas.txt ya nos aparecerán los números de líneas en él
    

##### 2. Generate a new file with twice the content of “Text_example.txt” inside. (one full text content after another)

    Usamos: cat Text_example.txt Text_example.txt > Text_example_doble.txt


##### 3. Open new shell inside a new terminal tab and using block search execute again the command where we printed the linux details (hint: it had “release” in the name)

    Para abrir una nueva pestaña de shell en la terminal: CTRL+shift+t
    Para buscar en el historial de comandos: CTRL+r
    Basta con empezar a escribir la palabra "release" y aparecen los comandos usados


##### 4. Generate a file with creation timestamp and name of the user who created it on the first line. Something like this:
##### "# This file  is created by VEGA on:Sun Nov 26 10:31:06 CET 2017"

    La función que nos da la hora es "$date"
    Cuidado a la hora de escribir con comillas porque no todas interpretan el texto:
          - ' (comilla simple): no interpreta el texto
          - "" (dobles comillas): interpreta la variable en el texto
          - ``: evalúa y reemplaza
    Por tanto: echo "This file is created by VEGA on: $(date)"
    
    
##### 5. Save the information of 3 largest files located inside ~/Data/us_dot/otp/ into a three_largest_file.txt. 
##### (Hint: use ls with sort option and pipe the result)

    Para obtener la información detallada del contenido de un directorio: ls -l
    Si además la queremos ordenada por tamaño, habría que añadirle un -S: ls -lS
    Al aplicar este comando la primera línea que se imprime es la del total de archivos, por lo tanto no nos cuenta.
    Aplicamos un head para sacar las 4 primeras lineas (la primera es un archivo): head -n 4
    Luego tenemos que aplicar un tail para no imprimir esa primera fila de las 4 anteriores: tail -n 3
    Y lo tenemos que redirigir a un archivo txt que vamos a crear: > three_largest_file.txt
    Para encadenar comandos usaremos el pipe: ls -lS ~/Data/us_dot/otp/ | head -n 4 | tail -n 3 > three_largest_file.txt
    

##### 6. Save last 20 commands used at command line to a file. (Hint: use history and redirect the output)

    Primero vemos como sacar el historial de comandos usados (con el número de línea): cat -n ~/.history
    Ahora aplicamos el comando tail para sacar los últimos 20: tail -n 20
    Y lo tenemos que redirigir a un archivo txt que vamos a crear: > last_20_commands.txt
    Para encadenar comandos usaremos el pipe: cat -n ~/.history | tail -n 20 > last_20_commands.txt
    
    
##### 7. Print first 3 lines of ~/Data/shell/Text_example.txt together with line numbers

    Solo tenemos que hacer un head de las 3 primeras lineas: head -n 3
    Pero el head no nos permite imprimir los números de líneas, por tanto necesitamos un cat -n
    El resultado sería: cat -n ~/Data/shell/Text_example.txt | head -n 3
    

##### 8. Print content of ~/Data/shell/Text_example.txt except first 2 and last 3 lines.

    Tenemos los comandos head y tail. 
    Haremos head -n -3 para imprimir todo excepto las 3 últimas líneas
    Y luego haremos tail -n +3 para imprimir todo a partir de la tercera línea (borra las 3-1 =2 primeras)
    Para encadenar comandos usaremos el pipe: head -n -3 Text_example.txt | tail -n +3


##### 9. How many lines does ~/Data/opentraveldata/optd_aircraft.csv file have?

    Para contar el número de líneas usamos: wc -l ~/Data/opentraveldata/optd_aircraft.csv
    

##### 10. How many words do the first 5 lines of the ~/Data/shell/Finn.txt have?

    Para contar el número de palabras usamos: wc -w 
    Pero primero hay que separar las 5 primeras líneas del texto: head -n 5 ~/Data/shell/Finn.txt | wc -w

    
    
    
## Parte 4 - Búsqueda de ficheros

##### 1. Find all files located ONLY inside subdirectories of your home directory which have been modified in last 60min

    Para buscar archivos o directorios usamos el comando find y sus atributos
    Para que busque solo archivos hay que añadir: -type f
    Para que solo busque en subdirectorios: -maxdepth 2 (1 es el directorio actual y 0 es la linea de comandos)
    Para que coja elementos modificados en los últimos 60 minutos: -mmin -60
    Combinando las opciones: find ~ -maxdepth 2 -type f -mmin -60
    

##### 2. Find all empty files inside subdirectories of your home directory which do NOT have read-write-execute permissions given to all users

    Para buscar archivos vacíos existe la opción "-empty" dentro de find
    Para buscar según los permisos: -perm 
    A los archivos con permisos read-write-execute se les asigna el valor 777
    Para invertir el resultado de la opción se puede usar -not o un punto de exclamación
    Combinando las opciones: find ~ -mindepth 1 -type f !-perm 777


##### 3. Expand previous command to grant these permissions using “ok” option

    La opción "-ok" te pregunta si quieres ejecutar el comando que la sigue antes de hacerlo.
    Después de escribir dicho comando hay que escribir siempre: {} \; (con espacio entre {} y \;)
    Por lo tanto sería: find ~ -mindepth 1 -type f !-perm 777 -ok chmod 777 {} \;
    

##### 4. Get top 3 largest files per subdirectory inside ~/Data/ 

    
