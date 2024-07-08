# Manejo del Entorno Conda `moena`

Este documento proporciona instrucciones detalladas sobre cómo manejar el entorno Conda para el proyecto `moena`.


## Crear Entorno a Partir de Archivo

Replicar el entorno en otra máquina o restaurarlo más tarde, puedes crear un nuevo entorno directamente desde el archivo YAML exportado:

```bash
# Crea un nuevo entorno a partir del archivo YAML
conda env create -f moena.yml
```

## Activar el Entorno  

Para trabajar dentro del entorno, activar con:

```bash
# Activa el entorno
conda activate moena
```

## Actualizar el Entorno

Para actualizar el entorno `moena` después de realizar cambios en el archivo YAML (como añadir o eliminar paquetes), usar el siguiente comando para asegurar que el entorno se sincronice correctamente con el archivo:

```bash
# Actualiza el entorno según el archivo YAML, y elimina paquetes que ya no se necesiten
conda activate moena
conda env update -f moena.yml --prune
```

