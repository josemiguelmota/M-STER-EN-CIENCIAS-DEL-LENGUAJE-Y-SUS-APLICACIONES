# 4. Colab dentro de VS Code

**Qué es.** La extensión oficial **Colab** de Google permite abrir los cuadernos en VS Code y ejecutarlos en los ordenadores de Colab. Así tienes los cuadernos en la carpeta de tu repositorio (controlados con GitHub Desktop), con Copilot a mano, y a la vez el mismo entorno que usaréis en las clases de lingüística.

El concepto clave es el **kernel**: el «motor» que ejecuta las celdas. En VS Code puedes elegir entre dos:

| | Kernel de Colab | Kernel de Python local |
| --- | --- | --- |
| Dónde se ejecuta el código | En un ordenador de Google | En tu ordenador, si tienes Python instalado |
| Hay que instalar bibliotecas externas | Solo las que no estén disponibles | Solo las que no estén instaladas en ese entorno |
| Ve los archivos de tu carpeta | **No** | Sí |
| Datos de esta práctica | Solo ficticios o públicos | Solo ficticios o públicos |

## Pasos

1. En VS Code, ve a *Extensiones*, busca **Colab** e instala la extensión de **Google**. Si VS Code solicita la extensión *Jupyter*, instálala también.
2. Desde el explorador de `laboratorio-textos`, abre `cuadernos/primer_cuaderno.ipynb`, que descargaste en el tema anterior.
3. Arriba a la derecha pulsa **Seleccionar kernel** (*Select Kernel*) › **Colab** › crea un servidor nuevo. Inicia sesión con tu cuenta de Google en el navegador y autoriza el acceso. Los nombres exactos pueden variar según la versión de la extensión.
4. Ejecuta las celdas con el ▶ de cada una o con *Ejecutar todo* (*Run All*).
5. **¿Dónde se ejecuta mi código?** Añade una celda de código y ejecútala:

```python
import os
print(os.getcwd())
print(os.listdir())
```

`os.getcwd()` dice en qué carpeta está trabajando el código, y `os.listdir()`, qué archivos ve. Con Colab verás una carpeta del ordenador de Google (`/content`), no la tuya.

6. **Prueba temporal.** Con el kernel de Colab, ejecuta esta celda para comprobar si el entorno remoto ve el `quijote.txt` que creaste en el tema 2:

```python
from pathlib import Path

ruta = Path("datos/quijote.txt")
if not ruta.is_file():
	ruta = Path("../datos/quijote.txt")
print(ruta.is_file())
```

En una sesión nueva de Colab verás `False`: guardar un cuaderno en el repositorio no envía al kernel los demás archivos del proyecto.

7. **Opcional, si tienes Python local.** Elige *Seleccionar kernel › Python Environments*, selecciona tu intérprete y acepta instalar `ipykernel` si se solicita. Ejecuta las dos celdas de diagnóstico: si el directorio de trabajo es la raíz o `cuadernos`, la prueba mostrará `True`. En ese caso puedes leer el fragmento público con `print(ruta.read_text(encoding="utf-8"))`.
8. **Las salidas viajan dentro del cuaderno.** Con cualquiera de los kernels, crea una celda con `print("Marca de prueba ficticia")`, ejecútala y guarda. Sin hacer commit, busca la marca en *Changes* de GitHub Desktop: puede aparecer tanto en el código como en la salida. `.gitignore` no oculta el contenido de un cuaderno seguido por Git.
9. Pulsa *Borrar todas las salidas* (*Clear All Outputs*), elimina las celdas temporales de los pasos 6 a 8 y guarda. Conserva la celda que usa `os`. Revisa en *Changes* que no quede la marca, haz commit con el mensaje `Pruebo Colab en VS Code` y sincroniza.

Si no puedes conectar la extensión, continúa los temas 5 y 6 en Colab desde el navegador y descarga el cuaderno siguiendo el tema 3.

## Puntos de comprobación

- [ ] La extensión Colab de Google está instalada en VS Code.
- [ ] He ejecutado celdas con el kernel de Colab en VS Code o he usado el navegador si la extensión no está disponible.
- [ ] Puedo explicar por qué el kernel de Colab no encuentra `datos/quijote.txt`.
- [ ] He visto en GitHub Desktop que las salidas se guardan dentro del `.ipynb` y he usado *Borrar todas las salidas*.
- [ ] Sé por qué no debo pegar datos personales en celdas ni enviarlos a un entorno remoto.

---

[← Anterior: Google Colab](03-google-colab.md) · [Índice](README.md) · [Siguiente: Conceptos básicos de Python →](05-conceptos-basicos-python.md)
