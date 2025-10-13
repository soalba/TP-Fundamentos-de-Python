# TP-Fundamentos-de-Python
TP individual 
ANÁLISIS EXPLORATORIO DEL MERCADO INMOBILIARIO DE CABA (PROPERATI 2020)

DESCRIPCIÓN DEL PROYECTO
Este trabajo corresponde al proyecto integrador de la materia Fundamentos de Python. 
El objetivo fue realizar un análisis exploratorio de datos (EDA) sobre el mercado inmobiliario de la Ciudad Autónoma de Buenos Aires (CABA), utilizando el dataset público de Properati 2020.

El análisis busca responder a la siguiente pregunta central:
¿Cómo varían los precios por metro cuadrado entre los diferentes barrios y tipos de propiedad en CABA, y qué factores explican dichas diferencias?


ETAPAS DEL PROCESO

1. Definición del problema
Analicé la formación de precios en el mercado inmobiliario porteño, identificando patrones de precio por barrio, la relación entre precio, superficie y tipo de propiedad, y diferencias entre zonas del norte, centro y sur de la ciudad.

2. Preparación y limpieza de datos
Trabajé con el dataset bsas_realstate_on_sale_properati_dataset_2020.csv.
Principales pasos aplicados:
- Eliminación de duplicados.
- Reemplazo de valores nulos en superficies por la mediana (ya que es un dato que relativamente podría ser reemplazado, no como la latitud y longitud, que cuando son nulos no pueden ser reemplazados por la media).
- Creación de una variable derivada: price_m2 = price / surface_total.
- Eliminación de valores atípicos mediante el método IQR (rango intercuartílico) en precio, superficie y precio por m².

3. Exploración inicial (EDA básico)
Analicé las relaciones fundamentales entre variables.
- Dispersión entre superficie total y precio: relación positiva, aunque con alta dispersión, mostrando que el tamaño no explica completamente el precio.
- Distribución del precio por m²: sesgada a la derecha, con mayor concentración entre 1.500 y 3.000 USD/m².

Visualización: gráfico de dispersión Precio vs. Superficie Total (sin valores atípicos). 
Se puede la tendencia general ascendente, con amplia variabilidad. Esto podría marcar que más factores determinan el precio, no solamente la superficie, si bien hay una tendencia general que es ascendente.


MINERÍA DE PATRONES (MINE)

Se buscaron patrones relevantes agrupando por barrio (l3) y tipo de propiedad.

- Precio promedio por m² por barrio:
  Se filtraron los barrios con al menos 30 publicaciones para evitar sesgos. 
  Los resultados muestran una fuerte heterogeneidad espacial.
  Barrios más caros: Puerto Madero, Las Cañitas, Palermo, Recoleta y Belgrano (3.500–5.000 USD/m²).
  Barrios más baratos: Villa Lugano, José C. Paz, Villa Soldati, Florencio Varela y Merlo (800–1.500 USD/m²).

- Precio por m² según tipo de propiedad:
  En los barrios más caros, los departamentos presentan valores más altos por m², seguidos por los PH, mientras que las casas muestran precios más bajos en relación a su superficie.

- Composición de tipos de propiedad por barrio:
  Se analizó la proporción de tipos de propiedad en los ocho barrios con mayor precio promedio por m². 
  Se observa que en las zonas de mayor valor (Puerto Madero, Las Cañitas, Palermo, Recoleta y Belgrano) predominan los departamentos, mientras que las casas y PH aparecen en proporciones menores. 
  Este patrón confirma que los precios más altos por m² se asocian a propiedades de menor superficie, alta densidad y ubicación central o del corredor norte.


MATRIZ DE CORRELACIÓN

Calculé la matriz de correlación para las variables numéricas del dataset.
Los resultados muestran:
- Correlación positiva alta entre price y surface_total (0.51), indicando que el tamaño es un factor determinante del precio total.
- Correlación negativa moderada entre price_m2 y surface_total (-0.33), lo que sugiere que las propiedades más grandes suelen tener menor precio por m².
- Alta correlación entre surface_total y surface_covered (0.90), confirmando que ambas variables miden dimensiones relacionadas.
- Correlación considerable entre las habitaciones y el precio. 

Visualización: mapa de calor de correlaciones con escala de colores rojo (positiva) y azul (negativa).


CONCLUSIONES Y DESCUBRIMIENTOS

- Existe una correlación positiva entre superficie y precio total, aunque no lineal. El valor depende de la ubicación.
- El precio por metro cuadrado varía significativamente entre barrios, reflejando diferencias estructurales de densidad, nivel socioeconómico y desarrollo urbano.
- El corredor norte de la ciudad concentra los valores más altos, confirmando su posicionamiento como zona premium.
- En los barrios del sur y el conurbano cercano, los precios son hasta un 70–80% inferiores, mostrando una brecha de valor inmobiliario marcada.
- Los departamentos son el tipo de propiedad dominante y más valorizado por m² en los barrios céntricos, mientras que las casas y PH predominan en zonas periféricas.
- Los barrios con precios más altos presentan mayor densidad vertical, mientras que los más económicos muestran una mayor proporción de viviendas unifamiliares.

------------------------------------------------------------

ANÁLISIS FINAL

El análisis demuestra que el barrio y el tipo de propiedad son los factores más determinantes en el valor por m² en CABA.
Para inversores, las zonas del corredor norte (Palermo, Recoleta, Belgrano, Puerto Madero) representan mercados consolidados, de alta demanda y bajo riesgo.
En cambio, los barrios del sur y del conurbano ofrecen oportunidades de inversión con potencial de revalorización a largo plazo, aunque con menor liquidez.

TECNOLOGÍAS UTILIZADAS
- Python: pandas, matplotlib, seaborn, statsmodels
- Google Colab para procesamiento y visualización
- Dataset: Properati (2020), propiedades en venta en Buenos Aires
