# Historial de procesos y decisiones:
 
 ## Proceso de limpieza:
* El proceso de limpieza se realizó utilizando **Python** y **Google Colab**. La decisión de usar programación sobre Excel se tomó para garantizar la replicabilidad del proceso en futuras temporadas de análisis musical.
* Explicación por pasos:
1. Unificación de formatos
    1. *Decisión*: el dataset original contenía duraciones en milisegundos, por lo que decidimos transformarlos a segundos y luego a formato **MM:SS** para que los lectores de la Webstory entiendan la extensión de las canciones.
2. Tratamiento de colaboraciones
    1. En el dataset "dataset_seleccionado.csv", los artistad estaban agrupados en una sola celda separados por **;**. Decidimos crear una nueva columna llamada **Número de artistas** mediante un conteo de separadores. 
3. Identificación de la variable "nacionalidad"
    1. Las bases de Spotify no traen la nacionalidad del artista. Realizamos un cruce de datos (_Lookup_) entre el nombre del artista y un dataset maestro de géneros (*spotify_artists_info*).
    2. Dado que los datasets de 2019 no incluían el "boom" urbano chileno de 2023-2026, creamos una lista de validación manual (whitelist) que incluía términos como "urbano chileno", "trap chileno" y nombres clave (Cris MJ, Pailita, etc.) para evitar falsos negativos.
4. Depuración de duplicados:
    1. Se detectaron múltiples entradas para una misma canción debido a su presencia en diferentes géneros (ej: una canción de Bad Bunny aparecía como 'Latino' y como 'Reggaetón').
    2. Se eliminaron duplicados manteniendo únicamente el registro con el valor de Popularidad más alto.

## Fuentes de datos utilizadas
| Fuente | Razón de la elección|
|---------|--------------------|
| **Spotify Web API** | Provee métricas estandarizadas a nivel mundial, permitiendo comparar artistas chilenos bajo la misma vara que a estrellas globales como Taylor Swift o Bad Bunny |
| **Dataset_seleccionado.csv** (2022-2024) | Elegido por su actualidad. Contiene los hits del movimiento urbano chileno post-pandemia, esenciales para observar el fenómeno de exportación actual |
|**Spotify Artist Info (Metadatos)**| Fundamental para la clasificación sociológica de la base, permitiendo aislar la variable "origen" a través de los micro-géneros declarados por la plataforma | 

## Preguntas de investigación:
* Al aplicar tablas dinámicas y cruces de variables sobre la base de datos limpia de Spotify Charts, nuestro proyecto responde a la pregunta **¿Cómo se construye un hit en la música urbana chilena?** a través de las siguientes interrogantes:
1. ¿Existe un "estándar de duración" para los hits urbanos chilenos en el Top 50?
    * Análisis con la base: Al segmentar la base por *track_genre* (urbano/reggaetón/trap) y filtrar por artistas chilenos en posiciones de alta popularidad, la base de datos permite calcular el promedio de duración exacto.
    * Pregunta respondida: **¿Son los hits chilenos más cortos que el promedio global para favorecer la repetición (loop) en Spotify?** (La data sugiere una tendencia hacia los _2:40 - 2:55_ minutos).

2. ¿Es la colaboración (Feat.) un requisito estadístico para entrar al Top 50?
    * Análisis con la base: Usando una tabla dinámica que cruce la variable **Número de artistas** con la **Posición en ranking (Popularidad)**.
    * Pregunta respondida: **¿Qué porcentaje de los hits urbanos chilenos son colaboraciones múltiples vs. canciones en solitario?** Esto permite probar si el patrón de éxito chileno se basa en la "unión de fuerzas" (escena) más que en el estrellato individual.

3. ¿Qué patrones de "Danceability" y "Tempo" definen el sonido urbano chileno exitoso?
    * Analizando las variables acústicas (danceability y tempo) de las canciones chilenas que logran _superar los 80 puntos de popularidad._
    * Pregunta respondida:**¿Hay un rango de BPM (latidos por minuto) específico que el público chileno premia?** Esto visibiliza si el hit chileno prefiere ritmos acelerados (estilo guaracha/mambo) o tempos más lentos y pesados (trap/reggaetón romántico).

## Nuestra investigación no solo identifica quiénes están en el ranking, sino que disecciona la **fórmula estructural del éxito nacional**. Al analizar los patrones de duración, el volumen de colaboraciones y las características sonoras, este reportaje visualiza la arquitectura detrás del fenómeno urbano chileno, permitiendo entender por qué Chile se ha convertido en una potencia exportadora de música en la era del algoritmo de Spotify.