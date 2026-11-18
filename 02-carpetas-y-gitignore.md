# 2. Organizar el proyecto: carpetas y `.gitignore`

Abre el repositorio que creaste en el [tema 1](01-github-desktop-y-vscode.md). De momento solo necesitas el README. Ahora crearás esta estructura:

```text
laboratorio-textos/
├── .gitignore        reglas para archivos que Git no debe incorporar
├── README.md         presentación del proyecto
├── cuadernos/        cuadernos de Colab (.ipynb)
├── datos/            textos que SÍ se pueden publicar
└── datos_privados/   carpeta local; en esta práctica solo contiene material ficticio
```

El archivo **`.gitignore`** indica a Git qué archivos sin seguimiento debe ignorar. No protege copias, salidas de cuadernos ni archivos que Git ya sigue. Se llama exactamente `.gitignore`: empieza por un punto y no lleva extensión.

## Pasos

1. En VS Code (abierto desde GitHub Desktop), crea las carpetas `cuadernos`, `datos` y `datos_privados` con el icono *Nueva carpeta* del explorador.
2. Dentro de `datos`, crea `quijote.txt` con este texto de dominio público:

```text
En un lugar de la Mancha, de cuyo nombre no quiero acordarme, no ha mucho tiempo
que vivía un hidalgo de los de lanza en astillero, adarga antigua, rocín flaco y
galgo corredor.
```

3. Dentro de `datos_privados`, crea `entrevista_01.txt` con esta entrevista ficticia:

```text
ENTREVISTADORA: ¿Dónde se crio usted?
CARMEN RUIZ: Yo me crie en el barrio de Santa María, en Cádiz, con mi abuela Dolores.
Mi hermano Antonio y yo íbamos juntos al colegio de la calle Sopranis.
ENTREVISTADORA: ¿Y cómo se hablaba en su casa?
CARMEN RUIZ: Mi abuela Dolores decía mucho «quillo» y «miarma». Antonio todavía lo dice.
```

4. Mira GitHub Desktop, pestaña *Changes*: aparecen los dos archivos. **No hagas commit todavía.**
5. En la carpeta principal del repositorio (no dentro de otra carpeta), crea un archivo llamado `.gitignore` y escribe:

```text
# Datos personales: nunca se suben
datos_privados/

# Claves y contraseñas
.env

# Archivos que crean Python, los cuadernos y el sistema
__pycache__/
.ipynb_checkpoints/
.venv/
.DS_Store
Thumbs.db
```

6. Guarda y vuelve a GitHub Desktop: **la entrevista ha desaparecido** de *Changes*, mientras que `quijote.txt` y `.gitignore` siguen ahí. Revisa la lista antes de hacer commit. No subas archivos arrastrándolos a la web de GitHub: esa vía no aplica el `.gitignore` de tu copia local.
7. Haz commit con el mensaje `Organizo carpetas y añado .gitignore` y sincroniza.
8. Abre tu repositorio en la web de GitHub y comprueba qué se ve y qué no.

## Dos cosas que conviene saber

- **Git no sube carpetas vacías.** La carpeta `cuadernos` no aparecerá en GitHub hasta que guardes un cuaderno dentro (lo harás en el [tema 3](03-google-colab.md)).
- **`.gitignore` no actúa hacia atrás.** Si un archivo ya se subió antes de añadirlo a la lista, sigue en GitHub y en su historial. Si alguna vez subes algo privado por error, avisa al profesor: borrarlo no basta.

GitHub Desktop también permite gestionar la lista: clic derecho sobre un archivo en *Changes* › *Ignore folder (add to .gitignore)*, o *Repository › Repository settings › Ignored files*.

## Puntos de comprobación

- [ ] Mi repositorio tiene las carpetas `cuadernos`, `datos` y `datos_privados` en mi ordenador.
- [ ] La pestaña *Changes* de GitHub Desktop no muestra `entrevista_01.txt`.
- [ ] En la web de GitHub se ven `.gitignore` y `datos/quijote.txt`, pero **no** `datos_privados`.
- [ ] Puedo explicar por qué arrastrar archivos a la web de GitHub se salta el `.gitignore`.
- [ ] Puedo explicar qué pasa si añado algo al `.gitignore` después de haberlo subido.

---

[← Anterior: GitHub Desktop y VS Code](01-github-desktop-y-vscode.md) · [Índice](README.md) · [Siguiente: Google Colab →](03-google-colab.md)
