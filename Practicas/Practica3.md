<h1 align="center">Práctica 3: Preparación y escritura de bloques en una tarjeta RFID</h1>

<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/235a864e-1ac4-47f5-bc70-364bb2fa154d" />

---
## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusión](#conclusión)

---
## Objetivo
Preparar una tarjeta RFID Magic borrando su contenido y escribiendo manualmente el bloque 0 a partir de los datos obtenidos de una tarjeta original.

---
## Material necesario
- Proxmark3
- Tarjeta RFID original (analizada en la práctica anterior)
- Tarjeta RFID Magic
- Ordenador con el entorno de Proxmark3 correctamente configurado

---
## Procedimiento

### Paso 1: Colocar la tarjeta RFID Magic
---

Colocar la tarjeta RFID Magic sobre la **antena de alta frecuencia (HF)** de la Proxmark3, situada en la parte superior.

---
### Paso 2: Wipear la tarjeta (Borrado)
---

Borrar completamente el contenido de la tarjeta Magic con el siguiente comando:

```bash
hf mf cwipe
```

<img width="1115" height="319" alt="image" src="https://github.com/user-attachments/assets/a1704dfc-3348-47a1-8916-4a1fe138e50f" />

Este comando deja la tarjeta limpia y lista para la escritura manual.

---
### Paso 3: Obtener los datos del bloque 0
---

Los datos necesarios para la escritura se obtienen de la **tarjeta original**, utilizando el comando:

```bash
hf mf info
```

<img width="1117" height="568" alt="image" src="https://github.com/user-attachments/assets/1f0d85f4-fa87-4afc-bfad-b9b56b217a45" />

En la salida de este comando se muestran los datos correspondientes al **bloque 0**. 

> Tal y como se comentó en la práctica anterior, se recomienda guardar estos datos, ya que se utilizarán en el siguiente paso.

---
### Paso 4: Escribir el bloque 0
---

Escribir los datos del bloque 0 en la tarjeta Magic mediante el siguiente comando:

```bash
hf mf csetblk --blk 0 --data XXXXXXXXXXXXXXXX
```

<img width="1113" height="319" alt="image" src="https://github.com/user-attachments/assets/f695ab76-d5ea-40c5-916b-1c2ee3aa45ad" />

Sustituir `XXXXXXXXXXXXXXXX` por los datos exactos del bloque 0 obtenidos anteriormente.  
La escritura del bloque 0 es necesaria para que la tarjeta pueda ser reconocida correctamente por sistemas de control de acceso.

> Este paso prepara la tarjeta para poder realizar una clonación completa en la siguiente práctica.

---
### Paso 5: Verificar la escritura del bloque 0
---

Para comprobar que el bloque 0 se ha modificado correctamente en la tarjeta Magic, volver a ejecutar el siguiente comando:

```bash
hf mf info
```

<img width="1111" height="568" alt="image" src="https://github.com/user-attachments/assets/29e08457-ff20-4f46-bcf2-0feb1f3ca59f" />

Comparar los datos del bloque 0 mostrados con los valores escritos en el paso anterior y verificar que coinciden.

---
## Resultados

La tarjeta RFID Magic queda correctamente wipeada (borrada) y el bloque 0 se ha modificado con los datos indicados, confirmando que la escritura se ha realizado con éxito.

---
## Conclusión

Esta práctica permite comprender cómo se puede manipular manualmente la memoria de una tarjeta RFID y verificar los cambios realizados antes de proceder a una clonación completa.
