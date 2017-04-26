# Práctica 3. Balanceo de carga
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

**1. Insertamos la clave del repositorio del software nginx.**

![Captura1](./capturas/C01%20Instalando.png?raw=true)

**2. Añadimos los repositorios para descargar nginx.**

![Captura2](./capturas/C02%20Instalando.png?raw=true)

**3. Instalamos el software balanceador de carga nginx.**
![Captura3](./capturas/C03%20Instalando.png)

**4. Configuramos el fichero nginx dejando el contenido siguiente que mostramos en la captura. El archivo no existe después de la instalación por lo que hay que crearlo a mano.
Se han obviado las líneas #ip_hash y #keepalive para que la petición del mismo equipo no mande siempre al mismo servidor y poder comprobar que el balanceo de carga funciona para las dos máquinas virtuales.**

![Captura4](./capturas/C04%20Configurando%20Nginx.png?raw=true)

**5. Una vez reiniciado el servicio, mostramos la comprobación de que el balanceo de carga se produce en ambos servidores observando que para la misma ip en el navegador, el servidor elegido saca por pantalla un mensaje diferente.**

![Captura5](./capturas/C05%20Respuesta%201.png?raw=true)

![Captura6](./capturas/C06%20Respuesta2.png?raw=true)

![Captura7](./capturas/C07%20Respuesta%201%20y%202%20comando.png?raw=true)

**6. Instalamos el software haproxy para balanceo de carga.**

![Captura8](./capturas/C21%20Instalando.png?raw=true)

**7. Buscamos el archivo de configuración creado después de la instalación y modificamos el archivo de configuración de haproxy añadiendo el siguiente contenido. Se han actualizado las directivas timeout connect, timeout client y timeout server ya que las especificadas en el guión serán eliminadas en la siguiente revisión de haproxy.**

![Captura9](./capturas/C22%20Configurando%20HA.png?raw=true)

**8. Reiniciamos el servicio y comprobamos con curl que el balanceo de carga funciona a la perfección una vez añadida la configuración en el fichero.**

![Captura10](./capturas/C23%20Probando%20HA.png?raw=true)

###Parte Optativa. Configuración de un balanceador de carga con Pound

**1. Instalamos pound con apt-get.**

![Captura11](./capturas/C31.png?raw=true)

**2. Ahora modificamos el archivo /etc/pound/pound.cfg de manera que se nos quedaría como se muestra a continuación: **

*En ListenHTTP podemos cambiar la escucha de una IP fija a 0.0.0.0 para que escuche por todas las interfaces*
![Captura12](./capturas/C32.png?raw=true)

**3. Para que funcione también es necesario cambiar el fichero '/etc/default/pound' y poner el startup=1. **
![Captura13](./capturas/C34.png?raw=true)

**4. Una vez hecho todo esto solo nos queda reiniciar el servicio con '/etc/init.d/pound restart'.**
![Captura14](./capturas/C35.png?raw=true)

**5. Comprobamos que la visualización es correcta en ambas máquinas realizando curl al balanceador de carga.'.**
![Captura15](./capturas/C36.png?raw=true)