## Ficha Técnica

### Fuente de los datos.
Los datos fueron extraídos de la plataforma Spotify, s través de Exportify, específicamente utilizando las métricas que provee su API (Application Programming Interface) para desarrolladores. Esto se evidencia en la presencia de identificadores únicos (Track URI) y métricas acústicas patentadas por la plataforma (como _Danceability, Energy, Valence_, entre otras).

### Metodología de la construcción de la base
La base de datos se construyó mediante la extracción estructurada de información a partir de una o varias listas de reproducción (playlists) alojadas en Spotify. El proceso metodológico consistió en recolectar 232 registros (canciones) y cruzar los metadatos básicos de cada pista (nombre, artista, álbum, año) con sus respectivos _"Audio Features"_ (análisis de la señal de audio que realiza el algoritmo de Spotify para determinar características musicales y acústicas).

### Alcance de los datos.
* __Temporalidad__: La base abarca múltiples décadas de la música chilena, incluyendo desde clásicos de los años 70 (por ejemplo, "Todos Juntos" de 1973) hasta lanzamientos contemporáneos.
* __Géneros__: Se centra en el rock chileno y sus subgéneros/derivados. Las clasificaciones de la columna **"Genres"** incluyen _latin rock, rock en español, folclor andino, stoner rock, doom metal, nueva trova, entre otros._
* __Volumen__:Contiene 232 filas (canciones) y 24 columnas (variables).
* __Geografía__: Aunque provienen de una plataforma global, la selección fue curada en torno al producto musical nacional (Chile).

### Características de los datos.
La base es de tipo estructurada, en formato tabular (CSV). Sus 24 dimensiones se dividen en tres grandes categorías de variables:
* Variables de Identificación y Metadatos (Texto/Categóricas)
    * TRACK_URI, TRACK_NAME, ALBUM_NAME, ARTIST_NAME, GENRES, RECORD LABEL.
* Variables Temporales y de Publicación (Fechas/Booleanas):
    * RELEASE_DATE, ADDED_AT, EXPLICIT
* Variables Acústicas y de Rendimiento (Numéricas continuas y discretas):
    * _Métricas de plataforma_: DURATION en (ms), POPULARITY (Índice de popularidad de 0 a 100 actual al momento de la extracción)
    * _Audio Features_(métricas sonoras de 0,0 a 1,0):  
        * DANCEABILITY bailabilidad
        * ENERGY intensidad
        * SPEECHINESS presencia de palarbas habladas
        * ACOUSTICNESS nivel acústico
        * INTRUMENTALNESS ausencia de voces
        * LIVENESS probabilidad de ser en vivo
        * VALENCE positividad.
    * _Variables musicales puras_:
        * KEY tonalidad
        * LOUDNESS volumen promedio db
        * MODE modalidad mayor(1) o menor(0)
        * TEMPO BPM
        * TIME SIGNATURE compás.

### Otras observaciones que tengan sobre la base
__Estandarización de las métricas sonoras:__ 
Es fundamental considerar, al momento de graficar o hacer cálculos (como lo de la "canción promedio"), que la mayoría de los Audio Features (Energy, Danceability, Valence, etc.) comparten una misma escala estandarizada continua entre 0.0 y 1.0. 
Sin embargo, variables como Loudness están en decibeles (valores negativos, ej: -6.5) y Tempo en BPM (ej: 114.2), por lo que si se cruzan directamente en un gráfico sin normalizar, pueden distorsionar la visualización.