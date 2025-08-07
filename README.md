Análisis y Predicción de Cancelación de Clientes (Churn) en TelecomX

Objetivo del Proyecto

Este proyecto tiene como finalidad analizar en profundidad los factores que influyen en la cancelación de clientes (Churn) dentro de la empresa de telecomunicaciones TelecomX. Además, se busca desarrollar modelos de predicción que permitan identificar con anticipación a aquellos usuarios con alta probabilidad de abandonar el servicio. Esto permitirá que TelecomX implemente estrategias de fidelización más efectivas, enfocando sus esfuerzos y recursos en retener a los clientes de mayor riesgo.

Estructura del Proyecto y Organización de Archivos
La organización del proyecto se ha estructurado de la siguiente manera:


[Nombre del Cuaderno Principal].ipynb: Es el cuaderno base en Google Colab donde se concentra todo el análisis, desde la exploración inicial hasta el desarrollo y evaluación de los modelos predictivos.

/tmp/df_telecom_processed.csv: Archivo que contiene los datos ya limpios y transformados, listos para ser utilizados en la fase de modelado.

Carpeta de Visualizaciones (opcional): Si se generan gráficos o imágenes, se recomienda almacenarlos en una carpeta específica (por ejemplo, visualizaciones/) para facilitar su gestión.


Parte 1: Análisis Exploratorio y Limpieza de Datos

En la fase inicial del análisis:

* Se realizó la carga de datos desde una API.

* Se trató la estructura anidada de algunas columnas, normalizándolas para simplificar el DataFrame.

* Se gestionaron valores atípicos o inconsistentes (como campos vacíos en Charges.Total) y se tipificaron correctamente los datos.

* Se eliminaron registros duplicados y se revisaron los valores nulos.

* Finalmente, se efectuó un análisis exploratorio (EDA) utilizando visualizaciones para conocer mejor la distribución del churn y otros patrones significativos en las variables.

Parte 2: Preparación de Datos para el Modelado


Esta sección se centra en dejar los datos en condiciones óptimas para ser utilizados por algoritmos de aprendizaje automático:

1. Selección de Variables: Se excluyeron columnas irrelevantes como customerID y se conservaron aquellas que aportan valor predictivo.

2. Clasificación de Variables:

3. Numéricas: como tenure, Charges.Monthly, Charges.Total, entre otras.

4. Categóricas: como gender, Partner, Contract, PaymentMethod, etc.

5. Conversión de la Variable Objetivo (Churn): Se transformó a formato binario (0 = No, 1 = Yes) para facilitar su uso en modelos de clasificación.

6. Codificación de Variables Categóricas: Se aplicó One-Hot Encoding para convertir las variables categóricas en variables dummy. Se evitó la multicolinealidad eliminando una categoría por variable (drop_first=True).

7. Normalización de Datos Numéricos: Se utilizó MinMaxScaler para escalar las variables numéricas entre 0 y 1. Aunque no todos los modelos requieren este paso, mejora la compatibilidad con algoritmos sensibles a la escala.

8. División del Dataset: Se separó el conjunto en entrenamiento (80%) y prueba (20%) mediante train_test_split, asegurando estratificación para mantener la proporción de churn en ambos subconjuntos.

Justificación de los Modelos Elegidos

Para la predicción de churn se emplearon dos algoritmos:

* K-Nearest Neighbors (KNN): Modelo simple y efectivo como punto de partida. Es sensible a la escala, por lo cual se aplicó normalización.

* Random Forest: Modelo más robusto y eficaz, ideal para problemas complejos de clasificación. No depende de la escala de los datos y ofrece buen rendimiento general.

Las métricas utilizadas para evaluar el desempeño incluyen: Exactitud, Precisión, Recall y F1-score, con énfasis en la detección correcta de los casos de churn (clase minoritaria). Se empleó también la matriz de confusión para observar los errores tipo I y tipo II (falsos positivos y falsos negativos).

Variables Clave en la Predicción

A partir de la correlación entre variables y la interpretación de los modelos entrenados, se destacan las siguientes variables como más relevantes:

* Tenure (antigüedad del cliente): Alta correlación negativa con el churn; cuanto mayor es la antigüedad, menor la probabilidad de cancelación.

* Tipo de contrato: Los contratos mensuales tienen tasas de cancelación mucho mayores en comparación con contratos anuales o bianuales.

* Servicio de Internet (fibra óptica): Los clientes con este servicio presentan una mayor tendencia a cancelar, lo que puede reflejar insatisfacción.

* Método de pago: Se detecta una relación directa entre el uso de "Cheque electrónico" y el aumento de churn.

* Facturación electrónica: También se asocia, aunque levemente, con una mayor probabilidad de cancelación.

Cargos mensuales elevados: Están relacionados con una mayor propensión a abandonar el servicio.

En cambio, variables como el género, la presencia de servicio telefónico y algunos servicios adicionales tienen un impacto limitado en la predicción del churn.

Visualizaciones e Insights Clave del EDA

Durante el análisis exploratorio se identificaron varios patrones relevantes:

* Distribución del churn: Un gráfico de barras mostró que aunque la mayoría de los clientes permanecen, existe un segmento importante que se retira.

* Tipo de contrato vs churn: Clientes con contratos mensuales mostraron tasas de cancelación considerablemente más altas.

* Relación entre cargos totales y churn: Mediante un boxplot se observó que los clientes que cancelan suelen tener menores cargos acumulados, lo que refleja su corta permanencia.

* Mapa de calor: Resaltó la correlación negativa de tenure y contratos largos con el churn, y la correlación positiva con métodos de pago como el cheque electrónico.

Conclusiones y Estrategias de Retención

Principales Factores de Cancelación

* Baja antigüedad del cliente.

* Contratos de corta duración.

* Servicio de internet por fibra óptica (posibles problemas).

* Falta de servicios adicionales (como seguridad, soporte técnico, respaldo).

* Pago mediante cheque electrónico.

* Cargos mensuales elevados.

* Preferencia por facturación electrónica.

Recomendaciones para Reducir el Churn

1.Programa de bienvenida y fidelización temprana: Enfocado en los primeros meses del cliente.

2.Fomentar contratos a largo plazo: A través de beneficios exclusivos y descuentos.

3.Revisión del servicio de fibra óptica: Identificar y resolver los problemas que impulsan la cancelación.

4.Ofertas combinadas de servicios adicionales: Paquetes que agreguen valor (seguridad, soporte, backup).

5.Análisis del método de pago: Comprender por qué quienes usan cheque electrónico tienden a cancelar.

6.Segmentación por costos mensuales: Evaluar si los clientes con altos cargos perciben suficiente valor.

7.Campañas personalizadas con modelos predictivos: Aplicar los resultados del modelo para actuar de forma proactiva.

Cómo Ejecutar el Proyecto

1.Abrir en Google Colab el archivo .ipynb.

2.Verificar bibliotecas: Instalar o confirmar que están disponibles (pandas, sklearn, seaborn, etc.). Colab ya tiene la mayoría preinstaladas.


