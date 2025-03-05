# Guía Completa de Volatility

## Comandos Importantes

### Identificar el perfil del sistema

```bash
vol.py  -f VOLCADO imageinfo
```

### Listar Procesos Activos

```bash
vol.py -f VOLCADO --profile=PERFIL pslist
```

- **pslist**: Muestra los procesos activos en el volcado de memoria.

### Listar Conexiones de Red

```bash
vol.py -f VOLCADO --profile=PERFIL netscan
```

- **netscan**: Muestra conexiones abiertas y sockets en uso.

### Ver Procesos Ocultos

```bash
vol.py -f VOLCADO --profile=PERFIL psscan
```

- **psscan**: Lista procesos terminados o ocultos por malware.

### Extraer un Proceso de la Memoria

```bash
vol.py -f VOLCADO --profile=PERFIL procdump -p <PID> -D output/
```

- **procdump**: Guarda el binario ejecutable del proceso especificado con el PID.

### Listar Módulos Cargados en Memoria

```bash
vol.py -f VOLCADO --profile=PERFIL modules
```

- **modules**: Muestra los módulos (DLLs y drivers) cargados en la memoria.

### Listar Servicios del Sistema

```bash
vol.py -f VOLCADO --profile=PERFIL svcscan
```

- **svcscan**: Revela los servicios activos y ocultos en el sistema.

### Analizar el Historial de Comandos de la Consola

```bash
vol.py -f VOLCADO --profile=PERFIL cmdscan
```

- **cmdscan**: Muestra comandos ejecutados recientemente en la terminal de Windows.

### Extraer Archivos de la Memoria

```bash
vol.py -f VOLCADO --profile=PERFIL dumpfiles -D output/
```

- **dumpfiles**: Recupera archivos desde la memoria RAM y los guarda en la carpeta de salida especificada.

### Buscar Cadenas de Texto en la Memoria

```bash
vol.py -f VOLCADO --profile=PERFIL strings
```

- **strings**: Extrae cadenas de texto presentes en el volcado de memoria.

### Extraer el Registro de Windows

```bash
vol.py -f VOLCADO --profile=PERFIL hivelist
```

- **hivelist**: Muestra ubicaciones de los archivos de registro de Windows cargados en memoria.

### Listar Conexiones USB

```bash
vol.py -f VOLCADO --profile=PERFIL usbdevs
```

- **usbdevs**: Muestra dispositivos USB conectados al sistema.

