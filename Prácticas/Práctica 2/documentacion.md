# Práctica 2. Clonar la información de un sitio web
## Autores:
Javier Martínez Montilla
Bryan Moreno Picamán

**1. Instalamos rsync en las dos máquinas virtuales.**

![Captura1](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C01%20Instalando%20rsync.png?raw=true)

**2. Capturas de pantalla del servidor web funcionando en ambas máquinas virtuales.**

![Captura2](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C02%20.png?raw=true)
![Captura3](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C03.png?raw=true)

**3. Prueba de rsync manual**

![Captura4](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C04%20Usando%20rsync.png?raw=true)

**4. Captura de la sincronización realizada**

![Captura5](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C05.png?raw=true)

![Captura6](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C06.png?raw=true)

**5. Generación de claves públicas y privadas en máquina de copia para ssh**

![Captura7](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C07%20generando%20claves.png?raw=true)

**6. Copia de la clave pública en servidor principal y prueba de acceso**

![Captura8](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C09.png?raw=true)

**7. Captura de estado de las máquinas antes de la prueba de automatización con crontab**

![Captura9](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C10.png?raw=true)

**8. Captura del script.sh que contiene el comando rsync para la sincronización**

![Captura10](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C11.png?raw=true)

**9. Captura del archivo crontab indicando la llamada al script**

![Captura11](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C12.png?raw=true)

**10. Resultado de la automatización**

![Captura12](https://github.com/Javiyo90/GradoInformatica-SWAP/blob/master/practicas/practica2/capturas/C13.png?raw=true)