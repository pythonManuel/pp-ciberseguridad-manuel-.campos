Modulo 3 -  Servicios y procesos.md

Introducción

En sistemas Linux modernos, los servicios son gestionados principalmente por systemd, el cual se encarga de iniciar, detener y supervisar procesos del sistema.
Los servicios permiten que distintas funciones del sistema operativo y de las aplicaciones se ejecuten de manera continua en segundo plano.

En este laboratorio se analizaron dos tipos de servicios:

Un servicio esencial del sistema

Un servicio de aplicación

El objetivo fue observar cómo se ejecutan, qué usuario los ejecuta, y qué ocurre si estos servicios fallan o se detienen inesperadamente.

![1 - modulo 3 ssh estatus](https://github.com/user-attachments/assets/c5e01491-11da-435a-b247-7aa55ab8e164)

Servicio esencial del sistema

Servicio seleccionado:

ssh.service

Este servicio permite conexiones remotas al sistema mediante el protocolo SSH (Secure Shell).

Verificar estado del servicio

![2 - ssh enable](https://github.com/user-attachments/assets/0ca30894-41fc-418d-8a98-8b9e39c2cf26)

systemctl status ssh

![1 - modulo 3 ssh estatus](https://github.com/user-attachments/assets/ca2dc681-a268-4937-8ee3-ce84974231cb)

Iniciar el servicio
sudo systemctl start ssh
Verificar si está habilitado al iniciar el sistema
systemctl is-enabled ssh

![3 - ssh enabled](https://github.com/user-attachments/assets/6c6171b3-34fe-4ab3-80c9-c28e22905b95)


Resultado esperado:

enabled

Esto significa que el servicio se inicia automáticamente cuando el sistema arranca.

luego procedemos a hacer lo mismo con apache

![3 - iniciamos el servicio apache t y vemos el status](https://github.com/user-attachments/assets/ceffecfa-590a-43b5-8830-858fcc016629)

y vemos si el servicio esta enable:

![3 - modulo tres servicio apache enable](https://github.com/user-attachments/assets/e13b28a0-799f-46d9-85c5-408af68e9f19)

Cómo se inician los servicios

Los servicios en Linux se gestionan mediante systemd, utilizando archivos de configuración llamados unit files, ubicados normalmente en:

/lib/systemd/system/
/etc/systemd/system/

Estos archivos definen:

cómo se inicia el servicio

dependencias

comportamiento ante fallos

usuario que ejecuta el proceso

Para ver la configuración de un servicio:

systemctl cat ssh

![3 modulo 3 cat ssh](https://github.com/user-attachments/assets/5d048440-b419-490c-bca5-e9f82539ce63)

o

systemctl cat apache2

![3 modulo 3 cat apache](https://github.com/user-attachments/assets/58af6bf4-52d9-492a-b6cf-38d31b2d50dd)

Usuario que ejecuta los servicios
Servicio SSH

Para verificar el usuario que ejecuta el servicio:

![3 modulo de usuarios ssh](https://github.com/user-attachments/assets/0f895762-fce0-4cec-a2a8-d2058b8f60f9)

resultado: root y linux4

Servicio Apache

Para verificar el usuario:

![3  - modulo 3 apache](https://github.com/user-attachments/assets/0772c3af-292b-477f-8229-fd44e6f23555)

root, www-data y linux4

Esto se hace por seguridad:
el proceso principal se ejecuta como root, pero los procesos que manejan solicitudes web se ejecutan como www-data, un usuario con menos privilegios.

Qué pasa si los servicios fallan

Cuando un servicio falla:

systemd puede reiniciarlo automáticamente

el servicio queda en estado failed

se registran errores en los logs del sistema

Para ver los registros:

journalctl -u apache2

![3 - modulo 3 log apache](https://github.com/user-attachments/assets/4979976b-0987-4be9-8784-3c6f072f1d11)

o

journalctl -u ssh

![3 -  modulo 3 diagnostico](https://github.com/user-attachments/assets/22eb8591-1830-487b-9f4a-cb016eece2b0)

Esto permite diagnosticar problemas en los servicios.

servicios críticos del sistema

Algunos servicios esenciales en Linux incluyen:

Servicio	Función
ssh	acceso remoto seguro
systemd-logind	gestión de sesiones de usuario
network-manager	conectividad de red
cron	ejecución de tareas programadas

Si estos servicios fallan, el sistema puede perder funcionalidades importantes.

Impacto si los servicios se caen
Caída del servicio SSH

Impacto:

no se pueden realizar conexiones remotas

los administradores no pueden gestionar el sistema a distancia

Caída del servicio Apache

Impacto:

el sitio web deja de estar disponible

usuarios no pueden acceder a la aplicación web

posibles pérdidas económicas si el servicio es productivo

Conclusión

Los servicios en Linux son componentes fundamentales del sistema operativo y de las aplicaciones.

El gestor systemd permite controlar su estado, supervisar su funcionamiento y reiniciarlos automáticamente en caso de fallos.

Durante este laboratorio se observó cómo iniciar servicios, verificar su estado, analizar el usuario que los ejecuta y simular fallos para comprender su impacto en el sistema.




