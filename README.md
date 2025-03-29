# Análisis de Datos Climáticos: BigQuery y NASA POWER API

Este proyecto analiza datos climáticos históricos y en tiempo real utilizando BigQuery y la API pública de NASA POWER. A continuación, se describen las etapas principales del proyecto y los hallazgos obtenidos.

## 1. Exploración de Datos

### Fuentes de Datos
- **BigQuery**: Dataset público `bigquery-public-data.noaa_gsod.gsod2024` para datos históricos de temperaturas globales.
- **NASA POWER API**: Datos meteorológicos horarios para una ubicación específica (Latitud: 40°N, Longitud: 100°W).

### Datos Extraídos
- **BigQuery**: Datos de temperaturas globales para el año 2024.
- **NASA POWER**: Datos meteorológicos horarios, incluyendo temperatura, humedad, velocidad del viento, entre otros.

---

## 2. Limpieza y Transformación de Datos

### Procesos Realizados
- **BigQuery**:
  - Eliminación de columnas irrelevantes.
  - Renombrado de columnas para mayor claridad.
  - Conversión de fechas al formato `datetime`.
  - Conversión de temperaturas de Fahrenheit a Celsius.
  - Ordenamiento de datos por fecha.

- **NASA POWER**:
  - Conversión del índice a formato `datetime`.
  - Normalización de datos para alinearlos con el formato de BigQuery.
  - Unión de ambos datasets utilizando la columna de fechas.

### Filtros Aplicados
- Período de estudio: Año 2024.
- Ubicación específica: Latitud 40°N, Longitud 100°W.

---

## 3. Visualización de Datos

Se generaron las siguientes visualizaciones utilizando **Matplotlib** y **Seaborn**:

### 3.1 Tendencia diaria de temperatura en 2024 (BigQuery)

![Tendencia diaria de temperatura](Temperartura_Diaria_2024.png)



### 3.2 Matriz de correlación de variables meteorológicas (BigQuery)

![Matriz de correlación BigQuery](Matriz_Correlacion_BigQuery.png)


### 3.3 Temperatura vs Tiempo (NASA POWER)

![Temperatura vs Tiempo](Temperatura_vs_Tiempo.png)


### 3.4 Matriz de correlación de variables meteorológicas (NASA POWER)

![Matriz de correlación NASA POWER](Matriz_Correlacion_NASA_POWER.png)


### 3.5 Correlaciones clave en datos meteorológicos

![Correlaciones clave](Correlaciones_Clave.png)


### 3.6 Comparación de temperaturas: NASA vs BigQuery

![Comparación de temperaturas](Comparacion_Temperaturas.png)

---

## 4. Análisis e Interpretación de Resultados

### Hallazgos Clave
- **Tendencias de Temperatura**: Aumento gradual de las temperaturas durante el año 2024.
- **Correlaciones**:
  - Fuerte correlación positiva entre temperatura y humedad específica (r = 0.78).
  - Correlación negativa entre temperatura y humedad relativa (r = -0.51).
- **Comparación de Fuentes**: Los datos de BigQuery y NASA POWER mostraron tendencias similares, validando la consistencia entre ambas fuentes.

### Conclusiones
- Los datos sugieren un aumento en las temperaturas globales, consistente con las tendencias de cambio climático.
- Las correlaciones identificadas pueden ser útiles para modelar el impacto del cambio climático en variables meteorológicas.

---

## 5. Requisitos y Ejecución

### Requisitos
El archivo `requirements.txt` incluye las librerías necesarias para ejecutar el proyecto:
```
google-cloud-bigquery
pandas
matplotlib
seaborn
requests
numpy
```

### Ejecución
1. Clonar el repositorio.
2. Instalar las dependencias: `pip install -r requirements.txt`.
3. Ejecutar el archivo Jupyter Notebook para reproducir el análisis.

---

## Créditos
Este proyecto fue desarrollado como parte de un análisis de datos climáticos utilizando herramientas modernas de ciencia de datos.







//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////








# Análisis de Eventos Climáticos y Comparación de Temperaturas

Este proyecto utiliza datos meteorológicos públicos de NOAA GSOD para analizar eventos climáticos y comparar temperaturas promedio diarias entre los años 2020 y 2024. El análisis incluye la limpieza de datos, el conteo de eventos climáticos, y la visualización de tendencias de temperatura y ocurrencias de eventos.

## Requisitos Previos

- **Python 3.7+**
- **Bibliotecas necesarias**:
  - `google-cloud-bigquery`
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `calendar`

## Configuración

1. **Google Cloud SDK**: Configura el SDK de Google Cloud y autentica tu cliente para acceder a BigQuery.
2. **Dependencias**: Instala las bibliotecas necesarias ejecutando:
   ```bash
   pip install google-cloud-bigquery pandas matplotlib seaborn
   ```

## Funcionalidades

### 1. Extracción de Datos
El código utiliza BigQuery para extraer datos meteorológicos de un año específico. Puedes cambiar el año modificando la variable `year` en el código.

### 2. Limpieza de Datos
Se eliminan columnas innecesarias y se convierten las fechas al formato adecuado. Además, se filtran filas con datos inválidos.

### 3. Análisis de Eventos Climáticos
- Se cuentan las ocurrencias de eventos como niebla, lluvia, nieve, granizo, tormentas eléctricas, y tornados.
- Los resultados se presentan en un DataFrame y en un gráfico de barras mensual.

### 4. Comparación de Temperaturas
- Se generan gráficos de líneas para comparar las temperaturas promedio diarias entre los años 2020 y 2024.
- Cada gráfico incluye una línea de referencia con la temperatura promedio anual.

## Uso

1. **Ejecutar el Notebook**:
   - Abre el archivo `.ipynb` en Jupyter Notebook o Google Colab.
   - Ejecuta las celdas en orden para realizar el análisis.

2. **Modificar el Año**:
   - Cambia la variable `year` para analizar un año diferente.

3. **Visualización**:
   - Los gráficos generados muestran tendencias de temperatura y ocurrencias de eventos climáticos.

## Resultados Esperados

- **Gráficos de Temperatura**: Comparación visual de las temperaturas promedio diarias para cada año.
- **Resumen de Eventos Climáticos**: Tabla y gráfico que muestran la cantidad de ocurrencias por tipo de evento y mes.

## Ejemplo de Salida

### Resumen de Eventos Climáticos
| Evento                  | Ocurrencia | Porcentaje |
|-------------------------|------------|------------|
| Fog                    | 120        | 10.5%      |
| Rain Drizzle           | 85         | 7.4%       |
| Snow Ice Pellets       | 30         | 2.6%       |

### Gráfico de Temperatura
![Ejemplo de Gráfico](https://via.placeholder.com/800x400?text=Gráfico+de+Temperatura)

## Notas

- Asegúrate de reiniciar el kernel si cambias el año para evitar errores de caché.
- Los datos extraídos están limitados a las columnas necesarias para optimizar el rendimiento.
