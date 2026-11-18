# Comprobación final y problemas frecuentes

Antes de irte, abre tu repositorio privado `laboratorio-textos` en GitHub. Comprueba las cuatro primeras casillas en clase y completa las demás cuando termines los temas 5 y 6.

- [ ] He creado el repositorio desde cero y en GitHub veo el README que escribí.
- [ ] En GitHub veo `.gitignore` y `datos/quijote.txt`, pero no `datos_privados`.
- [ ] He creado y ejecutado `cuadernos/primer_cuaderno.ipynb` y lo veo en GitHub.
- [ ] He ejecutado el primer cuaderno en VS Code con Colab o en el navegador si la extensión no está disponible. Sé por qué un kernel remoto no ve mis archivos locales.
- [ ] En `cuadernos/conceptos_basicos.ipynb` están mis predicciones y el recuento manual del tema 5.
- [ ] En ese mismo cuaderno, `Counter` y el recuento manual coinciden, y la tabla muestra `el` con frecuencia `3`.

## Problemas frecuentes

| Problema | Causa probable | Solución |
| --- | --- | --- |
| No aparece *Push origin* | Aún no has publicado el repositorio nuevo | Después del primer commit, usa *Publish repository* y deja marcada la opción de mantenerlo privado |
| La entrevista sigue apareciendo en *Changes* | `.gitignore` está mal nombrado, no está en la raíz o Git ya sigue la entrevista | Revisa nombre y ubicación, guarda y verifica antes de hacer commit. Si ya la publicaste, avisa al profesorado |
| La carpeta `cuadernos` no aparece en GitHub | Git no sube carpetas vacías | Guarda un archivo dentro y haz commit |
| No aparece la opción Colab al seleccionar kernel | La extensión no está instalada o VS Code no se ha reiniciado | Instala la extensión Colab de Google y reinicia VS Code |
| `NameError` | Una celda anterior no se ha ejecutado o la sesión se ha reiniciado | Ejecuta las celdas en orden, de arriba abajo (*Ejecutar todo*) |
| `FileNotFoundError` con el kernel de Colab | El ordenador de Google no ve tus archivos | Usa el kernel local o sube el archivo a Colab (solo si es público) |
| No encuentro el fragmento con el kernel local | La ruta se interpreta desde el directorio de trabajo | Comprueba `os.getcwd()`: usa `datos/quijote.txt` desde la raíz o `../datos/quijote.txt` desde `cuadernos` |
| GitHub muestra una versión anterior del cuaderno | Editaste la copia de Drive, no la del repositorio | Descarga la copia actual a `cuadernos`, revisa en *Changes*, haz commit y sincroniza |
| VS Code pide instalar `ipykernel` | Es lo que necesita el kernel local | Acepta la instalación |
| `ModuleNotFoundError` | La biblioteca no está instalada en ese kernel | Instálala con `%pip install nombre` |
| `IndentationError` | La sangría no es correcta | Revisa que las líneas dentro de `if` o `for` tengan 4 espacios |
| La conexión con Colab se corta | Colab cierra las sesiones inactivas | Vuelve a seleccionar el kernel y ejecuta todo otra vez |
| He subido datos privados por error | `.gitignore` no actúa hacia atrás | No hagas más cambios y avisa al profesor: quedan en el historial |

Antes de cada entrega, borra las salidas, guarda y revisa *Changes*. No incluyas datos personales ni en el código ni en el texto del cuaderno; borrar las salidas no elimina lo que has escrito en las celdas.

---

[← Anterior: Ampliaciones](07-ampliaciones.md) · [Índice](README.md)
