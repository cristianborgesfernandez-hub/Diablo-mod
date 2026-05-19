---

## 📥 Instalación (Termux / Linux)

### Opción 1: Instalación Rápida
<a href="https://www.mediafire.com/file/wkinzgpb0tdx5qh/com.termux_1022.apk/file">
  <img src="https://qu.ax/finc.jpg" height="80px" style="border-radius: 10px;">
</a>

Puedes descargar la última versión de Termux dando clic en la imagen superior. Una vez dentro de Termux, sigue los comandos a continuación:

<details>
<summary><b>🛠️ Ver Comandos de Instalación Manual</b></summary>

```bash
# 1. Dar permisos de almacenamiento
termux-setup-storage

# 2. Actualizar e instalar dependencias principales
apt update && apt upgrade -y
pkg install -y git nodejs ffmpeg imagemagick

# 3. Clonar el repositorio
git clone https://github.com/melodiabl/OguriCap-Bot.git
cd OguriCap-Bot

# 4. Instalar dependencias del bot
npm install

# 5. Iniciar el bot
npm start
```
*Si durante la actualización aparece `(Y/I/N/O/D/Z) [default=N] ?`, escribe la letra `y` y presiona ENTER.*
</details>

---

## ⚡ Mantenimiento y Ejecución Continua (PM2)

Para mantener el bot activo 24/7 incluso si cierras Termux, recomendamos usar **PM2**.

<details>
<summary><b>⚙️ Ver Comandos de PM2</b></summary>

```bash
# Iniciar con PM2 (dentro de la carpeta OguriCap-Bot)
termux-wake-lock && npm i -g pm2 && pm2 start index.js && pm2 save && pm2 logs 
```

**Comandos Útiles de PM2:**
* `pm2 logs` : Ver el registro en tiempo real.
* `pm2 stop index` : Detener el bot.
* `pm2 start index` : Iniciar el bot nuevamente.
* `pm2 delete index` : Eliminar el proceso del historial.
</details>

### Solución de Problemas Frecuentes
* **Pantalla blanca o caída de internet:**
  ```bash
  cd && cd OguriCap-Bot && npm start
  ```
* **Obtener nuevo código QR:** Detén el bot (Ctrl + Z) y escribe:
  ```bash
  cd && cd OguriCap-Bot && rm -rf sessions/Principal && npm run qr
  ```
* **Obtener nuevo código por Teléfono (Code):**
  ```bash
  cd && cd OguriCap-Bot && rm -rf sessions/Principal && npm run code
  ```

---

## 🔄 Actualización Automática

<details>
<summary><b>📦 Comandos para actualizar</b></summary>

> ⚠️ **Atención:** Esto reemplazará todos los archivos base para traer las últimas novedades. Tu archivo `database.json` será respaldado de forma segura para no perder el progreso de tus usuarios.

```bash
grep -q 'bash\|wget' <(dpkg -l) || apt install -y bash wget && wget -O - https://raw.githubusercontent.com/melodiabl/OguriCap-Bot/master/termux.sh | bash 
```
*(Compatible con Termux, Replit y Linux)*

**Volverte Owner:**
Si necesitas añadir tu número como administrador principal manualmente:
```bash
cd && cd OguriCap-Bot && nano settings.js
```
