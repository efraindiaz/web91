## 🔧 Actualización del sistema

```bash
sudo apt update && sudo apt upgrade
```

---

## 📦 Instalar NVM (Node Version Manager)

> NVM nos permite instalar y gestionar múltiples versiones de Node.js

📄 Referencia: [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

🔁 Recargar bash para que nvm funcione:

```bash
source ~/.bashrc
```

---

## 🟢 Instalar Node.js (LTS)

```bash
nvm install node --lts
```

---

## 📁 Crear directorio para tus proyectos

```bash
mkdir projects
cd projects
```

---

## 🔁 Instalar PM2 (Process Manager)

> PM2 permite ejecutar apps en segundo plano y las reinicia automáticamente si fallan.

```bash
npm install -g pm2
```

### ▶️ Ejecutar tu API

```bash
# Opción 1
pm2 start src/index.js --name "my-api"

# Opción 2
pm2 start index.js --name "my-api"
```

🧠 Recomendación: Cambia `"my-api"` por un nombre descriptivo del proyecto.

---

## 🔄 Mantener procesos activos tras reinicio del VPS

```bash
pm2 startup
pm2 save
```

---

## 🔐 Configurar Firewall (UFW)

```bash
sudo ufw allow http
sudo ufw allow https
sudo ufw reload
```

✅ Verifica estado:

```bash
sudo ufw status
```

---

## 🌐 Instalar y configurar NGINX como Proxy

```bash
sudo apt install nginx
```

### 📁 Configuración del sitio

```bash
cd /etc/nginx/sites-available/
sudo nano mywebsite.com
```

Contenido del archivo (ajusta `server_name` y `localhost:3000`):

```nginx
server {
    listen 80;
    server_name mywebsite.com www.mywebsite.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

🔗 Crear enlace simbólico:

```bash
sudo ln -s /etc/nginx/sites-available/mywebsite.com /etc/nginx/sites-enabled/
```

🧪 Verificar y reiniciar NGINX:

```bash
sudo nginx -t
sudo service nginx restart
sudo service nginx status
```

---

## 🔐 Activar HTTPS con Certbot (Let's Encrypt)

📄 Guía DigitalOcean: [Cómo asegurar NGINX con Let's Encrypt](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04-es)

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```

✅ Sigue las instrucciones para seleccionar el dominio y configurar HTTPS automáticamente.

---

## ✅ Verificación final

- Revisa tu dominio en el navegador.
    
- Usa `pm2 list` para verificar que tu app esté corriendo.
    
- Usa `systemctl status nginx` para validar NGINX.
    

---

## 🧠 Consejos finales

- Usa dominios reales (puedes comprar uno o usar `.dev`, `.app`, `.site`, etc.).
    
- Si usas IP pública, puedes probar antes de tener el dominio (solo sin HTTPS).
    
- Puedes usar un `.env` para variables de entorno (con `dotenv`).
