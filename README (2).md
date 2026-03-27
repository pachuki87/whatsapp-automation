# 🤖 WhatsApp Automation Plugin para Agent Zero

## 📋 Descripción

Plugin de automatización completa de WhatsApp Web con sesiones persistentes en Chrome headless. Permite enviar mensajes, leer conversaciones y monitorear chats sin necesidad de escanear el código QR cada vez.

## ✨ Características Principales

### 🔄 **Sesión Persistente**
- ✅ Mantiene sesión activa tras reinicios del sistema
- ✅ Compatible con contenedores Docker
- ✅ Funciona sin interfaz gráfica (modo headless)
- ✅ Sobrevive a cierres de navegador

### 🤖 **Automatización Completa**
- 📤 Enviar mensajes automáticamente
- 📥 Leer y monitorear conversaciones
- 🔍 Buscar mensajes específicos
- 📊 Extraer datos de conversaciones
- 🎯 Crear bots personalizados

### 🛠 **Integración con Agent Zero**
- 🔗 Chrome DevTools MCP nativo
- 📝 Scripts bash automatizados
- 🎯 Fácil integración con workflows
- 📈 Monitoreo en tiempo real

## 🚀 Instalación

### **Requisitos Previos**

- ✅ Agent Zero v1.0.0 o superior
- ✅ Google Chrome o Chromium instalado
- ✅ Permisos de root o sudo
- ✅ Acceso al puerto 9222
- ✅ Mínimo 500MB de espacio en disco

### **Instalación Automática**

```bash
# 1. Clonar el repositorio
git clone https://github.com/agent0ai/whatsapp-automation.git
cd whatsapp-automation

# 2. Ejecutar script de instalación
chmod +x scripts/install.sh
./scripts/install.sh

# 3. Verificar instalación
./scripts/check_persistence.sh
```

### **Instalación Manual**

```bash
# 1. Crear directorio persistente
mkdir -p /a0/usr/workdir/chrome-profile/
chmod -R 755 /a0/usr/workdir/chrome-profile/

# 2. Verificar Chrome instalado
google-chrome --version

# 3. Iniciar Chrome con sesión persistente
./scripts/start_whatsapp_persistent.sh

# 4. Escanear código QR (solo primera vez)
```

## 📖 Uso

### **Iniciar WhatsApp Persistente**

```bash
# Usar el script de inicio
./scripts/start_whatsapp_persistent.sh

# O iniciar Chrome manualmente
google-chrome \
  --headless=new \
  --disable-gpu \
  --no-sandbox \
  --disable-dev-shm-usage \
  --remote-debugging-port=9222 \
  --user-data-dir=/a0/usr/workdir/chrome-profile/ \
  https://web.whatsapp.com &
```

### **Verificar Estado de la Sesión**

```bash
# Usar script de verificación
./scripts/check_persistence.sh

# Verificar manualmente
ls -lh /a0/usr/workdir/chrome-profile/Default/{Cookies,"Session Storage",IndexedDB}
```

### **Monitorear Chrome en Tiempo Real**

```bash
# Usar script de monitoreo
./scripts/monitor_chrome.sh
```

## 🤖 Integración con Agent Zero

### **Ejemplo 1: Tomar Snapshot de WhatsApp**

```json
{
  "thoughts": ["Necesito ver el estado actual de WhatsApp Web"],
  "tool_name": "chrome_devtools.take_snapshot",
  "tool_args": {}
}
```

### **Ejemplo 2: Capturar Código QR**

```json
{
  "thoughts": ["Necesito capturar el código QR para escanearlo"],
  "tool_name": "chrome_devtools.take_screenshot",
  "tool_args": {
    "filePath": "/a0/usr/workdir/whatsapp_qr.png"
  }
}
```

### **Ejemplo 3: Enviar Mensaje**

```json
{
  "thoughts": ["Voy a enviar un mensaje al chat activo"],
  "tool_name": "chrome_devtools.fill",
  "tool_args": {
    "uid": "message-input-uid",
    "value": "Hello from Agent Zero! 🤖"
  }
}
```

### **Ejemplo 4: Hacer Click en un Chat**

```json
{
  "thoughts": ["Voy a seleccionar un chat específico"],
  "tool_name": "chrome_devtools.click",
  "tool_args": {
    "uid": "chat-element-uid"
  }
}
```

### **Ejemplo 5: Navegar a WhatsApp Web**

```json
{
  "thoughts": ["Voy a navegar a WhatsApp Web"],
  "tool_name": "chrome_devtools.navigate_page",
  "tool_args": {
    "type": "url",
    "url": "https://web.whatsapp.com"
  }
}
```

## 🔧 Scripts Disponibles

### **start_whatsapp_persistent.sh**

Inicia Chrome con perfil persistente y carga WhatsApp Web.

```bash
./scripts/start_whatsapp_persistent.sh
```

**Parámetros configurables:**
- `PROFILE_DIR`: Directorio del perfil (default: `/a0/usr/workdir/chrome-profile/`)
- `DEBUG_PORT`: Puerto de DevTools (default: `9222`)
- `WHATSAPP_URL`: URL de WhatsApp Web (default: `https://web.whatsapp.com`)

### **check_persistence.sh**

Verifica que los archivos de persistencia estén creados y funcionando.

```bash
./scripts/check_persistence.sh
```

**Verifica:**
- ✅ Archivo Cookies existe y tiene datos
- ✅ Directorio Session Storage existe
- ✅ Directorio IndexedDB existe
- ✅ Directorio Local Storage existe

### **monitor_chrome.sh**

Monitorea el proceso de Chrome en tiempo real.

```bash
./scripts/monitor_chrome.sh
```

## 🐛 Troubleshooting

### **Problema: Chrome no se inicia**

**Soluciones:**
```bash
# 1. Verificar puerto 9222
netstat -tlnp | grep 9222

# 2. Matar procesos zombies
pkill -9 -f google-chrome

# 3. Verificar que Chrome esté instalado
google-chrome --version

# 4. Verificar permisos
ls -la /a0/usr/workdir/chrome-profile/
chmod -R 755 /a0/usr/workdir/chrome-profile/
```

### **Problema: Sesión se pierde tras reinicio**

**Soluciones:**
```bash
# 1. Verificar directorio persistente
ls -lh /a0/usr/workdir/chrome-profile/Default/Cookies

# 2. Verificar espacio en disco
df -h /a0/usr/workdir/

# 3. Recrear perfil corrupto
rm -rf /a0/usr/workdir/chrome-profile/
mkdir -p /a0/usr/workdir/chrome-profile/
./scripts/start_whatsapp_persistent.sh
```

### **Problema: Código QR aparece cada vez**

**Soluciones:**
```bash
# 1. Verificar permisos del directorio
chmod -R 755 /a0/usr/workdir/chrome-profile/

# 2. Verificar que Cookies exista y tenga datos
ls -lh /a0/usr/workdir/chrome-profile/Default/Cookies

# 3. Verificar IndexedDB
ls -la /a0/usr/workdir/chrome-profile/Default/IndexedDB/
```

### **Problema: WhatsApp Web no carga**

**Soluciones:**
```bash
# 1. Verificar conexión a internet
ping -c 4 web.whatsapp.com

# 2. Verificar firewall
iptables -L -n | grep 9222

# 3. Reiniciar Chrome
pkill -f google-chrome
./scripts/start_whatsapp_persistent.sh
```

## 📊 Arquitectura Técnica

### **Archivos de Persistencia Críticos**

| Archivo | Propósito | Importancia |
|----------|-----------|-------------|
| **Cookies** | Tokens de sesión | 🔴 CRÍTICO |
| **Session Storage/** | Estado de sesión web | 🔴 CRÍTICO |
| **IndexedDB/** | Base de datos local | 🔴 CRÍTICO |
| **Local Storage/** | Almacenamiento local | 🔴 CRÍTICO |
| **Sessions/** | Sesiones del navegador | 🟡 IMPORTANTE |
| **GCM Store/** | Notificaciones push | 🟢 OPCIONAL |

### **Estructura del Directorio**

```
chrome-profile/
├── Default/                    # Perfil principal de usuario
│   ├── Cookies                 # ✅ Tokens de sesión
│   ├── Cookies-journal         # Transacciones de cookies
│   ├── Session Storage/        # ✅ Estado de sesión web
│   ├── Local Storage/          # ✅ Almacenamiento local
│   ├── IndexedDB/              # ✅ Base de datos local
│   ├── Sessions/               # ✅ Sesiones del navegador
│   ├── Web Data                # Formularios y contraseñas
│   ├── History                 # Historial de navegación
│   └── Preferences             # Configuración de usuario
└── Local State                 # Estado global de Chrome
```

## 🔒 Consideraciones de Seguridad

### **Datos Sensibles Almacenados**

El directorio persistente contiene:
- 🔒 Cookies de autenticación
- 🔒 Tokens de sesión
- 🔒 Contraseñas guardadas
- 🔒 Historial de navegación
- 🔒 Datos de conversaciones de WhatsApp

### **Recomendaciones de Seguridad**

```bash
# 1. Permisos restrictivos
chmod 700 /a0/usr/workdir/chrome-profile/

# 2. Copias de seguridad regulares
cp -r /a0/usr/workdir/chrome-profile/ /backup/

# 3. No compartir el directorio
# Mantener el directorio privado

# 4. Limitar acciones del bot
# Implementar confirmaciones para acciones críticas
```

## 🚀 Casos de Uso Avanzados

### **Caso 1: Bot de Notificaciones 24/7**

```bash
# 1. Iniciar Chrome persistente
./scripts/start_whatsapp_persistent.sh

# 2. Crear script de automatización
# El bot puede acceder a WhatsApp 24/7 sin escanear QR
```

### **Caso 2: Automatización de Respuestas**

```python
# Python script para respuestas automáticas
import time
from mcp import chrome_devtools

chrome = chrome_devtools.ChromeDevTools(port=9222)

while True:
    # Verificar nuevos mensajes
    snapshot = chrome.take_snapshot()
    # Procesar nuevos mensajes
    # (lógica de automatización)
    time.sleep(60)
```

### **Caso 3: Monitoreo de Chats Específicos**

```python
# Monitorear chat específico
chrome = chrome_devtools.ChromeDevTools(port=9222)
chrome.navigate_page(url="https://web.whatsapp.com")
# Buscar chat específico
# (lógica de búsqueda)
# Monitorear actividad
# (lógica de monitoreo)
```

### **Caso 4: Extracción de Datos**

```python
# Extraer datos de conversaciones
chrome = chrome_devtools.ChromeDevTools(port=9222)
snapshot = chrome.take_snapshot()
# Procesar datos de conversaciones
# (lógica de extracción)
```

## 📚 Recursos Adicionales

### **Documentación Oficial**
- [Chrome DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/)
- [WhatsApp Web FAQ](https://faq.whatsapp.com/web)
- [Agent Zero Documentation](https://docs.agentzero.ai)

### **Scripts y Ejemplos**
- `/scripts/start_whatsapp_persistent.sh` - Iniciar Chrome persistente
- `/scripts/check_persistence.sh` - Verificar persistencia
- `/scripts/monitor_chrome.sh` - Monitorear Chrome

### **Repositorio**
- [GitHub Repository](https://github.com/agent0ai/whatsapp-automation)
- [Issues](https://github.com/agent0ai/whatsapp-automation/issues)
- [Pull Requests](https://github.com/agent0ai/whatsapp-automation/pulls)

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas!

1. Fork del repositorio
2. Crear rama de característica (`git checkout -b feature/AmazingFeature`)
3. Commit de cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir Pull Request

## 📝 Licencia

Este plugin es parte de Agent Zero y está disponible bajo licencia MIT.

## 📞 Soporte

Si tienes problemas o preguntas:

1. Revisa la sección de troubleshooting
2. Consulta los issues en GitHub
3. Abre un nuevo issue si es necesario

## 🔖 Versión

**Versión actual:** 1.0.0  
**Última actualización:** 2026-03-26  
**Autor:** Agent Zero Team

## 🎯 Próximos Pasos

1. ✅ Instalar el plugin
2. ✅ Configurar Chrome persistente
3. ✅ Escanear código QR (primera vez)
4. ✅ Probar automatización básica
5. ✅ Implementar casos de uso avanzados

---

**¡Disfruta de la automatización de WhatsApp con Agent Zero! 🚀**
