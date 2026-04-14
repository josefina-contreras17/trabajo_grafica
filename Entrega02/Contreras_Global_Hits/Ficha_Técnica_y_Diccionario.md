
# Ficha Técnica y Diccionario
### Fuente de los datos
* Los datos primarios provinen de la API oficial de Spotify, específicamente de sus _endpoints_ de catálogo (como "tracks" y "artists") y de análisis acústico. 
* Para construir esta base de datos, se utilizaron dos bases:
    * un dataset histórico de hits globales y metadatos con registros hasta el 2019, que sirve como referencia.
    * Un dataset global reciente (dataset_seleccionado.csv) que captura los fenómenos virales de la era post-pandemia y la explosión del género urbano en Chile.

### Metodología de la construcción de la base
* La base de datos actual es el resultado de un proceso hecho a través de Google Colab de extracción, transformación de los datos, hecho específicamente para probar la hipótesis del trabajo.
* Transformación de los nombres: normalización de la columnade artistas para estandarizar las colaboraciones.
* Se crearon variables que no existían en la base original como **número de artistas** para calcular la canridad de colaboraciones y la variable **¿Es chileno? Sí/No**
* También se realizó un mapeo geográfico para iddentificar si los artistas eran Chilenos, contrarrestando el ID y nombre del artista con su nacionalidad en **spotify_artists_info.csv**, buscando etiquetas como "chilean" o "chile" y se complementó con un arreglo manual de validación para asegurar la inclusión de la escena urbana (como Cris MJ, Standly, FloyyMenor, etc).
* También se limpiaron lo registros duplicados para mentener solo la versión de mayor impacto comercial.

### Alcance de los datos.
* Alcance geográfico: aunque el análisis aísla el ffenómeno chileno, la base contiene el rendimiento de las canciones frente a competidores de todo el mundo, lo que permite medir e nivel de penetración de las exportaciones chilenas.
* Alcance global: abarca desde la era del _streaming_ temprano hasta los éxitos contemporáneos de la actualidad, cubriendo el punto de quiebre donde la música chilena se globalizó.
    
### Características de los datos.
* Es una base de datos híbrida, es decir, contiene datos cuantitativos y cualitativos.
    * _Cuantitativa_: mide métricas exactas de rendimiento (ranking de popularidad) y características del audio (duración en segundos y colaboraciones). En su versión cruda incluye métricas como _danceability_ o _energy_ calculados por el algoritmo de Spotify.
    * _Cualitativa_: Contiene variables de identificación nominal (nombre el artista, título de la obra) y clasificación categórica (nacionalidad).

### Otras observaciones que tengan sobre la base.
* Ausencia de Fechas Recientes: la base no incluye la variable *release_date*, por lo que no existe el dato de la fecha de lanzamiento. Los valores nulos en fechas se han imputado con la etiqueta de "no disponible".
* Naturaleza Dinámica de la Popularidad: La variable *popularidad* es una métrica algorítmica de Spotify que pondera reproducciones recientes vs. histórricas. Representa una "forografía" del impacto actual de la cancion en el ecosistema, no unasuma histórica estática.

### Diccionario de datos: 
* tabla con el nombre de cada variable, su descripción, tipo de dato, valores posibles y observaciones editoriales (si aplica).


| Variable  | Descripción de la variable| Tipo de dato | Variables posibles| Observaciones editoriales|
| ------------- |:----------------:|:------------|--------------|---------|
| **Nombre canción**  | Título oficial de la pista tal como aparece distribuida en plataformas.  | String (texto) | Texto libre (Ej: "BABY OTAKU") | Puede incluir la etiqueta "(feat. X)" en algunos casos, aunque las colaboraciones se aíslan en otra variable.
| **Artista**    | Intérprete(s) principal(es) de la obra.  | String (texto) | Texto libre separado por comas | Si hay más de un artista, se presentan concatenados (Ej: "Bizarrap, Quevedo"). |
| **¿Es chileno? sí/no**   | Indica si al menos uno de los artistas involucrados en la pista es de origen chileno. | Categórico | Sí/No | Creada cruzando los metadatos de género (chilean) y una lista de validación de artistas urbanos.
| **Fecha de lanzamiento**  | Fecha de publicación oficial del fonograma | Date / String | Formato YYYY-MM-DD o "No disponible" | En el dataset reciente se etiqueta como "No disponible" por carencia de datos de origen.
| **Duración**  | Extensión temporal de la canción expresada en segundos enteros | Integer (Entero) | 0 a n segundos | Originalmente extraída en milisegundos (duration_ms) y transformada/redondeada para mejor legibilidad.
| **Número de artistas** | Variable numérica calculada que indica cuántos artistas están acreditados en la pista | Integer (Entero) | 1 a n | Usada como métrica principal para probar la hipótesis del "Caballo de Troya" (Impacto del Remix).
| **Posición en ránking** | Índice logarítmico propietario de Spotify que evalúa el rendimiento actual de la canción basado en streams recientes y totales | Integer (entero) | 0 a 100 | Un valor cercano a 100 indica que la canción es un hit global en tiempo real.


https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset?resource=download
Esta es la base de datos que se utilizó, que contiene canciones de más de 125 géneros.
