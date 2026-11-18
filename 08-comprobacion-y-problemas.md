# Comprobación final y problemas frecuentes

Antes de irte, abre tu repositorio en la web de GitHub y repasa esta lista. Las cuatro primeras casillas son lo imprescindible.

- [ ] 1\. Escribo en VS Code y subo los cambios con GitHub Desktop (commit y push).
- [ ] 2\. Mi repositorio tiene `cuadernos`, `datos` y `.gitignore`, y no tiene `datos_privados`.
- [ ] 3\. Sé crear y ejecutar un cuaderno en Colab y guardarlo en mi repositorio.
- [ ] 4\. Ejecuto cuadernos en VS Code con el kernel de Colab y con el local, y sé cuándo usar cada uno.
- [ ] 5\. Entiendo los ejemplos de Python del tema 5 y sé explicar el 5.8.
- [ ] 6\. Sé qué es una biblioteca, cómo se importa y cómo se instala.

## Problemas frecuentes

| Problema | Causa probable | Solución |
| --- | --- | --- |
| La entrevista sigue apareciendo en *Changes* | El archivo se llama `.gitignore.txt`, no está en la carpeta principal o no se ha guardado | Revisa el nombre exacto y la ubicación, y guarda con `Ctrl+S` |
| La carpeta `cuadernos` no aparece en GitHub | Git no sube carpetas vacías | Guarda un archivo dentro y haz commit |
| No aparece la opción Colab al seleccionar kernel | La extensión no está instalada o VS Code no se ha reiniciado | Instala la extensión Colab de Google y reinicia VS Code |
| `NameError` | Una celda anterior no se ha ejecutado o la sesión se ha reiniciado | Ejecuta las celdas en orden, de arriba abajo (*Ejecutar todo*) |
| `FileNotFoundError` con el kernel de Colab | El ordenador de Google no ve tus archivos | Usa el kernel local o sube el archivo a Colab (solo si es público) |
| `FileNotFoundError` con el kernel local | La ruta no es correcta | El cuaderno está en `cuadernos`: usa `../datos/nombre.txt` |
| VS Code pide instalar `ipykernel` | Es lo que necesita el kernel local | Acepta la instalación |
| `ModuleNotFoundError` | La biblioteca no está instalada en ese kernel | Instálala con `%pip install nombre` |
| `IndentationError` | La sangría no es correcta | Revisa que las líneas dentro de `if` o `for` tengan 4 espacios |
| La conexión con Colab se corta | Colab cierra las sesiones inactivas | Vuelve a seleccionar el kernel y ejecuta todo otra vez |
| He subido datos privados por error | `.gitignore` no actúa hacia atrás | No hagas más cambios y avisa al profesor: quedan en el historial |

Recuerda: lo que muestras en un cuaderno se guarda dentro de él. Antes de cada commit, *Borrar todas las salidas* si has trabajado con datos que no deben publicarse.

---

[← Anterior: Ampliaciones](07-ampliaciones.md) · [Índice](README.md)
