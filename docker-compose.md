
# 🐳 **Docker Compose - Gestión de entornos multi-contenedor**

## 🔧 **¿Qué es Docker Compose?**

Docker Compose es una herramienta que permite:

- Definir múltiples contenedores en un solo archivo (`docker-compose.yml`).
    
- Ejecutarlos, detenerlos y gestionarlos juntos con **un solo comando**.
    

---

## 🎯 **¿Por qué usar Docker Compose?**

|Problema|Solución con Docker Compose|
|---|---|
|Levantar varios contenedores a mano es tedioso|`docker-compose up` lo hace todo|
|Quieres redes y volúmenes preconfigurados|Compose los crea automáticamente|
|Necesitas un flujo reproducible y versionado|El `docker-compose.yml` es infraestructura como código|

---

## 📦 **Elementos clave de un archivo `docker-compose.yml`**

|Clave|Descripción|
|---|---|
|**services**|Define los contenedores que necesitas levantar|
|**image** o **build**|Imagen existente o construir desde Dockerfile|
|**volumes**|Sincronización entre archivos locales y contenedor|
|**networks**|Comunicación entre servicios|
|**environment**|Variables de entorno|
|**ports**|Puertos a exponer|

---

## 🗂️ **Ejemplo simple de stack**

```yaml
version: '3.8'

services:
  web:
    image: nginx
    ports:
      - "80:80"

  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: 1234
```

---

## 🔗 **Comunicación entre servicios**

- Docker Compose crea una **red interna por defecto**.
    
- Los contenedores se comunican por **nombre de servicio**.
    
- Ejemplo: `web` puede hablar con `db` usando `db:5432`.
    

---

## 🚀 **Comandos básicos**

|Comando|¿Qué hace?|
|---|---|
|`docker-compose up -d`|Levanta los servicios|
|`docker-compose down`|Detiene y elimina servicios y red|
|`docker-compose ps`|Lista los contenedores corriendo|
|`docker-compose logs`|Muestra logs combinados|
|`docker-compose exec`|Ejecuta comandos dentro de un contenedor|

---

## ✅ **Ventajas principales**

- Facilidad para levantar entornos completos (frontend + backend + DB).
    
- Aislamiento de proyectos (cada stack tiene su propia red).
    
- Simplificación del despliegue local o en servidores.
    
- Menos errores por configuración manual.
    

---
