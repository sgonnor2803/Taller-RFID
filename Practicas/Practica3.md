<h1 align="center">Práctica 3: Preparación y escritura de bloques en una tarjeta RFID</h1>

## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusiones](#conclusiones)

---
## Objetivo
Preparar una tarjeta RFID en blanco borrando su contenido y escribiendo manualmente el bloque 0 a partir de los datos obtenidos de una tarjeta original.

---
## Material necesario
- Proxmark3
- Tarjeta RFID original (analizada en la práctica anterior)
- Tarjeta RFID en blanco
- Ordenador con ProxSpace configurado

---
## Procedimiento

### Paso 1: Colocar la tarjeta RFID en blanco
---

Colocar la tarjeta RFID en blanco sobre la **antena de alta frecuencia (HF)** de la Proxmark3, situada en la parte superior.

---
### Paso 2: Wipear la tarjeta (Borrado)
---

Borrar completamente el contenido de la tarjeta en blanco con el siguiente comando:

```bash
hf mf cwipe
```

Este comando deja la tarjeta limpia y lista para la escritura manual.

---
### Paso 3: Obtener los datos del bloque 0
---

Los datos necesarios para la escritura se obtienen de la **tarjeta original**, utilizando el comando:

```bash
hf mf info
```

En la salida de este comando se muestran los datos correspondientes al **bloque 0**.  

Tal y como se comentó en la práctica anterior, se recomienda guardar estos datos, ya que se utilizarán en el siguiente paso.

---
### Paso 4: Escribir el bloque 0
---

Escribir los datos del bloque 0 en la tarjeta en blanco mediante el siguiente comando:

```bash
hf mf csetblk --blk 0 --data XXXXXXXXXXXXXXXX
```

Sustituir `XXXXXXXXXXXXXXXX` por los datos exactos del bloque 0 obtenidos anteriormente.  
La escritura del bloque 0 es necesaria para que la tarjeta pueda ser reconocida correctamente por sistemas de control de acceso.

> Este paso prepara la tarjeta para poder realizar una clonación completa en la siguiente práctica.

---
### Paso 5: Verificar la escritura del bloque 0
---

Para comprobar que el bloque 0 se ha modificado correctamente, volver a ejecutar el siguiente comando:

```bash
hf mf info
```

Comparar los datos del bloque 0 mostrados con los valores escritos en el paso anterior y verificar que coinciden.

---
## Resultados

La tarjeta RFID queda correctamente wipeada y el bloque 0 se ha modificado con los datos indicados, confirmando que la escritura se ha realizado con éxito.

---
## Conclusiones

Esta práctica permite comprender cómo se puede manipular manualmente la memoria de una tarjeta RFID y verificar los cambios realizados antes de proceder a una clonación completa.