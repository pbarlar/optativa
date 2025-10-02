# 📘 Manual de Configuración de GitHub por SSH
Pablo Barranco Lara
## Introducción
En este manual aprenderás a configurar la conexión entre tu entorno de desarrollo y GitHub mediante **SSH**.  
Este método permite autenticarte de manera segura sin necesidad de introducir tu usuario y contraseña cada vez que trabajes con un repositorio.  

---

## 🔧 Pasos básicos para configurar SSH en GitHub

### 1️⃣ Verificar si ya tienes claves SSH
Abre la terminal y ejecuta:
```bash
ls -al ~/.ssh
```
Si aparecen archivos como `id_rsa.pub` o `id_ed25519.pub`, ya tienes claves creadas.

---

### 2️⃣ Generar una nueva clave SSH
Ejecuta el siguiente comando (sustituye el correo por el de tu cuenta de GitHub):
```bash
ssh-keygen -t ed25519 -C "tu_correo@example.com"
```
Si tu sistema no soporta ed25519, usa:
```bash
ssh-keygen -t rsa -b 4096 -C "tu_correo@example.com"
```

---

### 3️⃣ Iniciar el agente SSH y añadir la clave
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

### 4️⃣ Copiar tu clave pública
```bash
cat ~/.ssh/id_ed25519.pub
```
Copia todo el texto generado.

---

### 5️⃣ Añadir la clave en GitHub
1. Ve a **GitHub → Settings → SSH and GPG keys**
2. Haz clic en **New SSH key**
3. Pon un nombre descriptivo
4. Pega la clave pública copiada
5. Guarda los cambios

---

### 6️⃣ Probar la conexión
```bash
ssh -T git@github.com
```
Deberías ver un mensaje de confirmación como:
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

✅ ¡Listo! Ya puedes usar GitHub con conexión segura por SSH.
