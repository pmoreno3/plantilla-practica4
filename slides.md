# vsftpd
Servidor FTP

---

## 1. ¿Qué és vsftpd?
vsftpd (Very Secure FTP Daemon) es un servidor FTP ligero, rápido y centrado en la seguridad. Permite transferir archivos entre clientes y servidores usando los protocolos FTP, FTPS (FTP sobre TLS) y, opcionalmente, modos pasivo/activo.

---
## 2. Instalación
En entornos Linux de tipo Debian/Ubuntu
```sudo apt update
sudo apt install vsftpd
```
---
## 3. Operaciones sobre el servidor
| Comandos                     | Descripción                |
| ---------------------------- | :------------------------: |
| sudo service vsftpd start    | Encendido                  |
| sudo service vsftpd stop     | Apagado                    |
| sudo service vsftpd restart  | Reinicio        |
| sudo service vsftpd reload   | Reinicio        |
| sudo service vsftpd status   | Comprobación del estado    |

---
## 4. Ficheros de configuración
| Ficheros              | Descripción                        |
| --------------------- | :--------------------------------: |
| /etc/vsftpd.conf      | Archivo principal de configuración |
| /etc/ssl/certs/       | Certificados para FTPS (si se usa) |
| /var/ftp/             | Carpeta FTP anónima por defecto    |
| /home/usuario/        | Directorios de usuarios locales    |

### Importante
Cuaquier cambio en un fichero de configuración nos obliga a reiniciar el servidor para que se apliquen los cambios.

---
## 5. Fichero vsftpd.conf
```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022

# Modo pasivo (necesario si hay firewall)
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000

# Seguridad
chroot_local_user=YES
allow_writeable_chroot=YES
```
---
## 6. Usuario FTP
Comando para crear un usuario normal:
`sudo adduser nombre_usuario`
Restricción de acceso a carpetas (usuario enjaulado), añadiendo esta directiva en el fichero vsftpd.conf:
`chroot_local_user=YES`
