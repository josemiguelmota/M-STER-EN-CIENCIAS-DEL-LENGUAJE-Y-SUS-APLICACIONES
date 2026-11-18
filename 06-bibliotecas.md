# 6. Bibliotecas: código que otros ya han escrito

**Qué es.** Una **biblioteca** (también se dice *librería*, del inglés *library*) es un conjunto de funciones ya programadas para una tarea concreta. En lugar de escribir desde cero cómo contar palabras, tokenizar un texto o dibujar un gráfico, usas el trabajo de otros. Casi todo el análisis de textos en Python se apoya en bibliotecas.

Hay dos tipos:

- **Bibliotecas estándar**: vienen con Python y solo hay que importarlas. Por ejemplo, `collections` o `re` (expresiones regulares).
- **Bibliotecas externas**: hay que **instalarlas** antes de usarlas. Por ejemplo, `pandas`, `nltk` o `spacy`.

| Biblioteca | Tipo | Para qué sirve en lingüística |
| --- | --- | --- |
| `collections` | Estándar | Contar frecuencias con `Counter` |
| `re` | Estándar | Buscar patrones: palabras que terminan en *-mente*, fechas, signos |
| `pandas` | Externa | Organizar resultados en tablas |
| `matplotlib` | Externa | Hacer gráficos de frecuencias |
| `nltk` | Externa | Tokenizar, listas de palabras vacías, corpus de ejemplo |
| `spacy` | Externa | Lematizar y etiquetar categorías gramaticales |

## Cómo se incorporan

Con `import`, al principio del código. Hay tres formas habituales:

```python
import collections                # importa la biblioteca entera
from collections import Counter   # importa solo una parte
import pandas as pd               # importa con un nombre corto (alias)
```

## Cómo se instalan las externas

Depende del kernel (ver el [tema 4](04-colab-en-vscode.md)):

- **Kernel de Colab**: la mayoría ya vienen instaladas. Si falta alguna, se instala en una celda con `%pip install nombre`, pero **se pierde al cerrar la sesión** y hay que repetirlo cada vez.
- **Kernel local**: se instala una vez con `%pip install nombre` en una celda (o `pip install nombre` en la terminal) y queda en tu ordenador.

Instala solo bibliotecas conocidas y escribe bien el nombre: hay paquetes falsos con nombres casi idénticos a los de bibliotecas populares.

## Prueba 1: una biblioteca estándar

Compara con el [ejemplo 5.8](05-conceptos-basicos-python.md#58-todo-junto-contar-palabras):

```python
from collections import Counter
texto = "el gato y el perro y el ratón"
frecuencias = Counter(texto.split())
print(frecuencias.most_common(2))
```

**Predice:** ¿qué dos palabras aparecerán? Fíjate en que `Counter` hace en una línea lo que en el 5.8 necesitaba un bucle y una condición.

## Prueba 2: una biblioteca externa

Con el **kernel local**, ejecuta:

```python
import pandas as pd
```

Si aparece `ModuleNotFoundError`, la biblioteca no está instalada. Instálala en una celda nueva y vuelve a ejecutar la anterior:

```python
%pip install pandas
```

Después muestra las frecuencias como tabla:

```python
tabla = pd.DataFrame(frecuencias.most_common(), columns=["palabra", "frecuencia"])
tabla
```

Cambia al **kernel de Colab** y ejecuta `import pandas as pd`: funciona sin instalar nada, porque Colab ya la trae.

## Puntos de comprobación

- [ ] Puedo explicar qué es una biblioteca y la diferencia entre estándar y externa.
- [ ] Sé importar una biblioteca de las tres formas (`import`, `from … import`, `as`).
- [ ] He instalado `pandas` en el kernel local y sé por qué en Colab no hacía falta.
- [ ] Sé qué significa `ModuleNotFoundError` y cómo resolverlo.

---

[← Anterior: Conceptos básicos de Python](05-conceptos-basicos-python.md) · [Índice](README.md) · [Siguiente: Ampliaciones →](07-ampliaciones.md)
