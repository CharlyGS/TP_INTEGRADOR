# Trabajo Práctico Integrador - Computación Aplicada -  Universidad de Palermo

# Unico Integrante:
- Carlos Gallardo
---

# Descripción del Proyecto

Trabajo Práctico Integrador de la materia Computación Aplicada - UP .

El presente Proyecto se centra en la configuración y administración de un servidor GNU/Linux basado en **Debian 11 ("Bullseye")**, alojado en una máquina virtual.

La implementación abarca desde la configuración inicial del sistema y la red hasta el despliegue de servicios esenciales, la gestión del almacenamiento, la automatización de tareas y la creación de un sistema robusto de copias de seguridad.

**Hostname del Servidor:** `TPServer`

---

# Arquitectura y Servicios Configurados

Se ha implementado una arquitectura de servidor estándar con los siguientes componentes y servicios:

* [cite_start]**Sistema Operativo:** Debian 11 (Bullseye)[cite: 17, 491].
* [cite_start]**Servicio de Acceso Remoto:** `OpenSSH Server` configurado para autenticación segura mediante par de claves (pública/privada), deshabilitando el login por contraseña para `root`[cite: 501, 532].
* [cite_start]**Servidor Web:** `Apache2` con soporte para `PHP 7.4`, sirviendo un sitio de monitoreo desde una partición dedicada[cite: 503, 537].
* [cite_start]**Base de Datos:** `MariaDB Server`, con una base de datos de ejemplo cargada[cite: 505].
* [cite_start]**Programador de Tareas:** `Cron` para la ejecución automatizada de scripts de backup[cite: 378, 524].
* [cite_start]**Red:** Configuración de red con **IP estática** para garantizar la conectividad constante desde la red física[cite: 507].
* [cite_start]**Almacenamiento:** Gestión de un disco adicional con particiones dedicadas para el sitio web (`/www_dir`) y los backups (`/backup_dir`), montadas automáticamente al inicio[cite: 510, 511, 513, 514].

---

# Repositorio y Entregables

[cite_start]Este repositorio contiene los siguientes archivos comprimidos, que representan las configuraciones y datos clave del servidor `TPServer`[cite: 525, 526]:

* [cite_start]`root.tar.gz`: Directorio `/root`, incluyendo el historial de comandos, scripts de configuración y la clave pública SSH autorizada[cite: 525].
* [cite_start]`etc.tar.gz`: Directorio `/etc`, con todos los archivos de configuración de los servicios (SSH, Apache, Red, fstab, etc.)[cite: 525].
* [cite_start]`opt.tar.gz`: Directorio `/opt`, donde se aloja el script de backup principal[cite: 525].
* [cite_start]`proc.tar.gz`: Contiene el archivo `particion`, una copia persistente de la información de las particiones del sistema[cite: 515, 525].
* [cite_start]`www_dir.tar.gz`: Directorio `/www_dir`, con el código fuente del sitio web (`index.php` y `logo.png`)[cite: 525].
* [cite_start]`backup_dir.tar.gz`: Directorio `/backup_dir`, que almacena las copias de seguridad generadas[cite: 525].
* [cite_start]`var_splitted/`: Carpeta que contiene el directorio `/var` dividido en partes (`var_part_aa`, `var_part_ab`, etc.) para facilitar su subida a repositorios con límites de tamaño de archivo[cite: 526].

---
# Diagrama Topologico de la Infraestructura

+---------------------------+
|      Máquina Física       |
|   (PC de Carlos)          |
|  IP: 192.168.0.X (Host)   |
+-------------+-------------+
              |
              | (Adaptador Puente)
              |
+-------------+-------------+      +---------------------+      +-----------------+
|      Máquina Virtual      |<---->|  Router/Gateway     |<---->|    Internet     |
|         (TPServer)        |      | IP: 192.168.0.1     |      +-----------------+
|---------------------------|      +---------------------+
|      - Debian 11          |
|      - IP: 192.168.0.10   |
|      - Mask: 255.255.255.0|
|      - GW: 192.168.0.1    |
|      - SSH, Apache, MariaDB|
+---------------------------+

```
