

## Creacion de la maquina virtual en Azure Cli

### Conectarse desde Azure Cli A Azure

```
az login
```

Al preguntar sobre la cuenta, seleccionamos la proporcionada por nanfor:

<img src="img\01.png" alt="Selección de la cuenta" style="zoom:60%;" />

Confirmación de login de la cuenta:

<img src="img\02.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

Confirmación del proceso de login desde Powershell:

<img src="img\03.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />



### Creando un grupo de recursos

```
az group create -l EastUS -n myRGCLI 
```

Resultado:

<img src="img\04.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" /> 

### Creando una máquina virtual Linux

```
az vm create ^
 --name myVMCLI ^
 --resource-group myRGCLI ^
 --image UbuntuLTS ^
 --location EastUS ^
 --admin-username azureuser ^
 --admin-password Pa$$w0rd1234 ^
 --no-wait
```

Resultado:

<img src="img\05.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

Conectarse a la máquina Virtual de Linux

```
ssh azureuser@23.96.20.181
Nota: Dar que si en la creación del certificado SSH
```

Antes de acceder necesitamos resetear la contraseña por defecto:

<img src="img\06.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

Confirmación de conexión con linux:

<img src="img\07.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

1 - Actualizar en Linux

```
sudo apt-get update
```

Resultado:

<img src="img\08.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

2 - Hacer el upgrade

```
sudo apt upgrade
```

Resultado:

<img src="img\09.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

3 - Instalar un servidor web

```
sudo apt install -y apache2 apache2-utils
```

Resultado:

<img src="img\10.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

4 - Vemos el estatus de Apache

```
systemctl status apache2
```

Resultado:

<img src="img\11.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

5 - Ponemos un mensaje en nuestra página de Apache

```
cd /var/www/html
```

6 - Poner una nota en la página inde.html

```
sudo vi index.html <ENTER>
<ESC> : 198 <ENTER> // irme a la linea 198 que es donde esta el mensaje de index.html
<i> PONER EL MENSAJE <ESC>
: x <ENTER>

```

7 - Salir del SSH

```
exit <ENTER>
```

8 - Abrir puerto 80

<img src="img\12.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

9 - Resultado final:

<img src="img\13.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />



### Eliminando MV y recursos.

<img src="img\14.png" alt="Confirmación cuenta seleccionada" style="zoom:100%;" />

Borrar el grupo de recursos

```
az group delete -n myRGCLI  --yes --no-wait
```

## 