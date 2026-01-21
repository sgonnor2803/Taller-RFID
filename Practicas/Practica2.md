<h1 align="center">Práctica 2: Lectura y ataque a una tarjeta RFID</h1>

<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/7b9b8c1c-e7fc-4b33-8a08-c57fcfdb589d" />


---
## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusión](#conclusión)

---
## Objetivo
Obtener información de una tarjeta RFID y extraer sus claves mediante el uso de comandos de Proxmark3.

---
## Material necesario
- Proxmark3
- Tarjeta RFID
- Ordenador con ProxSpace configurado

---
## Procedimiento

### Paso 1: Colocar la tarjeta RFID
---

Colocar la tarjeta RFID **sobre la antena de alta frecuencia (HF)** de la Proxmark3.

---
### Paso 2: Identificar la tarjeta
---

Ejecutar el siguiente comando para identificar el tipo de tarjeta y obtener información básica:

```bash
hf search
```

En la salida del comando se muestra información general de la tarjeta y se indica la posibilidad de obtener información más detallada.

---
### Paso 3: Obtener información detallada
---

Según la información obtenida en el paso anterior, ejecutar el siguiente comando para extraer información más detallada de la tarjeta:

```bash
hf mf info
```

Este comando permite conocer el tipo de tarjeta, su estructura y otros datos relevantes.

> ⚠️ Importante: guardar los datos correspondientes al bloque 0 que se muestran en la salida del comando, ya que serán necesarios para la siguiente práctica.

---
### Paso 4: Extraer las claves de la tarjeta
---

Una vez identificada la tarjeta, ejecutar el siguiente comando para intentar obtener las claves:

```bash
hf mf autopwn
```

Durante el proceso se realizará un ataque automatizado y, si tiene éxito, se generarán archivos con las claves obtenidas.

> ⚠️ Importante: no mover la tarjeta RFID durante el proceso, ya que podría provocar fallos en la obtención de las claves.

---
## Resultados

Se obtiene información básica y detallada de la tarjeta RFID.
Tras ejecutar el ataque automatizado, se generan dos archivos con las claves extraídas, que quedan almacenados en la carpeta de ProxSpace.

---
## Conclusión

Esta práctica permite comprender cómo es posible identificar una tarjeta RFID y extraer sus claves utilizando herramientas automatizadas.
