Módulo 1 – Análisis del sistema

![1 - version del sistema](https://github.com/user-attachments/assets/cd95ce3c-184c-4efb-9cd6-05c51c92c604)

Resultado:

Distribución: Ubuntu

Versión: 25.10

Ubuntu es una de las distribuciones Linux más utilizadas tanto en entornos de escritorio como en servidores. Está basada en Debian y se caracteriza por su estabilidad, gran comunidad y amplio soporte de software.

![2 - kernel info](https://github.com/user-attachments/assets/a3b4f36c-b4d0-431b-8de3-978bbfb398a9)

El kernel de Linux es el núcleo del sistema operativo y se encarga de:

Gestionar el hardware

Administrar memoria

Controlar procesos

Manejar dispositivos

Gestionar el sistema de archivos

El kernel 6.17.0-14-generic pertenece a una versión moderna de Linux optimizada para compatibilidad general con hardware standart.

![3 - arquitectura](https://github.com/user-attachments/assets/fca7a93e-ca57-4b9f-9073-edb7d6eeb927)

La arquitectura x86_64 corresponde a sistemas de 64 bits, utilizada por la mayoría de procesadores modernos de Intel y AMD.

Ventajas de esta arquitectura:

Soporte para mayor cantidad de memoria RAM

Mejor rendimiento en aplicaciones modernas

Compatibilidad con la mayoría del software actual

![3 - uso de cpu](https://github.com/user-attachments/assets/8b13c44a-750b-4de7-91a3-b959eec2860f)

Resultados aproximados observados:

Uso de CPU total: 2%

CPU en estado idle: 95% - 99%

Esto indica que el sistema se encuentra prácticamente en reposo, con muy poca carga de trabajo.

El sistema utiliza 2 CPUs virtuales, lo que es típico en máquinas virtuales utilizadas para laboratorio o desarrollo como es el caso.

![4 - uso de memoria](https://github.com/user-attachments/assets/fec52f8c-6066-420c-91f6-21f4eba1b8d0)

Resultados relevantes:

Memoria total: 3.4 GB

Memoria disponible: 1.8 GB

Memoria libre: 335 MB

Memoria cacheada: 1.6 GB

Linux utiliza gran parte de la memoria como cache de disco, lo cual mejora el rendimiento del sistema. Esta memoria puede liberarse automáticamente si las aplicaciones la necesitan.

El sistema mantiene una swap de aproximadamente 3.6 GB, la cual sirve como memoria virtual en caso de que la RAM se sature.

![4 - uso de disco](https://github.com/user-attachments/assets/f8f2df52-b439-4c13-907c-8d37ac098ffe)

Resultados principales:

Partición	Tamaño	Usado	Disponible	Uso
/dev/sda2	20 GB	11 GB	7.7 GB	59%

El sistema principal se encuentra en la partición /dev/sda2, donde está instalado Ubuntu.

El uso del disco se encuentra dentro de valores normales para una instalación de laboratorio.

5. Recursos consumidos en reposo

Con el sistema recién iniciado y sin ejecutar aplicaciones pesadas:

CPU

Uso aproximado: 1% – 3%

Memoria

Uso efectivo: aproximadamente 1.5 GB

Disco

Uso total: 11 GB de 20 GB

Estos valores indican que el sistema es liviano y adecuado para entornos de prueba o laboratorio.

6. Procesos críticos del sistema

En un sistema Linux existen procesos esenciales para su funcionamiento. Algunos de los más importantes son:

systemd

Es el proceso padre del sistema (PID 1) y se encarga de:

Iniciar el sistema operativo

Gestionar servicios

Controlar procesos del sistema

Si este proceso falla, el sistema no puede funcionar correctamente.

systemd-journald

Este proceso se encarga de:

Gestionar los logs del sistema

Registrar eventos del sistema operativo

Facilitar auditorías y análisis de errores

Es crítico para monitoreo y troubleshooting.

systemd-resolved

Este proceso administra:

Resolución de nombres DNS

Consultas de red

Permite que el sistema pueda conectarse correctamente a servicios externos.

sshd (cuando está activo)

Permite el acceso remoto seguro al sistema mediante SSH, lo cual es esencial en servidores y entornos de administración remota.

Conclusión

El sistema analizado corresponde a una máquina virtual con Ubuntu 25.10, arquitectura x86_64 y kernel 6.17.0-14-generic.

Durante el análisis se observó que:

El uso de CPU en reposo es muy bajo.

El consumo de memoria es moderado.

El uso de disco se encuentra dentro de valores normales.

Esto demuestra que Ubuntu es un sistema eficiente y adecuado para entornos de desarrollo, laboratorio y ciberseguridad.

Además, el sistema depende de procesos críticos como systemd, journald y resolved, los cuales garantizan el funcionamiento correcto del sistema operativo.



