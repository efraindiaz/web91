
# Stack con Docker Compose

## Objetivo

Implementar un entorno de desarrollo y pruebas usando `Docker Compose` que permita gestionar varios servicios relacionados en una aplicación web fullstack.

## Servicios requeridos

Tu stack debe incluir al menos los siguientes contenedores:

* `api`: Backend de la aplicación.
* `landing`: Sitio web informativo o formulario de contacto.
* `dashboard` (opcional si aplica): Interfaz para gestión de leads o CRM.
* `bd`: Base de datos (elige **una** de las siguientes):

  * MySQL
  * PostgreSQL
  * MongoDB
  * SQL Server

---

## Estructura sugerida del proyecto

```plaintext
/mi-stack/
├── api/
│   ├── index.js
│   ├── package.json
│   └── Dockerfile
├── landing/
│   └── (React o HTML estático con Dockerfile)
├── dashboard/
│   └── (React u otra tecnología frontend)
├── docker-compose.yml
├── .env
└── README.md
```

---

## Requisitos técnicos

* Crea un `Dockerfile` funcional para cada servicio que lo requiera (mínimo para `api` y `landing`).
* Usa variables de entorno desde un archivo `.env`.
* Define una **red personalizada** en el `docker-compose.yml` para que los servicios se comuniquen entre sí.
* Asegúrate de que el `api` se conecte correctamente a la base de datos seleccionada.
* Expón los puertos necesarios para probar los servicios desde el navegador (por ejemplo: 3000 para la landing, 4000 para la API, 5432 para PostgreSQL).

---

## Instrucciones

1. **Elige la base de datos** con la que trabajará tu aplicación.
2. **Define los Dockerfile** para `api`, `landing` y `dashboard` (si aplica).
3. **Configura el archivo `docker-compose.yml`** incluyendo:

   * Imagen de base de datos con sus variables de entorno (`POSTGRES_USER`, etc.).
   * Montaje de volúmenes si se requiere persistencia.
   * Red compartida (`networks`).
   * Dependencias (`depends_on`).
4. **Crea un archivo `.env`** con las variables sensibles.
5. **Prueba localmente el stack** con `docker-compose up`.
6. **Verifica la conexión entre servicios**, especialmente `api` ↔ `bd`.

---

## Entregable (en PDF)

Tu entrega debe incluir lo siguiente en un **documento PDF**:

* Capturas de pantalla del stack funcionando (landing, API, dashboard, base de datos).
* Fragmento del `docker-compose.yml` configurado.
* Diagrama de arquitectura del stack.
* Explicación breve del rol de cada servicio y cómo se conectan.
* Lista de puertos expuestos y cómo se prueban.

---

