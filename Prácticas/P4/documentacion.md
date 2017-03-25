# Práctica 4. Asegurar la granja web
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

### Certificado SSL autofirmado
**1. Para generar un certificado ssl hemos habilitado ssl, reiniciado el servicio apache2 y creado la carpeta donde pondremos el certificado.**

![Captura1](./capturas/C01.png?raw=true)

**2. Ahora generamos el certificado y lo configuramos con los datos necesarios de región, ciudad, provincia, email, etc.**

![Captura1](./capturas/C01.png?raw=true)

**3. Para indicar donde hemos colocado el certificado generado debemos ir al archivo /etc/apache2/sites-available/default-ssl.conf y modificar las siguientes líneas.**

![Captura1](./capturas/C01.png?raw=true)

**4. Copiamos el certificado del servidor 1 al servidor 2 y al balanceador para que sea el mismo.**

![Captura1](./capturas/C01.png?raw=true)

**5. En ambos servidores ejecutamos los comandos "a2ensite default-ssl" y "service apache2 reload".**

![Captura1](./capturas/C01.png?raw=true)

**6. Para que tenga sentido la configuración, al balanceador de carga le añadimos al fichero /etc/nginx/conf.d/default.conf las directivas correspondientes para que atienda por el puerto 443 los certificados ssl.**

![Captura1](./capturas/C01.png?raw=true)

[Enlace para configurar ssl para nginx](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-load-balancing-with-ssl-termination)

**6. Ahora podemos comprobar que en el navegador muestra la advertencia de que el certificado no es válido por el protocolo https.**

![Captura1](./capturas/C01.png?raw=true)

### Cortafuegos
**1. .**


**2. .**


