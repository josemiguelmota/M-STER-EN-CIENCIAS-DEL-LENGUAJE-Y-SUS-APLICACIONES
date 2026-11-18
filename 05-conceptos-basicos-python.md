# 5. Conceptos básicos de Python: entender el código

**Qué vamos a hacer.** Todavía no vas a escribir programas. El objetivo es que, cuando veas un código de ejemplo en clase, sepas qué hace cada línea. Usaremos el método **predice, ejecuta, explica**: antes de ejecutar cada celda, escribe en una celda de texto qué crees que pasará; después ejecútala y, si te equivocaste, pide a Copilot o a Gemini que te explique por qué.

Crea un cuaderno nuevo `cuadernos/conceptos_basicos.ipynb` (en VS Code: `Ctrl+Shift+P` › *Create: New Jupyter Notebook*, y guárdalo en `cuadernos`). Puedes usar el kernel de Colab o el local: aquí no leemos archivos. Copia cada ejemplo en una celda de código.

## 5.1 Comentarios y `print`

Lo que va detrás de `#` es un comentario: Python lo ignora y sirve para explicar el código. `print()` muestra algo en pantalla.

```python
# Esto es un comentario: Python no lo ejecuta
print("Hola, lingüística")
```

## 5.2 Variables y tipos de datos

Una **variable** es una caja con nombre donde guardas un dato. Cada dato tiene un **tipo**. Para los nombres de las variables, usa minúsculas, sin tildes ni ñ.

```python
palabra = "morfologia"   # str: texto, siempre entre comillas
num_palabras = 1500      # int: número entero
ttr = 0.45               # float: número decimal (con punto)
es_verbo = False         # bool: verdadero (True) o falso (False)
print(type(palabra), type(num_palabras), type(ttr), type(es_verbo))
```

**Predice:** ¿qué tipo mostrará cada `type()`?

## 5.3 Funciones y métodos de texto

Una **función** hace una tarea con lo que le das entre paréntesis: `len()` cuenta elementos. Un **método** es una función propia de un tipo de dato y se escribe después de un punto: `.upper()`, `.split()`.

```python
oracion = "La lingüística es fascinante"
print(len(oracion))
print(oracion.upper())
print(oracion.split())
```

**Predice:** ¿`len()` cuenta también los espacios? ¿Qué devuelve `split()`?

## 5.4 Condiciones: `if`, `elif`, `else`

Permiten hacer algo solo si se cumple una condición. Las líneas que dependen de la condición van **sangradas** (con 4 espacios a la derecha); si la sangría está mal, Python da un `IndentationError`.

```python
palabra = "rápidamente"
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
print(tokens[0])
print(tokens[-1])
print(len(tokens))
tokens.append(".")
print(tokens)
```

**Predice:** ¿qué muestra `tokens[0]`? ¿Cuántos elementos tiene la lista al final?

## 5.6 El bucle `for`

Repite las líneas sangradas una vez por cada elemento de la lista.

```python
tokens = ["La", "lingüística", "computacional", "es", "útil"]
for token in tokens:
    print(token, len(token))
```

**Predice:** ¿cuántas líneas se imprimirán?

## 5.7 Diccionarios

Un **diccionario** guarda pares **clave : valor**, entre llaves. No se busca por posición, sino por clave, como en un diccionario de papel.

```python
categorias = {"casa": "sustantivo", "correr": "verbo", "bonito": "adjetivo"}
print(categorias["casa"])
categorias["rápido"] = "adjetivo"
print(categorias)
```

## 5.8 Todo junto: contar palabras

Este ejemplo combina variables, métodos, un bucle, una condición y un diccionario. Es la idea que había detrás del programa de frecuencias de la sesión 1.

```python
texto = "el gato y el perro y el ratón"
frecuencias = {}
for palabra in texto.split():
    if palabra not in frecuencias:
        frecuencias[palabra] = 1
    else:
        frecuencias[palabra] = frecuencias[palabra] + 1
print(frecuencias)
```

**Predice:** ¿qué número tendrá `"el"`? Después, explica en una celda de texto, con tus palabras, qué hace cada línea.

Cuando termines: *Borrar todas las salidas*, guarda, haz commit con el mensaje `Conceptos básicos de Python` y sincroniza.

## Puntos de comprobación

- [ ] Mi cuaderno tiene una celda de texto con mi predicción antes de cada ejemplo.
- [ ] Puedo explicar en una frase qué es una variable, una lista, un `for`, un `if` y un diccionario.
- [ ] He modificado al menos un ejemplo con palabras mías y el resultado era el que esperaba.
- [ ] Sé explicar línea a línea el ejemplo 5.8.
- [ ] `cuadernos/conceptos_basicos.ipynb` está en GitHub.

---

[← Anterior: Colab en VS Code](04-colab-en-vscode.md) · [Índice](README.md) · [Siguiente: Bibliotecas →](06-bibliotecas.md)
