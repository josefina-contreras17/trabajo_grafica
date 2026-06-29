# Análisis de las visualizaciones 

## Gráfico de barras 

![Gráfico de barras](imagenes/graficobarras.png)

## Radar general

![Radar general](imagenes/radargeneral.png)

**Codigo:** 
```import pandas as pd
import plotly.express as px

# Cargar la base de datos
df = pd.read_csv("mejorescancionesderock - Copia de mejorescancionesrocklatino_original.csv")

# Variables que vamos a usar para el radar
variables = [
    "Danceability",
    "Energy",
    "Acousticness",
    "Instrumentalness",
    "Liveness",
    "Speechiness",
    "Valence"
]

# Calcular promedios generales
promedios = df[variables].mean()

# Crear radar chart
fig = px.line_polar(
    r=promedios.values,
    theta=promedios.index,
    line_close=True
)

# Estilo del radar
fig.update_traces(
    fill="toself",
    line=dict(
        color="#654537",
        width=4
    ),
    fillcolor="rgba(227,122,53,0.45)"
)

# Estilo general
fig.update_layout(
    title="Perfil promedio del rock chileno",
    showlegend=False,
    paper_bgcolor="#ead3bc",
    plot_bgcolor="#ead3bc",
    font=dict(
        family="Arial",
        size=14,
        color="#654537"
    ),
    polar=dict(
        bgcolor="#ead3bc",
        radialaxis=dict(
            visible=True,
            range=[0, 1],
            gridcolor="#c15a49",
            linecolor="#c15a49"
        ),
        angularaxis=dict(
            gridcolor="#c15a49",
            linecolor="#c15a49"
        )
    )
)

fig.show()
```
