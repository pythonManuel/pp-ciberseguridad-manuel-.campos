Módulo 4 – Logs y trazabilidad
1. Introducción

Los logs son registros que almacenan eventos ocurridos dentro de un sistema informático. En sistemas Linux, los logs permiten monitorear el funcionamiento del sistema, identificar errores, auditar actividades de usuarios y realizar análisis forense ante incidentes de seguridad.

La correcta gestión de logs es un elemento fundamental en ciberseguridad, ya que permite reconstruir eventos, detectar comportamientos anómalos y analizar posibles ataques.

En sistemas Linux modernos, gran parte de los registros se gestionan mediante systemd-journald y el sistema de logs tradicional ubicado en /var/log.

![1 - logvar](https://github.com/user-attachments/assets/7c530f0e-b4d1-40d2-b4a4-a3adbc9f41a6)

Identificación de logs relevantes

En el sistema se identificaron los siguientes logs importantes:

Logs del sistema

Ubicación:

/var/log/syslog

Este archivo registra eventos generales del sistema operativo, incluyendo:

inicio y detención de servicios

mensajes del kernel

errores del sistema

eventos del sistema operativo

![2 - catlog](https://github.com/user-attachments/assets/fbf2db46-870f-4af1-ad0c-d27f0c839495)

También se pueden consultar mediante:

![3 - journal](https://github.com/user-attachments/assets/536f8951-b8f8-4881-bb04-eca528973029)

Logs de autenticación

Ubicación:

/var/log/auth.log

Este log registra eventos relacionados con autenticación de usuarios.

Eventos registrados:

inicios de sesión

intentos fallidos de login

uso de sudo

autenticaciones SSH

cambios de privilegios

![4 - auth](https://github.com/user-attachments/assets/55ae06ea-cf31-47fc-94d2-ebc618a3ef57)

Eventos registrados en los logs

Los logs permiten registrar distintos tipos de eventos, entre ellos:

inicio y detención de servicios

autenticaciones exitosas

intentos fallidos de acceso

uso de privilegios administrativos

errores del sistema

conexiones de red

accesos a servicios web

Estos registros son esenciales para monitoreo de seguridad y análisis posterior.

Eventos que normalmente NO se registran

A pesar de su importancia, no todos los eventos quedan registrados automáticamente.

Ejemplos de eventos que pueden no quedar registrados:

actividades ejecutadas dentro de aplicaciones sin logging

comandos ejecutados por usuarios sin auditoría habilitada

acciones realizadas por malware que manipula registros

accesos físicos al sistema sin autenticación

Por esta razón, en entornos profesionales se utilizan sistemas adicionales como:

SIEM

auditoría avanzada

monitoreo de integridad de archivos

Se simuló un evento legítimo ejecutando un comando administrativo.

Comando ejecutado:

![5 - apache](https://github.com/user-attachments/assets/f01c08fd-8bfb-470f-97c8-b089de710c5b)

Este evento queda registrado en:

/var/log/auth.log

![6 - register apache](https://github.com/user-attachments/assets/5b698bc6-02a9-4cf5-ada6-0c500cd679a6)

Simulación de evento sospechoso

Se simuló un intento fallido de autenticación.

![7- sshd](https://github.com/user-attachments/assets/f543a1d9-8cc0-4379-b7d1-7beb2946e490)

Este evento indica un intento fallido de acceso mediante SSH.

Este tipo de registro puede indicar:

errores de usuario

intentos de acceso no autorizados

ataques de fuerza bruta.
Análisis de valor forense

Los logs poseen un alto valor en análisis forense digital, ya que permiten reconstruir la secuencia de eventos ocurridos en un sistema.

Mediante el análisis de logs es posible:

identificar el momento exacto de un incidente

determinar qué usuario realizó una acción

analizar direcciones IP de origen

detectar intentos de acceso no autorizados

correlacionar eventos entre diferentes servicios

Por esta razón, en entornos profesionales los logs se almacenan de forma centralizada y protegida para evitar su manipulación.

la mejor forma de encontrarlos es abrir un log con nano, apretar f6 que es el buscador y poner el nombre de lo que se sospecha encontrar.

Conclusión

La gestión y análisis de logs constituye una de las herramientas más importantes dentro de la ciberseguridad. Los registros permiten monitorear el comportamiento del sistema, detectar incidentes y realizar investigaciones forenses.

Durante este laboratorio se identificaron diferentes tipos de logs en Linux, se analizaron los eventos registrados y se simularon escenarios de actividad legítima y sospechosa. 

Este tipo de análisis permite comprender el valor de los logs como fuente crítica de información para la seguridad y administración de sistemas.


