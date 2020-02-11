## Servidor de jenkins

Este proyecto contiene un servidor de jenkins con docker, en el cual hacemos conexiones con ssh


Para generar las llaves se hace con la siguiente instrucción
```
    $ ssh-keygen -t rsa -b 4096 -C "mail@domain.com" -f key_name
```

El cual generá 2 archivos
```
    $ ls 
    key_name    key_name.key
```

Para poder hacer la conexion dentro de jenkins el server se queda con el key_name

El servior anfitrion se quedará con la llave publica pudiendola conectar con
```
    $ ssh-copy-id -i ~/route/to/new/key_name.key user@host 
```

En el servidor de jenkins se hacen las siguientes configuraciones

* Agregar confuguración > gestor de plugins buscando para instalar ssh
* Configuración de credenciales en **credentials > System > Global credentials > Add Credentials**
* Agregar la conexion ssh dentro de **Adminditrar Jenkins > Configurar Sistema > SSH remote hosts** y se agrega la conexión con la nueva llave creada y el host
* Finalmente se puede hacer una ejecución con un bash y el remoto, creando una tarea de estilo  libre y agregando en la sección de ejecutar la opcion de **Execute shell script on remote host using ssh**