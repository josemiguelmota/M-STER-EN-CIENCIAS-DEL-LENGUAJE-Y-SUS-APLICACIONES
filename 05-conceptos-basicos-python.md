# 5. Conceptos básicos de Python: entender el código

**Qué vamos a hacer.** Aprenderás a leer código de Python y a modificarlo sin depender de Copilot. Antes de ejecutar una celda, escribe qué crees que hace y qué resultado esperas. Ejecútala, compara el resultado y prueba un cambio pequeño. Si no entiendes una diferencia, localiza la línea y prueba con un ejemplo más corto. Solo después, si sigues atascado, pide a Copilot en VS Code una pista sobre esa línea, no una solución completa.

Crea un cuaderno nuevo en VS Code: abre la paleta de comandos (`⌘⇧P` en macOS, `Ctrl+Shift+P` en Windows y Linux), elige *Create: New Jupyter Notebook* y guárdalo como `cuadernos/conceptos_basicos.ipynb` dentro de `laboratorio-textos`. Selecciona el kernel de Colab como en el [tema 4](04-colab-en-vscode.md). Si usas el navegador, crea allí `conceptos_basicos.ipynb` y descárgalo al terminar. Este cuaderno no necesita archivos de datos. Copia cada ejemplo en una celda de código.

## 5.1 Comentarios y `print`

Fuera de un texto entre comillas, `#` marca el comienzo de un comentario: Python ignora lo que queda de esa línea. En este curso, acompaña cada función o método nuevo de un comentario que diga qué hace en ese ejemplo. Si defines una función, indica qué recibe y qué devuelve o qué efecto tiene. Cuando cambies el código, revisa también el comentario.

```python
# print() muestra un saludo en la salida de la celda.
print("Hola, lingüística")
```

## 5.2 Variables y tipos de datos

Una **variable** es una caja con nombre donde guardas un dato. Cada dato tiene un **tipo**. Para los nombres de las variables, usa minúsculas, sin tildes ni ñ.

```python
palabra = "morfologia"   # str: texto, siempre entre comillas
num_palabras = 1500      # int: número entero
ttr = 0.45               # float: número decimal (con punto)
es_verbo = False         # bool: verdadero (True) o falso (False)
# type() identifica el tipo de cada valor; print() muestra los cuatro tipos.
print(type(palabra), type(num_palabras), type(ttr), type(es_verbo))
```

**Predice:** ¿qué tipo mostrará cada `type()`?

## 5.3 Funciones y métodos de texto

Una **función** hace una tarea con lo que le das entre paréntesis: `len()` cuenta elementos. Un **método** es una función propia de un tipo de dato y se escribe después de un punto: `.upper()`, `.split()`.

```python
oracion = "La lingüística es fascinante"
# len() cuenta los caracteres; print() muestra cada resultado de la prueba.
print(len(oracion))
# upper() devuelve una copia del texto en mayúsculas.
print(oracion.upper())
# split() separa el texto por espacios en blanco y devuelve una lista.
print(oracion.split())
```

**Predice:** ¿`len()` cuenta también los espacios? ¿Qué devuelve `split()`?

## 5.4 Condiciones: `if`, `elif`, `else`

Permiten hacer algo solo si se cumple una condición. Las líneas que dependen de la condición van **sangradas** (con 4 espacios a la derecha); si la sangría está mal, Python da un `IndentationError`.

```python
palabra = "rápidamente"
# endswith() comprueba el sufijo; print() muestra la hipótesis de la rama elegida.
if palabra.endswith("mente"):
    print(palabra, "es probablemente un adverbio")
elif palabra.endswith("ar"):
    print(palabra, "podría ser un infinitivo")
else:
    print("No sé qué categoría tiene", palabra)
```

**Predice:** ¿qué escribe si cambias la palabra por `"cantar"`? ¿Y por `"casa"`?

## 5.5 Listas

Una **lista** guarda varios elementos en orden, entre corchetes. Se accede a cada uno por su posición, que empieza en 0; `-1` es el último.

```python
tokens = ["La", "lingüística", "computacional", "es", "útil"]
# print() muestra el primer y el último token, y len() cuenta todos los tokens.
print(tokens[0])
print(tokens[-1])
print(len(tokens))
# append() añade un elemento al final de la misma lista.
tokens.append(".")
# print() muestra la lista después de añadir el punto.
print(tokens)
```

**Predice:** ¿qué muestra `tokens[0]`? ¿Cuántos elementos tiene la lista al final?

## 5.6 El bucle `for`

Repite las líneas sangradas una vez por cada elemento de la lista.

```python
tokens = ["La", "lingüística", "computacional", "es", "útil"]
for token in tokens:
    # len() mide cada token; print() muestra el token junto con su longitud.
    print(token, len(token))
```

**Predice:** ¿cuántas líneas se imprimirán?

## 5.7 Diccionarios

Un **diccionario** guarda pares **clave : valor**, entre llaves. No se busca por posición, sino por clave, como en un diccionario de papel.

```python
categorias = {"casa": "sustantivo", "correr": "verbo", "bonito": "adjetivo"}
# print() muestra primero la categoría de una palabra y luego el diccionario actualizado.
print(categorias["casa"])
categorias["rápido"] = "adjetivo"
print(categorias)
```

## 5.8 Todo junto: contar palabras

Este ejemplo combina variables, métodos, un bucle, una condición y un diccionario. El resultado es una tabla de frecuencias en forma de diccionario: cada palabra tiene asociado el número de veces que aparece.

```python
texto = "el gato y el perro y el ratón"
frecuencias = {}
# split() separa las formas para recorrerlas de una en una.
for palabra in texto.split():
    if palabra not in frecuencias:
        frecuencias[palabra] = 1
    else:
        frecuencias[palabra] = frecuencias[palabra] + 1
# print() muestra el recuento final de cada forma.
print(frecuencias)
```

**Predice:** ¿qué número tendrá `"el"`? Después, explica en una celda de texto qué hace cada línea. Prueba también con `"El gato, y el perro"`: `split()` separa por espacios en blanco, pero no elimina comas ni convierte a minúsculas. Restablece el texto original antes de seguir al tema 6 para poder comparar ambos recuentos.

Cuando termines, ejecuta las celdas de arriba abajo, usa *Borrar todas las salidas*, guarda y, si usas Colab en el navegador, descarga la copia a `cuadernos`. Haz commit con el mensaje `Conceptos básicos de Python` y sincroniza. En el siguiente tema añadirás las pruebas de bibliotecas a este mismo cuaderno.

## Práctica de lectura de código

Descarga el [cuaderno de ejercicios de lectura](ejercicios-lectura-python.ipynb) desde los materiales del curso. Puedes trabajar en una copia dentro de `cuadernos/` de tu propio repositorio o abrirla en Colab desde el navegador. Haz la primera pasada sin Copilot: escribe tus predicciones, ejecuta una celda cada vez e intenta hacer y explicar un cambio por ejercicio. Consulta las soluciones al final, después de haber probado tus cambios.

## Puntos de comprobación

- [ ] Mi cuaderno tiene una celda de texto con mi predicción antes de cada ejemplo.
- [ ] Puedo explicar en una frase qué es una variable, una lista, un `for`, un `if` y un diccionario.
- [ ] He modificado al menos un ejemplo con palabras mías y el resultado era el que esperaba.
- [ ] Sé explicar línea a línea el ejemplo 5.8.
- [ ] Puedo cambiar un ejemplo, predecir el efecto y actualizar su comentario sin pedir a Copilot que lo reescriba.
- [ ] `cuadernos/conceptos_basicos.ipynb` está en GitHub.

---

[← Anterior: Colab en VS Code](04-colab-en-vscode.md) · [Índice](README.md) · [Siguiente: Bibliotecas →](06-bibliotecas.md)
