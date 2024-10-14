# Guía para Configurar un Servidor DNS con BIND9

## 1. Instalar BIND9

```bash
sudo apt update
sudo apt install bind9
```

## 2. Configurar IP fija y reiniciar la red

```bash
sudo nano /etc/network/interfaces
sudo systemctl restart networking
```

## 3. Configurar IP fija y reiniciar la red

```bash
sudo nano /etc/bind/named.config.options
sudo systemctl restart bind9
```

## 4. Configurar la zona directa e inversa

```bash
sudo nano /etc/bind/named.conf.local
```

## 5. Crear archivos de zona

```bash
sudo nano /etc/bind/zones/db.mi-dominio.com
sudo nano /etc/bind/zones/db.192.168.1
sudo systemctl restart bind9
```

## 6. Comprobamos que el servidor DNS funciona y vemos que el archivo /etc/resolv.conf está correctamente configurado.

```bash
dig @192.168.1.10 -x 192.168.1.10
sudo nano /etc/resolv.conf
```

## 7. Verificar que la configuración es correcta

```bash
sudo named-checkconf
sudo named-checkzone ejemplo.com /etc/bind/db.ejemplo.com
sudo named-checkzone 1.168.192.in-addr.arpa /etc/bind/db.192
```

## 7. Comprobar el funcionamiento

```bash
nslookup www.ejemplo.com 192.168.1.10
nslookup 192.168.1.10 192.168.1.10
```
