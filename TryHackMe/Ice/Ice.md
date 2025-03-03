
## Escaneo de puertos

```bash
nmap -sV -O ip
```

-sV: para ver la version de los servicios
-O: para ver el SO

![[Pasted image 20250220204820.png]]

Ahora para ver la peligrosidad de la vulnerabilidad nos vamos a https://www.cvedetails.com/ y buscamos la vulnerabilidad de Icecast y vemos que nos pide una que tiene nota de 7.5 y nos pide el Impact Score entonces buscamos todas las de 7.5 de Base Score y hemos encontrado esta

![[Pasted image 20250220205433.png]]

## Metasploit

Ahora entramos en metasploit y buscamos vulnerabilidades de icecast y nos aparece esto:


![[Pasted image 20250220205959.png]]

Usamos el único que nos aparece y lo configuramos

![[Pasted image 20250220210234.png]]

Para saber el información del sistema ponemos el siguiente comando:

```bash
sysinfo | findstr /B /C:"OS"
```


![[Pasted image 20250220211258.png]]

Ahora usamos el  `post/multi/recon/local_exploit_suggester` ejecutamos y seleccionamos la que pone `winwos/local/bypassuac_eventvwr` y la configuramos y ejecutamos.

![[Pasted image 20250220212718.png]]

Una vez estemos en el meterpreter usamos el comando `getprivs` para ampliar los permisos.

![[Pasted image 20250220213010.png]]

Ahora hacemos ps para ver la lista de procesos para ver si encontramos alguno sospechoso

![[Pasted image 20250220213732.png]]

Ahora nos migramos de proceso con  el comando 
```bash
migrate -N nombreDelProceso
```

![[Pasted image 20250220213911.png]]

Despúes miramos que usuario esta listado con el siguiente comando

```bash
getuid
```


![[Pasted image 20250220214048.png]]


Ahora instalamos kiwi que es una Mejora de la version de Mimikatz

![[Pasted image 20250220214453.png]]

Y obtenemos todas las credenciales con el comando  `creds_all`

![[Pasted image 20250220214719.png]]

Y vemos que la contraseña del usuario `Dark` es `Password01!`


 Para dumpear todas las contraseñas utilizamos `hashdump`

![[Pasted image 20250220214855.png]]


Para ver en remoto el escritorio del usuario en tiempo real usamos `screenshare`

![[Pasted image 20250220220009.png]]

Para probar la grabacion de micro probamos `record_mic` y para modificar la MAC utilizamos `timestomp` y para mantener la persistencia y autenticación utilizamos `golden_ticket_create`.

