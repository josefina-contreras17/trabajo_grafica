## Archivo README de la entrega personal:
### Explicación de cómo se realizó el proceso de visualización, con los pasos y descinones tomados.
El proceso para llegar a la visualización final se dividió en distintas fases estratégicas, combinando el análisis de datos con decisiones de diseño orientadas a responder nuestra hipótesis:
* __Exploración y definición de ejes__: Primero, analizamos las variables acústicas disponibles. Para comprobar la existencia de una "canción promedio", decidimos cruzar métricas que definen el carácter de una canción. Tomamos la decisión de contrastar variables como Danceability (bailabilidad) vs. Energy (energía) o Tempo (BPM), ya que estas son las dimensiones donde más destacan bandas como Los Prisioneros.
* __Identificación de Agrupamientos__: Al plotear los datos utilizando la librería Vega-Altair, observamos cómo los puntos (canciones) se comportaban. La decisión clave aquí fue aplicar color (color) o tamaño (size) para diferenciar agrupaciones temporales (décadas de los 80s y 90s) o bandas específicas (Los Prisioneros vs. otras bandas), permitiendo que el "clúster" de la canción promedio se hiciera visualmente evidente.
* __Interactividad y Contexto__: Para que la visualización permitiera explorar la información, configuramos tooltips (etiquetas emergentes) en Vega-Altair. De esta forma, al pasar el cursor sobre un punto que se encuentra en el "centro" del clúster promedio, el usuario puede leer exactamente qué canción es, su artista y sus métricas exactas.
* __Diseño para Webstory__: Se decidió exportar el gráfico eliminando el ruido visual (fondos limpios, cuadrículas tenues y tipografías legibles) para asegurar que, al guardarlo como archivo JPG e incrustarlo en el HTML, dialogara perfectamente con la crónica periodística sin sobrecargar al lector.

### Base de datos (CSV) que utilizaron, cómo la procesaron hasta dejarla lista para usar en la visualización que quieren hacer y por qué la seleccionaron.
Base utilizada "mejorescancionesderock UTF8.csv"

* __Por qué se seleccionó__: Elegimos esta base de datos porque ofrece una radiografía cuantitativa (a través de la API de Spotify) de un fenómeno cualitativo y cultural: el rock chileno. Permite salir de la crítica musical subjetiva y analizar la historia sonora del país con datos matemáticos, acústicos y de comportamiento de usuarios.
* __Procesamiento__:
    * _Carga y revisión de formatos_: Se cargó el CSV en un entorno de Python, Google Colab. Se verificó que variables numéricas como Energy, Valence o Tempo estuvieran en formato float (decimal) o int (entero) para poder graficarlas sin errores matemáticos.
    * _Manejo de temporalidad_: La columna Release Date se procesó para extraer el año de publicación, lo que facilitó el filtro de las canciones pertenecientes específicamente a las décadas de los 80 y 90 (época de auge post Nueva Ola).
    * _Tratamiento de dimensionalidad_: Al notar que métricas como Loudness están en decibeles (valores negativos) y Tempo en BPM (ej. 120), mientras que Energy va de 0 a 1, se decidió mapearlas en ejes separados en Altair para no distorsionar la escala visual del gráfico.

### Ejemplos sobre preguntas que puede responder su visualización de datos final (o el conjunto de visualizaciones que crearon).
* ¿Existe un patrón acústico medible (ej. niveles de energía y bailabilidad) que comparta la mayoría de los éxitos del rock chileno de los 80 y 90?
* Al aislar los datos de "Los Prisioneros", ¿se alejan de la media del rock chileno o, por el contrario, son ellos quienes definen el centro del clúster de la "canción promedio"?
* ¿Cómo contrasta el nivel de "Loudness" (volumen acústico) de bandas de nicho (como las agrupaciones de stoner o doom metal) con las bandas de pop-rock más populares en plataformas de streaming?
* ¿Es la "bailabilidad" (Danceability) un factor determinante para que una canción de rock nacional mantenga un alto índice de "Popularidad" en la actualidad?

### Ficha técnica de la base de datos:
1.  Característica de los datos si es necesario
Se trata de un conjunto de datos estructurados de formato tabular. Contiene 232 registros (filas) que representan canciones individuales, y 24 dimensiones (columnas) que mezclan datos de tipo texto (metadatos), fechas, booleanos y variables numéricas continuas (Audio Features extraídos del algoritmo de Spotify).

2. Variables incorporadas: variable | descripción
    * Track Name | Título oficial de la canción.
    * Artist Name(s) | Nombre de la banda o artista intérprete.
    * Release Date | Fecha en la que la pista o el álbum fue publicado originalmente.
    * Popularity | Índice numérico (0 a 100) que calcula Spotify basado en la cantidad de reproducciones recientes de la pista.
    * Genres | Etiquetas categóricas asignadas al artista (ej. latin rock, folclor andino).
    * Danceability | Métrica de 0.0 a 1.0 que describe qué tan adecuada es una pista para bailar, basada en el tempo, la estabilidad del ritmo y la fuerza del compás.
    * Energy | Medida de 0.0 a 1.0 que representa la intensidad y actividad perceptiva de la canción (pistas rápidas, ruidosas y estridentes marcan cerca de 1.0).
    * Loudness | El volumen promedio de la pista expresado en decibeles (dB). Suele oscilar en valores negativos.
    * Valence | Métrica de 0.0 a 1.0 que describe la "positividad" musical. Valores altos suenan más alegres/eufóricos, valores bajos suenan más melancólicos o sombríos.
    * Tempo | La velocidad o el ritmo estimado de la pista, medido en pulsaciones por minuto (BPM).

3. Observaciones que tengan sobre la base de datos:
* Las variables acústicas ("Audio Features" como _Energy o Danceability_) provienen de un análisis algorítmico automatizado, no de la valoración de un crítico musical humano.
* La variable _Popularity_ tiene un sesgo de "actualidad"; es decir, mide las reproducciones en el momento de la extracción de los datos, no el éxito histórico de ventas físicas de la canción en los años 80 o 90.
* La columna _Genres_ agrupa múltiples etiquetas en una sola celda (separadas por comas), lo que requiere tokenización si se desean hacer gráficos de barras estritos por subgénero individual.
