# Práctica 5. Replicación de bases de datos MySQL
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

### Crear una BD e insertamos datos
**1. Lo primero que hacemos es crear una base de datos llamada 'contactos', cambiar a esa BD, crear una tabla 'datos' con un campo nombre (varchar(100) y un campo telefono (int)).**

![Captura1](./capturas/C01.png?raw=true)

**2. Insertamos un usuario en la tabla y mostramos el contenido de esa tabla.**

![Captura2](./capturas/C02.png?raw=true)

### Replicar una BD MySQL con mysqldump

**1. En la máquina principal accedemos a mysql como root y evitamos que haya acceso a la BD mientras se hace la copia de seguridad.
Ahora sí realizamos el guardado con el comando 'mysqldump ejemplodb -u root -p > /root/ejemplodb.sql' y desbloqueamos las tablas **

![Captura3](./capturas/C03.png?raw=true)

**2. Ahora toca copiar el archivo en la máquina esclavo de manera que realizamos el comando 
'scp root@192.168.43.77:/root/ejemplodb.sql /root/'.**

![Captura4](./capturas/C04.png?raw=true)

**3. Es importante saber que se copia en fichero de texto plano y que se necesita montar en una base de datos creada anteriormente.**

![Captura5](./capturas/C05.png?raw=true)

### Replicación de BD mediante una configuración maestro-esclavo.

**1. Lo primero que hacemos es configurar la máquina maestro modificando el archivo de configuración de mysql. Aunque en el guión se indica el fichero '/etc/mysql/my.cnf', realizando varias pruebas hemos descubierto que el fichero que hay que modificar es '/etc/mysql.conf.d/mysql.cnf'. Ahora muestro el contenido de ambos ficheros donde se ve que el primero que es el especificado en el guión de prácticas no contiene nada y el segundo mencionado tiene todas las directivas a modificar.**

-- Fichero /etc/mysql/my.cnf
![Captura6](./capturas/C06.png?raw=true)


-- Fichero /etc/mysql.conf.d/mysql.cnf
![Captura7](./capturas/C07.png?raw=true)


**2. Una vez realizadas las modificaciones oportunas, guardamos el documento y reiniciamos el servicio mysql.
En el esclavo realizamos la misma configuración en el fichero y la guardamos. La única diferencia es que en el maestro el server-id es 1 y en el esclavo es 2. 
Creamos el usuario esclavo y le damos permidos de acceso para la replicación.**

![Captura8](./capturas/C08.png?raw=true)

**3. Ahora volvemos a la máquina maestro y hacemos SHOW MASTER STATUS y vemos los campos File y Position que son los que nos interesan para realizar la conexión.**

![Captura9](./capturas/C09.png?raw=true)

**4. Desde el esclavo ahora realizamos el comando 
'CHANGE MASTER TO MASTER_HOST='192.168.43.77',
MASTER_USER='esclavo', MASTER_PASSWORD='esclavo',
MASTER_LOG_FILE='bin.000001', MASTER_LOG_POS=154,
MASTER_PORT=3306;' de manera que se conecta con la BD de la máquina maestra. No hay que olvidar hacer 'START SLAVE;' para que comience la replicación.**

![Captura10](./capturas/C10.png?raw=true)

**5. Para asegurarnos de que todo funciona correctamente miramos con 'SHOW SLAVE STATUS\G' en el esclavo y el campo Seconds_Behind_Master contiene un 0. Eso indica que está funcionando.**

![Captura11](./capturas/C11.png?raw=true)

**6. Ahora comprobamos que al insertar un campo en la máquina maestro inmediatamente se copia en la máquina esclavo sin ningún problema.**

![Captura12](./capturas/C12.png?raw=true)

**7. Creamos dos usuarios más para asegurarnos y efectivamente, todas las inserciones realizadas en la máquina maestra se replican en la máquina esclava.**

![Captura13](./capturas/C13.png?raw=true)