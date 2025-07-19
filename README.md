# -Laboratorios-del-Modulo-VII
Practica 2: Creacion de fileserver compatible con Windows utilizando SAMBA 
cat << EOF > comandos_samba.txt
# COMANDOS SAMBA - PRÁCTICA 2
# Archivo generado el $(date)

## INSTALACIÓN Y CONFIGURACIÓN INICIAL
1. sudo yum install samba samba-client -y
   # Instala paquetes Samba (servidor y cliente)

2. sudo systemctl enable smb nmb
   # Habilita servicios Samba para iniciar automáticamente

3. sudo systemctl start smb nmb
   # Inicia servicios Samba inmediatamente

## CONFIGURACIÓN DE CARPETA COMPARTIDA
4. sudo mkdir -p /samba/compartida
   # Crea directorio compartido (-p crea subdirectorios necesarios)

5. sudo groupadd sambausers
   # Crea grupo para usuarios Samba

6. sudo useradd -G sambausers adrian
   # Crea usuario y lo añade al grupo sambausers

7. sudo smbpasswd -a adrian
   # Añade usuario a Samba y establece contraseña

## PERMISOS Y PROPIEDAD
8. sudo chown -R adrian:sambausers /samba/compartida
   # Cambia dueño y grupo del directorio (-R recursivo)

9. sudo chmod -R 2770 /samba/compartida
   # Establece permisos (2=SGID, 7=rwx para dueño/grupo)

## CONFIGURACIÓN SAMBA
10. sudo nano /etc/samba/smb.conf
    # Edita configuración principal de Samba

11. sudo testparm
    # Verifica sintaxis del archivo smb.conf

## CREACIÓN DE ARCHIVOS
12. for i in {1..100}; do sudo touch /samba/compartida/adrian\${i}; done
    # Crea 100 archivos (adrian1 a adrian100)

## MONITOREO Y SOLUCIÓN DE PROBLEMAS
13. sudo tail -f /var/log/samba/log.smbd
    # Muestra logs de Samba en tiempo real

14. smbclient -L localhost -U adrian
    # Lista recursos compartidos disponibles

15. sudo systemctl restart smb nmb
    # Reinicia servicios Samba para aplicar cambios

## WINDOWS
# Comando para mapear unidad: \\IP\compartida
EOF
