# Taller de RFID - Grupo 5

## Índice
1. [Introducción](#introducción)
2. [Objetivos del Taller](#objetivos-del-taller)
3. [Hardware Requerido](#hardware-requerido)
4. [Fundamentos de RFID](#fundamentos-de-rfid)
5. [Configuración del Entorno](#configuración-del-entorno)
6. [Módulo 1: Introducción a Proxmark](#módulo-1-introducción-a-proxmark)
7. [Módulo 2: Introducción a Flipper Zero](#módulo-2-introducción-a-flipper-zero)
8. [Ejercicios Prácticos](#ejercicios-prácticos)
9. [Consideraciones de Seguridad y Legales](#consideraciones-de-seguridad-y-legales)
10. [Recursos Adicionales](#recursos-adicionales)

---

## Introducción

Bienvenidos al **Taller de RFID (Radio Frequency Identification)** del Grupo 5. Este taller está diseñado para proporcionar una comprensión práctica y teórica de la tecnología RFID utilizando dos de las herramientas más populares en el campo de la seguridad: **Proxmark** y **Flipper Zero**.

### ¿Qué es RFID?

RFID es una tecnología de identificación automática que utiliza ondas de radio para transmitir datos entre un lector y una etiqueta (tag). Esta tecnología se utiliza ampliamente en:
- Control de acceso
- Tarjetas de transporte público
- Pagos sin contacto
- Gestión de inventarios
- Identificación de vehículos

---

## Objetivos del Taller

Al finalizar este taller, los participantes serán capaces de:

1. **Comprender** los fundamentos teóricos de la tecnología RFID
2. **Identificar** diferentes tipos de tarjetas y protocolos RFID
3. **Operar** el Proxmark para análisis avanzado de RFID
4. **Utilizar** el Flipper Zero para pruebas de seguridad RFID
5. **Analizar** la seguridad de sistemas RFID comunes
6. **Clonar** tarjetas RFID (con fines educativos y legales)
7. **Reconocer** vulnerabilidades en implementaciones RFID
8. **Aplicar** mejores prácticas de seguridad RFID

---

## Hardware Requerido

### Proxmark3

El **Proxmark3** es una herramienta avanzada de investigación RFID que permite:
- Leer y escribir tarjetas RFID de baja y alta frecuencia
- Analizar protocolos de comunicación
- Realizar ataques de sniffing
- Emular tarjetas RFID

**Modelos recomendados:**
- Proxmark3 RDV4
- Proxmark3 Easy
- Proxmark3 ICEMAN

### Flipper Zero

El **Flipper Zero** es un dispositivo multifuncional portátil que incluye:
- Lector/escritor RFID de 125kHz (LF)
- Lector/escritor NFC de 13.56MHz (HF)
- Interfaz intuitiva con pantalla
- Capacidades de emulación

**Características principales:**
- Portabilidad y facilidad de uso
- Firmware actualizable
- Comunidad activa de desarrollo
- Múltiples protocolos soportados

### Accesorios Adicionales

- Tarjetas RFID de práctica (T5577, MIFARE Classic, etc.)
- Cables USB para conexión
- Antenas adicionales (opcional)
- Llaveros RFID reutilizables

---

## Fundamentos de RFID

### Tipos de Sistemas RFID

#### 1. RFID de Baja Frecuencia (LF) - 125kHz
- **Alcance:** Corto (hasta 10 cm)
- **Aplicaciones:** Control de acceso, identificación animal
- **Protocolos comunes:**
  - EM4100/EM4102
  - HID Prox
  - Indala
  - T5577 (programable)

#### 2. RFID de Alta Frecuencia (HF) - 13.56MHz
- **Alcance:** Medio (hasta 1 metro)
- **Aplicaciones:** Pagos NFC, transporte público, pasaportes
- **Protocolos comunes:**
  - ISO 14443A/B (MIFARE)
  - ISO 15693
  - NFC (Near Field Communication)

#### 3. RFID de Ultra Alta Frecuencia (UHF) - 860-960MHz
- **Alcance:** Largo (hasta 12 metros)
- **Aplicaciones:** Logística, gestión de inventarios

### Componentes de un Sistema RFID

1. **Tag (Etiqueta):**
   - Pasivo: Sin batería, alimentado por el lector
   - Activo: Con batería propia
   - Semi-pasivo: Batería para funciones, energía del lector para transmisión

2. **Lector/Reader:**
   - Genera el campo electromagnético
   - Envía comandos a las etiquetas
   - Recibe y procesa respuestas

3. **Antena:**
   - Transmite y recibe señales de radiofrecuencia
   - Determina el alcance efectivo

### Protocolos de Seguridad

- **Sin autenticación:** EM4100, HID Prox básico
- **Con autenticación débil:** MIFARE Classic
- **Con criptografía fuerte:** MIFARE DESFire, MIFARE Plus

---

## Configuración del Entorno

### Instalación de Software para Proxmark

#### En Linux (Ubuntu/Debian)
```bash
# Instalar dependencias
sudo apt update
sudo apt install --no-install-recommends git ca-certificates build-essential pkg-config \
libreadline-dev gcc-arm-none-eabi libnewlib-dev qtbase5-dev \
libbz2-dev liblz4-dev libbluetooth-dev libpython3-dev libssl-dev

# Clonar repositorio
git clone https://github.com/RfidResearchGroup/proxmark3.git
cd proxmark3

# Compilar
make clean && make all

# Instalar
sudo make install
```

#### En Windows
1. Descargar ProxSpace desde el repositorio oficial
2. Seguir las instrucciones de instalación
3. Utilizar el cliente desde el entorno ProxSpace

#### En macOS
```bash
# Instalar Homebrew si no está instalado
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar dependencias
brew install readline qt5 pkgconfig coreutils

# Clonar y compilar (similar a Linux)
```

### Configuración de Flipper Zero

1. **Actualizar Firmware:**
   - Conectar Flipper Zero al ordenador
   - Visitar: https://update.flipperzero.one/
   - Seguir instrucciones de actualización

2. **Instalar qFlipper:**
   - Descargar desde: https://flipperzero.one/update
   - Instalar según el sistema operativo
   - Usar para gestión de archivos y actualizaciones

3. **Firmware alternativo (Opcional):**
   - Unleashed Firmware
   - RogueMaster Firmware

---

## Módulo 1: Introducción a Proxmark

### 1.1 Conexión y Prueba Inicial

```bash
# Conectar Proxmark vía USB
pm3

# Una vez dentro de la consola Proxmark
hw status
hw version
```

### 1.2 Comandos Básicos de LF (125kHz)

#### Búsqueda Automática
```bash
lf search
```

#### Lectura de Tarjetas Específicas

**EM4100:**
```bash
lf em 410x reader
```

**HID Prox:**
```bash
lf hid reader
```

**T5577:**
```bash
lf t55xx detect
lf t55xx info
```

#### Clonación de Tarjetas

**Clonar EM4100 a T5577:**
```bash
lf em 410x reader    # Leer tarjeta original
lf em 410x clone --id [ID]    # Clonar a tarjeta T5577
```

### 1.3 Comandos Básicos de HF (13.56MHz)

#### Búsqueda Automática
```bash
hf search
```

#### MIFARE Classic

**Lectura:**
```bash
hf mf autopwn    # Ataque automático
hf mf dump       # Volcar contenido
```

**Análisis de claves:**
```bash
hf mf nested     # Ataque nested
hf mf hardnested # Ataque hardnested
```

**Clonación:**
```bash
hf mf cload --1k -f hf-mf-[UID]-dump.bin
hf mf cview
```

#### MIFARE Ultralight

```bash
hf mfu info
hf mfu dump
hf mfu restore -f hf-mfu-[UID]-dump.bin
```

### 1.4 Sniffing de Comunicaciones

```bash
# Para LF
lf sniff

# Para HF
hf 14a sniff
hf 14a list
```

---

## Módulo 2: Introducción a Flipper Zero

### 2.1 Navegación por el Menú

**Estructura del menú principal:**
- **125 kHz RFID:** Tarjetas de baja frecuencia
- **NFC:** Tarjetas de 13.56 MHz
- **Sub-GHz:** Señales de radio (no RFID)
- **Infrared:** Control remoto IR
- **iButton:** Llaves de contacto
- **GPIO:** Pines de entrada/salida
- **Settings:** Configuración del dispositivo

### 2.2 Trabajar con RFID LF (125kHz)

#### Leer una Tarjeta
1. Navegar a: `125 kHz RFID` → `Read`
2. Acercar la tarjeta al lector (parte trasera del Flipper)
3. Esperar detección automática
4. Ver información de la tarjeta

#### Guardar una Tarjeta
1. Después de leer, presionar el botón central
2. Seleccionar `Save`
3. Nombrar el archivo
4. Confirmar guardado

#### Emular una Tarjeta
1. Navegar a: `125 kHz RFID` → `Saved`
2. Seleccionar la tarjeta guardada
3. Elegir `Emulate`
4. Acercar el Flipper al lector como si fuera la tarjeta original

#### Escribir en Tarjetas T5577
1. Navegar a: `125 kHz RFID` → `Saved`
2. Seleccionar la tarjeta
3. Elegir `Write`
4. Colocar tarjeta T5577 en el lector
5. Confirmar escritura

### 2.3 Trabajar con NFC (13.56MHz)

#### Leer una Tarjeta NFC
1. Navegar a: `NFC` → `Read`
2. Acercar la tarjeta
3. Ver tipo y contenido
4. Opciones disponibles según el tipo

#### MIFARE Classic
```
NFC → Read → [Detecta MIFARE Classic]
→ Opciones:
  - Info: Ver información básica
  - More: Opciones avanzadas
  - Save: Guardar dump parcial o completo
```

#### MIFARE Ultralight
```
NFC → Read → [Detecta MIFARE Ultralight]
→ Se muestra el contenido completo
→ Save: Guardar tarjeta
```

#### Emular NFC
1. Navegar a: `NFC` → `Saved`
2. Seleccionar tarjeta guardada
3. Elegir `Emulate`
4. Acercar a lector NFC

### 2.4 Diccionarios de Claves

**Actualizar diccionarios MIFARE:**
1. Conectar Flipper Zero al ordenador
2. Abrir qFlipper
3. Navegar a: `SD Card/nfc/assets/`
4. Actualizar archivo `mf_classic_dict.nfc` con más claves
5. Reiniciar Flipper Zero

**Formato de diccionarios:**
```
# Claves por defecto
FFFFFFFFFFFF
A0A1A2A3A4A5
B0B1B2B3B4B5
...
```

---

## Ejercicios Prácticos

### Ejercicio 1: Identificación de Tarjetas

**Objetivo:** Identificar diferentes tipos de tarjetas RFID

**Materiales:**
- Conjunto de tarjetas RFID variadas
- Proxmark o Flipper Zero

**Pasos:**
1. Tomar cada tarjeta sin identificar
2. Usar `lf search` o `hf search` en Proxmark
3. O usar las funciones de lectura en Flipper Zero
4. Documentar:
   - Tipo de tarjeta
   - Frecuencia (LF/HF)
   - Protocolo detectado
   - UID/ID
   - Capacidad de memoria (si aplica)

### Ejercicio 2: Clonación de Tarjeta EM4100

**Objetivo:** Clonar una tarjeta EM4100 a una T5577

**Con Proxmark:**
```bash
# Paso 1: Leer tarjeta original
lf em 410x reader

# Paso 2: Anotar el ID (ejemplo: 1234567890)
# Paso 3: Colocar tarjeta T5577 virgen
lf em 410x clone --id 1234567890

# Paso 4: Verificar
lf em 410x reader
```

**Con Flipper Zero:**
1. Leer tarjeta EM4100 original
2. Guardar con nombre descriptivo
3. Colocar T5577 virgen
4. Seleccionar tarjeta guardada → Write
5. Verificar lectura de tarjeta clonada

### Ejercicio 3: Análisis de MIFARE Classic

**Objetivo:** Extraer claves y datos de una tarjeta MIFARE Classic

**Con Proxmark:**
```bash
# Ataque automático
hf mf autopwn

# Si no funciona, probar nested attack
hf mf nested --1k

# Volcar contenido
hf mf dump

# Ver contenido en formato legible
hf mf view -f hf-mf-[UID]-dump.bin
```

**Análisis de resultados:**
- Identificar sectores y bloques
- Localizar claves A y B
- Identificar bloques de datos vs. bloques de control
- Buscar patrones en los datos

### Ejercicio 4: Sniffing de Comunicación

**Objetivo:** Capturar la comunicación entre un lector y una tarjeta

**Con Proxmark:**
```bash
# Iniciar captura HF
hf 14a sniff

# Realizar transacción con tarjeta real en lector real
# (Proxmark debe estar cerca del lector)

# Detener y analizar
hf 14a list

# Guardar captura
hf 14a list -s filename.trace
```

**Análisis:**
- Identificar comandos del lector
- Identificar respuestas de la tarjeta
- Buscar datos sensibles
- Identificar protocolo de autenticación

### Ejercicio 5: Emulación de Tarjetas

**Objetivo:** Usar el Flipper Zero para emular diferentes tarjetas

**Tarjetas a emular:**
1. Tarjeta de acceso LF
2. Tarjeta de transporte NFC
3. Llavero RFID

**Proceso:**
1. Leer cada tarjeta con Flipper Zero
2. Guardar con nombres descriptivos
3. Probar emulación en lectores reales
4. Documentar:
   - ¿Funciona la emulación?
   - ¿Hay limitaciones?
   - ¿El lector detecta diferencias?

### Ejercicio 6: Ataque de Diccionario MIFARE

**Objetivo:** Usar diccionarios de claves para atacar MIFARE Classic

**Preparación:**
1. Crear tarjeta MIFARE Classic con claves conocidas
2. Preparar diccionario con claves comunes

**Con Proxmark:**
```bash
# Ataque con diccionario personalizado
hf mf chk --1k -f my_dictionary.dic

# Ver resultados
hf mf fchk --dump
```

**Con Flipper Zero:**
1. Actualizar diccionario en SD
2. Intentar leer MIFARE Classic
3. Observar cuántas claves se encuentran

### Ejercicio 7: Creación de Badge Personalizado

**Objetivo:** Crear una tarjeta RFID personalizada con datos específicos

**Pasos:**
1. Tomar tarjeta T5577 virgen (LF) o MIFARE Classic virgen (HF)
2. Programar con ID personalizado
3. Para HF, escribir datos en sectores específicos
4. Verificar lectura correcta
5. Probar en lector si está disponible

**Con Proxmark (EM4100 personalizado):**
```bash
lf em 410x clone --id AAAAAAAAAA
lf em 410x reader
```

---

## Consideraciones de Seguridad y Legales

### Aspectos Legales

⚠️ **IMPORTANTE:** El uso de herramientas RFID debe cumplir con las leyes locales.

**Prohibido:**
- Clonar tarjetas sin autorización del propietario
- Acceder a sistemas sin permiso explícito
- Uso fraudulento de tarjetas clonadas
- Interferir con sistemas de seguridad

**Permitido:**
- Análisis de tus propias tarjetas
- Investigación en entornos controlados
- Pruebas de seguridad con autorización
- Educación y formación

### Mejores Prácticas de Seguridad

#### Para Usuarios
1. **Protección contra skimming:**
   - Usar carteras con blindaje RFID
   - Mantener tarjetas alejadas de lectores desconocidos
   - Monitorear transacciones regularmente

2. **Tarjetas de acceso:**
   - No prestar tarjetas personales
   - Reportar tarjetas perdidas inmediatamente
   - Usar tarjetas con criptografía fuerte cuando sea posible

#### Para Administradores de Sistemas
1. **Implementación segura:**
   - Usar tarjetas con autenticación fuerte (MIFARE DESFire, iClass SE)
   - Implementar autenticación de múltiples factores
   - Evitar protocolos legacy inseguros (EM4100, HID Prox básico)

2. **Mantenimiento:**
   - Actualizar firmware de lectores regularmente
   - Monitorear logs de acceso
   - Implementar detección de anomalías
   - Revocar acceso de tarjetas perdidas

3. **Seguridad en profundidad:**
   - No confiar solo en RFID
   - Combinar con PIN, biometría o vigilancia
   - Implementar zonas de seguridad escalonadas

### Vulnerabilidades Comunes

#### Tarjetas Antiguas (EM4100, HID Prox)
- **Sin cifrado:** ID transmitido en claro
- **Fácilmente clonables**
- **Solución:** Actualizar a tecnología más segura

#### MIFARE Classic
- **Criptografía débil (Crypto-1)**
- **Vulnerable a ataques nested/hardnested**
- **Solución:** Migrar a MIFARE Plus o DESFire

#### Implementaciones NFC
- **Posible relay attack**
- **Skimming de datos**
- **Solución:** Límites de transacción, tokenización

---

## Recursos Adicionales

### Documentación Oficial

#### Proxmark
- **Repositorio oficial:** https://github.com/RfidResearchGroup/proxmark3
- **Wiki:** https://github.com/RfidResearchGroup/proxmark3/wiki
- **Foro:** http://www.proxmark.org/forum/

#### Flipper Zero
- **Sitio oficial:** https://flipperzero.one/
- **Documentación:** https://docs.flipperzero.one/
- **GitHub:** https://github.com/flipperdevices/
- **Foro:** https://forum.flipperzero.one/

### Comunidades y Recursos

#### Comunidades Online
- **Reddit:**
  - r/proxmark
  - r/flipperzero
  - r/RFID
- **Discord:** Flipper Zero Official Discord
- **Telegram:** Grupos de RFID en español

#### Herramientas Complementarias

**Software:**
- **Proxmark Client:** Interfaz gráfica para Proxmark
- **qFlipper:** Gestor oficial de Flipper Zero
- **NFC Tools:** App móvil para análisis NFC
- **MIFARE Classic Tool:** App Android para MIFARE

**Hardware:**
- **ACR122U:** Lector NFC USB económico
- **Chameleon Mini/Tiny:** Emulador RFID portátil
- **HydraNFC:** Herramienta de investigación NFC

### Libros y Papers Recomendados

1. **"RFID Security"** - Simson Garfinkel & Beth Rosenberg
2. **"Dismantling MIFARE Classic"** - Nohl et al.
3. **"Wirelessly Pickpocketing a Mifare Classic Card"** - Verdult & Kooman
4. **"Practical Attacks on NFC Enabled Cell Phones"** - Roland & Langer

### Videos y Tutoriales

- **YouTube:** Buscar "Proxmark3 Tutorial"
- **YouTube:** Buscar "Flipper Zero RFID"
- **Defcon/BlackHat talks** sobre RFID
- **Canal de Lab401** (tienda especializada)

### Estándares y Especificaciones

- **ISO/IEC 14443:** Estándar para tarjetas de proximidad (HF)
- **ISO/IEC 15693:** Tarjetas de vecindad (HF)
- **ISO/IEC 18000:** Estándares para RFID UHF
- **NFC Forum:** Especificaciones NFC

### Proveedores de Hardware

- **Lab401:** https://lab401.com/
- **Hackerwarehouse:** https://hackerwarehouse.com/
- **Dangerous Things:** https://dangerousthings.com/
- **AliExpress/Amazon:** Para tarjetas de práctica económicas

---

## Apéndices

### Apéndice A: Tabla de Frecuencias RFID

| Frecuencia | Rango | Aplicaciones Típicas | Protocolos Comunes |
|------------|-------|----------------------|-------------------|
| 125 kHz (LF) | 10 cm | Control de acceso, ID animal | EM4100, HID Prox, T5577 |
| 13.56 MHz (HF) | 1 m | Pagos, transporte, pasaportes | MIFARE, ISO 14443, NFC |
| 860-960 MHz (UHF) | 12 m | Logística, inventarios | EPC Gen2 |
| 2.45 GHz | 100 m | Activos de alto valor | Propietarios |

### Apéndice B: Tabla de Compatibilidad

| Característica | Proxmark3 | Flipper Zero |
|----------------|-----------|--------------|
| RFID LF (125kHz) | ✅ Excelente | ✅ Bueno |
| NFC HF (13.56MHz) | ✅ Excelente | ✅ Bueno |
| MIFARE Classic | ✅ Ataque completo | ⚠️ Limitado |
| MIFARE Ultralight | ✅ Sí | ✅ Sí |
| Emulación | ✅ Limitada | ✅ Excelente |
| Sniffing | ✅ Sí | ❌ No |
| Portabilidad | ⚠️ Media | ✅ Excelente |
| Precio | $$$ | $$ |
| Curva de aprendizaje | Alta | Baja |

### Apéndice C: Glosario de Términos

- **UID:** Unique Identifier - Identificador único de una tarjeta
- **SAK:** Select Acknowledge - Byte de reconocimiento de selección
- **ATQA:** Answer To Request Type A - Respuesta a solicitud tipo A
- **ATS:** Answer To Select - Respuesta a selección
- **Sector:** Grupo de bloques en MIFARE Classic (4 bloques)
- **Block:** Unidad básica de datos (16 bytes en MIFARE)
- **Key A/B:** Claves de autenticación en MIFARE Classic
- **Access Bits:** Bits de control de acceso en MIFARE
- **Nested Attack:** Ataque criptográfico contra MIFARE Classic
- **Relay Attack:** Ataque de relevo de comunicación
- **Skimming:** Lectura no autorizada de tarjetas
- **Cloning:** Duplicación de una tarjeta RFID

### Apéndice D: Comandos Rápidos

#### Proxmark - Cheat Sheet

```bash
# General
hw status          # Estado del hardware
hw tune            # Ajustar antena

# LF
lf search          # Búsqueda automática
lf em 410x reader  # Leer EM4100
lf hid reader      # Leer HID
lf t55xx detect    # Detectar T5577

# HF
hf search          # Búsqueda automática
hf mf autopwn      # Ataque MIFARE automático
hf 14a info        # Info ISO14443A
hf mfu info        # Info MIFARE Ultralight
```

#### Flipper Zero - Atajos

- **Menú principal:** Botón de retroceso largo
- **Favoritos:** Botón de retroceso desde menú principal
- **Archivo de aplicación:** Navegación rápida
- **Configuración rápida:** Mantener arriba en menú

---

## Conclusión

Este taller proporciona las bases necesarias para comprender y trabajar con tecnología RFID utilizando Proxmark y Flipper Zero. La práctica responsable y ética es fundamental para el desarrollo de habilidades en seguridad de sistemas RFID.

### Próximos Pasos

1. **Práctica continua** con diferentes tipos de tarjetas
2. **Experimentación** en entornos controlados
3. **Participación** en comunidades de seguridad
4. **Actualización** constante de conocimientos
5. **Contribución** al desarrollo de herramientas open source

### Contacto y Soporte

Para dudas, consultas o colaboraciones relacionadas con este taller:

- **Repositorio:** [Incluir enlace al repositorio del grupo]
- **Instructor:** [Incluir información de contacto si aplica]
- **Grupo 5:** [Información del grupo]

---

**Última actualización:** Noviembre 2025  
**Versión:** 1.0  
**Licencia:** [Especificar licencia si aplica]

---

## Agradecimientos

Agradecemos a la comunidad de código abierto de RFID, especialmente a:
- RfidResearchGroup (Proxmark3)
- Flipper Devices
- Todos los investigadores de seguridad que han contribuido al conocimiento público

**¡Feliz hacking (ético)!** 🔐
