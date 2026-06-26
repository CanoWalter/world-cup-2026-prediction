# Comprensión de los Datos

## Fuente

International Football Results Dataset.

## Cantidad de registros

49.477 partidos.

## Rango temporal

1872-11-30 a 2026-06-27.

## Valores faltantes

Se detectaron 44 registros con valores faltantes en las variables home_score y away_score.

Estos registros corresponden a encuentros programados para la Copa Mundial FIFA 2026 y fueron separados del conjunto histórico para su posterior utilización en la etapa de simulación.

## Dataset histórico

49.433 partidos con resultado conocido.

## Dataset de predicción

44 partidos correspondientes al Mundial FIFA 2026.

## Analisis Rapido

Victoria local (H): 24.227  → 49.0%
Victoria visitante (A): 13.963 → 28.2%
Empate (D): 11.243 → 22.8%

Esto evidencia una ventaja de localía histórica bastante marcada, algo que más adelante nuestro modelo debería capturar utilizando la variable: neutral

El análisis exploratorio reveló una ventaja de localía significativa. Aproximadamente el 49% de los encuentros finalizaron con victoria del equipo local, mientras que sólo el 28% concluyeron con victoria visitante.

## estado actual de los equipos

Se generaron variables de rendimiento reciente mediante ventanas móviles (rolling windows) de cinco partidos. Para evitar fuga de información se aplicó un desplazamiento temporal (shift=1), garantizando que las estadísticas utilizadas para predecir un encuentro estuvieran construidas exclusivamente con información disponible antes del mismo.

## Fase de depuración

Durante la fase de depuración se identificó un registro duplicado exacto correspondiente a un encuentro amistoso entre Gibraltar y Cayman Islands. El registro fue eliminado utilizando una estrategia de deduplicación basada en fecha, equipos participantes y resultado del encuentro. Los casos restantes con la misma fecha y participantes pero resultados diferentes fueron conservados al considerarse encuentros distintos.

Se eliminaron registros sin historial suficiente para el cálculo de variables de forma reciente. La eliminación afectó menos del 0,5% de las observaciones, por lo que no comprometió la representatividad de la muestra. -> 195 / 49432 ≈ 0.39%