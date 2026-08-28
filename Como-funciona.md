# Cómo funciona Ahorro (Pahorrar)

Esta app responde a una sola pregunta que cualquiera con ahorros se hace alguna vez: **"de todo lo que tengo ahorrado, ¿cuánto me puedo gastar hoy sin arrepentirme mañana?"**

La respuesta no es "todo" ni "nada". Es una cifra que cambia cada mes según cuánto tengas guardado, cuánto hayas gastado últimamente y qué tan lejos estés de tu colchón ideal. La app hace ese cálculo por ti, cada vez que anotas algo.

---

## La idea de fondo

La mayoría de la gente ahorra en un único cajón: la cuenta. Y ese cajón no distingue entre "esto es intocable", "esto es mi red de seguridad" y "esto ya lo puedo disfrutar". El resultado es que, o no te gastas nunca nada por miedo, o te lo gastas todo y luego no tienes colchón cuando lo necesitas.

Esta app divide mentalmente tu dinero en **compartimentos** con reglas distintas, y calcula automáticamente cuánto de ese dinero ya "se ha ganado el derecho" a ser gastado libremente. Cuanto más llenos están los compartimentos importantes, más suelta la correa.

---

## 1. Los compartimentos del dinero

Con los números que tienes configurados ahora mismo (coste de vida 1.900 €/mes, suelo 1.500 €, colchón de 3 y 6 meses de vida):

| Compartimento | Qué es | Hasta dónde llega |
|---|---|---|
| **Suelo** | El fondo de emergencia puro. No cuenta como "ahorro disponible" nunca; es el último cortafuegos. | 1.500 € |
| **Colchón 1** | Los primeros meses de margen (aquí, 3 meses de vida). Empieza a liberar algo de dinero, pero poco. | hasta 7.200 € |
| **Colchón 2** | El colchón "completo" (aquí, 6 meses de vida en total). Cuanto más te acercas, más se libera. | hasta 12.900 € |
| **Libre** | Todo lo que ahorres por encima del colchón completo. Aquí ya se libera al ritmo máximo. | sin techo |

El suelo **no es parte del colchón**: es un compartimento aparte. Si una emergencia te obliga a tocarlo, la app lo nota y bloquea casi todo lo demás hasta que lo repongas (más abajo, el estado "Sin fondo").

---

## 2. La rampa: cuánto te puedes gastar

Aquí está el corazón de la app. La idea es simple: **cuanto menos ahorrado tengas, menos disponible; cuanto más te acerques a tu colchón completo, más disponible** — y ese aumento es progresivo, no un interruptor de todo o nada.

- Con el colchón vacío, solo un pequeño porcentaje de lo ahorrado se libera (por defecto, un 25 %).
- Con el colchón lleno del todo (el "techo 2"), se libera el porcentaje máximo (por defecto, un 50 %).
- Entre medias, el porcentaje sube poco a poco según lo llenos que estén el Colchón 1 y el Colchón 2.
- Por encima del colchón completo, todo el excedente se libera siempre al porcentaje máximo.

Ese porcentaje se aplica sobre el colchón (el ahorro menos el suelo), no sobre todo tu saldo. Es la cantidad "bruta" disponible, antes de reservar nada para vacaciones.

**Por qué funciona así:** si gastas, tu saldo baja — pero además el porcentaje disponible también baja, porque estás más lejos del colchón completo. Así que gastar te frena el doble: menos dinero, y una tasa peor sobre ese dinero. Es un autocorrectivo automático contra el gasto impulsivo.

---

## 3. El bote de vacaciones

De ese dinero "bruto" disponible, la app aparta automáticamente una parte para un bote de vacaciones (o cualquier gasto grande que quieras planificar aparte).

- Al principio de la rampa (colchón casi vacío) se reserva un porcentaje más alto para el bote (por defecto, 50 %) — la lógica es: si aún no tienes colchón, prioriza construir un fondo antes que gastar suelto.
- Al final de la rampa se reserva menos (por defecto, 25 %) — con más colchón ya puedes permitirte gastar más libremente y reservar menos.

Lo que sobra después de apartar el bote es el **"disponible libre"**: el dinero que de verdad puedes gastar en el día a día sin tocar ni el suelo ni el bote.

---

## 4. La tensión: la "resaca" de gastar

Cada vez que haces un gasto libre (no una emergencia, no algo pagado con el bote), ese gasto abre una especie de "deuda contigo mismo": se apunta como pendiente de recuperar.

- Tienes una **aportación mensual** (por defecto, 200 €) que va amortizando esa deuda, empezando por el gasto más antiguo.
- Tienes una **ventana de referencia** (por defecto, 12 meses) que marca el ritmo de recuperación "sano": aportación × ventana es tu **capacidad de recuperación**.
- La **tensión** es el porcentaje de esa capacidad que está comprometido en deuda pendiente. La deuda **no caduca**: se queda contando hasta que se amortiza del todo, por mucho tiempo que pase — la ventana solo dice cuánta deuda es razonable llevar, no cuándo se te perdona.

Cuanta más tensión acumulada, menos margen tienes para nuevos gastos libres — y a partir de cierto punto (75 %), los gastos libres quedan bloqueados del todo, aunque tengas saldo de sobra. Solo se permiten emergencias.

**La idea:** no es solo cuánto tienes ahorrado, sino cuánto te has estado gastando *últimamente*. Puedes tener mucho saldo y aun así estar "sobregastando" en los últimos meses — la tensión detecta eso antes de que se convierta en un problema.

**Cuando un gasto libre no cabe:** la app no puede impedir un gasto que ya has hecho de verdad, pero antes de anotarlo te pregunta. Puedes convertirlo en un **deseo** (entra en la cola de la sección 7 y se coloca solo, más adelante, cuando sí quepa) o anotarlo igual porque ya lo has gastado — en ese caso queda marcado con 🔥 como **forzado**, para que quede claro que se anotó a pesar del aviso.

---

## 5. Los semáforos de salud

Con esa tensión, la app resume tu situación en un color:

- 🟢 **Estable** — tensión por debajo del 25 %. Margen amplio.
- 🟡 **Ajustada** — entre 25 % y 50 %. Margen medio.
- 🟠 **Tensa** — entre 50 % y 75 %. Margen corto.
- 🔴 **Bloqueada** — 75 % o más. Sin margen: los gastos libres se bloquean.
- ⚫ **Sin fondo** — el suelo (el fondo de emergencia) está tocado. Aquí manda esto por encima de todo lo demás: se bloquea prácticamente todo hasta reponerlo.

---

## 6. El diario: cómo se registra la vida real

Todo lo que pasa con tu dinero se anota como un "evento" con un tipo, y cada tipo se comporta distinto:

- **Aportación** — lo que metes ese mes (sustituye a la aportación por defecto de Ajustes).
- **Gasto libre** — sale del disponible libre y genera tensión (es lo que hay que "recuperar" después).
- **Emergencia** — no genera tensión. Se paga primero con el disponible libre, luego con el suelo, y si hace falta con el colchón.
- **Extra** (nómina extra, paga doble...) — entra al ahorro y amortiza deuda pendiente, pero no cuenta como aportación fija de cara a la capacidad.
- **Retiro al bote** — mueve dinero del ahorro al bote de vacaciones.
- **Aporte extra al bote** — dinero que entra directamente al bote desde fuera (no genera disponible, porque no pasa por el ahorro).
- **Gasto del bote** — se paga con el bote; tampoco genera tensión.
- **Cambio de política** — a partir de ese mes, algún parámetro (coste de vida, aportación, etc.) cambia de valor. Lo anterior no se retoca.

---

## 7. Los deseos: cosas que quieres pero aún no has comprado

Es una lista de caprichos o compras futuras, separada del diario porque **todavía no ha pasado**: no afecta al saldo real ni a la tensión, solo aparece de forma orientativa (punteada) en los gráficos.

Hay dos tipos:

- **Flexible** — no tiene fecha fija. La app calcula cuándo te lo podrás permitir sin desequilibrar nada, según cómo evolucione tu disponible libre. Van en cola: hasta que el primero de la lista no "cabe", los siguientes esperan su turno.
- **Anclado** — tiene fecha fija (por ejemplo, un viaje ya reservado). Se paga con el bote de vacaciones. Si el bote no va a llegar a tiempo, la app calcula cuánto extra tendrías que apartar cada mes para lograrlo.

---

## 8. La proyección a 10 años

Con todo lo anterior, la app simula mes a mes cómo evolucionará tu ahorro durante los próximos años, asumiendo que sigues aportando lo mismo y que no pasa nada más. Se ven dos líneas:

- Cómo evoluciona el ahorro solo con lo que ya has anotado de verdad.
- Cómo evolucionaría si además fueras cumpliendo los deseos de tu lista, en el orden en que están.

Esto te deja ver, por ejemplo, cuándo alcanzarás el colchón completo, o si un deseo concreto te va a hacer retroceder de color.

---

## 9. Dónde vive tu información

Nada se sube a ningún servidor. La app guarda todo en un único archivo `.json` en tu ordenador (el que tienes vinculado ahora es `ahorro.json`), y lo reescribe automáticamente cada vez que cambias algo. Los extractos bancarios que importas se leen también en local, solo en tu navegador.

---

## Resumen en una frase

La app no te dice "no gastes"; te dice **"esto es lo que ya te has ganado poder gastar hoy, dado lo lleno que está tu colchón y lo reciente que ha sido tu gasto"** — y ese número se recalcula solo, mes a mes, según lo que realmente haces.
