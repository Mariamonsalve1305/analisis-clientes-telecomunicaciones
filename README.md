# 📊 Proyecto RappiPlus: de datos a decisiones de negocio

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es evaluar el desempeño del servicio **RappiPlus** para apoyar **decisiones de negocio basadas en datos** dentro del periodo registrado.

A través de un enfoque analítico, el proyecto busca seguir una lógica clara y progresiva:
* **Evaluar si podemos confiar en los datos** (análisis de calidad de datos en Python).
* **Analizar si el negocio es rentable** (revenue, costos y profit).
* **Entender dónde se pierden los usuarios** (funnel de conversión).
* **Evaluar si los usuarios regresan** (retención por cohortes).
* **Validar si los cambios generan impacto** (test estadístico con pruebas de hipótesis).
* **Comunicar los resultados** (dashboard en herramientas de BI).

A lo largo del proyecto, se transforman datos en insights para responder preguntas clave del negocio y proponer **recomendaciones accionables**.

---

## 💾 Datasets Utilizados
El análisis se realiza mediante la integración y el procesamiento de múltiples fuentes de información del negocio:

1. **`rappiplus_orders_raw.csv`**: Información transaccional de pedidos, precios, descuentos y revenue.
2. **`rappiplus_catalog.csv`**: Costos unitarios de productos, categorías y proveedores.
3. **`rappiplus_marketing_spend.csv`**: Inversión en marketing segmentada por canal y país.
4. **`events / users / user_activity (SQL)`**: Datos estructurados sobre el comportamiento del usuario dentro de la plataforma.
5. **`experiment_checkout_ui.csv`**: Resultados de un experimento A/B aplicado en el proceso de pago (*checkout*).

---

## 🛠️ Etapas del Análisis Realizadas

### 1. Carga y Exploración Inicial
* Importación del stack analítico esencial de Python (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `statsmodels`).
* Auditoría estructural preliminar usando métodos de inspección dimensional (`.shape`, `.head()`, `.info()`) para validar la correcta lectura en memoria de los tipos de datos primarios y verificar valores nulos en los distintos datasets.

### 2. Identificación y Diagnóstico de Calidad de Datos
* **Análisis de Ausencias y Anomalías:** Detección de registros con campos incompletos en variables categóricas (como `pais`, `dispositivo`, `fuente_referencia`, `nombre_producto`, `categoria_producto` y `canal`) y numéricas (`cantidad`, `precio_unitario`, `monto_descuento`).
* **Detección de Valores Atípicos (*Outliers* y *Sentinels*):** Localización de anomalías numéricas graves, tales como cantidades negativas y valores extremadamente altos (ej. cantidades de `20000` o `10000` en los pedidos) que distorsionan las métricas estadísticas.
* **Inconsistencias Categóricas:** Identificación de diferencias de formato y mayúsculas/minúsculas en variables geográficas (ej. `mexico`, `colombia`, `argentina` frente a sus versiones en mayúsculas).

### 3. Limpieza, Imputación y Transformación
* **Estandarización de Textos:** Normalización de la variable `pais` aplicando conversión a mayúsculas y limpieza de espacios en blanco en los datasets de órdenes y marketing.
* **Conversión de Tipos de Datos:** Transformación de columnas de fechas almacenadas como texto (*object*) a formatos de fecha temporales (`datetime64`) utilizando `pd.to_datetime()`. Conversión de variables numéricas clave a tipos enteros.
* **Tratamiento de Valores Nulos y Anomalías:** 
  * Reemplazo estratégico de valores centinela extremos en `cantidad` mediante el uso de medidas de tendencia central robustas (como la mediana).
  * Imputación de valores faltantes en variables categóricas con etiquetas descriptivas como `'NO INFORMADO'` o `'Desconocido'` para preservar la integridad de los registros sin sesgar las distribuciones analíticas.
 
### 3. Análisis del funnel de conversión con SQL
* **Analizar el recorrido del usuario**
* **Funnel completo**
* **Detectar puntos de abandono**
* **Identificación del mayor drop-off**

### 4 Análisis de retención por cohortes con SQL
* **Analizar comportamiento en el tiempo**
* **Construir cohortes**
* **Insight de retención**

### 5 Evaluación de impacto (experimentación A/B) con Python
* **Resultado del experimento**
* **Recomendación.**

### 6  Construcción del dashboard y comunicación de insights
* **Traducir análisis en visualización.**
* **Comunicar insights.**

---

## 🚀 Cómo Ejecutar el Notebook

Este entorno está configurado para ejecutarse de manera óptima utilizando **Google Colab** o un servidor **Jupyter Notebook** local.

### Opción Recomendada: Google Colab
1. Ve a [Google Colab](https://colab.research.google.com/).
2. Selecciona la pestaña **Subir / Upload** y selecciona el archivo `.ipynb` de este repositorio.
3. Los conjuntos de datos se cargan directamente mediante enlaces remotos seguros configurados en el código, por lo que no es estrictamente necesario subir archivos CSV de forma local a menos que se requiera evaluar fuentes personalizadas.
