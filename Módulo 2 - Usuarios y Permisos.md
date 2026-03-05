Módulo 2 - Usuarios y permisos.

Para controlar el acceso al sistema se definieron distintos roles de usuario aplicando el principio de mínimo privilegio, donde cada usuario solo posee los permisos estrictamente necesarios. lo haremos segun la ley del minimo privilegio.

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

Evaluación de riesgos por mala gestión de permisos

Una mala configuración de usuarios, grupos o permisos en un sistema Linux puede generar vulnerabilidades importantes que comprometan la seguridad del sistema. Aunque en este caso se definió una estructura basada en roles y se aplicó el principio de mínimo privilegio, existen varios escenarios en los que una configuración incorrecta podría generar riesgos.

A continuación se describen algunos casos hipotéticos asociados a la gestión de los usuarios root, admin, analista y usuario, así como a los directorios /admin, /analisis y /public.

Acceso no autorizado a información administrativa

El directorio /admin fue configurado con permisos 700, lo que significa que solo el usuario administrador puede acceder a él. Sin embargo, si por error se configuraran permisos demasiado abiertos, por ejemplo:

chmod 777 /admin

cualquier usuario del sistema podría:

leer archivos administrativos

modificar configuraciones

ejecutar scripts administrativos

Esto podría permitir que un usuario sin privilegios modifique configuraciones críticas o introduzca código malicioso.

Manipulación de información de análisis

El directorio /analisis está destinado al usuario analista para revisar registros o ejecutar herramientas de monitoreo. Si los permisos fueran configurados incorrectamente, por ejemplo:

chmod 777 /analisis

otros usuarios podrían:

modificar registros de análisis

alterar resultados de monitoreo

eliminar evidencia de incidentes de seguridad

Esto representa un riesgo especialmente grave en entornos de ciberseguridad, donde la integridad de los registros es fundamental para detectar ataques o incidentes.

Alteración de archivos compartidos

El directorio /public fue configurado con permisos 755, lo que permite a otros usuarios leer el contenido pero no modificarlo. Sin embargo, si se configurara con permisos 777, cualquier usuario podría escribir en esa carpeta.

Un atacante podría:

introducir archivos maliciosos

reemplazar archivos legítimos

utilizar la carpeta para distribuir scripts dañinos

Esto podría facilitar ataques internos o comprometer la integridad de los archivos compartidos.

Escalada de privilegios

Si un usuario estándar obtuviera acceso a archivos del sistema o configuraciones administrativas, podría intentar escalar privilegios.

Por ejemplo, si se otorgaran permisos incorrectos en archivos sensibles como:

/etc/sudoers
/etc/passwd
/etc/shadow

un atacante podría:

modificar cuentas de usuario

otorgarse privilegios administrativos

obtener acceso completo al sistema

Por esta razón, estos archivos solo pueden ser modificados por root.

Uso indebido del usuario root

El usuario root posee control total sobre el sistema. Si su contraseña fuera débil o si su acceso se utilizara de forma innecesaria, podría ocurrir:

modificación accidental de archivos críticos

eliminación de configuraciones importantes

instalación de software malicioso

Por esta razón, en sistemas Linux se recomienda utilizar usuarios administrativos como admin con sudo, reservando el uso directo de root solo para tareas críticas.

Conclusión del análisis de riesgos

La correcta gestión de permisos y roles es fundamental para mantener la seguridad de un sistema Linux. Configuraciones incorrectas pueden permitir accesos no autorizados, manipulación de información o incluso comprometer completamente el sistema.

La estructura implementada en este análisis, basada en la separación de roles entre root, admin, analista y usuario, junto con permisos específicos en los directorios /admin, /analisis y /public, permite reducir significativamente estos riesgos y mantener un entorno más seguro y controlado.


Conclusión

Para mejorar la seguridad y organización del sistema Linux se definió una estructura de usuarios basada en roles y control de privilegios, aplicando el principio de mínimo privilegio, el cual establece que cada usuario debe tener únicamente los permisos necesarios para realizar sus tareas.

En este contexto se definieron tres tipos principales de usuarios: admin, analista y usuario, además del usuario root, que corresponde al superadministrador del sistema.

El usuario root posee acceso completo a todos los recursos del sistema operativo. Este usuario puede modificar archivos críticos, instalar software, administrar procesos y cambiar configuraciones del sistema. Debido a su alto nivel de privilegios, su uso debe ser limitado únicamente a tareas administrativas críticas, ya que un uso incorrecto podría comprometer la seguridad o estabilidad del sistema.

El usuario admin fue creado para realizar tareas administrativas cotidianas sin utilizar directamente la cuenta root. Este usuario puede administrar el sistema mediante privilegios elevados (por ejemplo usando sudo) y tiene control total sobre el directorio /admin, el cual fue configurado con permisos 700, permitiendo únicamente al propietario leer, escribir y ejecutar dentro de ese directorio. Esto evita que otros usuarios puedan acceder a información administrativa sensible.

El usuario analista fue definido para tareas de monitoreo y análisis del sistema, como la revisión de registros o ejecución de herramientas de diagnóstico. Para este usuario se creó el directorio /analisis, configurado con permisos 750, lo que permite al propietario acceso completo mientras que el grupo puede leer y ejecutar. Esta configuración permite el análisis de información sin otorgar privilegios excesivos que puedan afectar la configuración del sistema.

El usuario usuario corresponde a un usuario estándar del sistema, destinado a tareas básicas y acceso a archivos compartidos. Para este caso se creó el directorio /public, configurado con permisos 755, permitiendo que el propietario pueda modificar archivos mientras que otros usuarios pueden leer o acceder al contenido sin poder alterarlo.

Esta estructura permite separar responsabilidades dentro del sistema, reducir riesgos de seguridad y evitar que usuarios sin privilegios puedan modificar configuraciones críticas. Además, la correcta gestión de permisos mediante herramientas como chmod y chown permite controlar el acceso a recursos del sistema de manera precisa, contribuyendo a mantener la integridad, confidencialidad y disponibilidad de la información.

ANEXO

ahora toca explicar un tipo de permiso llamado suid, la definicion estandart es la siguiente:

"SUID (Set User ID) es un bit de permiso especial en Linux que permite que un archivo ejecutable se ejecute con los privilegios del propietario del archivo, en lugar de los privilegios del usuario que lo ejecuta."

Esto se utiliza principalmente para permitir que usuarios no privilegiados ejecuten tareas que requieren permisos elevados, de forma controlada.

En la mayoría de los sistemas Linux, el propietario de estos binarios suele ser root, y se representa con la letra s, como en la siguiente imagen:

![8 - modulo 2 suid](https://github.com/user-attachments/assets/2ce6c567-d105-424e-8b30-f411bb427494)

como se puede apreciar, la salida es la siguiente: -rwsr-xr-x 1 root root

la "s" representa este permiso especial.

asi es como se aplica con chmod este permiso especial, a continuacion le daremos el siguiente permiso a una carpeta llamada programa que tendra los valores 

4 = SUID

7 = rwx propietario

5 = r-x grupo

5 = r-x otros

![9 modulo 2 suid](https://github.com/user-attachments/assets/444a87c2-a9ee-4f44-aae5-69f1968296f5)

y se quita de la siguiente manera "chmod u-s programa", a continuacion la imagen de la carpeta creada, los permisos que vienen por defecto, luego los permisos suid aplicado y luego quitado

![10 modulo 2 suid quitado](https://github.com/user-attachments/assets/da567605-a26b-4adc-9f64-eb5511acb412)


En auditorías de seguridad es fundamental identificar todos los binarios con SUID.

![11 modulo 2 todos suid](https://github.com/user-attachments/assets/5c8ce575-6888-4113-9622-b9800699e0c4)

Escalamiento de privilegios

Por definicion el escalamiento de privilegios es una técnica utilizada por un atacante para obtener permisos superiores a los que inicialmente posee en un sistema.

En Linux generalmente implica pasar de usuario por defecto a usuario root

Esto permite al atacante: modificar archivos críticos, instalar malware, persistir en el sistema, comprometer completamente el sistema operativo.

se puede hacer de la siguiente manera, preguntamos por el kernel y buscamos exploit, o ocupamos leanpeas para ver distintas vulnerabilidades.

![13   modulo 2 leanpeas](https://github.com/user-attachments/assets/c3f8dff9-affa-43c3-a57a-8170bb154eff)

esto sirve para enumerar los servicios y encontrar alguno que permita escalar privilegios. pero eso no lo haremos ahora es solo una demostracion.








