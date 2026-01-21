<h1 align="center">Práctica 4: Clonación completa de una tarjeta RFID y comprobación de acceso</h1>

<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/19931792-d8af-47d8-8b16-b9a14a8bccb8" />

---
## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusión](#conclusión)

---
## Objetivo
Realizar la clonación completa de una tarjeta RFID y comprobar si la tarjeta clonada permite abrir una cerradura de control de acceso.

---
## Material necesario
- Proxmark3
- Tarjeta RFID original
- Tarjeta RFID Magic *(preparada en la práctica anterior)*
- Ordenador con el entorno de Proxmark3 correctamente configurado
- Cerradura RFID

---
## Procedimiento

### Paso 1: Colocar la tarjeta RFID original
---

Colocar la tarjeta RFID original sobre la **antena de alta frecuencia (HF)** de la Proxmark3.

---
### Paso 2: Realizar el volcado de la tarjeta
---

Ejecutar el siguiente comando para realizar un volcado completo de la tarjeta:

```bash
hf mf dump
```

<img width="1114" height="741" alt="image" src="https://github.com/user-attachments/assets/393cfd80-987a-4cfd-9f35-35cfae53e093" />

Este comando generará un archivo `.bin` con toda la información de la tarjeta, que se guardará automáticamente en la carpeta `Client/`.

---
### Paso 3: Colocar la tarjeta RFID Magic
---

Retirar la tarjeta original y colocar la **tarjeta RFID Magic preparada en la práctica anterior**, en la que ya se escribió el bloque 0, sobre la antena HF de la Proxmark3.

---
### Paso 4: Restaurar la información en la tarjeta RFID Magic

Utilizar el archivo generado en el paso anterior para completar la clonación de la tarjeta:

```bash
hf mf restore -f hf-mf-XXXXXXXX.bin
```

<img width="1114" height="550" alt="image" src="https://github.com/user-attachments/assets/49887212-bf60-459b-a613-f16ba43f16bd" />

Sustituir `hf-mf-XXXXXXXX.bin` por el nombre del archivo generado durante el [volcado (Paso 2)](#paso-2-realizar-el-volcado-de-la-tarjeta).

---
### Paso 5: Comprobar la cerradura
---

Una vez finalizado el proceso, los participantes pueden ir comprobando si la **tarjeta Magic clonada** abre correctamente la cerradura RFID.

---
## Resultados

La tarjeta preparada reproduce el comportamiento de la tarjeta original y, en caso de éxito, permite abrir la cerradura.

---
## Conclusión

Esta práctica muestra cómo, tras preparar una tarjeta y clonar completamente su contenido, es posible acceder a un sistema de control de acceso.
