# Análisis de Datos Climáticos: NOAA Global Surface Summary of the Day y NASA POWER API

Este proyecto analiza datos climáticos históricos y en tiempo real utilizando el dataset de **NOAA Global Surface Summary of the Day** y la API pública de **NASA POWER**. A continuación, se describen las etapas principales del proyecto, los hallazgos obtenidos y las deducciones realizadas.

---

## 1. Exploración de Datos

### Fuentes de Datos
- **NOAA Global Surface Summary of the Day**: Dataset público [`NOAA Global Surface Summary of the Day`](https://console.cloud.google.com/bigquery?ws=!1m4!1m3!3m2!1sbigquery-public-data!2snoaa_gsod) para datos históricos de temperaturas globales.
- **NASA POWER API**: Datos meteorológicos horarios obtenidos de la API pública de NASA POWER. Más información disponible en [`NASA POWER`](https://power.larc.nasa.gov/).

### Datos Extraídos
- **NOAA Global Surface Summary of the Day**: Datos de temperaturas globales para el año 2024.
- **NASA POWER**: Datos meteorológicos horarios, incluyendo temperatura, humedad, velocidad del viento, entre otros.

---

## 2. Limpieza y Transformación de Datos

### Procesos Realizados
- **NOAA Global Surface Summary of the Day**:
  - Eliminación de columnas irrelevantes.
  - Renombrado de columnas para mayor claridad.
  - Conversión de fechas al formato `datetime`.
  - Conversión de temperaturas de Fahrenheit a Celsius.
  - Ordenamiento de datos por fecha.

- **NASA POWER**:
  - Conversión del índice a formato `datetime`.
  - Normalización de datos para alinearlos con el formato del dataset de NOAA.
  - Unión de ambos datasets utilizando la columna de fechas.

### Filtros Aplicados
- Período de estudio: Año 2024.
- Ubicación específica: Latitud 40°N, Longitud: 100°W.

---

### 3.1 Tendencia diaria de temperatura en 2024 (NOAA)

![Tendencia diaria de temperatura](Images/Temperartura_Diaria_2024.png)



### 3.2 Matriz de correlación de variables meteorológicas (NOAA)

![Matriz de correlación BigQuery](Images/Matriz_Correlacion_BigQuery.png)


### 3.3 Temperatura vs Tiempo (NASA POWER)

![Temperatura vs Tiempo](Images/Temperatura_vs_Tiempo.png)


### 3.4 Matriz de correlación de variables meteorológicas (NASA POWER)

![Matriz de correlación NASA POWER](Images/Matriz_Correlacion_NASA_POWER.png)


### 3.5 Correlaciones clave en datos meteorológicos

![Correlaciones clave](Images/Correlaciones_Clave.png)


### 3.6 Comparación de temperaturas: NASA vs NOAA

![Comparación de temperaturas](Images/Comparacion_Temperaturas.png)


---

## 4. Análisis de Eventos Climáticos y Comparación de Temperaturas

Este proyecto utiliza datos meteorológicos públicos de NOAA GSOD para analizar eventos climáticos y comparar temperaturas promedio diarias entre los años 2020 y 2024. El análisis incluye la limpieza de datos, el conteo de eventos climáticos, y la visualización de tendencias de temperatura y ocurrencias de eventos.

### Funcionalidades

#### 1. Extracción de Datos
El código utiliza BigQuery para extraer datos meteorológicos de un año específico. Puedes cambiar el año modificando la variable `year` en el código.

#### 2. Limpieza de Datos
Se eliminan columnas innecesarias y se convierten las fechas al formato adecuado. Además, se filtran filas con datos inválidos.

#### 3. Análisis de Eventos Climáticos
- Se cuentan las ocurrencias de eventos como niebla, lluvia, nieve, granizo, tormentas eléctricas, y tornados.
- Los resultados se presentan en un DataFrame y en un gráfico de barras mensual.

#### 4. Comparación de Temperaturas
- Se generan gráficos de líneas para comparar las temperaturas promedio diarias entre los años 2020 y 2024.
- Cada gráfico incluye una línea de referencia con la temperatura promedio anual.

---

## Resultados Esperados

### Resumen de Eventos Climáticos
| Evento                  | Ocurrencia | Porcentaje |
|-------------------------|------------|------------|
| Fog                    | 120        | 10.5%      |
| Rain Drizzle           | 85         | 7.4%       |
| Snow Ice Pellets       | 30         | 2.6%       |

### Gráficos
#### 1. Cantidad de eventos climáticos mensual 2024
![Cantidad de eventos climáticos mensual](Images/Cantidad_de_eventos_climaticos_mensual.png)

#### 2. Cantidad de eventos climáticos mensual 2023
![Cantidad de eventos climáticos mensual](Images/Cantidad_de_eventos_climaticos_mensual_2023.png)

#### 3. Cantidad de eventos climáticos mensual 2022
![Cantidad de eventos climáticos mensual](Images/Cantidad_de_eventos_climaticos_mensual_2022.png)

#### 4. Temperaturas promedio 2020-2024
![Temperaturas promedio 2020-2024](Images/Temperaturas_promedio_2020-2024.png)

---

## Análisis Detallado

### 1. **Eventos Climáticos**
El análisis de eventos climáticos incluye fenómenos como niebla, lluvia, nieve, granizo, tormentas eléctricas y tornados. Los datos se procesan para calcular la cantidad de ocurrencias de cada evento por mes y se visualizan en gráficos de barras.

#### Observaciones:
- **Frecuencia Relativa**: Algunos eventos, como la niebla, ocurren con mayor frecuencia que otros, como los tornados, que son más raros pero potencialmente más destructivos.
- **Evento más recurrente**: El fenómeno meteorológico más común es la lluvia-llovizna, probablemente influenciado por la ubicación geográfica de los datos (E.E.U.U.).
- **Cantidad de registros**: Se puede apreciar una gran cantidad de registros de cada fenómeno, lo que puede deberse a la frecuencia con la que se registraron las mediciones.

### 2. **Tendencias de Temperatura**
Se comparan las temperaturas promedio diarias de los años 2020 a 2024 mediante gráficos de líneas. Cada gráfico incluye una línea de referencia que representa la temperatura promedio anual.

#### Observaciones:
- **Variabilidad Anual**: Las temperaturas muestran fluctuaciones ligeras entre los años, lo que podría estar relacionado con el cambio climático.
- **Estacionalidad**: Se observa un patrón estacional claro, con temperaturas más altas en verano y más bajas en invierno.
- **Promedio Anual**: Aunque las temperaturas promedio anuales son relativamente estables, hay ligeras tendencias de aumento en algunos años, lo que podría ser indicativo de un cambio climático gradual.

---

## Conclusiones

1. **Impacto de los Eventos Climáticos**:
   - Los eventos climáticos tienen una distribución estacional marcada, lo que sugiere que están influenciados por factores como la ubicación geográfica y las condiciones climáticas globales.

2. **Tendencias de Temperatura**:
   - Las temperaturas promedio anuales muestran una ligera tendencia al alza, lo que podría ser consistente con los efectos del cambio climático.
   - La variabilidad estacional y anual destaca la importancia de monitorear las temperaturas a largo plazo para identificar patrones significativos.

3. **Recomendaciones**:
   - **Monitoreo Continuo**: Es crucial continuar recopilando y analizando datos meteorológicos para comprender mejor los patrones climáticos y sus implicaciones.
   - **Preparación para Eventos Extremos**: Las comunidades deben estar preparadas para eventos climáticos extremos, especialmente aquellos que son menos frecuentes pero más destructivos, como los tornados.

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

