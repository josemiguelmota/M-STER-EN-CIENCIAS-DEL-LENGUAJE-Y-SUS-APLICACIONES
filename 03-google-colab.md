# 3. Cuadernos en Google Colab

**Qué es.** Un **cuaderno** (archivo `.ipynb`, también llamado *Jupyter notebook*) mezcla texto explicativo y código que se ejecuta por trozos, con el resultado justo debajo. Es el formato de los materiales que usaréis en las clases de lingüística. **Google Colab** es el servicio de Google que ejecuta cuadernos en el navegador, en ordenadores de Google, sin instalar nada. Los cuadernos se guardan en tu Google Drive, en la carpeta *Colab Notebooks*.

| Elemento | Qué es |
| --- | --- |
| Celda de texto | Explicaciones escritas en Markdown, como las que ya sabes hacer |
| Celda de código | Código de Python que se ejecuta con ▶ o con `Mayús+Intro` |
| Salida | El resultado que aparece debajo de la celda. **Se guarda dentro del archivo** |
| Entorno de ejecución | El ordenador de Google donde se ejecuta el código. Se borra al cerrar la sesión |

## Pasos

1. Entra en [colab.research.google.com](https://colab.research.google.com) con tu cuenta de Google y pulsa *Nuevo cuaderno*. No necesitas importar archivos ni abrir un repositorio en Colab.
2. Haz clic en el nombre (arriba a la izquierda) y cámbialo a `primer_cuaderno.ipynb`.
3. En la primera celda de código escribe y ejecuta estas dos líneas. La primera ejecución puede tardar unos segundos: Colab está preparando el entorno.

	```python
	# print() muestra un saludo debajo de la celda.
	print("Hola, lingüística")
	```
4. Pulsa *+ Texto* y escribe en Markdown un título (`# Mi primer cuaderno`) y una frase que explique para qué es.
5. Pulsa *+ Código* y crea dos celdas:

```python
# Guardamos la frase para usarla en la siguiente celda.
frase = "La lingüística computacional es útil"
```

```python
# len() cuenta los caracteres de la frase, incluidos los espacios.
len(frase)
```

Ejecútalas en orden. Fíjate en que la segunda muestra el resultado sin `print`: en un cuaderno, la última línea de una celda se muestra sola.

6. **El orden importa.** Ve a *Entorno de ejecución › Reiniciar sesión* y ejecuta **solo** la celda `len(frase)`. Aparece un error `NameError`: el ordenador de Google ha olvidado la variable. Ejecuta las celdas de arriba abajo y vuelve a funcionar.
7. Después de comprobar el resultado, usa *Borrar todas las salidas*. Guarda y descarga el cuaderno: *Archivo › Descargar › Descargar .ipynb*. Muévelo a `laboratorio-textos/cuadernos/primer_cuaderno.ipynb`. La copia de Drive y la del repositorio son independientes: los cambios no pasan solos de una a otra.
8. Haz commit con el mensaje `Primer cuaderno de Colab` y sincroniza. Abre `cuadernos/primer_cuaderno.ipynb` en tu repositorio privado de GitHub y comprueba que ves las celdas.

## Puntos de comprobación

- [ ] Tengo en Colab un cuaderno con una celda de texto y al menos tres de código.
- [ ] He provocado el error `NameError` y sé por qué ocurre.
- [ ] `cuadernos/primer_cuaderno.ipynb` está en mi repositorio y GitHub lo muestra con formato.
- [ ] Puedo explicar la diferencia entre una celda de texto y una de código.

---

[← Anterior: Carpetas y .gitignore](02-carpetas-y-gitignore.md) · [Índice](README.md) · [Siguiente: Colab en VS Code →](04-colab-en-vscode.md)
