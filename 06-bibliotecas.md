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

Sigue en `cuadernos/conceptos_basicos.ipynb`, que creaste en el tema anterior. Añade al final una celda de texto con el título `## Bibliotecas` y una celda de código por cada prueba. Usa el mismo kernel o vuelve a ejecutar las celdas en orden si cambias de entorno.

## Cómo se incorporan

Con `import`, al principio del código. Hay tres formas habituales:

```python
import collections                # importa la biblioteca entera
from collections import Counter   # importa solo una parte
import pandas as pd               # importa con un nombre corto (alias)
```

## Cómo se instalan las externas

Depende del kernel (ver el [tema 4](04-colab-en-vscode.md)):

- **Kernel de Colab**: muchas bibliotecas ya vienen instaladas. Las que añadas con `%pip install nombre` estarán disponibles mientras conserves ese entorno de ejecución.
- **Kernel local**: `%pip install nombre` en una celda instala la biblioteca en el entorno de Python que usa ese cuaderno.

Instala solo bibliotecas conocidas y escribe bien el nombre: hay paquetes falsos con nombres casi idénticos a los de bibliotecas populares.

## Prueba 1: una biblioteca estándar

Compara con el [ejemplo 5.8](05-conceptos-basicos-python.md#58-todo-junto-contar-palabras). Usamos el mismo texto y guardamos este recuento con otro nombre para poder comprobar que coinciden:

```python
from collections import Counter
texto = "el gato y el perro y el ratón"
# split() separa las formas; Counter() cuenta cuántas veces aparece cada una.
frecuencias_counter = Counter(texto.split())
# most_common(2) devuelve las dos formas más frecuentes con sus recuentos.
# print() muestra los pares de forma y frecuencia.
print(frecuencias_counter.most_common(2))
# print() muestra también si el resultado coincide con el recuento manual.
print(frecuencias_counter == frecuencias)
```

**Predice:** ¿qué dos palabras aparecerán? Si ejecutaste el ejemplo 5.8 con el texto original, la segunda salida será `True`: ambos recuentos coinciden.

## Prueba 2: una biblioteca externa

Con el kernel que estés usando, ejecuta:

```python
# Importamos pandas con el alias pd para construir la tabla.
import pandas as pd
```

Colab suele traer `pandas`. Si aparece `ModuleNotFoundError`, añade antes del `import` una celda con esta instrucción y ejecútala:

```python
# %pip instala pandas en el entorno que ejecuta este cuaderno.
%pip install pandas
```

Vuelve a ejecutar el `import` y después muestra las frecuencias como tabla:

```python
# most_common() devuelve todos los pares ordenados por frecuencia.
# DataFrame() convierte los pares en una tabla con las dos columnas indicadas.
tabla = pd.DataFrame(frecuencias_counter.most_common(), columns=["palabra", "frecuencia"])
tabla
```

Comprueba que la primera fila muestra `el` con frecuencia `3`. Ejecuta todo en orden, borra las salidas y guarda. Si estás en el navegador, descarga la versión actualizada y sustituye la copia de `cuadernos`. Haz commit con el mensaje `Comparo recuentos y añado la tabla de frecuencias` y sincroniza.

## Puntos de comprobación

- [ ] Puedo explicar qué es una biblioteca y la diferencia entre estándar y externa.
- [ ] Sé importar una biblioteca de las tres formas (`import`, `from … import`, `as`).
- [ ] He comprobado que ambos recuentos coinciden y he visto `el` con frecuencia `3` en la tabla de `pandas`.
- [ ] Sé qué significa `ModuleNotFoundError` y cómo resolverlo.

---

[← Anterior: Conceptos básicos de Python](05-conceptos-basicos-python.md) · [Índice](README.md) · [Siguiente: Ampliaciones →](07-ampliaciones.md)
