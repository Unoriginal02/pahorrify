# Cómo funciona Ahorro (Pahorrar)

Esta app responde a una sola pregunta: **"de todo lo que tengo ahorrado, ¿cuánto me puedo gastar hoy sin arrepentirme mañana?"**

El modelo se apoya en **dos ejes independientes**:

1. **Gasto disponible** — el presupuesto operativo. Es lo único que decide qué puedes gastar.
2. **Salud de la cuenta** — un indicador informativo de capacidad de devolución. No decide nada, con una única excepción (asumir un gasto imprevisto).

---

## 1. Los compartimentos del dinero

Con los valores por defecto (coste de vida 2.000 €/mes, suelo 1.500 €, colchón de 3 y 6 meses):

| Compartimento | Qué es | Hasta dónde |
|---|---|---|
| **Suelo** | Fondo de emergencia puro. Va **aparte**, fuera del sistema de colchones. | 1.500 € |
| **Colchón 1** | Los primeros 3 meses de vida, contados desde 0 **por encima** del suelo. | +6.000 € (7.500 € totales) |
| **Colchón 2** | Completa 6 meses de vida. Su final es donde el disponible cae al 25 %. | +12.000 € (13.500 € totales) |
| **Libre** | Todo lo que ahorres por encima. | sin techo |

---

## 2. La rampa: invertida

**Cuanto menos colchón acumulado, mayor porcentaje disponible.** Al revés de lo que parece intuitivo:

- Al principio del colchón 1 (0 € sobre el suelo): **75 %**
- Al final del colchón 2 (12.000 € sobre el suelo): **25 %**
- Entre medias baja de forma lineal; por encima del colchón 2 se queda en el 25 %.

Ese porcentaje se aplica al colchón (ahorro menos suelo), y el resultado es el **disponible del mes**.

---

## 3. El bote de vacaciones

Un **único porcentaje configurable** (por defecto un **10 %**) sobre el ahorro que hay por encima del suelo. Eso es lo que debería haber en el bote en todo momento.

- Cada mes, la app calcula lo que falta para llegar a ese objetivo y te lo muestra en un aviso: *"Retira 50 € para vacaciones este mes"*. El aviso sigue ahí durante todo el mes, entres cuando entres, hasta que lo marcas como hecho.
- El importe se **redondea a la decena más cercana** (48 € → 50 €) para que sea una cantidad que el cajero pueda dar.
- El botón **Fet** lo anota en el Diario como retirada y pasa al historial de la tarjeta.
- El bote no se descuenta del disponible: al retirarlo ya sale del ahorro.

---

## 4. Los tres canales de gasto

No compiten entre sí.

### 4.A Gasto libre

- Se paga contra el **disponible del mes**.
- **Puede excederlo**: un gasto ya hecho llega hasta **todo el colchón**, mientras no haya que tocar el suelo. Si el disponible son 214 € y el colchón 290 €, un gasto de 250 € entra sin preguntar.
- Lo que quede por saldar **se descuenta del disponible** de los meses siguientes. Mientras la deuda sea mayor que el disponible, el disponible es **cero** — así no se pueden encadenar dos gastos libres.
- En el mes en que la deuda ya es menor que el disponible, queda libre la diferencia: si ibas a tener 500 € y solo faltaban 100 €, te quedan **400 €**.
- El disponible no consumido se mantiene mes a mes sin caducar.
- Si un gasto libre no cabe ni con el colchón entero, no se anota: se convierte solo en un **deseo de gasto libre**.

### 4.B Gasto imprevisto

Una nevera, una lavadora: importe grande que se paga de golpe y se devuelve mes a mes.

- **Sí afecta a la salud** mientras se amortiza.
- **Nunca bloquea el gasto libre**: el disponible mensual sigue funcionando con normalidad. Es justo el motivo de separarlo — una nevera larga no puede dejarte sin caprichos un año.
- Su **admisión** depende de la salud: hace falta **≥ 50 %**. Es la única cosa que la salud decide.

### 4.C Gasto de emergencia

Orden de consumo estricto: **1)** disponible del mes → **2)** fondo suelo → (y solo si aún falta) el resto del colchón.

- Si toca el suelo, el disponible pasa a **cero** y no se reactiva hasta que el suelo esté **completamente** reconstituido.
- No afecta a la salud: no fue una decisión.

---

## 5. La salud de la cuenta

Se fija un **plazo objetivo para saldar la deuda** (parámetro configurable, por defecto 12 meses).

- **Capacidad de devolución** = aportación mensual × plazo objetivo.
- **Salud** = qué porcentaje de esa capacidad queda **libre** una vez cubierta la deuda viva (gasto libre pendiente + imprevistos pendientes).

Con 200 €/mes y 2.000 € de deuda:

| Plazo objetivo | Capacidad | La deuda consume | Salud |
|---|---|---|---|
| 24 meses | 4.800 € | 42 % | **58 % — Estable** (verde) |
| 12 meses | 2.400 € | 83 % | **17 % — Crítica** (rojo) |

El mismo saldo da lecturas opuestas según el plazo: es la palanca que calibra lo exigente que quieres ser.

Bandas: ≥50 % Estable · ≥35 % Ajustada · ≥20 % Tensa · <20 % Crítica · suelo tocado → Sin fondo (manda por encima de todo).

La salud **no bloquea gastos, no cambia el disponible y no afecta a los deseos de gasto libre**. Solo habilita o pausa los imprevistos.

---

## 6. Los deseos, por canal

Cada canal predice su fecha **de forma independiente**, así que la nevera y pintar la cocina no se estorban.

| Tipo | Canal | Cómo se predice |
|---|---|---|
| **Flexible** | Disponible mensual | Según se acumula el disponible; hacen cola entre ellos (un gasto libre vivo a la vez) |
| **Imprevisto** | Canal de imprevistos | Cola tras el imprevisto en curso **+** que la salud llegue al 50 % |
| **Anclado** | Fecha fija | Se coloca en su mes; la app calcula cuánto aportar para llegar |

"Ja ho he fet" lo pasa al Diario como evento real. Si allí no cabe, aparece bajo la entrada una fila de aviso para elegir canal: pasarlo a Deseos o anotarlo como emergencia.

---

## 7. El diario

- **Aportación** — se suma a la aportación fija de Configuración.
- **Gasto libre** — descuenta disponible hasta saldarse.
- **Emergencia** — cascada disponible → suelo → colchón, sin tocar la salud.
- **Despesa imprevista** — solo salud, nunca el disponible.
- **Retiro al bote** — del ahorro al bote de vacaciones.
- **Cambio de política** — a partir de ese mes, un parámetro vale otra cosa.

---

## 8. Dónde vive tu información

Todo en Firestore, vinculado a tu cuenta. Los extractos que importas se leen en local, solo en tu navegador.
