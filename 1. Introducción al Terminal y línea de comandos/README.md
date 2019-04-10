# Ejercicios de introducción al terminal y línea de comandos

##### 1. Create a directory “first_dir” in you home folder
    Creamos el directorio: mkdir first_dir
    
##### 2. Create an empty file “text_file.txt” inside “first_dir” directory. 

    Primero nos situamos en el directorio donde queremos crear el archivo: cd first_dir
    Creamos el archivo: touch text_file.txt


#### 3. Add execute permissions to group users, and write permissions to other users to “text_file.txt”

    Primero miramos qué permisos tiene nuestro archivo: ls -l text_file.txt
    Los permisos tienen el formato user/group/other y read/write/execute
    Añadimos los permisos: chmod g+x, ugo+w text_file.txt


4. Create 3 subdirectories inside “first_dir”: “sub1”, “sub2”, “text_file” 

5. Copy the “text_file.txt” file into “sub1” directory.

6. Move the “text_file.txt” into sub2 under name “text_file.txt.2” . 

7. Copy the whole directory “sub1” to “sub3” directory. 

8. Change file name of “first_dir /sub2/text_file.txt.2” to “first_dir /sub2/text_file.txt.backup”

9. Move “first_dir /sub2/text_file.txt.backup” to “first_dir” directory as hidden file

10. Delete the “sub2” subdirectory

