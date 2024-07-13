
# Optimización de Procesamiento de GeoJSON para Torres Eléctricas

Este repositorio contiene un proyecto optimizado que originalmente tomaba más de una hora para ejecutarse y ahora se ejecuta en segundos. La optimización se realizó utilizando diversas técnicas y bibliotecas, detalladas a continuación.

## Optimización del Código

Para lograr esta significativa mejora en el rendimiento, se implementaron las siguientes optimizaciones:

1. **Uso de Multiprocessing**:
   - Se utilizó la biblioteca `multiprocessing` para paralelizar el procesamiento de las características. Esto permite aprovechar múltiples núcleos de la CPU, reduciendo drásticamente el tiempo de procesamiento.

2. **Índice Espacial con R-tree**:
   - Se utilizó la biblioteca `rtree` para crear un índice espacial que optimiza la búsqueda de elementos cercanos. El uso de R-tree mejora significativamente la eficiencia en comparación con la búsqueda lineal tradicional.

3. **Procesamiento Asíncrono**:
   - La función `process_feature` se procesó de manera asíncrona utilizando el método `pool.imap`, lo que permite manejar grandes volúmenes de datos de manera más eficiente.

4. **Barra de Progreso**:
   - Se integró `tqdm` para proporcionar una barra de progreso durante el procesamiento, lo que mejora la experiencia del usuario al mostrar el progreso en tiempo real.

## Estructura del Proyecto

- `TORRES_FINAL_PRUEBA.geojson`: Archivo GeoJSON con las características originales.
- `TORRES_500KV_19S_PRUEBA_CODIGO.geojson`: Archivo GeoJSON con las características que se utilizarán para actualizar `TORRES_FINAL_PRUEBA.geojson`.
- `moenardo.py`: Script principal que realiza las actualizaciones optimizadas.

## Instalación

Para ejecutar el proyecto localmente, sigue estos pasos:

1. Clona el repositorio:
   ```bash
   git clone https://github.com/ignacioalbornoz/moenardo.git
   cd moenardo
   ```

2. Crea un entorno Conda a partir del archivo YAML:
   ```bash
   conda env create -f moena.yml
   ```

3. Activa el entorno:
   ```bash
   conda activate moena
   ```

## Uso

1. Asegúrate de tener los archivos `TORRES_FINAL_PRUEBA.geojson` y `TORRES_500KV_19S_PRUEBA_CODIGO.geojson` en el directorio del proyecto.

2. Ejecuta el script principal:
   ```bash
   python moenardo.py
   ```

3. El script procesará los archivos y generará un archivo de salida `TORRES_FINAL_PRUEBA_ACTUALIZADO.geojson` con las propiedades actualizadas.

## Resultados

- **Tiempo de Ejecución Original**: Aproximadamente 1 hora
- **Tiempo de Ejecución Optimizado**: 3 Segundos

La optimización se logró mediante el uso de técnicas avanzadas de procesamiento paralelo y estructuras de datos eficientes.

## Manejo del Entorno Conda `moena`

Este documento proporciona instrucciones detalladas sobre cómo manejar el entorno Conda para el proyecto `moena`.

### Crear Entorno a Partir de Archivo

Para replicar el entorno en otra máquina o restaurarlo más tarde, puedes crear un nuevo entorno directamente desde el archivo YAML exportado:

```bash
# Crea un nuevo entorno a partir del archivo YAML
conda env create -f moena.yml
```

### Activar el Entorno

Para trabajar dentro del entorno, actívalo con:

```bash
# Activa el entorno
conda activate moena
```

### Actualizar el Entorno

Para actualizar el entorno `moena` después de realizar cambios en el archivo YAML (como añadir o eliminar paquetes), usa el siguiente comando para asegurar que el entorno se sincronice correctamente con el archivo:

```bash
# Actualiza el entorno según el archivo YAML, y elimina paquetes que ya no se necesiten
conda activate moena
conda env update -f moena.yml --prune
```
