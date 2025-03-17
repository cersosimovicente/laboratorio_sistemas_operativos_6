# Laboratorio: Configuración de Acceso Remoto a un Servidor Ubuntu con SSH
## Objetivo
El objetivo de este laboratorio es configurar y asegurar el acceso remoto a un servidor Ubuntu mediante SSH, utilizando autenticación con clave pública y privada. Aprnderemos a transferir archivos entre tu máquina y el servidor utilizando PuTTY y SCP.

## Requisitos previos
- Un servidor Ubuntu (puede ser una máquina virtual o un servidor en la nube).
- Cliente Windows con PuTTY y WinSCP instalados.
- Conexión de red entre el cliente y el servidor.
- Acceso como usuario con privilegios de superusuario `(sudo)`.

# Parte 1: Instalación y Configuración del Servidor SSH
1. Acceder al servidor Ubuntu
2. Inicia sesión en el servidor Ubuntu con un usuario con privilegios sudo.
3. Instalar OpenSSH Server (si no está instalado)

```bash
sudo apt update
sudo apt install -y openssh-server
```
3. Verificar el estado del servicio SSH
```bash
sudo systemctl status ssh
```
Si el servicio no está activo, iniciar y habilitar 
```bash
sudo systemctl enable --now ssh
```

# Parte 2: Crear un Usuario para el Acceso Remoto
