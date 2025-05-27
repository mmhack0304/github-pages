Fases de una auditoria Hacking
  1.Reconocimiento / Recoleccion de informacion 
  2.Enumeraacion / Escanep
  3.Explotacion
  4.Post-Explotacion / Escalacion de privilegios 
  5.Informe



PRIMERA FASE 
Reconocimiento y Recoleccion de informacion
Consiste en recoger todo tipo de informacion sobre el objetivo (IPs, DNS, Dominios, Nombres, etc..)

Algunas de las paginas web mas utilizadas son :
-Censys
-DNSDumpster
-DNslookup
-Maltego
-Records


SEGUNDA FASE
Enumeracion / Escaneo
Consiste en una vez obtenido direcciones IP, Dominios, etc.. Realizar un escaneo para descubrir puertos abiertos, Servicios operativos, Sistemas operativos, Versiones , para posteriormente buscar vulnerabilidades y ejecutarlas.

Algunas de las herramientas mas usadas son :
-Ping
-Smbclient
-Nbtscan
-Nmap
-ARPscan

NMAP
Guia basica de nmap:

Seleccion de Objetivos:
nmap 192.168.1.1 (-20)    *escanea la ip o un rango y los 1000 puertos mas comunes
nmap http://google.com    *escanea un host

Seleccion de Puertos:
nmap -p 80           *escanea el puerto 80 en especifico
nmap --top-ports n   *escanea los puertos mas comunes

Tipos de escaneos:
nmap -sT   *escaneo TCP
nmap -sU   *escaneo UDP
nmap -sn   *escaneo PING
nmap -Pn   *escaneo de solo puertos

Deteccion de Sistemas Operativos y Servicios:
nmap -A    *detecta Sistemas operativos y versiones
nmap -sV   *detecta servicios y versiones

Nmap Scripting Engine:
nmap -sC   *lanza un escaneo con una lista de scripts que contiene el propio nmap

Timing templates:
nmap -T0   *modo paranoico
nmap -T1   *modo furtivo
nmap -T2   *modo educado
nmap -T3   *modo normal
nmap -T4   *modo agresivo
nmap -T5   *modo insane, solo recomendado en entornos controlados

Extras:
nmap -n   *ignora la resolucion DNS
nmap -v   *modo verbose, lista la salida a medida que va ejecutando el scan

Tecnicas de Evasion de Firewalls con Nmap:
nmap -vv -sV --mtu 8 (o multiplo de 8)       *ajusta el tamaño de los paquetes enviados para evitar que el firewall los detecte.
nmap -vv -sV --source-port 443               *permite especificar manualmente el puerto de origen haciendose pasar por un puerto en especifico, en  este caso por un servidor web HTTPS por el puerto 443
nmap -vv -sV -D 8.8.8.8,20.20.20.20          *permite al usuario enviar paquetes falsos a la red desde IPs falsas para confundir al firewall
nmap -vv -sV -f                              *sirve para fragmentar los paquetes yy que el firewall no lo detecte como un escaneo
nmap -vv -sV --spoof-mac 81:49:fd:6a:54:09   *sirve para falsificar la direccion MAC del origen del escaneo
nmap -sS                                     *permite realizar un escaneo SYN sin establecer una conexion completa lo que hace que el firewall no detecte el escaneo
nmap -vv -sV --max-rate 200                  *sirve para controlar la velocidad de los paquetes, muy parecido al -T(0-5).
