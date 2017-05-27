# Práctica 4. Asegurar la granja web
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

### Certificado SSL autofirmado
**1. Para generar un certificado ssl hemos habilitado ssl, reiniciado el servicio apache2 y creado la carpeta donde pondremos el certificado.**

![Captura1](./capturas/C01.png?raw=true)

**2. Ahora generamos el certificado y lo configuramos con los datos necesarios de región, ciudad, provincia, email, etc.**

![Captura2](./capturas/C02.png?raw=true)

**3. Para indicar donde hemos colocado el certificado generado debemos ir al archivo /etc/apache2/sites-available/default-ssl.conf y modificar las siguientes líneas.**

![Captura3](./capturas/C03.png?raw=true)

**4. Copiamos el certificado del servidor 1 al servidor 2 y al balanceador para que sea el mismo.**

![Captura4](./capturas/C04.png?raw=true)

![Captura5](./capturas/C05.png?raw=true)

**5. En ambos servidores ejecutamos los comandos "a2ensite default-ssl" y "service apache2 reload".**

![Captura6](./capturas/C07.png?raw=true)

**6. Para que tenga sentido la configuración, al balanceador de carga le añadimos al fichero /etc/nginx/conf.d/default.conf las directivas correspondientes para que atienda por el puerto 443 los certificados ssl.**

![Captura7](./capturas/C08.png?raw=true)

[Enlace para configurar ssl para nginx](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-load-balancing-with-ssl-termination)

**6. Ahora podemos comprobar que en el navegador muestra la advertencia de que el certificado no es válido por el protocolo https pero es accesible tras confirmar que queremos acceder al sitio.**

![Captura8](./capturas/C09.png?raw=true)

![Captura9](./capturas/C10.png?raw=true)

![Captura10](./capturas/C11.png?raw=true)

### Cortafuegos

**1. Antes de añadir reglas a iptables vemos que reglas hay activas.**

![Captura10](./capturas/C21.png?raw=true)

**2. Añadimos las reglas por medio de un script con el contenido mostrado a continuación.**

![Captura11](./capturas/C22.png?raw=true)

**4. Reiniciamos el servicio y vemos que todo funciona correctamente.**

![Captura13](./capturas/C23.png?raw=true)

**5. Finalmente incluimos el script en crontab.**

![Captura14](./capturas/C24.png?raw=true)

