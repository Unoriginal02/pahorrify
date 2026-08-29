# Cómo funciona Ahorro (Pahorrar)

Esta app responde a una sola pregunta: **"de todo lo que tengo ahorrado, ¿cuánto me puedo gastar hoy sin arrepentirme mañana?"**

El modelo se apoya en **dos ejes independientes**:

1. **Gasto libre** — el presupuesto operativo del mes. Es lo que decide qué puedes gastar hoy.
2. **Tensión** — el termómetro de lo caldeado que está el ambiente. Sube con la deuda viva, y decide dos cosas: si se admite un imprevisto nuevo y si se libera un deseo retenido.

---

## 1. Los compartimentos del dinero

Con los valores por defecto (coste de vida 2.000 €/mes, suelo 1.500 €, colchón de 3 y 6 meses):

| Compartimento | Qué es | Hasta dónde |
|---|---|---|
| **Suelo** | Fondo de emergencia puro. Va **aparte**, fuera del sistema de colchones. | 1.500 € |
| **Colchón 1** | Los primeros 3 meses de vida, contados desde 0 **por encima** del suelo. | +6.000 € (7.500 € totales) |
| **Colchón 2** | Completa 6 meses de vida. Su final es donde el disponible cae al 25 %. | +12.000 € (13.500 € totales) |
| **Libre** | Todo lo que ahorres por encima. | sin techo |

Del colchón solo se saca dinero por **dos canales**: el gasto libre y los gastos imprevistos. El suelo tiene su propio canal, la emergencia.

---

## 2. La rampa: invertida

**Cuanto menos colchón acumulado, mayor porcentaje disponible.** Al revés de lo que parece intuitivo:

- Al principio del colchón 1 (0 € sobre el suelo): **75 %**
- Al final del colchón 2 (12.000 € sobre el suelo): **25 %**
- Entre medias baja de forma lineal; por encima del colchón 2 se queda en el 25 %.

Ese porcentaje se aplica al colchón (ahorro menos suelo), y el resultado es el **presupuesto del mes**: un saldo de gasto libre orientativo, calculado sobre lo que hay ahorrado.

**El presupuesto se congela al principio del mes.** Se calcula una sola vez, justo después de que entre la aportación mensual y de apartar el bote, y ya no se recalcula por mucho que gastes. Gastar solo vacía el saco, no lo recorta: si el presupuesto son 50 € y te gastas 25 €, te quedan **25 €** — no menos. Puedes ir descontando a mordiscos, de 10 € en 10 €, hasta dejarlo a cero.

---

## 3. El bote de vacaciones

Un **único porcentaje configurable** (por defecto un **10 %**) sobre todo el ahorro que hay por encima del suelo — **colchón más bote**. Eso es lo que debería haber en el bote en todo momento.

> El bote cuenta dentro de la base a propósito. Si el objetivo se midiera solo sobre el colchón, retirar 250 € bajaría el colchón 250 € y con él el propio objetivo: siempre acabarías pasado (250 € en el bote contra un objetivo de 225 €). Sobre colchón + bote, mover dinero de un bolsillo a otro no cambia la base y el objetivo se queda quieto.

- Cada mes, la app calcula lo que falta para llegar a ese objetivo y te lo muestra en un **cartel lila arriba del panel**: *"Retira 50 € para vacaciones este mes"*. Es el único cartel de la portada, y sigue ahí todo el mes, entres cuando entres, hasta que lo marcas como hecho.
- El importe se **redondea a la decena más cercana** (48 € → 50 €) para que sea una cantidad que el cajero pueda dar.
- El botón **Fet** lo anota en el Diario como retirada y pasa al historial de la tarjeta.
- El bote no se descuenta del disponible: al retirarlo ya sale del ahorro.

---

## 4. Los tres canales de gasto

No compiten entre sí.

### 4.A Gasto libre y el umbral de interrupción

- Se paga contra el **presupuesto del mes**, que está fijado desde el día 1. Lo que ves como *Disponible* es `presupuesto − lo ya gastado este mes`.
- **En el momento en que un gasto no cabe en el saldo que queda, el motor se para.** Da igual que el saldo ya fuera cero o que queden 3 €: si el gasto es mayor, no se aplica solo. La entrada se queda **detenida** en el Diario —sin mover un euro— con una fila que dice por qué y te obliga a decidir entre dos botones:

  **Forzar la despesa.** Sale **entera del colchón** de ahorros, siempre que haya fondos suficientes (nunca toca el suelo; si no cabe ni en todo el colchón, el botón no aparece). Al elegirlo, el presupuesto de gasto libre de **los meses venideros queda bloqueado automáticamente** hasta que la totalidad de ese coste esté saldada. Mientras dura el bloqueo, cualquier gasto libre nuevo vuelve a pasar por el mismo umbral: o lo cargas de nuevo forzándolo contra el colchón, o lo mandas a la lista de deseos.

  **Convertir en deseo.** No se gasta nada ahora. El gasto pasa a la lista de deseos y se ejecuta solo en cuanto se cumplen las dos condiciones de §6.

- Todo gasto libre que sí se aplica abre una **línea por reponer** por su importe entero: salió del ahorro, y la aportación mensual lo va reponiendo mes a mes. Es lo que dibuja la línea temporal (cuánto tardas en devolverlo) y lo que cuenta para la tensión. **No** toca el disponible.
- El presupuesto no consumido no se acumula al mes siguiente: al no gastarlo, el ahorro se queda más alto y el presupuesto del mes siguiente se calcula ya sobre esa cifra mayor.
- La app calcula y te dice **cuántos meses queda bloqueado** el disponible y en qué mes vuelve a haber.

### 4.B Gasto imprevisto

Algo importante pero no catastrófico: renovar la lavadora que va fatal **antes** de que reviente, cambiar la nevera. Importe grande que se paga de golpe y se amortiza a largo plazo (uno o dos años).

- **Sí afecta a la tensión** mientras se amortiza.
- **Nunca bloquea el gasto libre**: el presupuesto mensual sigue funcionando con normalidad. Es justo el motivo de separarlo — una nevera larga no puede dejarte sin caprichos un año.
- Su **admisión** depende de la tensión: hace falta estar **por debajo del umbral configurable** (Configuración · *Tensió màxima per admetre imprevistos*, por defecto 25 %).
- Si no puede admitirse —porque la tensión está alta o porque haría falta tocar el suelo— la entrada se **detiene** igual que un gasto libre, con dos botones idénticos en diseño: **convertir en deseo** o **convertir en emergencia** (el único canal que sí puede tocar el suelo).

### 4.C Gasto de emergencia

Orden de consumo estricto: **1)** disponible del mes → **2)** fondo suelo → (y solo si aún falta) el resto del colchón.

- Si toca el suelo, el disponible pasa a **cero** y no se reactiva hasta que el suelo esté **completamente** reconstituido.
- No afecta a la tensión: no fue una decisión.

---

## 5. La tensión

Se fija un **plazo objetivo para saldar la deuda** (parámetro configurable, por defecto 12 meses).

- **Capacidad de devolución** = aportación mensual × plazo objetivo.
- **Tensión** = qué porcentaje de esa capacidad tiene **ocupado** la deuda viva (gasto libre pendiente de reponer + imprevistos pendientes).

Ambas las repone la aportación mensual, en orden FIFO y primero el gasto libre. La deuda del gasto forzado es una cuenta aparte: no la paga la aportación sino los presupuestos de los meses siguientes, y es lo único que deja el disponible a cero.

Con 200 €/mes y 2.000 € de deuda:

| Plazo objetivo | Capacidad | La deuda ocupa | Tensión |
|---|---|---|---|
| 24 meses | 4.800 € | 42 % | **42 % — Tensión baixa** (amarillo) |
| 12 meses | 2.400 € | 83 % | **83 % — Tensión màxima** (rojo) |

El mismo saldo da lecturas opuestas según el plazo: es la palanca que calibra lo exigente que quieres ser.

### El indicador, ascendente

La aguja se mueve **de izquierda a derecha**, de menos a más tensión. Cuatro cuartos iguales más la franja negra:

| Tensión | Color | Qué significa |
|---|---|---|
| **0 %** | verde | Tranquilidad absoluta |
| **25 %** | amarillo | Estrés bajo |
| **50 %** | naranja | Estrés moderado |
| **75 %** | rojo | Tensión máxima, ambiente caldeado |
| **100–110 %** | negro | Has tocado fondo (suelo tocado; manda por encima de todo) |

---

## 6. Los deseos, por canal

Cada canal predice su fecha **de forma independiente**, así que la nevera y pintar la cocina no se estorban.

| Tipo | Canal | Cómo se predice |
|---|---|---|
| **Flexible** | Presupuesto mensual | Se ejecuta solo el primer mes en que se cumplen **las dos** condiciones: la deuda del gasto forzado anterior está **saldada** y la **tensión es menor del 75 %**. Además tiene que caber en el presupuesto de ese mes |
| **Imprevisto** | Canal de imprevistos | Cola tras el imprevisto en curso **+** que la tensión baje del umbral configurable |
| **Anclado** | Fecha fija | Se coloca en su mes; la app calcula cuánto aportar para llegar |

"Ja ho he fet" lo pasa al Diario como evento real. Si allí se pasa del saldo, aparece bajo la entrada la fila de decisión.

---

## 7. El diario

- **Aportación** — se suma a la aportación fija de Configuración.
- **Gasto libre** — consume el presupuesto del mes y abre una línea por reponer. Si se pasa del saldo, se detiene hasta que elijas: forzarlo o convertirlo en deseo.
- **Emergencia** — cascada disponible → suelo → colchón, sin tocar la tensión.
- **Despesa imprevista** — solo tensión, nunca el disponible. Si no cabe o la tensión está alta, se detiene: deseo o emergencia.
- **Retiro al bote** — del ahorro al bote de vacaciones.
- **Cambio de política** — a partir de ese mes, un parámetro vale otra cosa.

---

## 8. Dónde vive tu información

Todo en Firestore, vinculado a tu cuenta. Los extractos que importas se leen en local, solo en tu navegador.
