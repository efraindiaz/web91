# 🚢 **Dockerfiles y Creación de Imágenes**

---

## ✅ **¿Qué es un Dockerfile?**

Un **Dockerfile** es un archivo de texto que contiene **las instrucciones para construir una imagen Docker**.

Es como un **recetario** donde describes:

- Qué sistema base usar.
    
- Qué archivos copiar.
    
- Qué dependencias instalar.
    
- Qué comando ejecutar al iniciar el contenedor.
    
---

## 🧱 **Sintaxis básica de un Dockerfile**

### 🗂️ **Principales instrucciones:**

|Instrucción|¿Qué hace?|
|---|---|
|`FROM`|Define la **imagen base** (por ejemplo: `node:20`, `python:3.12`, `mcr.microsoft.com/dotnet/aspnet:8.0`)|
|`COPY`|Copia archivos locales al contenedor|
|`RUN`|Ejecuta comandos al construir la imagen (ej: instalar paquetes)|
|`CMD`|Define el **comando principal** al iniciar el contenedor|
|`EXPOSE`|Indica qué puerto usa la app (no abre el puerto, solo documenta)|

---

### 🔧 **Ejemplo básico: Dockerfile para Node.js**

```dockerfile
# Imagen base
FROM node:20

# Carpeta de trabajo en el contenedor
WORKDIR /app

# Copiamos archivos
COPY package*.json ./

# Instalamos dependencias
RUN npm install

# Copiamos el resto de la app
COPY . .

# Exponemos el puerto 3000
EXPOSE 3000

# Comando por defecto
CMD ["node", "index.js"]
```

---

## 🏗️ **Comandos relacionados**

### 🚀 **Construir una imagen**

```bash
docker build -t mi-app:latest .
```

|Opción|Descripción|
|---|---|
|`-t`|Etiqueta la imagen (nombre:tag)|
|`.`|Indica que el `Dockerfile` está en el directorio actual|

---

### 🏷️ **Etiquetar una imagen**

```bash
docker tag mi-app:latest miusuario/mi-app:latest
```

Esto es necesario si quieres subir la imagen a Docker Hub o un registry.

---

## 🛡️ **Buenas prácticas al escribir un Dockerfile**

|Práctica|Descripción|
|---|---|
|**Usar imágenes oficiales**|Ej: `node:20`, `python:3.12`|
|**Minimizar capas**|Agrupa comandos en un solo `RUN` cuando sea posible|
|**Evitar copiar archivos innecesarios**|Usa `.dockerignore`|
|**No guardar secretos en el Dockerfile**|Usa variables de entorno en tiempo de ejecución|
|**Usar imágenes slim o alpine**|Para reducir el tamaño|

---
