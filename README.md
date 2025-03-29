# Climate Data Analysis with NASA POWER API and BigQuery

Este proyecto combina datos climáticos obtenidos de la API de NASA POWER y datos históricos de BigQuery para realizar un análisis completo del clima en el año 2024.

## Descripción del proyecto

El proyecto realiza las siguientes tareas:

1. **Consulta a la API de NASA POWER:**
   - Obtiene datos climáticos horarios para un rango de fechas específico (en este caso, todo el año 2024).
   - Los datos incluyen temperatura, humedad relativa, velocidad y dirección del viento, precipitación, nubosidad y más.

2. **Consulta a BigQuery:**
   - Extrae datos históricos de la tabla pública `bigquery-public-data.noaa_gsod.gsod2024` para el año 2024.
   - Los datos incluyen información meteorológica global, como temperatura, precipitación y presión atmosférica.

3. **Procesamiento de datos:**
   - Convierte los datos obtenidos de ambas fuentes en DataFrames de pandas para análisis.
   - Combina y analiza los datos para identificar patrones y tendencias.

4. **Exportación de datos:**
   - Guarda los datos procesados en un archivo CSV para análisis local.
   - Los datos también pueden ser cargados en una tabla de BigQuery para análisis avanzado.

## Requisitos previos

Antes de ejecutar este proyecto, asegúrate de tener instalados los siguientes programas y bibliotecas:

- **Python 3.8 o superior**
- **Bibliotecas de Python:**
  - `requests`
  - `pandas`
  - `google-cloud-bigquery`

Puedes instalar las dependencias ejecutando:

```bash
pip install requests pandas google-cloud-bigquery

Además, asegúrate de tener configurado el SDK de Google Cloud y autenticado con una cuenta que tenga acceso a BigQuery. Puedes autenticarte ejecutando:
gcloud auth application-default login

Cómo ejecutar el proyecto:
Clona el repositorio ejecutando:
git clone https://github.com/JosElias23/Climate-change-analysis.git
Navega al directorio del proyecto:
cd Climate-change-analysis
Ejecuta el script en Python:
python mineria_S1.ipynb

Resultados esperados:

Los datos de la API de NASA POWER y BigQuery se combinarán en un DataFrame.
Se generará un archivo CSV con los datos procesados.

Configuración de BigQuery
El script utiliza la tabla pública bigquery-public-data.noaa_gsod.gsod2024 para obtener datos meteorológicos históricos. Asegúrate de que:

Tienes un proyecto de Google Cloud configurado.

Estás autenticado con una cuenta que tiene acceso a BigQuery.

El script está configurado correctamente para ejecutar la consulta SQL:
query = """
SELECT *  # Selecciona todas las columnas
FROM `bigquery-public-data.noaa_gsod.gsod2024`  # Tabla completa
WHERE date BETWEEN '2024-01-01' AND '2024-12-31'
"""

El resultado de esta consulta se convierte en un DataFrame de pandas para análisis.

Resultados clave
Archivo CSV: Los datos combinados se guardan en un archivo CSV para análisis local.
BigQuery: Los datos procesados pueden ser cargados nuevamente en BigQuery para análisis avanzado.
Manejo de errores
Si la solicitud a la API de NASA POWER falla, el script mostrará un mensaje de error con el código de estado HTTP y el contenido de la respuesta.
Si ocurre un error al ejecutar la consulta en BigQuery, se mostrará un mensaje detallado en la consola.
Contribuciones
Si deseas contribuir a este proyecto, por favor sigue estos pasos:

Haz un fork del repositorio.

Crea una nueva rama para tus cambios:

