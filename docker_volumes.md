# 📦 Persistencia en Docker

Docker, por defecto, crea **contenedores efímeros**.  
Cuando eliminas un contenedor, **se pierde todo lo que estaba dentro**, incluyendo archivos generados durante su ejecución.

### ¿Por qué es un problema?

- Bases de datos sin persistencia
    
- Archivos o logs que desaparecen al reiniciar
    
- Estado de la aplicación perdido
    

---

## ¿Qué es la **persistencia en Docker**?

La **persistencia** permite guardar datos fuera del ciclo de vida del contenedor, en el sistema host o en volúmenes de Docker.

---

# Tipos de almacenamiento en Docker

## 1️⃣ **Bind Mounts**

- Montan un **directorio o archivo específico del sistema host** dentro del contenedor.
    
- Es el método más flexible, pero menos seguro y menos portable.
    

### Ejemplo:

```bash
docker run -v /ruta/local:/ruta/contenedor imagen
```

---

## 2️⃣ **Named Volumes**

- Son gestionados por Docker.
    
- No necesitas conocer rutas físicas en tu sistema.
    
- Docker se encarga de almacenar los datos en:
    

```bash
/var/lib/docker/volumes/
```

### Crear volumen:

```bash
docker volume create mi_volumen
```

### Usar volumen:

```bash
docker run -v mi_volumen:/ruta/contenedor imagen
```

---

## 3️⃣ **¿Cuál usar?**

|Caso|Tipo recomendado|
|---|---|
|Desarrollo local|Bind Mounts|
|Producción o persistencia segura|Named Volumes|

---

# Cómo montar archivos y carpetas del host

### Montar un archivo individual:

```bash
docker run -v $(pwd)/archivo.txt:/app/archivo.txt imagen
```

### Montar un directorio completo:

```bash
docker run -v $(pwd)/mi-carpeta:/app carpeta imagen
```

Esto permite hacer **hot reload** o compartir archivos entre host y contenedor.
