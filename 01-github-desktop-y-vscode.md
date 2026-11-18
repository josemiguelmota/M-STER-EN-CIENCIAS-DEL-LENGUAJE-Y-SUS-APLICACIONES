# 1. Crear un repositorio con GitHub Desktop y VS Code

**Qué vamos a hacer.** Crearás tu propio repositorio sin clonar ningún proyecto. Usarás **VS Code para editar** y **GitHub Desktop para revisar los cambios, hacer commit y enviarlos a GitHub**.

| Palabra | Qué significa | Dónde está en GitHub Desktop |
| --- | --- | --- |
| Repositorio | La carpeta del proyecto, en tu ordenador y en GitHub | *Current repository*, arriba a la izquierda |
| Commit | Guardar una «foto» de los cambios con un mensaje | Botón *Commit to main*, abajo a la izquierda |
| Push | Enviar a GitHub los commits hechos en tu ordenador | Botón *Push origin*, arriba |
| Publish | Crear en GitHub la copia remota de un repositorio local nuevo | Botón *Publish repository*, arriba |

## Pasos

1. Abre GitHub Desktop y elige *File › New repository*.
2. En *Name*, escribe `laboratorio-textos`. En *Local path*, selecciona una carpeta que no sea otro repositorio, por ejemplo *Documentos*. GitHub Desktop creará dentro la carpeta `laboratorio-textos`. Deja sin marcar *Initialize this repository with a README*, selecciona *None* en *Git ignore* y *License*, y pulsa *Create repository*.
3. En GitHub Desktop, elige *Repository › Open in Visual Studio Code*. Comprueba en el explorador de VS Code que la carpeta raíz es `laboratorio-textos`.
4. Crea `README.md` en la raíz y escribe:

	```markdown
	# Laboratorio de textos

	Prácticas de análisis de textos con Python para el máster.
	```

5. Guarda con `⌘S` en macOS o `Ctrl+S` en Windows y Linux. Vuelve a GitHub Desktop y comprueba que *Changes* muestra tu README.
6. Escribe `Creo el README del laboratorio` en *Summary* y pulsa *Commit to main*.
7. Pulsa *Publish repository*, deja marcada la opción *Keep this code private* y confirma. Abre el repositorio con *Repository › View on GitHub* y comprueba que ves tu README en tu cuenta. Mantener el repositorio privado no autoriza a subir datos personales.

**A partir de aquí**, cuando los materiales digan «haz commit y sincroniza», significa: en GitHub Desktop, escribe el mensaje, pulsa *Commit to main* y después *Push origin*.

## Puntos de comprobación

- [ ] GitHub Desktop muestra `laboratorio-textos` como un repositorio que he creado yo.
- [ ] Abro el repositorio en VS Code desde GitHub Desktop.
- [ ] En mi cuenta de GitHub veo el README del repositorio privado.
- [ ] Puedo explicar con mis palabras la diferencia entre *commit* y *push*.

---

[Índice](README.md) · [Siguiente: Carpetas y .gitignore →](02-carpetas-y-gitignore.md)
