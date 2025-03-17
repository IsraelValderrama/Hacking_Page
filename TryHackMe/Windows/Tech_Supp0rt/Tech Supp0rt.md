# TECH_SUPP0RT

## Escaneo de puertos

```bash
nmap -sV -O ip
```

-sV: para las versiones

-O: para el SO

![1](1.png)

## Entramos en el samba

```bash
smbclient -L //10.10.193.97/ -N
```

![2](2.png)

Probamos a entrar en algunos de los recursos y el único en el que hemos encontrado algo interesante es en `websvr`

![3](3.png)

Y nos traemos el archivo con el comando `get`

![4](4.png)

Entramos en el archivo y vemos el siguiente mensaje

![5](5.png)

Para descifrar la contraseña hemos utilizado `hashcat` pero no hemos encontrado la contraseña y entonces nos hemos metido en la web `cyber chef` y hemos utilizado la opción `magic` y nos ha dado que la contraseña es `Scam2021`

![6](6.png)

Ahora entramos en `/Subrion/panel` para iniciar sesión, en el login vemos que la versión es `Subrion CMS v4.2.1` y lo que vamos hacer es buscar vulnerabilidades para poder explotarlas  y ponemos las credenciales y nos conseguimos loguear:

![7](7.png)

Buscamos el exploit de Subrion CMS v4.2.1

![8](8.png)

Nos descargamos el .py con el siguiente comando `searchsploit -m php/webapps/49876.py` y ejecutamos el comando

```bash
sudo python 49876.py -u http://10.10.70.111/subrion/panel/ -l admin -p Scam2021
```

![9](9.png)

-u: para la url
-l: para el usuario
-p: para la contraseña

Una vez dentro miramos que somos en el sistema con whoami. Ahora lo que vamos a a hacer es buscar algun usuario y para ello nos vamos a `/etc/passwd` y nos hemos encontrado que hay un usuario que se llama `scamsite`

![10](10.png)

Ahora como tenemos un nuevo usuario vamos a intentar conectarnos por ssh al usuario `scamsite`

```bash
ssh scamsite@10.10.70.111
```

![11](11.png)

No lo hemos conseguido porque nos falta la contraseña entonces ejecutamos otra vez el python para entrar y ver si en algunas configuraciones encontramos algo. Buscando configuraciones hemos encontrado la configuración del worpress y vamos a buscar si en algunos de los archivos hay algo relacionado con la contraseña:

![12](12.png)

Hemos mirado en el `wp-login` pero no hay nada

![13](13.png)

Despues hemos mirado en `wp-config.php` y hemos encontrado la contraseña que es `ImAScammerLOL!123!`

![15](14.png)

Ahora nos volvemos a intentar a conectar por ssh con esta contraseña y ahora si entramos

![15](15.png)

sudo -l : Muestra los comandos que el usuario puede ejecutar con sudo.
file=/root/root.txt : Define una variable llamada `file` con la ruta del archivo.
sudo iconv -f 8859_1 -t 8859_1 "$file: Usa `iconv` con privilegios de sudo para convertir la codificación del archivo, aunque en este caso, la conversión es redundante (8859_1 a 8859_1)

Y nos da la flag `851b8233a8c09400ec30651bd1529bf1ed02790b`
