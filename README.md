# Creación de una máquina virtual 
**Objetivo:** Crear dos máquinas virtuales que se puedan conectar entre sí, utilizando los recursos de Azure.   

![](/imagenes/virtual%20machine.png)

**Requisitos**
- Cuenta de Azure con una suscripción activa
- Equipo de cómputo con sistema operativo: Windows, Linux o MacOs.
- Descargar la aplicación de escritorio remoto de Microsoft de Microsoft Store o descargarla desde un navegador.  


**Pasos**  
Se inicia sesión en Portal.Azure.com.  
En la barra de búsqueda escribimos “máquinas virtuales” y lo seleccionamos.  
Damos clic en el apartado crear y ahí escogemos la primer opción que se nos muestra de la lista desplegable.
![Imagen 1](/imagenes/Imagen1.jpg)

En la pestaña datos básicos, llenamos lo siguiente:  
**En Detalles del proyecto**  
Suscripción: La suscripción que queramos utilizar.  
Grupo de recursos: Podemos crear uno o seleccionar uno ya existente.
![](/imagenes/Imagen2.png)

**En Detalles de Instancia**  
Nombre de maquina virtual: El que queramos ponerle  
Región: Podemos escoger cualquiera, pero si no queremos que haya mucha latencia escogemos uno cercano a donde vivimos. Sin embargo, si en el apartado de Tamaño no nos deja seleccionar ninguno, tendremos que buscar una región que si nos permita seleccionar un tamaño.  
Opciones de disponibilidad: Lo dejamos como esta por defecto.  
Tipo de seguridad: Lo dejamos como esta por defecto.  
Imagen: Escogemos Windows 10 pro.  
Tamaño: Escogemos la primer opción de la lista desplegable.
![](/imagenes/Imagen3.png)

**En Cuenta de Administrador**  
Nombre de usuario: El que queremos colocar  
Contraseña: La que queramos colocar.  
Confirmar contraseña: Volvemos a escribir la contraseña que pusimos anteriormente.

**En Reglas de puerto de Entrada**  
Puertos de entrada públicos: Seleccionamos permitir los puertos seleccionados.  
Seleccionar puerto de entrada: Seleccionamos solo RDP.  
Licencias: Marcamos la casilla que esta.

Por último, damos clic en el botón de revisar y crear, y luego en crear.
![](/imagenes/Imagen4.png)

Esperamos a que se cree nuestra maquina virtual, Cuando se haya terminado de crear, lo que haremos será crear una segunda maquina virtual con los pasos descriptos anteriormente, esta maquina virtual la pondremos en el mismo grupo de recursos y en la misma región que pusimos en la primera. 

Después de llenar los campos de la pestaña datos básicos, nos iremos a la pestaña de redes, ahí revisaremos que esta nueva máquina virtual se encuentre en la misma red virtual que tiene la otra máquina virtual, de no ser así seleccionaremos la red correcta. Si todo está bien, le daremos clic al botón de Revisar y crear.
![](/imagenes/Imagen5.png)

Cuando se haya creado esta segunda maquina virtual nos iremos al grupo de recursos que contiene a las dos maquinas virtuales. Seleccionaremos la primer maquina virtual que hicimos. 
![](/imagenes/Imagen6.jpg)

Daremos clic en el apartado de conectar y en las opciones de la lista escogeremos RDP, a continuación, le daremos clic en el botón de descargar archivo RDP. Ese archivo que acabamos de descargar lo abriremos con la aplicación de escritorio remoto. Una vez que se abra nuestra máquina virtual nos pedirá nuestro usuario y contraseña para poder ingresar. 
![](/imagenes/Imagen7.png)

Una vez que hayamos ingresado nuestro usuario y contraseña le daremos en aceptar a lo que nos pida, y de esta forma habremos ingresado de forma exitosa a nuestra maquina virtual. Ahí dentro de nuestra maquina virtual abriremos el PowerShell y pondremos el siguiente comando:   
New-NetFirewallRule -DisplayName "Allow ICMPv4-In" -Protocol ICMPv4

Después ingresamos el siguiente comando:   
mstsc /v:10.0.0.5     (La ip que se colocó aquí es la de la segunda máquina virtual).
![](/imagenes/Imagen8.png)

Con el comando anterior lo que hacemos es que la primer maquina virtual pueda abrir a la segunda. Colocamos el usuario y contraseña que pusimos en la segunda máquina virtual y se nos abrirá la segunda maquina virtual dentro de la primera. Con esto logramos conectar dos máquinas virtuales de forma exitosa.
![](/imagenes/Imagen9.png)

