# Práctica 6. Discos RAID
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

### Configurando RAID
**1. Comenzamos instalando mdamd para configurar el servicio de RAID.**

![Captura1](./capturas/C01.png?raw=true)

**2. Examinamos los discos para comprobar que están disponibles los que usaremos en nuestro RAID.**

![Captura2](./capturas/C02.png?raw=true)

**3. Creamos el RAID.**

![Captura3](./capturas/C03.png?raw=true)

**4. Creando el sistema de ficheros .**

![Captura4](./capturas/C04.png?raw=true)

**5. Montamos en /dat nuestro raid y examinamos si está montado correctamente.**

![Captura5](./capturas/C05.png?raw=true)

**6. Detalle del RAID del sistema.**

![Captura6](./capturas/C06.png?raw=true)

**7. Configuramos el montado automático del RAID en /dat.**

![Captura7](./capturas/C07.png?raw=true)

**8. Simulamos un fallo, desconexión y conexión del disco y observamos que los ficheros se mantienen sin ningún problema.**

![Captura8](./capturas/C08.png?raw=true)

**9. Detalle del RAID del sistema con todos los discos.**

![Captura9](./capturas/C09.png?raw=true)

**10. Detalle del RAID del sistema con un disco menos.**

![Captura10](./capturas/C10.png?raw=true)

**11. Detalle del RAID del sistema. Un disco añadido en caliente y que está reconstruyendo el sistema de datos para ser coherente con el disco existente.**

![Captura11](./capturas/C11.png?raw=true)





