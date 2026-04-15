# Historial de procesos y decisiones

## Proceso de limpieza de datos

El proceso de limpieza de la base de datos se realizó de manera manual y progresiva, con el objetivo de asegurar la consistencia, claridad y utilidad analítica de la información recolectada.

En una primera etapa, revisé la estructura general de la base y detecté inconsistencias en los nombres de las variables. Por ejemplo, algunas columnas tenían espacios o formatos distintos (como “mes/año”), por lo que decidí estandarizarlas utilizando formato snake_case (mes_año), lo que facilita su uso posterior en herramientas de análisis.

Luego, trabajé en la limpieza de los valores dentro de cada variable. En la columna de artistas, identifiqué que algunas canciones incluían múltiples nombres separados por distintos formatos (comas, “feat.”, “&”). Para mantener consistencia, decidí no separar a los artistas en distintas columnas, pero sí unificar el criterio de registro, manteniendo el nombre completo tal como aparece en Spotify, lo que permite identificar colaboraciones.

En la variable “colaboracion”, detecté que no estaba sistematizada en todos los casos, por lo que tomé la decisión de recodificarla completamente. Para esto, revisé cada fila y asigné manualmente “Sí” cuando había más de un artista involucrado y “No” cuando era un artista único. Este proceso fue clave para poder analizar patrones de colaboración en las canciones.

En cuanto a la variable “duración”, encontré que estaba en distintos formatos (minutos:segundos y en algunos casos solo números). Para evitar errores en el análisis, opté por mantener un solo formato (mm:ss), aunque reconozco que para análisis más avanzados sería recomendable convertir todo a segundos.

Otro problema importante se presentó en la variable “posición_ranking”, donde algunas entradas estaban expresadas como rangos (por ejemplo, “1-3”). En este caso, decidí mantener el dato original para no perder información, pero lo dejé documentado como una limitación, ya que dificulta ciertos análisis cuantitativos. En una versión futura, esto podría resolverse asignando un valor promedio o separando en dos variables.

También revisé la variable “género_musical”, que fue construida manualmente. Para evitar dispersión excesiva de categorías, agrupé los géneros en etiquetas más amplias (por ejemplo, reggaetón y trap dentro de “urbano”), lo que permite hacer comparaciones más claras.

Finalmente, eliminé posibles duplicados y verifiqué que no hubiera filas completamente vacías o con datos irrelevantes. Este proceso se realizó utilizando herramientas básicas como Excel/Google Sheets, particularmente funciones de ordenamiento, filtros y revisión manual.

---

## Herramientas utilizadas

- Google Sheets / Excel: para limpieza, ordenamiento y estandarización de datos  
- Funciones utilizadas:
  - Filtros
  - Ordenamiento
  - Búsqueda manual
  - Revisión visual  

El proceso fue mayoritariamente manual debido al tamaño acotado de la base, lo que permitió un mayor control sobre la calidad de los datos.

---

## Fuentes de datos utilizadas

Las principales fuentes de datos utilizadas fueron:

- Spotify Charts (Top 50 Chile)  
  https://charts.spotify.com/  

- Plataforma Spotify (información de canciones)  

Estas fuentes fueron elegidas por su alta confiabilidad y relevancia para el estudio del consumo musical contemporáneo. Spotify Charts permite acceder a rankings oficiales basados en reproducciones, lo que lo convierte en un indicador válido de popularidad. Por su parte, la plataforma Spotify permite complementar con información específica de cada canción, como duración y artistas.

Se optó por no utilizar datos de otras plataformas como TikTok o Instagram debido a la dificultad de acceso a datos sistematizados y confiables.

---

## Preguntas que se pueden responder con la base de datos

Una vez limpia la base de datos, es posible responder diversas preguntas relevantes para el análisis del fenómeno musical. A continuación, se presentan tres ejemplos:

### 1. ¿Las canciones con colaboraciones tienen mejor desempeño en el ranking?

A través de una tabla dinámica, se puede comparar la posición promedio de canciones con y sin colaboraciones, lo que permite evaluar si existe una relación entre trabajo colaborativo y éxito.

---

### 2. ¿Cuál es la duración promedio de las canciones que aparecen en el ranking?

Esto permite identificar si existe un patrón en la duración de los hits, por ejemplo, si tienden a ser más cortos para facilitar su consumo en plataformas digitales.

---

### 3. ¿Qué géneros musicales predominan en el Top 50 de Spotify Chile?

Mediante el conteo de frecuencias por género musical, se puede observar la concentración de estilos y determinar si existe una hegemonía de la música urbana en los rankings.

---

### 4. ¿Qué artistas aparecen con mayor frecuencia en el ranking?

A partir de un conteo de ocurrencias, se puede identificar si existe una concentración de éxito en ciertos artistas, lo que permitiría analizar la estructura de la industria musical local.

---

## Reflexión final

El proceso de limpieza de datos fue fundamental para transformar una base inicial heterogénea en un conjunto de datos utilizable para el análisis. Las decisiones tomadas buscaron equilibrar la fidelidad a los datos originales con la necesidad de generar una estructura coherente.

Si bien el proceso fue principalmente manual, esto permitió un mayor control sobre la calidad de los datos, aunque también implica limitaciones en términos de escalabilidad. En futuras etapas, sería posible automatizar parte del proceso para trabajar con bases más grandes.

Este trabajo de limpieza no solo mejora la calidad del análisis, sino que también asegura la transparencia y replicabilidad del proceso, aspectos clave en el periodismo de datos.
