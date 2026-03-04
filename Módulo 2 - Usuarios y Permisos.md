Módulo 2 - Usuarios y permisos.

Para controlar el acceso al sistema se definieron distintos roles de usuario aplicando el principio de mínimo privilegio, donde cada usuario solo posee los permisos estrictamente necesarios.

Se definieron los siguientes usuarios:
![1 - roles y niveles de acceso](https://github.com/user-attachments/assets/3485f509-52b3-4583-a1fe-90f3684de6c9)

![2 - modulo dos- creamos tres carpetas](https://github.com/user-attachments/assets/0dbc5ec8-b804-4fd3-b1e8-eb39b8e63777)

a las carpetas que hemos creado le vamos asignar grupos y usuarios para que trabajen sobre ellas, entonces lo primero que haremos sera crear los grupos: 

![3 modulo dos - creacion de grupos](https://github.com/user-attachments/assets/0f040aa0-4ef0-4416-93d0-3252a7282210)

verificamos que esten creados en cat /etc/group

![4 - modulo dos, verificamos que estan creados](https://github.com/user-attachments/assets/740c6fc5-6337-4126-8426-99c450ddb951)

<img width="874" height="329" alt="Captura de pantalla 2026-03-04 222523" src="https://github.com/user-attachments/assets/de1bcaf3-c7ef-4e17-9d81-46275ec1585a" />

como se puede ver escribimos: 
sudo useradd -m -g administradores -s /bin/bash admin

donde agregamos usuarios primero en el directorio home -m, luego creamos el grupo con -g y luego la shell a que va pertenecer, en este caso /bin/bash que es la mas usual y ponemos el nombre
del usuario que es admin

![6 modulo dos permisos](https://github.com/user-attachments/assets/caa46b93-00ef-4456-9d52-07ee907c839a)

como se puede ver se editaron los permisos solo para que admin pueda ver todos, en analisis los analistas y admin puedan leer, y public donde todos pueden ver.

Conclusión

Para mejorar la seguridad y organización del sistema Linux se definió una estructura de usuarios basada en roles y control de privilegios, aplicando el principio de mínimo privilegio, el cual establece que cada usuario debe tener únicamente los permisos necesarios para realizar sus tareas.

En este contexto se definieron tres tipos principales de usuarios: admin, analista y usuario, además del usuario root, que corresponde al superadministrador del sistema.

El usuario root posee acceso completo a todos los recursos del sistema operativo. Este usuario puede modificar archivos críticos, instalar software, administrar procesos y cambiar configuraciones del sistema. Debido a su alto nivel de privilegios, su uso debe ser limitado únicamente a tareas administrativas críticas, ya que un uso incorrecto podría comprometer la seguridad o estabilidad del sistema.

El usuario admin fue creado para realizar tareas administrativas cotidianas sin utilizar directamente la cuenta root. Este usuario puede administrar el sistema mediante privilegios elevados (por ejemplo usando sudo) y tiene control total sobre el directorio /admin, el cual fue configurado con permisos 700, permitiendo únicamente al propietario leer, escribir y ejecutar dentro de ese directorio. Esto evita que otros usuarios puedan acceder a información administrativa sensible.

El usuario analista fue definido para tareas de monitoreo y análisis del sistema, como la revisión de registros o ejecución de herramientas de diagnóstico. Para este usuario se creó el directorio /analisis, configurado con permisos 750, lo que permite al propietario acceso completo mientras que el grupo puede leer y ejecutar. Esta configuración permite el análisis de información sin otorgar privilegios excesivos que puedan afectar la configuración del sistema.

El usuario usuario corresponde a un usuario estándar del sistema, destinado a tareas básicas y acceso a archivos compartidos. Para este caso se creó el directorio /public, configurado con permisos 755, permitiendo que el propietario pueda modificar archivos mientras que otros usuarios pueden leer o acceder al contenido sin poder alterarlo.

Esta estructura permite separar responsabilidades dentro del sistema, reducir riesgos de seguridad y evitar que usuarios sin privilegios puedan modificar configuraciones críticas. Además, la correcta gestión de permisos mediante herramientas como chmod y chown permite controlar el acceso a recursos del sistema de manera precisa, contribuyendo a mantener la integridad, confidencialidad y disponibilidad de la información.
