## 🚀 **Mini CRM de Leads**

Un **CRM (Customer Relationship Management)** es un sistema que permite **gestionar las relaciones con los clientes** y leads de forma organizada, centralizada y eficiente.  
Un **lead**, por su parte, es una **persona interesada en nuestros servicios o productos**, que ha dejado su información de contacto a través de un formulario, llamada, mensaje o campaña.

En el contexto de este pequeño proyecto, cada vez que alguien llena el formulario de contacto de la landing page, **genera un lead**. Hasta ahora, ya contamos con una API que recibe y almacena esa información. El siguiente paso es construir un **Mini CRM** que permita visualizar, clasificar y gestionar esos leads de manera más profesional.

Esta extensión del proyecto **converge con varios aspectos** relacionados al desarrollo seguro, y permite además cubrir los siguientes puntos referentes a implementación de servicios web de forma aplicada:
- Realizar la implementación de web services propios: API que recibe, almacena y expone los leads para el CRM.
- Realizar la integración de API’s de terceros: Integración de servicios como Slack o Emailjs.
- Implementar mecanismos de autenticación remota a Web Services: Login con JWT para proteger el panel del CRM.

### 📌 Objetivo

Convertir la API que actualmente recibe formularios en el backend de un pequeño **CRM para gestionar los leads provenientes de nuestro formulario de contacto**, incorporando autenticación, vistas protegidas, y servicios externos (correo).

---

## 🧱 Estructura 

| Módulo                                       | Descripción                                                                                                                              |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| 🌐 **Landing pública**                       | **Ya creada**, formulario con aviso de privacidad                                                                                        |
| 📩 **API de recepción**                      | **Ya creada**, sanitiza y almacena leads en base de datos (considerar los cambios necesarios para adaptarla a los nuevos requerimientos) |
| 📊 **Dashboard (CRM)**                       | **Nuevo**: interfaz protegida con login para visualizar y clasificar los leads.                                                          |
| 🔐 **Autenticación remota**                  | **Nuevo**: implementación de login seguro (JWT) en el dashboard                                                                          |
| 🔗 **API externa (Mailing, Notificaciones)** | **Nuevo**: integración con un servicio como EmailJS o Slack para notificar un nuevo lead.                                                |

---

## 💻 Funcionalidades requeridas del mini CRM

- 🧑‍💼 **Login seguro** (JWT)
    
- 📋 **Tabla de leads** con paginación
    
- 📝 Posibilidad de cambiar el estado del lead (**nuevo, contactado, descartado**)
    
- 📧 **Notificación** al administrador cada vez que entra un lead
    

---

## 🔗 Servicios externos recomendados (API de terceros)

Cada equipo deberá **integrar al menos un servicio externo** de tipo **mailing** o **notificaciones**.  
La elección es libre, siempre y cuando esté **justificada** y correctamente **integrada al flujo del sistema**.

| Categoría             | Ejemplos sugeridos                             | ¿Para qué se usaría?                              |
| --------------------- | ---------------------------------------------- | ------------------------------------------------- |
| ✉️ **Mailing**        | SendGrid, EmailJS, Mailgun, Brevo              | Enviar notificación por correo al recibir un lead |
| 🔔 **Notificaciones** | Slack Webhooks, Discord Webhooks, Telegram Bot | Avisar al equipo en tiempo real de un nuevo lead  |

---

🎯 **Indicaciones:**

- Solo se permite la integración de **uno** de los siguientes tipos:  
    → **Servicio de mailing** **o** **servicio de notificación**
    
- No es necesario implementar ambos
    
- La integración debe estar activa en producción y evidenciada en el entregable PDF
    

---

## 🎯 Entregables

La entrega final deberá realizarse en un **documento en formato PDF**, que contenga lo siguiente:

- ✅ **Aplicación funcional**
    
    - Proyecto completo compuesto por: **Landing Page + API + Dashboard (CRM)**
        
    - Todas las funcionalidades deben estar integradas y operativas
        
- 📸 **Capturas de pantalla**
    
    - Evidencia del funcionamiento de:
        
        - Envío del formulario
            
        - Visualización de leads
            
        - Notificación o integración con API externa
            
        - Panel o autenticación si aplica
            
- 📄 **README técnico (en el mismo PDF)**  
    Incluye:
    
    - Justificación de los servicios externos utilizados (ej. EmailJS, SendGrid, Slack.)
        
    - Diagrama de arquitectura del sistema (puede ser hecho en Draw.io, Figma, Lucidchart, etc.)
        
    - Descripción de las medidas de seguridad aplicadas:
        
        - Validación y sanitización
            
        - Protección de datos personales
            
        - HTTPS y certificados (si aplica)
            
- ☁️ **Proyecto desplegado y operativo**
    
    - El documento debe incluir los **enlaces públicos** al proyecto:
        
        - 🌐 **Landing page**
            
        - 🔗 **API (con documentación breve si está protegida)**
            
        - 🔐 **Dashboard CRM** (protegido por autenticación)
            
    - Puede estar alojado en servicios como: **Vercel**, **Railway**, **Render**, **Heroku**, **Netlify**, o un **VPS propio (DigitalOcean)**
