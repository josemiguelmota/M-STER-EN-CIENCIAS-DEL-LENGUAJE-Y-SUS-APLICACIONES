# Funciones en Python

**Introducción a la programación para lingüistas · Máster en Lingüística · Universidad de Cádiz**

Ya has usado muchas funciones sin saberlo: `print()`, `len()`, `type()`. En este tema aprenderás a **crear las tuyas**. Una función es un bloque de código con nombre que hace una tarea concreta: la escribes una vez y la usas todas las veces que quieras.

¿Por qué importa en lingüística? Porque casi todo análisis repite las mismas operaciones (limpiar un texto, contar palabras, clasificar terminaciones) sobre muchos textos distintos. Con funciones, escribes la operación una vez y la aplicas a todo el corpus.

## 0. Preparar el entorno

Este tema **no necesita instalar ninguna biblioteca**: solo usa Python. Elige una de estas dos formas de trabajar.

### Opción A: en VS Code (en tu ordenador)

1. Abre tu repositorio en VS Code desde GitHub Desktop (*Repository › Open in Visual Studio Code*).
2. Crea un cuaderno nuevo: `Ctrl+Shift+P` (`Cmd+Shift+P` en Mac) › *Create: New Jupyter Notebook*. Guárdalo en la carpeta `cuadernos` como `funciones.ipynb`.
3. Arriba a la derecha, **Seleccionar kernel** › *Python Environments* › elige tu Python. Si VS Code propone instalar `ipykernel`, acepta. (También puedes elegir el kernel de **Colab** con la extensión de Colab: este tema no lee archivos, así que funciona igual.)
4. Para cada bloque de código de este documento: pulsa **+ Código**, pega el bloque y ejecútalo con ▶ o con `Mayús+Intro`. Para tus predicciones, pulsa **+ Markdown**.

*Alternativa sin cuaderno:* crea un archivo `funciones.py`, pega los bloques uno tras otro y ejecútalo con ▶. Verás todos los resultados juntos en la terminal y el programa se detendrá en los bloques de errores del apartado 10: bórralos o coméntalos después de verlos.

### Opción B: en Google Colab (en el navegador)

1. Entra en [colab.research.google.com](https://colab.research.google.com) › *Nuevo cuaderno* y llámalo `funciones.ipynb`.
2. Para cada bloque de código: **+ Código**, pega y ejecuta con ▶. Para tus predicciones: **+ Texto**.
3. Al terminar: *Archivo › Descargar › Descargar .ipynb* y guárdalo en la carpeta `cuadernos` de tu repositorio.

En los dos casos, ejecuta los bloques **uno a uno**: los del apartado 10 fallan a propósito y *Ejecutar todo* se detendría en el primero.

### Cómo trabajar con este material

Copia cada bloque de código en VS Code o en Colab y ejecútalo **en orden**, de arriba abajo: muchos bloques usan variables o funciones de los anteriores. Usa el método **predice, ejecuta, explica**: cuando veas **Predice** o **Explica**, escribe tu respuesta *antes* de ejecutar, en una celda de texto del cuaderno o como comentario (`# ...`) en tu archivo. Si te equivocas, pide a Copilot o a Gemini que te explique por qué.

## 1. ¿Por qué usar funciones?

Antes de aprender a escribir funciones, veamos **qué problema resuelven**. Queremos analizar tres oraciones y, para cada una, saber cuántas palabras tiene, cuántos adverbios en *-mente* contiene y cuál es su palabra más larga.

```python
texto1 = "Rápidamente la profesora explicó claramente la lección"
texto2 = "El niño corría alegremente por el parque"
texto3 = "Finalmente llegamos a casa muy cansados"
```

### Sin funciones: copiar y pegar

La forma más directa es escribir el análisis para el primer texto y después copiarlo y pegarlo para los otros dos, cambiando el nombre de la variable.

```python
# Texto 1
palabras = texto1.lower().split()
print("Número de palabras:", len(palabras))
adverbios = 0
for palabra in palabras:
    if palabra.endswith("mente"):
        adverbios = adverbios + 1
print("Adverbios en -mente:", adverbios)
mas_larga = ""
for palabra in palabras:
    if len(palabra) > len(mas_larga):
        mas_larga = palabra
print("Palabra más larga:", mas_larga)
```

```python
# Texto 2
palabras = texto2.lower().split()
print("Número de palabras:", len(palabras))
adverbios = 0
for palabra in palabras:
    if palabra.endswith("mente"):
        adverbios = adverbios + 1
print("Adverbios en -mente:", adverbios)
mas_larga = ""
for palabra in palabras:
    if len(palabra) > len(mas_larga):
        mas_larga = palabra
print("Palabra más larga:", mas_larga)
```

```python
# Texto 3
palabras = texto2.lower().split()
print("Número de palabras:", len(palabras))
adverbios = 0
for palabra in palabras:
    if palabra.endswith("mente"):
        adverbios = adverbios + 1
print("Adverbios en -mente:", adverbios)
mas_larga = ""
for palabra in palabras:
    if len(palabra) > len(mas_larga):
        mas_larga = palabra
print("Palabra más larga:", mas_larga)
```

**Predice:** antes de ejecutar el bloque del texto 3, cuenta a mano las palabras de `texto3`. ¿Coincide con lo que muestra Python?

**Explica:** mira con atención la segunda línea del bloque del texto 3. ¿Qué ha pasado?

Es un error muy habitual al copiar y pegar: se nos olvidó cambiar `texto2` por `texto3`, y el programa no avisa de nada, simplemente da resultados equivocados. Además, este método tiene otros problemas:

- **Es largo y difícil de leer:** 39 líneas para hacer tres veces lo mismo.
- **Cada cambio hay que hacerlo en varios sitios:** si mañana quieres contar también las palabras en *-ción*, tendrás que modificar los tres bloques… y acordarte de todos.
- **No escala:** con un corpus de 100 textos, sería imposible.

### Con una función: escribirlo una vez y usarlo muchas

Ahora escribimos el análisis **una sola vez**, le damos un nombre (`analizar_texto`) y lo usamos con cada texto. No te preocupes todavía por la sintaxis: la verás paso a paso en los apartados siguientes.

```python
def analizar_texto(texto):
    palabras = texto.lower().split()
    print("Número de palabras:", len(palabras))
    adverbios = 0
    for palabra in palabras:
        if palabra.endswith("mente"):
            adverbios = adverbios + 1
    print("Adverbios en -mente:", adverbios)
    mas_larga = ""
    for palabra in palabras:
        if len(palabra) > len(mas_larga):
            mas_larga = palabra
    print("Palabra más larga:", mas_larga)


analizar_texto(texto1)
analizar_texto(texto2)
analizar_texto(texto3)
```

Fíjate en lo que hemos ganado:

- **El error desaparece:** cada llamada recibe su texto, sin variables que renombrar.
- **Un solo sitio para cambiar:** si quieres contar también las palabras en *-ción*, lo cambias dentro de la función y se aplica a todos los textos.
- **Añadir textos cuesta una línea:** pruébalo con una oración tuya.

```python
analizar_texto("Afortunadamente el examen resultó sorprendentemente sencillo")
```

### La abstracción

Cuando lees `analizar_texto(texto1)`, entiendes **qué hace** sin necesidad de leer **cómo lo hace**. Eso es la **abstracción**: dar un nombre a un conjunto de pasos para poder pensar en el conjunto y olvidarte de los detalles. Es lo mismo que hacemos en lingüística al hablar de un *sintagma nominal* sin enumerar cada vez las palabras que lo forman.

La regla práctica: **si te descubres copiando y pegando el mismo código, probablemente necesitas una función.**

En el apartado 5 verás que hay una forma mejor de que una función entregue sus resultados (`return`), en lugar de mostrarlos con `print`.

## 2. Funciones que ya conoces

Una función se **llama** escribiendo su nombre y, entre paréntesis, los datos que necesita (los **argumentos**).

```python
palabra = "fonología"
print(len(palabra))
print(type(palabra))
```

## 3. Crear tu primera función: `def`

Para crear una función se usa la palabra `def`, el nombre de la función, paréntesis y dos puntos. Las líneas que forman parte de la función van **sangradas** (4 espacios).

Crear la función no la ejecuta: solo la deja preparada. Para que haga algo, hay que **llamarla**.

```python
def saludar():
    print("Hola, lingüistas")

# Ahora la llamamos dos veces
saludar()
saludar()
```

**Predice:** ¿qué ocurre si borras las dos últimas líneas y ejecutas la celda?

## 4. Parámetros: darle datos a la función

Un **parámetro** es una variable que la función recibe entre paréntesis. Cada vez que la llamas, le das un valor distinto.

```python
def presentar_palabra(palabra):
    print("La palabra", palabra, "tiene", len(palabra), "letras")

presentar_palabra("sintaxis")
presentar_palabra("pragmática")
```

**Predice:** ¿qué escribirá `presentar_palabra("ñu")`? Compruébalo en la celda siguiente.

```python
# Escribe aquí la llamada y ejecútala
```

## 5. `return`: devolver un resultado

Esta es la idea más importante del tema. Hay dos formas de que una función «dé» algo:

- `print` **muestra** un resultado en pantalla, pero no lo guarda: no se puede seguir usando.
- `return` **devuelve** el resultado: puedes guardarlo en una variable y usarlo después.

Casi siempre querrás `return`.

```python
def contar_palabras(texto):
    palabras = texto.split()
    return len(palabras)

n = contar_palabras("En un lugar de la Mancha")
print("Número de palabras:", n)
print("El doble:", n * 2)
```

Ahora la misma función, pero con `print` en lugar de `return`:

```python
def contar_palabras_con_print(texto):
    palabras = texto.split()
    print(len(palabras))

n = contar_palabras_con_print("En un lugar de la Mancha")
print("Lo que se ha guardado en n:", n)
```

**Explica:** ¿qué se ha guardado en `n` en la segunda versión? `None` significa «nada» en Python. ¿Por qué ocurre?

## 6. Funciones que responden sí o no

Una función puede devolver `True` o `False`. Son muy útiles para clasificar palabras.

```python
def es_adverbio_mente(palabra):
    return palabra.lower().endswith("mente")

print(es_adverbio_mente("rápidamente"))
print(es_adverbio_mente("Lentamente"))
print(es_adverbio_mente("mente"))
```

**Predice y explica:** la tercera llamada devuelve `True`, pero *mente* no es un adverbio. ¿Qué te dice esto sobre las reglas basadas solo en terminaciones? Piensa cómo mejorar la función (pista: la longitud de la palabra).

## 7. Varios parámetros y valores por defecto

Una función puede recibir varios datos. Si a un parámetro le das un valor con `=`, ese valor se usa cuando no indicas otro.

```python
def palabras_largas(texto, minimo=7):
    resultado = []
    for palabra in texto.split():
        if len(palabra) >= minimo:
            resultado.append(palabra)
    return resultado

frase = "La lingüística computacional estudia el lenguaje con ordenadores"
print(palabras_largas(frase))
print(palabras_largas(frase, minimo=10))
```

**Predice:** ¿qué devolverá `palabras_largas(frase, minimo=3)`? ¿Y con `minimo=20`?

```python
# Compruébalo aquí
```

## 8. Funciones que usan otras funciones

Las funciones se pueden combinar como piezas. Aquí convertimos en función el contador de frecuencias que ya conoces y lo usamos dentro de otra función.

```python
def frecuencias(texto):
    """Devuelve un diccionario con cuántas veces aparece cada palabra."""
    resultado = {}
    for palabra in texto.lower().split():
        if palabra not in resultado:
            resultado[palabra] = 1
        else:
            resultado[palabra] = resultado[palabra] + 1
    return resultado


def ttr(texto):
    """Ratio tipo/token: palabras distintas entre palabras totales."""
    tokens = texto.lower().split()
    tipos = frecuencias(texto)
    return len(tipos) / len(tokens)


texto = "el gato y el perro y el ratón"
print(frecuencias(texto))
print("TTR:", round(ttr(texto), 2))
```

**Predice:** el texto tiene 8 tokens. ¿Cuántos tipos tiene? Calcula el TTR a mano y compáralo con el resultado.


El texto entre tres comillas debajo de `def` se llama **docstring**: explica qué hace la función. Python lo muestra si pides ayuda:

```python
help(ttr)
```

## 9. Variables locales: lo que pasa en la función se queda en la función

Las variables que creas dentro de una función solo existen mientras la función se ejecuta.

```python
def ejemplo():
    mensaje_interno = "Solo existo dentro de la función"
    return len(mensaje_interno)

print(ejemplo())
print(mensaje_interno)
```

**Explica:** ¿por qué la última línea da `NameError`?

## 10. Errores frecuentes

Ejecuta cada celda, lee el error y explica qué ha pasado.

```python
# Error 1: olvidar los paréntesis al llamar a la función
print(contar_palabras)
```

```python
# Error 2: no darle el dato que necesita
contar_palabras()
```

```python
# Error 3: sangría incorrecta
def mal_sangrada(texto):
return texto.upper()
```

## 11. Practica

Escribe estas funciones. Puedes pedir ayuda a Copilot, pero **predice siempre** el resultado antes de ejecutar y explica cada línea con un comentario.

1. `contar_vocales(palabra)`: devuelve cuántas vocales tiene una palabra, incluidas las acentuadas (`"aeiouáéíóúü"`).
2. `es_participio(palabra)`: devuelve `True` si la palabra termina en *-ado* o *-ido*.
3. `palabra_mas_frecuente(texto)`: usa la función `frecuencias` y devuelve la palabra que más se repite.

```python
# 1. contar_vocales
```

```python
# 2. es_participio
```

```python
# 3. palabra_mas_frecuente
```

## Puntos de comprobación

- [ ] Puedo explicar con un ejemplo por qué una función es mejor que copiar y pegar el mismo código.
- [ ] Puedo explicar la diferencia entre **definir** una función y **llamarla**.
- [ ] Sé qué es un parámetro y qué es un valor por defecto.
- [ ] Puedo explicar con un ejemplo la diferencia entre `print` y `return`.
- [ ] Entiendo por qué una variable creada dentro de una función no existe fuera.
- [ ] He escrito al menos dos de las funciones del apartado 11 y funcionan.

Antes de hacer commit: si trabajas en un cuaderno, *Borrar todas las salidas*; después guarda y sincroniza con GitHub Desktop.
