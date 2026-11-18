# 4. Colab dentro de VS Code

**Qué es.** La extensión oficial **Colab** de Google permite abrir los cuadernos en VS Code y ejecutarlos en los ordenadores de Colab. Así tienes los cuadernos en la carpeta de tu repositorio (controlados con GitHub Desktop), con Copilot a mano, y a la vez el mismo entorno que usaréis en las clases de lingüística.

El concepto clave es el **kernel**: el «motor» que ejecuta las celdas. En VS Code puedes elegir entre dos:

| | Kernel de Colab | Kernel de Python local |
| --- | --- | --- |
| Dónde se ejecuta el código | En un ordenador de Google | En tu ordenador (el Python de la sesión 1) |
| Hay que instalar bibliotecas | No, trae muchas ya instaladas | Sí, con `pip` |
| Ve los archivos de tu carpeta | **No** | Sí |
| Adecuado para datos privados | **No** | Sí |

## Pasos

1. En VS Code, ve a *Extensiones* (`Ctrl+Shift+X`), busca **Colab** e instala la de **Google** (con la marca de verificación azul). Se instala también la extensión *Jupyter*, que necesita.
2. Abre `cuadernos/primer_cuaderno.ipynb` desde el explorador de VS Code.
3. Arriba a la derecha pulsa **Seleccionar kernel** (*Select Kernel*) › **Colab** › crea un servidor nuevo. Inicia sesión con tu cuenta de Google en el navegador y autoriza el acceso. Los nombres exactos pueden variar según la versión de la extensión.
4. Ejecuta las celdas con el ▶ de cada una o con *Ejecutar todo* (*Run All*).
5. **¿Dónde se ejecuta mi código?** Añade una celda de código y ejecútala:

```python
import os
print(os.getcwd())
print(os.listdir())
```

`os.getcwd()` dice en qué carpeta está trabajando el código, y `os.listdir()`, qué archivos ve. Con Colab verás una carpeta del ordenador de Google (`/content`), no la tuya.

6. Añade otra celda que intente leer tu texto de dominio público. `..` significa «la carpeta de arriba», porque el cuaderno está dentro de `cuadernos`:

```python
texto = open("../datos/quijote.txt", encoding="utf-8").read()
print(texto)
```

Con el kernel de Colab da un error `FileNotFoundError`: el ordenador de Google no ve los archivos de tu ordenador.

7. Cambia de kernel: **Seleccionar kernel** › *Python Environments* › elige tu Python. Si VS Code te propone instalar `ipykernel`, acepta. Vuelve a ejecutar las dos celdas: ahora ves tu carpeta y el texto se lee sin problemas.
8. Pide ayuda a Copilot: abre el chat y pregunta «Explícame qué hace esta celda» sobre cualquiera de las anteriores.
9. **Las salidas viajan dentro del cuaderno.** Con el kernel local, añade una celda que lea y muestre `../datos_privados/entrevista_01.txt` y ejecútala. Guarda y mira en GitHub Desktop: en el cambio de `primer_cuaderno.ipynb` aparece el texto de la entrevista. Aunque `datos_privados` esté en el `.gitignore`, **lo que muestras en pantalla se guarda en el cuaderno y se subiría con él.**
10. Pulsa **Borrar todas las salidas** (*Clear All Outputs*) en la barra superior del cuaderno y guarda. En GitHub Desktop, el texto de la entrevista ha desaparecido del cambio.
11. Borra también la celda de la entrevista, haz commit con el mensaje `Pruebo Colab en VS Code` y sincroniza.

## Puntos de comprobación

- [ ] La extensión Colab de Google está instalada en VS Code.
- [ ] He ejecutado celdas con el kernel de Colab y con el kernel local.
- [ ] Puedo explicar por qué el kernel de Colab no encuentra `datos/quijote.txt`.
- [ ] He visto en GitHub Desktop que las salidas se guardan dentro del `.ipynb` y he usado *Borrar todas las salidas*.
- [ ] Sé qué kernel usar si trabajo con datos privados.

---

[← Anterior: Google Colab](03-google-colab.md) · [Índice](README.md) · [Siguiente: Conceptos básicos de Python →](05-conceptos-basicos-python.md)
