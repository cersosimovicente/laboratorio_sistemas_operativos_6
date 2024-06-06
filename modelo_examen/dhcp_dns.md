# DHCP (Dynamic Host Configuration Protocol)

### 1. ¿Cuál es la función principal del servidor DHCP?
 - a) Asignar nombres de dominio a las direcciones IP 
 - b) Asignar direcciones IP dinámicas y otros parámetros de configuración de red
 - c) Proveer seguridad en la red
 - d) Gestionar la resolución de nombres
### 2. ¿Qué protocolo utiliza DHCP para asignar direcciones IP a los dispositivos?
 - a) TCP
 - b) UDP
 - c) ICMP
 - d) ARP
### 3. ¿Cuál es el puerto utilizado por el servidor DHCP para enviar y recibir mensajes?
 - a) 67
 - b) 68
 - c) 53
 - d) 80
### 4. En el proceso de asignación de una dirección IP, ¿cuál es el orden correcto de los mensajes DHCP?
 - a) Discover, Offer, Request, Acknowledge
 - b) Discover, Request, Offer, Acknowledge
 - c) Offer, Discover, Request, Acknowledge
 - d) Request, Discover, Offer, Acknowledge
### 5. ¿Qué ocurre si un dispositivo no recibe una respuesta de un servidor DHCP?
 - a) Utiliza una dirección IP estática preconfigurada
 - b) Utiliza una dirección IP de un rango de direcciones APIPA (Automatic Private IP Addressing)
 - c) Utiliza la última dirección IP que recibió
 - d) Se desconecta de la red

# DNS (Domain Name System)
### 1. ¿Cuál es la función principal del sistema DNS?
 - a) Traducir direcciones IP a nombres de dominio
 - b) Traducir nombres de dominio a direcciones IP
 - c) Proveer conectividad entre dispositivos en la red
 - d) Asignar direcciones IP dinámicas a dispositivos
### 2. ¿Qué tipo de registro DNS se utiliza para asociar un nombre de dominio a una dirección IPv4?
 - a) MX
 - b) A
 - c) CNAME
 - d) AAAA
### 3. ¿Cuál es el nombre del protocolo utilizado por DNS para realizar consultas y respuestas?
 - a) TCP
 - b) UDP
 - c) HTTP
 - d) ICMP
### 4. ¿Qué tipo de registro DNS se utiliza para definir el servidor de correo electrónico para un dominio?
 - a) A
 - b) AAAA
 - c) MX
- d) PTR
### 5. En una consulta DNS recursiva, ¿quién es responsable de resolver completamente el nombre de dominio solicitado?
 - a) El servidor DNS raíz
 - b) El servidor DNS recursivo
 - c) El servidor autoritativo
 - d) El cliente DNS


## Ejercicio 1: DHCP 
Situación
Un administrador de red configuró un servidor DHCP, pero los dispositivos en la red no pueden obtener direcciones IP. Configuración del servidor DHCP:
```plaintext
# Configuración del Servidor DHCP
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.50;
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
    default-lease-time 600;
    max-lease-time 7200;
}
```
### Pregunta
Identifica los posibles errores en la configuración del servidor DHCP y propone las soluciones adecuadas.
## Ejercicio 2: DNS
Situación
Un administrador configuró el archivo de zona para un dominio, pero la resolución de nombres no está funcionando correctamente. Aquí está el archivo de zona:
```plaintext
$TTL 86400
@   IN  SOA ns1.example.com. admin.example.com. (
                2023060601 ; Serial
                3600       ; Refresh
                1800       ; Retry
                1209600    ; Expire
                86400 )    ; Minimum TTL

@       IN  NS  ns1.example.com.
@       IN  NS  ns2.example.com.
@       IN  A   192.168.1.1
www     IN  A   192.168.1.2
mail    IN  MX  10 mail.example.com.
ftp     IN  A   192.168.1.3
```
Pregunta
Identifica los errores en el archivo de zona y corrígilos.
### Ejercicio 3: DHCP
Situación
En una red, el administrador configuró el servidor DHCP y algunas máquinas con direcciones IP estáticas. Aquí está la configuración del servidor DHCP:
```text
# Configuración del Servidor DHCP
subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.100 10.0.0.200;
    option routers 10.0.0.1;
    option domain-name-servers 10.0.0.2, 10.0.0.3;
    default-lease-time 600;
    max-lease-time 7200;
}
```
Las configuraciones IP estáticas de algunas máquinas:

Máquina A: 10.0.0.101
Máquina B: 10.0.0.150
Máquina C: 10.0.0.199

Pregunta
Identifica los problemas en la configuración y propone una solución adecuada.

### Ejercicio 4: DNS
Situación
Un administrador configuró el archivo de zona DNS para el manejo de correo, pero los correos electrónicos no están llegando correctamente. Aquí está la configuración:
```textplain
$TTL 86400
@   IN  SOA ns1.example.com. admin.example.com. (
                2023060601 ; Serial
                3600       ; Refresh
                1800       ; Retry
                1209600    ; Expire
                86400 )    ; Minimum TTL

@       IN  NS  ns1.example.com.
@       IN  NS  ns2.example.com.
@       IN  A   192.168.1.1
www     IN  A   192.168.1.2
mail    IN  A   192.168.1.3
@       IN  MX  10 mail.example.com.
ftp     IN  A   192.168.1.3
```
Pregunta
Encontrá y corrigí los errores en la configuración del archivo de zona DNS.


