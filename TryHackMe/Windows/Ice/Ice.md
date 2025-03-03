# ICE
## Escaneo de puertos

```bash
nmap -sV -O ip
```

-sV: para ver la version de los servicios
-O: para ver el SO

![image](1.png)

Ahora para ver la peligrosidad de la vulnerabilidad nos vamos a https://www.cvedetails.com/ y buscamos la vulnerabilidad de Icecast y vemos que nos pide una que tiene nota de 7.5 y nos pide el Impact Score entonces buscamos todas las de 7.5 de Base Score y hemos encontrado esta

![image](2.png)

## Metasploit

Ahora entramos en metasploit y buscamos vulnerabilidades de icecast y nos aparece esto:


![image](3.png)

Usamos el único que nos aparece y lo configuramos

![image](4.png)

Para saber el información del sistema ponemos el siguiente comando:

```bash
sysinfo | findstr /B /C:"OS"
```


![image](5.png)

Ahora usamos el  `post/multi/recon/local_exploit_suggester` ejecutamos y seleccionamos la que pone `winwos/local/bypassuac_eventvwr` y la configuramos y ejecutamos.

![image](6.png)
Una vez estemos en el meterpreter usamos el comando `getprivs` para ampliar los permisos.
![image](7.png)


Ahora hacemos ps para ver la lista de procesos para ver si encontramos alguno sospechoso

![image](8.png)


Ahora nos migramos de proceso con  el comando 
```bash
migrate -N nombreDelProceso
```


![image](9.png)

Despúes miramos que usuario esta listado con el siguiente comando

```bash
getuid
```

![image](10.png)




Ahora instalamos kiwi que es una Mejora de la version de Mimikatz


![image](11.png)


Y obtenemos todas las credenciales con el comando  `creds_all`


![image](12.png)


Y vemos que la contraseña del usuario `Dark` es `Password01!`


 Para dumpear todas las contraseñas utilizamos `hashdump`

![image](13.png)


Para ver en remoto el escritorio del usuario en tiempo real usamos `screenshare`

![image](14.png)

Para probar la grabacion de micro probamos `record_mic` y para modificar la MAC utilizamos `timestomp` y para mantener la persistencia y autenticación utilizamos `golden_ticket_create`.

