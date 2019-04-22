# Ejercicios de introducción al terminal y línea de comandos

* [Parte 1 - Manejo de ficheros](https://github.com/VegaLaguna/master-data-science/tree/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos#parte-1---manejo-de-ficheros)
* [Parte 2 - Manejo del contenido](https://github.com/VegaLaguna/master-data-science/tree/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos#parte-2---manejo-del-contenido)
* [Parte 3 - Manejo del fichero y su contenido](https://github.com/VegaLaguna/master-data-science/tree/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos#parte-3---manejo-del-fichero-y-su-contenido)
* [Parte 4 - Búsqueda de ficheros](https://github.com/VegaLaguna/master-data-science/tree/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos#parte-4---b%C3%BAsqueda-de-ficheros)
* [Parte 5 - Selección y recuento](https://github.com/VegaLaguna/master-data-science/blob/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos/README.md#parte-5---selecci%C3%B3n-y-recuento)
* [Parte 6 - Procesado y filtrado](https://github.com/VegaLaguna/master-data-science/blob/master/1.%20Introducci%C3%B3n%20al%20Terminal%20y%20l%C3%ADnea%20de%20comandos/README.md#parte-6---procesado-y-filtrado)

----------------------------------------------------------------------------------------------------------------------------------------

## Parte 1 - Manejo de ficheros

#### 1. Create a directory “first_dir” in you home folder
- Creamos el directorio:`mkdir` first_dir
    
#### 2. Create an empty file “text_file.txt” inside “first_dir” directory.
- Primero nos situamos en el directorio donde queremos crear el archivo: `cd` first_dir
- Creamos el archivo: `touch` text_file.txt

#### 3. Add execute permissions to group users, and write permissions to other users to “text_file.txt”

- Primero miramos qué permisos tiene nuestro archivo: `ls -l` text_file.txt
- Los permisos tienen el formato user/group/other y read/write/execute
- Añadimos los permisos: `chmod g+x, ugo+w` text_file.txt

#### 4. Create 3 subdirectories inside “first_dir”: “sub1”, “sub2”, “text_file”
- Se pueden crear los 3 subdirectorios a la vez: `mkdir` sub1 sub2 text_file

#### 5. Copy the “text_file.txt” file into “sub1” directory. 
- Copiamos al directorio sub1: `cp -r` text_file.txt sub1
- Si queremos comprobar si está en sub1: `cd` sub1 y luego `ls` (para ver los ficheros que contiene el directorio)

#### 6. Move the “text_file.txt” into sub2 under name “text_file.txt.2”.
- Primero volvemos al directorio inicial: `cd -`
- Luego movemos el archivo y le cambiamos el nombre: `mv` text_file.txt sub2/text_file.txt.2

#### 7. Copy the whole directory “sub1” to “sub3” directory.
- Copiamos el directorio: `cp -r` sub1 sub3

#### 8. Change file name of “first_dir /sub2/text_file.txt.2” to “first_dir /sub2/text_file.txt.backup”
- Para cambiar el nombre usamos el mismo comando que para mover archivos:`mv` sub2/text_file.txt.2 sub2/text_file.txt.backup

#### 9. Move “first_dir /sub2/text_file.txt.backup” to “first_dir” directory as hidden file.
- Hay que tener en cuenta dos conceptos:
        - Para llamar al directorio en el que estamos se usa un punto "./"
        - Los archivos ocultos llevan un punto "." delante del nombre
- Por tanto para mover el archivo al directorio donde estamos y ponerlo como archivo oculto: `mv` sub2/text_file.txt.backup ./.text_file.txt.backup

#### 10. Delete the “sub2” subdirectory
- Para borrar se usa el comando: `rm -r` sub2
    
----------------------------------------------------------------------------------------------------------------------------------------


## Parte 2 - Manejo del contenido

#### 1. Go to data/shell/ directory and use less to open Finn.txt
- Primero nos colocamos en el directorio que nos piden: `cd` data/shell/
- Abrimos el archivo Finn.txt usando `less` en lugar de `cat` (porque queremos trabajar de manera interactiva con él): `less` Finn.txt

#####    a) Locate the lines starting with “The”
- Usamos el siguiente comando para localizar palabras que estén al principio de lineas: `/^`The
- Para movernos sobre las distintas palabras que hemos localizado: `n` (si queremos la siguiente) y `N` (si queremos ver la anterior)

#####    b) Locate the lines ending with “works”
- Usamos el siguiente comando: `/works$`


#### 2. Open ~/Data/opentraveldata/optd_aircraft.csv with less command. Search for “Canada” and then search for “Puma”
- Como en la primera parte del punto anterior: `cd ../`opentraveldata
- Abrimos el archivo: `less` optd_aircraft.csv
- Buscamos Canada: /Canada (`/`si buscamos hacia delante o `?` si buscamos hacia atrás)
- Volvemos al inicio y buscamos Puma: `g` y luego /Puma


#### 3. Use help to find out how to get the list of subdirectories limited to 2 sublevels by using “tree” command
- Si no tenemos instalado el comando tree, primero hay que poner: `sudo apt-get install tree`
- La ayuda se despliega con el comando man (de manual): `man tree`
- Vemos que el comando para desplegar los subdirectorios es: `tree -L 2`

----------------------------------------------------------------------------------------------------------------------------------------



## Parte 3 - Manejo del fichero y su contenido

#### 1. Go to ~/Data/Shell/ and use Text_example.txt to generate a new file with the same content but with line number at the beginning of each line.
- Cambiamos de directorio: `cd` ~/Data/Shell
- Para ver los números de líneas en un archivo usamos el comando: `cat -n` Text_example.txt
- Como queremos crear un nuevo archivo donde vayan directamente escritas las líneas sin tener que poner nosotros el -n:
    `cat -n` Text_example.txt `>` Text_example_lineas.txt
- Al abrir este último archivo con cat Text_example_lineas.txt ya nos aparecerán los números de líneas en él
    

#### 2. Generate a new file with twice the content of “Text_example.txt” inside. (one full text content after another)
- Usamos: `cat` Text_example.txt Text_example.txt `>` Text_example_doble.txt


#### 3. Open new shell inside a new terminal tab and using block search execute again the command where we printed the linux details (Hint: it had “release” in the name)
- Para abrir una nueva pestaña de shell en la terminal: `CTRL+shift+t`
- Para buscar en el historial de comandos: `CTRL+r`
- Basta con empezar a escribir la palabra "release" y aparecen los comandos usados


#### 4. Generate a file with creation timestamp and name of the user who created it on the first line. Something like this:
#### "# This file  is created by VEGA on:Sun Nov 26 10:31:06 CET 2017"
- La función que nos da la hora es `$date`
- Cuidado a la hora de escribir con comillas porque no todas interpretan el texto:
          - ' (comilla simple): no interpreta el texto
          - "" (dobles comillas): interpreta la variable en el texto
          - \`\`: evalúa y reemplaza
- Por tanto: `echo` "This file is created by VEGA on: $(date)"
    

#### 5. Save the information of 3 largest files located inside ~/Data/us_dot/otp/ into a three_largest_file.txt. 
#### (Hint: use ls with sort option and pipe the result)
- Para obtener la información detallada del contenido de un directorio: `ls -l`
- Si además la queremos ordenada por tamaño, habría que añadirle un -S: `ls -lS`
- Al aplicar este comando la primera línea que se imprime es la del total de archivos, por lo tanto no nos cuenta.
- Aplicamos un head para sacar las 4 primeras lineas (la primera es un archivo): `head -n 4`
- Luego tenemos que aplicar un tail para no imprimir esa primera fila de las 4 anteriores: `tail -n 3`
- Y lo tenemos que redirigir a un archivo txt que vamos a crear: `>` three_largest_file.txt
- Para encadenar comandos usaremos el pipe: `ls -lS` ~/Data/us_dot/otp/ `| head -n 4 | tail -n 3 > `three_largest_file.txt
    

#### 6. Save last 20 commands used at command line to a file. (Hint: use history and redirect the output)
- Primero vemos como sacar el historial de comandos usados (con el número de línea): `cat -n ~/.history`
- Ahora aplicamos el comando tail para sacar los últimos 20: `tail -n 20`
- Y lo tenemos que redirigir a un archivo txt que vamos a crear: `> `last_20_commands.txt
- Para encadenar comandos usaremos el pipe: `cat -n ~/.history | tail -n 20 > `last_20_commands.txt
    

#### 7. Print first 3 lines of ~/Data/shell/Text_example.txt together with line numbers
- Solo tenemos que hacer un head de las 3 primeras lineas: `head -n 3`
- Pero el head no nos permite imprimir los números de líneas, por tanto necesitamos un `cat -n`
- El resultado sería: `cat -n` ~/Data/shell/Text_example.txt `| head -n 3`
    

#### 8. Print content of ~/Data/shell/Text_example.txt except first 2 and last 3 lines.
- Tenemos los comandos `head` y `tail`. 
- Haremos `head -n -3` para imprimir todo excepto las 3 últimas líneas
- Y luego haremos `tail -n +3` para imprimir todo a partir de la tercera línea (borra las 3-1 =2 primeras)
- Para encadenar comandos usaremos el pipe: `head -n -3 `Text_example.txt `| tail -n +3`


#### 9. How many lines does ~/Data/opentraveldata/optd_aircraft.csv file have?
- Para contar el número de líneas usamos: `wc -l` ~/Data/opentraveldata/optd_aircraft.csv
    

#### 10. How many words do the first 5 lines of the ~/Data/shell/Finn.txt have?
- Para contar el número de palabras usamos: `wc -w` 
- Pero primero hay que separar las 5 primeras líneas del texto: `head -n 5 `~/Data/shell/Finn.txt `| wc -w`

----------------------------------------------------------------------------------------------------------------------------------------   
    
    
## Parte 4 - Búsqueda de ficheros

#### 1. Find all files located ONLY inside subdirectories of your home directory which have been modified in last 60min
- Para buscar archivos o directorios usamos el comando `find` y sus atributos
- Para que busque solo archivos hay que añadir: `-type f`
- Para que solo busque en subdirectorios: `-maxdepth 2` (1 es el directorio actual y 0 es la linea de comandos)
- Para que coja elementos modificados en los últimos 60 minutos: `-mmin -60`
- Combinando las opciones: `find ~ -maxdepth 2 -type f -mmin -60`
    

#### 2. Find all empty files inside subdirectories of your home directory which do NOT have read-write-execute permissions given to all users
- Para buscar archivos vacíos existe la opción `-empty` dentro de find
- Para buscar según los permisos: `-perm`
- A los archivos con permisos read-write-execute se les asigna el valor 777
- Para invertir el resultado de la opción se puede usar `-not` o un punto de exclamación `!`
- Combinando las opciones: `find ~ -mindepth 1 -type f !-perm 777`


#### 3. Expand previous command to grant these permissions using “ok” option
- La opción `-ok` te pregunta si quieres ejecutar el comando que la sigue antes de hacerlo.
- Después de escribir dicho comando hay que escribir siempre: `{} \;` (con espacio entre {} y \;)
- Por lo tanto sería: `find ~ -mindepth 1 -type f !-perm 777 -ok chmod 777 {} \;`
    

#### 4. Get top 3 largest files per subdirectory inside ~/Data/ 

    
----------------------------------------------------------------------------------------------------------------------------------------


## Parte 5 - Selección y recuento

#### 1. Find top 10 files by size in your home directory including the subdirectories. Sort them by size and print the result including the size and the name of the file (Hint: use find with -size and -exec ls -s parameters)
- Como hemos visto en la parte 4, usamos el comando `find` y sus opciones.
- Para coger los 10 ficheros más grandes usamos: `-size +10M` (podríamos poner un límite superior más alto también)
- Para sacar el tamaño y nombre de los archivos hay que aplicar el comando `ls -s` dentro del `find`: `-exec ls -s -sh {} \;` 
- Lo primero que se imprime es el tamaño, y es lo que tenemos que ordenar: `sort -nr` (reverse porque pone primero los más pequeños y nosotros queremos los más grandes)
- Para sacar los 10 primeros ficheros hacemos un `head`
- El código quedaría: `find -type f -size +10M -exec ls -sh {} \; | sort -nr | head`


#### 2. Create a dummy file with this command : seq 15 > 20lines.txt; seq 9 1 20 >> 20lines.txt; echo "20\n20" >> 20lines.txt; (check the content of file first)
- Creamos el archivo que nos piden: seq 15 > 20lines.txt; seq 9 1 20 >> 20lines.txt; echo "20\n20" >> 20lines.txt

##### a) Sort the lines of file based on alphanumeric characters
- Usamos el comando `sort -d` 20lines.txt (podríamos obviar el -d porque es la opción por defecto)

##### b) Sort the lines of file based on numeric values and eliminate the duplicates
- Usamos el comando `sort -n` para ordenarlos por valor numérico
- Usamos la opción `-u` para eliminar los duplicados
- Por tanto: `sort -nu` 20lines.txt

##### c) Print all duplicated lines of the file
- Para imprimir todos los duplicados tenemos que usar el comando `uniq -d`
- Pero `uniq` solo reconoce los duplicados si son consecutivos, es decir que primero hay que ordenarlos.
- Los comandos serían: `sort -n` 20lines.txt `| uniq -d`

##### d) Print the line which has most repetitions
- El comando `uniq -c` nos muestra cuantas veces se repite cada elemento.
- Hay que aplicarle un `sort` para ordenar esta lista y luego un `head` del primer elemento. 
- El código quedaría: `sort -n `20lines.txt `| uniq -c | sort -nr | head -1`

##### e) Print all lines with the number of repetitions sorted by the number of repetitions from lowest to highest
- Aplicamos los comandos del ejercicio anterior: `sort -n` 20lines.txt `| uniq -c | sort -n`


#### 3. Create another file with this command : seq 0 2 40 > 20lines2.txt
- Creamos el nuevo archivo: seq 0 2 40 > 20lines2.txt (es una lista de números de 0 a 40 con un paso de 2)

##### a) Create 3rd file from the first two but without duplicates
- Para concatenar dos archivos en un tercero: 20lines.txt 20lines.txt `>` 20lines3.txt
- Pero queremos que no haya repeticiones, por lo tanto hay que aplicarle un `sort -nu`
- El código quedaría: `sort -nu` 20lines.txt 20lines.txt `>` 20lines3.txt

##### b) Merge the first two files. Print unique lines together with the number of occurrences inside the merged file and sorted based on line content.
- Podemos concatenar los archivos sin tener que crear un tercero.
- Habría que aplicar un código parecido al anterior pero usando un pipe con `uniq -c`, que cuenta el número de elementos repetidos.
- El código sería: `sort -n` 20lines.txt 20lines.txt `| uniq -c`

#### 4. Go to ~/Data/opentraveldata. Get the line with the highest number of engines from optd_aircraft.csv using sort.
- Primero vemos el contenido del archivo optd_aircraft.csv: `less` optd_aircraft.csv
- Vemos que la variable que nos piden (number of engines) está en la 7ª columna.
- Los delimitadores de las columnas en este caso son "^", por lo tanto se usará la opción `sort -t "^"`
- Tendremos que hacer un `sort` que se base en esa columna: `sort -t "^" -k 7rn,7` optd_aircraft.csv | head -1`
(hacemos un reverse porque sino empieza por las columnas vacías)

    
----------------------------------------------------------------------------------------------------------------------------------------


## Parte 6 - Procesado y filtrado

#### 1. Change the delimiter of optd_aircraft.csv to “,”
- Sabemos que el archivo optd_aircraft.csv tiene como delimitador "^"
- Para cambiar de delimitador usamos el comando `tr`, pero no se puede ejecutar directamente sobre un archivo. 
- Primero hay que leer el archivo con un `cat` por ejemplo y luego aplicarle el `tr` con un pipe.
- El código quedaría: `cat` optd_aircraft.csv `| tr "^" ","`

#### 2. Check if optd_por_public.csv has repeated white spaces.
- El comando `tr` tiene la opción `-s` que reduce el caracter que le indicamos si lo encuentra repetido. 
- Por tanto lo que se podría hacer es: `cat` optd_por_public `| tr -s [:blank:] | wc`
- Este código nos contaría las líneas, palabras y caracteres del archivo optd_por_public después de quitarle los posibles espacios repetidos.
- Si comparamos el número de caracteres con el que había en el archivo original (`wc`optd_por_public) veremos que ha disminuido, por lo tanto si que habían espacios en blanco repetidos.

#### 3. How many columns has optd_por_public.csv? (Hint: use head and tr)
- Sabemos que en la primera linea del archivo están los títulos de las columnas, por tanto hacemos un `head -1`
- Vemos que el delimitador es "^", por lo tanto podemos aplicar un `tr "^" "\n"` para que convierta el delimitador que teníamos en saltos de línea. 
- Una vez tenemos los títulos de las columnas uno por fila, podemos hacer un `wc -l` para que cuente las líneas/filas.
- El código quedaría: `head -1` optd_por_public.csv `| tr "^" "\n" | wc -l`

#### 4. Print column names of optd_por_public.csv together with their column number. (Hint: use paste)
- Usamos el comando `paste` que nos permite concatenar dos archivos en paralelo (no uno detrás del otro).
- En el apartado anterior hemos visto cuantas columnas tenía nuestro archivo : 46
- También hemos sacado los nombres de cada una de esas columnas: `tr "^" "\n"`
- Podemos encadenar estos dos elementos: `paste <(seq 46) <(head -1 `optd_por_public.csv` | tr "^" "\n")`

#### 5. Use optd_airlines.csv to obtain the airline with the most flights?
- Al abrir el archivo vemos que su delimitador también es "^". 
- Las columnas que nos interesan son la 8 (nombre de la aerolínea) y la 14 (cantidad de vuelos), por tanto haremos un `cut` por esas dos columnas: `cut -d "^" -f8,14` optd_airlines.csv
- Ahora tenemos que ordenarlas con `sort -t "^" -k2nr,2` para que ordene en orden descendente la cantidad de vuelos.
- Como solo queremos ver la primera línea, hacemos un `head -1`

#### 6. Use optd_airlines.csv to obtain number of airlines in each alliance?
- La columna que nos interesa ahora es la 10 (nombre de las alliances): `cut -d "^" -f10` optd_airlines.csv
- Lo ordenamos con un `sort` y con un `uniq -c` contamos los valores repetidos de cada alliance.






