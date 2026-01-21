<h1 align="center">Práctica 1: Preparación del entorno</h1>

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

Preparar el entorno de trabajo y verificar el correcto funcionamiento de la Proxmark3 antes de comenzar las prácticas de explotación RFID.

---
## Material necesario

- Proxmark3  
- Ordenador  
- Cliente Proxmark3 (archivo ZIP descargable desde Drive)

---
## Procedimiento

### Paso 1: Descargar y descomprimir el Cliente Proxmark3
---

Descargar el archivo ZIP del cliente Proxmark3 desde el siguiente enlace:

- [Descargar Cliente Proxmark3 desde Drive](https://drive.google.com/file/d/1mvhAZZd0Ig34hq4moS08ZSAkzooyC-Yz/view?usp=sharing)

Una vez descargado, descomprimir el archivo en el sistema.

<img width="979" height="541" alt="image" src="https://github.com/user-attachments/assets/fa5da76d-21d8-49d9-9792-196324cef524" />

---
### Paso 2: Ejecutar el Cliente Proxmark3
---

Acceder a la carpeta descomprimida y ejecutar el archivo `pm3.bat`.

<img width="1010" height="508" alt="image" src="https://github.com/user-attachments/assets/e697e18b-a082-4222-953a-78e3c004c3fe" />

Se abrirá una terminal con el entorno del cliente preparado.

<img width="1015" height="378" alt="image" src="https://github.com/user-attachments/assets/6fcfa4b9-13cb-4142-a52d-4d95bdee2a0c" />

---
### Paso 3: Conectar la Proxmark3
---

Conectar la Proxmark3 al ordenador mediante el cable USB mientras el cliente se encuentra en ejecución. Una vez conectada, el dispositivo será reconocido automáticamente y se iniciará la comunicación con el cliente en la terminal.

<img width="1012" height="719" alt="image" src="https://github.com/user-attachments/assets/e70d62dc-a23b-4371-9f70-5efc32e75e6b" />

---
### Paso 4: Comprobar el hardware
---

Dentro del entorno de la Proxmark3, ejecutar el siguiente comando para comprobar el estado del hardware y de las antenas:

```bash
hw tune
```

<img width="1014" height="702" alt="image" src="https://github.com/user-attachments/assets/b585aca2-c72e-4707-a22a-ba77c5e9ff25" />

Este comando permite verificar que la Proxmark3 es reconocida correctamente y que las antenas funcionan de manera adecuada.

---
## Resultados

El entorno queda configurado correctamente y la Proxmark3 es detectada sin errores, mostrando valores adecuados en las mediciones de las antenas.

---
## Conclusión

El entorno de trabajo queda correctamente preparado, permitiendo continuar con las siguientes prácticas del taller.
