# 🌀 Mini-Torneo Beyblade – Ronda Única
**El Villano vs El Coleccionista** · “último gol gana todo”

---

## 🎯 Objetivo (qué debes lograr)
Construir un programa en **Kotlin** que, para **una sola ronda**, calcule el puntaje de **El Villano** y **El Coleccionista**, aplique **bonus** según reglas, valide datos con una **excepción personalizada**, use **funciones** con parámetros, emplee una **List** para un cálculo simple y determine el **ganador**.

> Contenidos a aplicar:
> - Tipos y operadores: `Int`, `Double`, `String`, comparaciones, `if/else`.
> - **List** + recorrido básico (iteración/cálculo simple).
> - Funciones simples con parámetros.
> - **POO (clases, herencia, polimorfismo)`.
> - Manejo **básico** de excepciones.

---

## 📦 Estructura del proyecto (4 archivos)
```
src/
 ├─ Main.kt
 ├─ Blader.kt
 ├─ Villano.kt
 └─ Coleccionista.kt
```

> **Nota:** Todos los archivos sin `package` para evitar imports.

---

## 🧮 Reglas de puntaje
1) **Puntaje base**  
   ```
   puntajeBase = (potencia * precision) + (poderBase * 0.1)
   ```
   Convierte a `Int` (truncando).

2) **Bonus por frase o gesto (String)**  
   - `"A pastar"` → **+5**  
   - `"No podrás con el giro izquierdo"` → **+7**  *(frase del Villano)*  
   - `"😛"` → **+6**  *(gesto del Coleccionista)*  
   - cualquier otra → **+0**

3) **Bonus de estilo (polimorfismo)**  
   - **Villano:** si `potencia >= 80` → **+10**  
   - **Coleccionista:** si `precision >= 0.85` → **+10**

4) **Puntaje final**  
   ```
   puntajeFinal = puntajeBase + bonusFrase + bonusEstilo
   ```

5) **Ganador de la ronda (y del torneo)**  
   - Mayor puntaje → gana.  
   - Igual puntaje → “**Empate total**”.

---

## 🧪 Datos de prueba sugeridos
- **Villano** → `poderBase = 60`, `potencia = 85`, `precision = 0.70`, `frase = "No podrás con el giro izquierdo"`
- **Coleccionista** → `poderBase = 55`, `potencia = 75`, `precision = 0.88`, `frase = "😛"`

---

## 🧭 Pasos (guía de laboratorio)

### 1) Crear la excepción personalizada
- En `Main.kt`, define:
  ```kotlin
  class DatoInvalidoException(msg: String) : Exception(msg)
  ```
- La usarás para **validar** rangos de entrada:
  - `potencia` ∈ **1..100**
  - `precision` ∈ **0.0..1.0**

### 2) Definir la clase base (POO)
- Archivo `Blader.kt`:
  - `open class Blader(nombre: String, poderBase: Int)`
  - Método **polimórfico**:
    ```kotlin
    open fun calcularBonus(potencia: Int, precision: Double, frase: String): Int {
        // TODO: sobrescribir en subclases
        return 0
    }
    ```

### 3) Crear las subclases (herencia + polimorfismo)
- `Villano.kt`: sobrescribe `calcularBonus` con la regla **potencia ≥ 80 → +10**.
- `Coleccionista.kt`: sobrescribe `calcularBonus` con la regla **precision ≥ 0.85 → +10**.

### 4) Implementar **funciones** con parámetros (en `Main.kt`)
Crea e implementa estas funciones (observa los esqueletos y completa la lógica):

- **Cálculo del puntaje base**
  ```kotlin
  fun puntajeBase(potencia: Int, precision: Double, poderBase: Int): Int {
      // TODO: validar rangos y calcular (potencia * precision) + (poderBase * 0.1)
      return 0
  }
  ```

- **Bonus por frase**
  ```kotlin
  fun bonusFrase(frase: String): Int {
      return when {
          // TODO: comparar la frase y devolver el bonus correspondiente
          else -> 0
      }
  }
  ```

- **Decidir ganador**
  ```kotlin
  fun ganadorRonda(puntajeVillano: Int, puntajeColeccionista: Int): String {
      // TODO: usar if/else para decidir
      return ""
  }
  ```

### 5) Preparar los datos de la ronda única (en `main`)
- **Instancia** a cada blader con su `poderBase`.
- Define variables **descriptivas** para `potencia`, `precision` y `frase` de cada uno (usa los **datos de prueba** o ingrésalos tú).

### 6) Calcular los puntajes finales
- Para **cada** blader:
  1. `puntajeBase(...)`
  2. `bonusFrase(...)`
  3. `calcularBonus(...)` (polimorfismo)
  4. `puntajeFinal = base + bonusFrase + bonusEstilo`

### 7) **Usar una List** y hacer un cálculo simple
- Crea una `List<Int>` con los 2 puntajes finales:
  ```kotlin
  val puntajesFinales = listOf(puntajeFinalVillano, puntajeFinalColeccionista)
  ```
- **Recórrela** con un ciclo (`for`) para:
  - Encontrar el **máximo** (o verificar si hay empate).
  - (Alternativa): sumar ambos y mostrar el **total combinado**.

### 8) Decidir y mostrar el **ganador**
- Llama a `ganadorRonda(...)`.
- Imprime en consola, por ejemplo:
  ```
  Ronda Única → Villano=XX | Coleccionista=YY | Ganador: ZZZ
  ```

### 9) Manejo básico de **excepciones**
- Encierra la lógica del `main` en `try/catch`.
- Si hay datos inválidos, muestra:
  ```
  Dato inválido: <mensaje>
  ```
  y termina de forma controlada.

---

## 📤 Salida esperada (formato de ejemplo)
```
Ronda Única → Villano=XX | Coleccionista=YY | Ganador: Coleccionista
```
*(Los valores XX/YY dependen de tu cálculo.)*

---

## ✅ Checklist antes de entregar
- [ ] Usaste `Int`, `Double`, `String` y `if/else` para las reglas.  
- [ ] Implementaste las funciones solicitadas y las llamaste desde `main`.  
- [ ] Definiste `Blader` y **sobrescribiste** `calcularBonus` en ambas subclases.  
- [ ] Creaste una **List** con los puntajes finales y la **recorriste** con un ciclo.  
- [ ] Validaste rangos y lanzaste **DatoInvalidoException** si correspondía.  
- [ ] Mostraste el **ganador** (o empate) de forma clara en consola.

---

### Tips
- Usa **nombres de variables descriptivos** (`potenciaVillano`, `precisionColeccionista`…).  
- Si cambias los datos de prueba, **mantén** los rangos válidos.

¡Éxitos y a pastar!
