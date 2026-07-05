# Renderizar Markdown a Documento Word

Porque la herramienta interna de JetBrains no ayuda para nada y necesita demasiada configuración.

## Dependencias:

- Pandoc (https://pandoc.org/)

## Instrucciones:

### A. Usando la terminal

En la terminal, teniendo Pandoc instalado y en el mismo directorio que el archivo MD a renderizar, ejecutar:

```
pandoc README.md -o <nombre>.docx --from markdown+raw_html --lua-filter ./tables.lua
```

En donde `<nombre>` es el nombre del archivo MD a renderizar, igualmente con el DOCX renderizado.

En el mismo directorio, se debería crear un archivo con el mismo nombre que el MD con extensión .docx, el cual es el documento Word renderizado.

### B. Usando External Tools de JetBrains

Esta opción es para renderizar más rápido sin necesidad de una terminal.

1. Ir a `File > Settings > Tools > External Tools` y hacer click en el botón `+` para agregar una nueva herramienta externa.
2. Nombrar la herramienta y agregar una descripción a preferencia.
3. Especificar la configuración de herramienta como se muestran:

    - **Program:** (Windows)`%APPDATA%\pandoc`, (Linux)`/usr/bin/pandoc`, (MacOS)`/usr/local/bin/pandoc`, o el directorio donde se instaló el programa.
    - **Arguments:** `$FileName$ -o $FileNameWithoutExtension$.docx --from markdown+raw_html --lua-filter ./tables.lua`
    - **Working directory:** `$ProjectFileDir$`
4. Hacer click en `OK` para guardar la configuración.

Cuando se desee renderizar un archivo MD a DOCX, hacer click derecho sobre el archivo y seleccionar `External Tools > <nombre de la herramienta>` para ejecutar la herramienta y generar el documento Word en el mismo directorio.