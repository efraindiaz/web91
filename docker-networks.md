
# 🌐 **Redes en Docker: Comunicación y Aislamiento de Servicios**

Docker no solo sirve para contenerizar aplicaciones, también permite controlar **cómo se comunican los contenedores entre sí** y con el exterior a través de redes virtuales.

---

## 🔧 **¿Por qué es importante entender las redes en Docker?**

- **Simulas entornos reales** con múltiples servicios conectados (frontend, backend, base de datos).
    
- **Aíslas servicios** para mejorar seguridad y evitar interferencias entre proyectos.
    
- **Simplificas la configuración** usando nombres en lugar de IPs.
    
- **Gestionas el tráfico** entre contenedores y hacia el mundo exterior.
    

---

## 🚢 **¿Qué pasa si no configuras una red?**

Si no defines una red personalizada, Docker conecta automáticamente los contenedores a la red **bridge por defecto**.  
Esto puede funcionar, pero es **limitado y no escalable** si tienes varios proyectos o múltiples servicios.

---

# 🗂️ **Tipos de Redes en Docker**

## 🛳️ **Bridge (Red por defecto)**

- Es la **red predeterminada** que Docker crea al instalarse.
    
- Los contenedores pueden comunicarse entre sí usando **IP internas**, pero no por nombre.
    
- Solo expone los servicios al exterior si usas `-p` o `ports:` en `docker-compose`.
    

---

## 🏗️ **Redes personalizadas

Cuando creas una red personalizada, Docker configura un **DNS interno** automáticamente.  
Esto permite que los contenedores se encuentren por nombre sin necesidad de conocer sus IPs.

### 🔧 **Crear una red personalizada**

```bash
docker network create mi_red
```

---

## ☁️ **Otros tipos de red**

| Tipo de red              | ¿Para qué se usa?                                  |
| ------------------------ | -------------------------------------------------- |
| **Bridge personalizada** | Proyectos locales y ambientes aislados             |
| **Host**                 | Comparte la red del sistema host (sin aislamiento) |
| **None**                 | Sin red (totalmente aislado)                       |

---

# 🧩 **Ventajas de usar redes personalizadas**

|Ventaja|Descripción|
|---|---|
|🔗 **Comunicación por nombre**|Los contenedores pueden hablar entre sí usando su nombre (DNS interno).|
|🧳 **Aislamiento de proyectos**|Cada proyecto puede tener su propia red sin interferir con otros.|
|🔒 **Mayor seguridad**|Solo los contenedores conectados a la red pueden comunicarse entre sí.|
|📦 **Facilidad de despliegue**|No necesitas configurar IPs manualmente.|

---

# 🔄 **¿Cómo se comunican los contenedores?**

Cuando los contenedores están en la **misma red personalizada**, pueden llamarse por nombre:

### 🧪 **Ejemplo en Node.js (MySQL)**

```js
const connection = mysql.createConnection({
  host: 'db', // nombre del contenedor de la base de datos
  user: 'root',
  password: 'password'
});
```
