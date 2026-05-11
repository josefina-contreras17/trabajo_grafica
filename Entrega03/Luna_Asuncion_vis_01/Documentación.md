# Documentación

## 1. Proceso de visualización
Para hacer las visualizaciones de datos use Google Colab utilizando Python y las librerías Pandas y Altair. En Google Colab subí la base de datos previamente trabajada y en formato CSV. Luego calcule los promedios de las atributos musicales que seleccioné (Energy, Danceability, Valence, Acousticness, Instrumentalness, Liveness y Speechiness.)
Para sacar el promedio use el siguiente código: 
promedios = {
   'Atributo': [
       'Danceability',
       'Energy',
       'Acousticness',
       'Instrumentalness',
       'Liveness',
       'Speechiness',
       'Valence'
   ],
  
   'Promedio': [
       df['Danceability'].mean(),
       df['Energy'].mean(),
       df['Acousticness'].mean(),
       df['Instrumentalness'].mean(),
       df['Liveness'].mean(),
       df['Speechiness'].mean(),
       df['Valence'].mean()
   ]
}

A partir de esos promedios hice dos visualizaciones: 
* Un gráfico radial (Radar Chart) para representar el perfil promedio del rock chileno.
* Un gráfico de barras horizontales para comparar visualmente la intensidad promedio de cada atributo.

Para los códigos me ayudé de las guías de las ayudantías, clases y tutoriales online.
Luego guardé y descargué los gráficos como imagen y html.

## 2. Desarrollo de la base de datos 
La base de datos la hicimos en base a la lista de 250 mejores canciones de rock chilenas de la revista Rockaxis. Guardamos la playlist en Spotify y usamos Exportify para exportar la playlist a una base de datos en Excel. Limpiamos la base y arreglamos algunos problemas que tenían las fechas, eligiendo solo el año como variable (eliminando día y mes de publicación). Finalmente la playlist, y por consiguiente la base de datos, tenía 232 canciones, un poco menos de lo que decía la lista. Usamos esa lista porque fue hecha por un medio especializado en música, por lo que cuenta con expertos que nos garantizan que las canciones elegidas como las mejores tengan un sustento y no elegidas al azar. 

Link fuente ranking:

https://www.24horas.cl/data/las-250-mejores-canciones-del-rock-chileno-revisa-el-listado-completo

## 3. Preguntas que puede responder la visualización de datos

¿Existe una identidad sonora dentro del rock chileno?
¿Qué atributos musicales predominan en las canciones más representativas?
¿El rock chileno tiende a ser más energético o más acústico?
¿Las canciones del ranking comparten patrones similares?
¿Qué tan bailable o emocionalmente positiva es la “canción promedio” del rock chileno?

## 4. Ficha técnica de la base de datos:

* Característica de los datos: la base de datos contiene variables numéricas obtenidas desde Spotify. Los atributos musicales son calculados por Spotify. 

* Variables: Danceability, Energy, Acousticness, Instrumentalness, Liveness, Speechiness, Valence. Estas fueron elegidas ya que comparten una misma escala de medición entre 0 y 1, lo que facilita su visualización. Variables como Tempo y Loudness no fueron incluidas en los gráficos principales debido a que utilizan escalas distintas, lo que dificultaba su comparación visual.

Danceability: qué tan bailable es una canción

Energy: nivel de intensidad y actividad.

Loudness: volumen general en decibeles.
Speechiness: presencia de palabras habladas.
Acousticness: probabilidad de que una canción sea acústica.
Instrumentalness: probabilidad de ausencia de voces.
Liveness: probabilidad de grabación en vivo.
