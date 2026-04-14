# Ficha técnica y diccionario de datos

## Ficha técnica

### Fuente de los datos

Los datos fueron recolectados a partir de:

- Spotify Charts (Top 50 Chile)  
  https://charts.spotify.com/  

- Información complementaria obtenida desde la plataforma Spotify:
  - duración de canciones  
  - artistas  
  - colaboraciones  

- Clasificación manual realizada por la autora para variables como:
  - género musical  
  - género del artista (hombre/mujer)  

---

### Metodología de construcción de la base

Para construir la base de datos, se siguieron los siguientes pasos:

1. Se seleccionaron canciones presentes en el Top 50 de Spotify Chile en distintos momentos del tiempo.
2. Se registraron manualmente variables principales como:
   - nombre de la canción  
   - artista  
   - posición en el ranking  
3. Se complementó la información con datos obtenidos desde Spotify:
   - duración de la canción  
   - presencia de colaboraciones  
4. Se realizó una clasificación manual para variables interpretativas:
   - género musical  
   - identificación del artista (hombre/mujer)  
5. Se estructuró la base en formato CSV para su análisis posterior.

---

### Alcance de los datos

- La base incluye canciones que han alcanzado posiciones relevantes en el ranking de Spotify Chile.
- El análisis se enfoca principalmente en música urbana y popular contemporánea.
- El periodo cubierto corresponde a distintos meses/años según la muestra recolectada.
- No es una base exhaustiva, sino una muestra acotada y no probabilística.

---

### Características de los datos

- Tipo de datos: mixtos (cualitativos y cuantitativos)  
- Unidad de análisis: canción  
- Nivel de observación: individual (cada fila corresponde a una canción)  
- Variables: descriptivas, categóricas y numéricas  
- Método de recolección: principalmente manual  

---

### Otras observaciones

- Algunas variables, como género musical, pueden tener un grado de subjetividad debido a su clasificación manual.
- La variable “Hombre/Mujer” simplifica la identidad de género y no contempla diversidad.
- No se incluyen datos de reproducciones ni métricas internas de plataformas debido a su carácter privado.
- La variable “Posición Ranking” presenta algunos valores en rango (ej: “1-3”), lo que podría requerir estandarización para análisis cuantitativo.

---

## Diccionario de datos

| Variable | Descripción | Tipo de dato | Valores posibles | Observaciones |
|--------|-------------|-------------|------------------|--------------|
| canción | Nombre de la canción | Texto | Libre | Puede contener caracteres especiales |
| artista | Nombre del artista principal o colaboradores | Texto | Libre | Puede incluir más de un artista |
| mes_año | Fecha de aparición en el ranking | Texto | Formato mes/año | Puede requerir estandarización a formato fecha |
| duración | Duración de la canción | Numérico / Texto | Segundos o mm:ss | Se recomienda unificar formato |
| género_musical | Clasificación del género de la canción | Categórico | Urbano, reggaetón, trap, pop, etc. | Clasificación manual |
| genero_artista | Identificación de género del artista principal | Categórico | Hombre / Mujer | Simplificación de identidad de género |
| colaboracion | Indica si la canción tiene más de un artista | Binario | Sí / No | Basado en presencia de múltiples artistas |
| plataforma | Plataforma donde se registra el ranking | Texto | Spotify | Constante en esta base |
| posicion_ranking | Posición de la canción en el ranking | Texto / Numérico | 1–50, o rangos | Algunos valores no son numéricos exactos |

---

## Nota final

Esta base de datos permite analizar patrones en canciones exitosas dentro del mercado chileno, especialmente en relación a variables como colaboraciones, duración y género musical. Su estructura facilita la identificación de características comunes en los hits contemporáneos.
