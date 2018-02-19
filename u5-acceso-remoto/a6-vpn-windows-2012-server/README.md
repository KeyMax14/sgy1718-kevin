# U4-A6 | VPN en Windows 2012 Server

En esta actividad vamos a crear una máquina virtual con Windows 2012 server, la cual dispondra de dos insterfaces, una interna y otra externa. Esta máquina servirá como VPN.

# 1. Configuración de las interfaces

Con nuestra máquina con WS 2012 ya instalada vamos a configurar una interfaz en virtualbox con red interna y otra con adaptador puente para la red externa.

- Red Externa:

  ![Imagen](img/001.png)

- Red Interna:

  ![Imagen](img/002.png)

Ya dentro del sistema operativo vamos a indicar cual es la interna y cual es la externa fijándonos un sus MAC.

![Imagen](img/003.png)

## 1.2 Configuración Interfaz Externa

Configuramos la interfaz externa de modo que solo dejamos habilitado TCP/IP v4.

![Imagen](img/004.png)

Dentro de la configuración avanzada de TCP/IPv4 nos vamos a las pestaña `WINS` y deshabilitamos las dos opciones marcadas en la siguiente captura.

![Imagen](img/005.png)

## 1.2 Configuración Interfaz Interna

En la interfaz interna solo vamos a configurar una IP para tener localizada la puerta de enlace desde las máquinas clientes.

![Imagen](img/006.png)

# 2. Configuración del acceso remoto

Nos dirigimos al `Administrador del servidor` y agregamos un nuevo rol, en este caso será el rol de `Acceso Remoto`.

![Imagen](img/007.png)

![Imagen](img/008.png)

![Imagen](img/009.png)

Este rol lo seleccionamos exclusivamente para poder seleccionar la opción `DirectAccess y VPN (RAS)`.

![Imagen](img/010.png)

Terminamos la instalación del rol con las opciones por defecto. Una vez acabada nos indica que debemos configurarlo, por lo que clicamos el enlace.

![Imagen](img/011.png)

En este apartado se nos indicará si queremos activar ambos servicios de acceso remoto, a nosotros solo nos interesa el acceso VPN.

![Imagen](img/012.png)

![Imagen](img/013.png)

## 2.1. Configuración de Enrutamiento y acceso remoto para VPN

Vamos a configurar ahora el servicio VPN. Pulsamos clic derecho en nuestro servidor y escogemos la primera opción.

![Imagen](img/014.png)

Esto nos mandará a un asistente. Vamos a seleccionar las siguientes opciones:

![Imagen](img/015.png)

![Imagen](img/016.png)

- Seleccionamos el VPN.

![Imagen](img/017.png)

- Seleccionamos la interfaz por la que salimos a internet.

![Imagen](img/018.png)

![Imagen](img/019.png)

![Imagen](img/020.png)

![Imagen](img/021.png)

![Imagen](img/022.png)

![Imagen](img/023.png)

Al clicar en finalizar podemos comprobar que ya esta activo el servicio.

![Imagen](img/024.png)

### 2.1.1. Configurar filtros

En el caso de que queramos configurar filtros podemos dirigirnos a `IPv4` -> `Externa` y pulsamos sobre propiedades.

![Imagen](img/025.png)

![Imagen](img/026.png)

Desde hay pulsamos `Filtros entrantes...` y ya podemos configurar lo que queramos.

![Imagen](img/027.png)

# 3. Configuración del cliente.

Vamos a configurar la interfaz como adaptador puente.

![Imagen](img/028.png)

Configuramos la IP, le colocamos la siguiente respecto a nuestro servidor.

![Imagen](img/029.png)

## 3.1. Configuración del VPN

Nos dirigimos al centro de redes y recursos y seleccionamos `Configurar una nueva conexión de red`.

![Imagen](img/030.png)

- Seleccionamos conectar a una Red de trabajo.

  ![Imagen](img/031.png)

- Seleccionamos `VPN`.

  ![Imagen](img/032.png)

![Imagen](img/033.png)

> En el siguiente paso nos pedirán un usuario y contraseña, al menos si utilizamos Wndows 7. Por lo que vamos a tener que configurar un usuario de active directory en nuestro servidor.
>
>![Imagen](img/034.png)
>
>En las propiedades de este usuario debemos ir al apartado `Marcado` y permitir las conexiones desde redes externas.
>
>![Imagen](img/035.png)
>
>Ya podremos iniciar sesión.
>
>![Imagen](img/036.png)

Esperamos a que inicie sesión y nos indica que estamos conectados.

![Imagen](img/037.png)

# 4. Comprobaciones de la conexión

Si nos dirigimos a la ubicación de los ajustes de red podemos comprobar que estamos conectados a la red `VPN`.

![Imagen](img/038.png)

Ejecutando `ipconfig` desde un `cmd` podemos comprobar que la IP que se nos ha asignado pertenece al rango establecido.

![Imagen](img/039.png)

Una vez hecho estas comprobaciones podemos dar por finalizada la práctica.
