# BASE DE DATOS
## ZENODO
https://zenodo.org/records/4778563

### Autor y publicación de los datos: 
* Los autores son Gabriel P. Oliveira, Mariana O. Silva, Danilo B. Seufitelli, Anisio Lacerda y Mirella M. Moro. La base de datos fue publicada originalmente en Zenodo para complementar un artículo presentado en la 21ª Conferencia de la Sociedad Internacional para la Recuperación de Información Musical (ISMIR 2020).

### Contenido: 
Es un conjunto de datos sobre géneros musicales y colaboraciones basado en el éxito comercial. 
Incluye:
* __Gráficos__: Top 200 semanal de Spotify por país.
* __Artistas__: Información sobre artistas presentes en las listas y sus colaboradores.
* __Datos de canciones__: Datos y características de las canciones que llegaron a las listas.
* __Redes de Colaboración__: Mapeos de cómo colaboran los artistas y cómo se entrelazan los géneros (redes de géneros y redes de artistas).
* __Mapeo de Géneros__: Una traducción de los micro-géneros de Spotify a "super-géneros" más amplios.
* __Variables__: ncluye nombres de artistas, IDs de Spotify, géneros musicales, métricas de éxito en listas (posiciones), y conexiones de colaboración (quién grabó con quién).
* __Periodo__: Los datos cubren desde enero de 2017 hasta diciembre de 2019.

### Pertinencia: 
* Esta base es valiosa porque no solo lista canciones exitosas, sino que __analiza la interconectividad__. Permite entender cómo los géneros musicales se mezclan para crear éxitos y cómo las redes de colaboración profesional influyen en la industria.
* Permite visualizar la _evolución de los géneros dominantes_ antes de la pandemia.
* Sirve para identificar quiénes son los "nodos" centrales (artistas con más poder de colaboración) en la industria musical global y regional.
* Ayuda a sustentar historias sobre la globalización de la música, comparando mercados (el dataset incluye datos de EE. UU., Japón, Reino Unido, Alemania, Francia, Canadá, Australia y Brasil).

### Metodología: 
Los datos fueron recolectados utilizando la API de Spotify. Los autores extrajeron las listas semanales de los "Top 200" de los mercados más importantes definidos por la IFPI (Federación Internacional de la Industria Fonográfica).

Instrumentos:
* Se utilizaron scripts para recolectar datos de las listas de éxitos.
* Se empleó una metodología de Análisis de Redes Complejas para construir los archivos de "Genre Networks" y "Artist Networks".
* Para el mapeo de géneros, los autores crearon un sistema para agrupar los miles de nichos que usa Spotify en categorías más manejables para el análisis estadístico.

