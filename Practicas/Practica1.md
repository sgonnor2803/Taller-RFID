<h1 align="center">Práctica 1: Preparación del entorno ProxSpace</h1>

<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/1c5557ff-3ad0-4ff0-92e4-02a6c495556f" />

---
## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusión](#conclusión)

---
## Objetivo
Preparar el entorno de trabajo con ProxSpace y comprobar que la Proxmark3 funciona correctamente antes de comenzar las prácticas de explotación RFID.

---
## Material necesario
- Proxmark3
- Ordenador
- ProxSpace (archivo ZIP descargable desde Drive)

---
## Procedimiento

### Paso 1: Descargar y descomprimir ProxSpace
---

Descargar el archivo ZIP de ProxSpace desde el siguiente enlace:

- [Descargar ProxSpace desde Drive](https://drive.google.com/file/d/1HZorp_ZoIgyFwLCBr50S-buoaHkzL4h4/view?usp=sharing)

Una vez descargado, descomprimir el archivo en el sistema.

---
### Paso 2: Ejecutar ProxSpace
---

Acceder a la carpeta descomprimida y ejecutar el archivo `runme64.bat`.  
Esto abrirá una terminal con el entorno de ProxSpace preparado.

---
### Paso 3: Conectar el Proxmark3
---

Conectar la Proxmark3 al ordenador mediante el cable USB.

---
### Paso 4: Comprobar detección de la Proxmark3
---

En la terminal de ProxSpace, entrar en la carpeta `proxmark3/` y ejecutar el siguiente comando para listar los dispositivos conectados:

```bash
./pm3 --list
```

Se mostrará un puerto COM (por ejemplo, `COM3`, `COM4`, etc.).

> **Nota:** si no se muestra ningún puerto, esperar unos segundos hasta que el sistema asigne el dispositivo a un puerto COM.

---
### Paso 5: Acceder al cliente de Proxmark3
---

Entrar en la carpeta `client/` y ejecutar el cliente indicando el puerto COM detectado:

```bash
cd client
./proxmark3 comX
```

(Sustituir `X` por el puerto obtenido en el paso anterior).

---
### Paso 6: Comprobar el hardware
---

Una vez dentro del entorno de la Proxmark3, ejecutar el siguiente comando para comprobar el estado del hardware y las antenas:

```bash
hw tune
```

Este comando permite verificar que la Proxmark3 es reconocida correctamente y que las antenas funcionan correctamente.

---
### Paso 7: Configurar las rutas de guardado (trace y dump)
---

Una vez dentro del entorno de la Proxmark3, ejecutar los siguientes comandos para definir las carpetas donde se guardarán las trazas y los volcados generados durante el uso del dispositivo:

> **Nota:** sustituir **C:\Users\.....** por la ruta de la carpeta ProxSpace.

```bash
prefs set savepaths --trace C:\Users\.....
prefs set savepaths --dump  C:\Users\.....

````

---
## Resultados

El entorno ProxSpace queda configurado correctamente y la Proxmark3 es detectada sin errores, mostrando valores adecuados de las antenas.

---
## Conclusión

El entorno de trabajo queda listo para continuar con las siguientes prácticas del taller.
