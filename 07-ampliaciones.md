# Ampliaciones para quien termine antes

## A. Abrir en Colab un cuaderno de GitHub

En Colab, ve a *Archivo › Abrir cuaderno › GitHub*, pega la dirección de tu repositorio y abre `cuadernos/conceptos_basicos.ipynb`. Como `laboratorio-textos` es privado, necesitarás autorizar a Colab a acceder a él si tu cuenta y tu organización lo permiten. Si no puedes o prefieres no dar acceso, usa *Archivo › Subir cuaderno* y elige tu copia local. No cambies la visibilidad del repositorio para hacer esta prueba.

- [ ] He abierto en Colab el cuaderno desde GitHub o desde mi copia local.

## B. Contar palabras en el fragmento del Quijote

En Colab desde el navegador, abre el panel *Archivos* y sube `datos/quijote.txt`, el fragmento de dominio público que creaste en el [tema 2](02-carpetas-y-gitignore.md). En una celda nueva, lee el archivo de la sesión y cuenta las cinco formas más frecuentes:

```python
from collections import Counter
from pathlib import Path
import re

texto_quijote = Path("/content/quijote.txt").read_text(encoding="utf-8")
tokens_quijote = re.findall(r"[^\W\d_]+", texto_quijote.lower())
print(Counter(tokens_quijote).most_common(5))
```

Compara el resultado con `texto_quijote.split()`: ¿qué les pasa a las mayúsculas y a la puntuación? El patrón aproxima qué cuenta como palabra; no agrupa formas como `vivía` y `vivir`. Si la sesión de Colab caduca o se elimina, tendrás que subir el archivo otra vez. Nunca subas `datos_privados`.

- [ ] He contado las palabras del fragmento y puedo explicar qué cambia respecto a `split()`.

## C. Explicar el recuento sin memorizarlo

Pide a Copilot o Gemini tres preguntas sobre el ejemplo 5.8, o prepáralas con otra persona. Usa únicamente el ejemplo ficticio de la guía. No necesitas una Gema configurada anteriormente.

- [ ] Puedo contestar qué ocurre con una palabra nueva, una repetida y un texto vacío.

## D. Un reto pequeño

Modifica el ejemplo 5.4 para que reconozca también los participios terminados en *-ado* e *-ido*. Predice el resultado con tres palabras antes de ejecutarlo.

- [ ] Puedo explicar por qué la terminación sola no siempre identifica la categoría; prueba con `cantado`, `vivido` y `mercado`.

---

[← Anterior: Bibliotecas](06-bibliotecas.md) · [Índice](README.md) · [Siguiente: Comprobación final →](08-comprobacion-y-problemas.md)
