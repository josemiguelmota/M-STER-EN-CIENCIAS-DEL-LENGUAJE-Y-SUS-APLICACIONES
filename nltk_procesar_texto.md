# Procesar texto con NLTK

**Introducción a la programación para lingüistas · Máster en Lingüística · Universidad de Cádiz**

**NLTK** (*Natural Language Toolkit*) es una de las bibliotecas más veteranas para el procesamiento del lenguaje natural en Python. Reúne herramientas para tokenizar, contar frecuencias, buscar concordancias, extraer raíces o trabajar con n-gramas, además de corpus y listas de palabras de muchas lenguas.

En este tema usarás NLTK con un texto en español y verás también **qué no hace bien** en nuestra lengua.

**Antes de empezar:** necesitas haber trabajado el tema de **[funciones](funciones.md)**, porque al final las combinaremos con NLTK.

## 1. Preparar el entorno: instalar NLTK

Este tema necesita dos bibliotecas externas: **`nltk`** y, para el gráfico del apartado 7, **`matplotlib`**. Cómo se instalan depende de dónde trabajes.

### Opción A: en VS Code (en tu ordenador)

**1. Instala las bibliotecas** (solo la primera vez; después quedan en tu ordenador). En VS Code abre la terminal (*Terminal › Nuevo terminal*) y escribe:

```bash
pip install nltk matplotlib
```

En Mac, usa `pip3` en lugar de `pip`. En Windows, si `pip` no se reconoce, prueba `py -m pip install nltk matplotlib`.

Si trabajas en un cuaderno de VS Code, también puedes instalarlas desde una celda; así te aseguras de que se instalan en el mismo Python que usa el kernel:

```python
%pip install nltk matplotlib
```

**2. Crea el cuaderno:** `Ctrl+Shift+P` (`Cmd+Shift+P` en Mac) › *Create: New Jupyter Notebook*, guárdalo en `cuadernos` como `nltk_procesar_texto.ipynb` y elige el kernel **local** (*Seleccionar kernel* › *Python Environments*).

**3. Copia y ejecuta** cada bloque de código en una celda nueva (**+ Código**), en orden.

**Comprueba la instalación:** si al ejecutar `import nltk` aparece `ModuleNotFoundError`, la biblioteca no está instalada en el Python que usa el kernel. Instálala con `%pip install nltk` en una celda y vuelve a ejecutar.

*Alternativa sin cuaderno:* puedes pegar los bloques en un archivo `nltk_procesar_texto.py` y ejecutarlo con ▶. El gráfico se abrirá en una ventana aparte; ciérrala para que el programa continúe.

### Opción B: en Google Colab (en el navegador)

1. Entra en [colab.research.google.com](https://colab.research.google.com) › *Nuevo cuaderno* y llámalo `nltk_procesar_texto.ipynb`.
2. **No hace falta instalar nada:** Colab ya trae `nltk` y `matplotlib`. Si algún día necesitas una biblioteca que no esté, instálala en una celda con `%pip install nombre`. Lo que instales en Colab **se pierde al cerrar la sesión**, así que tendrías que repetirlo.
3. Copia y ejecuta cada bloque en una celda nueva (**+ Código**), en orden.
4. Al terminar: *Archivo › Descargar › Descargar .ipynb* y guárdalo en `cuadernos`.

### Comprueba que funciona

Sea cual sea tu opción, ejecuta este primer bloque:

```python
import nltk
print("Versión de NLTK:", nltk.__version__)
```

### Cómo trabajar con este material

Copia cada bloque de código en VS Code o en Colab y ejecútalo **en orden**, de arriba abajo: muchos bloques usan variables o funciones de los anteriores. Usa el método **predice, ejecuta, explica**: cuando veas **Predice** o **Explica**, escribe tu respuesta *antes* de ejecutar, en una celda de texto del cuaderno o como comentario (`# ...`) en tu archivo. Si te equivocas, pide a Copilot o a Gemini que te explique por qué.

## 2. Descargar los recursos

NLTK separa la **biblioteca** (el código) de los **recursos** (los datos: modelos para tokenizar, listas de palabras, corpus). Los recursos se descargan aparte con `nltk.download()`.

- `punkt` y `punkt_tab`: modelos para dividir un texto en oraciones y palabras.
- `stopwords`: listas de palabras vacías de varias lenguas.

En Colab hay que repetir esta celda en cada sesión; en local, basta una vez.

```python
nltk.download("punkt")
nltk.download("punkt_tab")
nltk.download("stopwords")
```

## 3. El texto

Trabajaremos con el comienzo del *Quijote*, de dominio público. Si usas el kernel local y tienes el texto en tu carpeta `datos`, puedes leerlo con `open("../datos/quijote.txt", encoding="utf-8").read()` desde un cuaderno guardado en `cuadernos`, o con `open("datos/quijote.txt", encoding="utf-8").read()` desde un archivo `.py` en la carpeta principal.

```python
texto = (
    "En un lugar de la Mancha, de cuyo nombre no quiero acordarme, no ha mucho tiempo "
    "que vivía un hidalgo de los de lanza en astillero, adarga antigua, rocín flaco y "
    "galgo corredor. Una olla de algo más vaca que carnero, salpicón las más noches, "
    "duelos y quebrantos los sábados, lantejas los viernes, algún palomino de añadidura "
    "los domingos, consumían las tres partes de su hacienda. El resto della concluían "
    "sayo de velarte, calzas de velludo para las fiestas, con sus pantuflos de lo mesmo, "
    "y los días de entresemana se honraba con su vellorí de lo más fino."
)
print(texto)
```

## 4. Tokenizar: dividir en oraciones y palabras

**Tokenizar** es dividir un texto en unidades: oraciones o palabras (*tokens*). Indicamos `language="spanish"` para que use las reglas del español.

```python
from nltk.tokenize import sent_tokenize, word_tokenize

oraciones = sent_tokenize(texto, language="spanish")
print("Número de oraciones:", len(oraciones))
for oracion in oraciones:
    print("-", oracion)
```

**Predice:** compara `split()`, que ya conoces, con `word_tokenize()`. ¿En qué se diferenciarán los primeros 12 elementos? Fíjate en las comas.

```python
print(texto.split()[:12])
print(word_tokenize(texto, language="spanish")[:12])
```

`[:12]` significa «los 12 primeros elementos de la lista».

**Explica:** ¿qué ventaja tiene `word_tokenize` para contar palabras?

## 5. Normalizar: minúsculas y sin signos de puntuación

Para contar palabras conviene que *El* y *el* cuenten como la misma, y quitar los signos. El método `isalpha()` devuelve `True` si un token solo tiene letras (incluidas tildes y ñ).

```python
tokens = word_tokenize(texto, language="spanish")

palabras = []
for token in tokens:
    if token.isalpha():
        palabras.append(token.lower())

print("Tokens totales:", len(tokens))
print("Palabras (sin signos):", len(palabras))
print(palabras[:15])
```

## 6. Palabras vacías (*stopwords*)

Las **palabras vacías** son palabras gramaticales muy frecuentes (artículos, preposiciones, conjunciones) que suelen eliminarse para ver las palabras con más contenido. NLTK trae una lista para el español.

```python
from nltk.corpus import stopwords

vacias = stopwords.words("spanish")
print("Palabras vacías en la lista:", len(vacias))
print(vacias[:20])
```

**Predice:** ¿estarán *della* y *mesmo* en la lista? Piensa por qué podrían no estar.

```python
print("della" in vacias, "mesmo" in vacias, "de" in vacias)

contenido = []
for palabra in palabras:
    if palabra not in vacias:
        contenido.append(palabra)

print(contenido)
```

**Explica:** la lista de palabras vacías está pensada para el español actual. ¿Qué problema plantea con un texto del siglo XVII? ¿Cómo podrías ampliarla? (Pista: `vacias.append(...)`.)

## 7. Frecuencias con `FreqDist`

`FreqDist` cuenta frecuencias, como el diccionario que construiste a mano o como `Counter`, pero con funciones extra para el análisis lingüístico.

```python
from nltk import FreqDist

fd_todas = FreqDist(palabras)
fd_contenido = FreqDist(contenido)

print("Con palabras vacías:", fd_todas.most_common(5))
print("Sin palabras vacías:", fd_contenido.most_common(5))
print("¿Cuántas veces aparece 'los'?", fd_todas["los"])
```

**Explica:** sin palabras vacías, todas las palabras aparecen una sola vez. ¿Qué te dice esto sobre el tamaño del texto que necesitas para que las frecuencias sean informativas?

Puedes verlo en un gráfico. Necesita `matplotlib`, que instalaste en el apartado 1 (en Colab ya viene incluida).

```python
fd_todas.plot(10, title="Las 10 palabras más frecuentes")
```

## 8. Concordancias

Una **concordancia** (KWIC, *keyword in context*) muestra cada aparición de una palabra con su contexto a izquierda y derecha. Es una de las herramientas básicas de la lingüística de corpus.

```python
texto_nltk = nltk.Text(tokens)
texto_nltk.concordance("los", width=60)
```

**Prueba:** cambia `"los"` por otra palabra del texto. ¿Qué pasa si buscas una palabra que no aparece?

## 9. Raíces: el *stemmer* de Snowball

Un **stemmer** recorta las palabras para quedarse con una raíz aproximada, aplicando reglas de sufijos. NLTK incluye uno para el español.

**Predice:** ¿qué raíz obtendrá para *cantaba*, *cantando*, *cantaremos* y *canción*? ¿Será la misma para las cuatro?

```python
from nltk.stem import SnowballStemmer

stemmer = SnowballStemmer("spanish")
for palabra in ["cantaba", "cantando", "cantaremos", "canción", "fui", "iré"]:
    print(palabra, "→", stemmer.stem(palabra))
```

**Explica:** fíjate en *fui* e *iré*. ¿Por qué el stemmer no sabe que son formas del mismo verbo? Esa es la diferencia entre **raíz** (*stem*, recorte mecánico) y **lema** (la forma de diccionario, *ir*), que necesita conocimiento de la lengua.

## 10. N-gramas

Un **n-grama** es una secuencia de *n* palabras seguidas: bigramas (2), trigramas (3)… Sirven para estudiar combinaciones frecuentes y colocaciones.

```python
from nltk import bigrams

pares = list(bigrams(palabras))
print(pares[:8])

fd_bigramas = FreqDist(pares)
print(fd_bigramas.most_common(5))
```

## 11. NLTK y funciones juntos

Ahora reunimos los pasos anteriores en **una función** reutilizable, como aprendiste en el tema de [funciones](funciones.md). Así puedes aplicar el mismo proceso a cualquier texto.

```python
def preparar_texto(texto, quitar_vacias=True):
    """Tokeniza, pasa a minúsculas, quita signos y, si se pide, palabras vacías."""
    resultado = []
    for token in word_tokenize(texto, language="spanish"):
        if token.isalpha():
            token = token.lower()
            if not (quitar_vacias and token in vacias):
                resultado.append(token)
    return resultado


otro_texto = "La lengua es un sistema de signos. Los signos se combinan según reglas."
print(preparar_texto(otro_texto))
print(preparar_texto(otro_texto, quitar_vacias=False))
```

## 12. Lo que NLTK no hace bien en español

NLTK es excelente para aprender y para tareas como tokenizar, contar o buscar concordancias, pero tiene límites en español:

- **No lematiza** el español: solo recorta raíces (apartado 9).
- **No etiqueta** bien las categorías gramaticales del español sin entrenar un modelo propio.

Para eso se usan bibliotecas como **spaCy**, con modelos ya entrenados para el español. Las veréis más adelante en el curso.

## 13. Practica

Usa Copilot si lo necesitas, pero **predice antes de ejecutar** y comenta cada línea.

1. Escribe una función `oracion_mas_larga(texto)` que use `sent_tokenize` y devuelva la oración con más palabras.
2. Escribe una función `palabras_unicas(texto)` que devuelva las palabras que aparecen **una sola vez** (los *hápax*). Pista: `FreqDist` tiene el método `.hapaxes()`.
3. Aplica `preparar_texto` y `FreqDist` a un texto tuyo de dominio público y comenta en una celda de texto qué palabras destacan.

```python
# 1. oracion_mas_larga
```

```python
# 2. palabras_unicas
```

```python
# 3. Tu texto
```

## Puntos de comprobación

- [ ] Sé instalar NLTK en mi ordenador (`pip install` o `%pip install`) y sé por qué en Colab no hace falta.
- [ ] Puedo explicar la diferencia entre la biblioteca y sus recursos (`nltk.download`).
- [ ] Sé tokenizar en oraciones y en palabras, y por qué es mejor que `split()`.
- [ ] Sé filtrar palabras vacías y conozco sus limitaciones con textos antiguos.
- [ ] Puedo obtener las palabras más frecuentes y una concordancia.
- [ ] Puedo explicar la diferencia entre raíz y lema.
- [ ] He escrito al menos una de las funciones del apartado 13.

Antes de hacer commit: si trabajas en un cuaderno, *Borrar todas las salidas*; después guarda y sincroniza con GitHub Desktop.
