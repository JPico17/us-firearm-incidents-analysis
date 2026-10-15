[README.md](https://github.com/user-attachments/files/33504338/README.md)
# Análisis exploratorio de incidentes con armas de fuego en Estados Unidos

Proyecto académico de análisis de datos desarrollado en la asignatura de Inteligencia Artificial de la Universidad Industrial de Santander (UIS). Utiliza Python para preparar datos, explorar patrones temporales y geográficos y visualizar características de los incidentes registrados en un conjunto de datos histórico.

**Tecnologías:** Python · pandas · NumPy · Matplotlib · Seaborn · Folium · Google Colab

## Objetivo

Caracterizar los incidentes contenidos en el conjunto de datos mediante estadística descriptiva, visualizaciones y un mapa de calor geográfico, con énfasis en la frecuencia de registros, la distribución de víctimas y la exploración de variables asociadas.

## Alcance

El notebook implementa análisis exploratorio de datos (EDA). No incluye entrenamiento de modelos de aprendizaje automático, predicciones ni pruebas formales de hipótesis. Aunque algunos textos del notebook mencionan análisis inferencial, esa etapa no está implementada en el código disponible.

## Flujo de trabajo

1. **Carga:** lectura del archivo `TiroteosUSA.csv` desde Google Drive.
2. **Preparación:** eliminación de columnas, tratamiento de valores faltantes, recodificación de categorías y conversión de edades y fechas.
3. **Exploración:** estadísticas descriptivas, conteos por año y estado, agrupaciones y matriz de correlación de variables numéricas.
4. **Visualización:** gráficos de líneas y barras, diagramas de caja y violín, gráficos circulares y mapa de correlaciones.
5. **Análisis geográfico:** creación de un mapa interactivo con Folium y exportación a `heatmap.html`.

## Análisis incluidos

| Componente | Contenido |
| --- | --- |
| Temporal | Número de registros por año y edad promedio por año entre registros con edad distinta de cero. |
| Geográfico | Conteos por estado extraído de `Location` y mapa de calor de coordenadas. |
| Víctimas | Distribuciones de fallecidos, heridos y víctimas; comparación visual entre categorías. |
| Variables categóricas | Exploración de tipo de objetivo, género, empleo, raza y salud mental según las etiquetas del dataset. |
| Correlaciones | Matriz de correlación entre las variables numéricas seleccionadas. |

El mapa representa concentración de registros por ubicación; no incorpora ponderación por población ni por número de víctimas.

## Datos y estado de los resultados

El notebook requiere **`TiroteosUSA.csv`**, que no está incluido en el archivo `.ipynb`. La fuente original, la licencia y los criterios de inclusión del dataset no están documentados en el notebook y deben incorporarse antes de redistribuir los datos.

Las salidas guardadas muestran:

- **691 registros y 16 columnas** en una etapa de preparación.
- **688 observaciones** en la tabla de estadísticas descriptivas.
- Fechas entre **1966 y 2017** en esa tabla descriptiva.

Estas cifras proceden de salidas almacenadas, no de una nueva ejecución. Hay indicios de ejecución fuera de orden: la tabla descriptiva ya contiene fechas convertidas y una muestra menor antes de las celdas que realizan esas operaciones. Por ello, las cifras deben confirmarse al ejecutar todo el notebook desde un entorno limpio con el CSV original.

## Archivos para el repositorio

| Archivo | Función |
| --- | --- |
| `README.md` | Documentación del proyecto. |
| `Proyecto_Final_IA.ipynb` | Notebook académico con código, explicaciones y salidas guardadas. |
| `TiroteosUSA.csv` | Entrada externa necesaria; obtener de la fuente original y verificar su licencia. |
| `heatmap.html` | Salida generada al ejecutar la última celda; no es un archivo de entrada. |

## Ejecución en Google Colab

1. Abre `Proyecto_Final_IA.ipynb` en Google Colab.
2. Obtén el CSV original y guárdalo en `Mi unidad/ProyectoIA/TiroteosUSA.csv` de tu Google Drive, o ajusta la ruta de lectura del notebook.
3. Comprueba que estén disponibles las dependencias. Si falta alguna, instala los paquetes en una celda:

   ```python
   %pip install numpy pandas matplotlib seaborn folium
   ```

4. Ejecuta la primera celda y autoriza el montaje de tu propio Google Drive.
5. Reinicia el entorno y ejecuta las celdas en orden, de principio a fin.
6. Revisa los gráficos y el archivo `heatmap.html` exportado al finalizar.

La ruta de entrada utilizada por el notebook es:

```python
df = pd.read_csv('/content/drive/MyDrive/ProyectoIA/TiroteosUSA.csv', sep=',')
```

La versión actual depende de `google.colab.drive` y `google.colab.files`. Para ejecutarla en Jupyter local deben adaptarse el montaje de Drive, la ruta del CSV y la descarga del HTML. Las versiones originales de las dependencias no están registradas; la reproducción exacta del entorno está pendiente.

## Limitaciones y mejoras identificadas

- **Valores faltantes:** algunos se sustituyen por cero y luego se eliminan filas con otros nulos. Esto puede sesgar distribuciones; un dato desconocido de empleo no equivale necesariamente a desempleo, y una edad desconocida no equivale a cero años.
- **Recodificación de género:** `M` se convierte primero a `Unclear`, por lo que la sustitución posterior de `M` por `Male` no tiene efecto. Debe corregirse el orden.
- **Edades:** sustituir comas por puntos puede interpretar incorrectamente registros con varias edades. Es necesario revisar su significado en la fuente.
- **Categorías:** la normalización de mayúsculas no unifica todas las etiquetas equivalentes; también se mezclan valores desconocidos con otras categorías.
- **Víctimas:** se usan tanto `Total victims` del CSV como una suma calculada de `Fatalities` e `Injured`. Debe aclararse la definición y comprobarse su consistencia.
- **Tamaño de muestra:** actualizar los textos y resultados tras una ejecución completa; el texto original menciona dimensiones que no coinciden con las salidas guardadas.
- **Interpretación:** los conteos describen el dataset y no tasas poblacionales ni cobertura completa de Estados Unidos. Las correlaciones y comparaciones gráficas no demuestran causalidad o significancia estadística, ni permiten atribuir riesgo individual a grupos demográficos.

## Competencias demostradas

- Manipulación y exploración de datos tabulares con pandas.
- Preparación de variables numéricas, categóricas y temporales.
- Visualización estadística con Matplotlib y Seaborn.
- Visualización geográfica interactiva con Folium.
- Documentación de un análisis en notebooks y trabajo académico colaborativo.

## Autores

- Jean Carlo Rodríguez Pico
- Juan Pablo Ávila Quitián
- Juan David Saavedra Gonzalez

**Universidad Industrial de Santander — Escuela de Ingeniería de Sistemas**  
Asignatura: Inteligencia Artificial.

## Licencia

La licencia del código debe ser definida por los autores. Los datos conservan las condiciones de uso de su fuente original, pendiente de documentar. Este README no otorga permisos de redistribución sobre el dataset.
