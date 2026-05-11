# Documentación

## 1. Proceso de visualización
Para hacer las visualizaciones de datos use Google Colab utilizando Python y las librerías Pandas y Altair. En Google Colab subí la base de datos previamente trabajada y en formato CSV. Luego calcule los promedios de las atributos musicales que seleccioné (Energy, Danceability, Valence, Acousticness, Instrumentalness, Liveness y Speechiness.)
Para sacar el promedio use el siguiente código: promedios = {
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
