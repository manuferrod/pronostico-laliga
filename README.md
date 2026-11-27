# Pronóstico LaLiga

[![¿Se puede pronosticar LaLiga mejor que Bet365?](docs/portada.png)](https://manuferrod.github.io/pronostico-laliga/)

**[Ver la página del proyecto](https://manuferrod.github.io/pronostico-laliga/)**: el pronóstico de la próxima jornada, los resultados de 13 temporadas y un buscador con todos los partidos.

Un modelo pronostica local, empate o visitante en cada partido de Primera y se compara, partido a partido, con apostar siempre al favorito de Bet365.

## Resultados

De 2014/15 a 2026/27, con datos hasta el 23 de noviembre de 2026. Los de la página se actualizan cada jornada.

| 4.689 partidos | Modelo | Favorito de Bet365 |
|---|---:|---:|
| Partidos acertados | **55,3 %** | 54,2 % |
| Rentabilidad por apuesta | **+3,7 %** | −2,7 % |
| Unidades, apostando 1 por partido | **+172,9** | −124,4 |
| Pérdida logarítmica (menos es mejor) | 1,002 | **0,958** |

La ventaja sobre el favorito es de **+6,34 puntos** de rentabilidad, con un intervalo del 95 % entre +4,08 y +8,60.

### Cómo se mide

- **Nunca ve el futuro.** Cada partido se pronostica con un modelo entrenado solo con los anteriores.
- **Mismos partidos y mismas cuotas** para el modelo y para Bet365: las de apertura.
- **Se apuesta a todo**, una unidad por partido.
- Es una simulación con datos históricos y las variables se seleccionaron con estas mismas temporadas. No es una recomendación para apostar.

## Cómo funciona

1. **Extracción.** Resultados y cuotas (football-data), goles esperados (Understat), estadística de partido (SofaScore), nivel de cada club (ClubElo) y valor de plantilla (Transfermarkt).
2. **Limpieza y variables.** La estadística se convierte en rachas, promedios y tendencias, siempre anteriores al partido.
3. **Preprocesado.** Se comparan los dos equipos, se tratan los huecos y queda una fila por partido.
4. **Modelado.** Regresión logística multinomial, reentrenada antes de cada fecha con los 1.520 partidos anteriores (cuatro temporadas). Los 380 últimos pesan el triple.
5. **Presentación.** Lee lo que publica el modelo, comprueba que las cifras coinciden y escribe la página.

El modelo usa 14 variables: la cuota de Bet365 (probabilidad de que gane el local frente a la de que gane el visitante), los puntos de cada equipo en sus 10 últimos partidos en la misma condición (el local en casa, el visitante fuera), los pases filtrados de cada equipo, si el local viene de ganar a cuota mayor que 4, si a algún equipo ya no le queda nada en juego, la diferencia de goles de los 6 últimos partidos (del local, del visitante y la de uno menos la del otro), el xG concedido, los toques en el área rival, las ocasiones claras del local, cuánto movieron las casas la cuota del visitante en sus 5 últimos partidos y la efectividad (puntos por tiro a puerta en la temporada).

## Qué hay aquí

| Archivo | Contenido |
|---|---|
| `docs/` | la página publicada |
| `PREPROCESADO_trabajo.ipynb` | paso 3 |
| `MODELADO_trabajo.ipynb` | paso 4: validación, pronóstico y evaluación |
| `PRESENTACION_trabajo.ipynb` | paso 5 |

Los datos y los cuadernos que los descargan no se publican, así que los cuadernos se pueden leer con sus resultados, pero no ejecutar desde aquí.

Hecho con Python, pandas y scikit-learn. La página es HTML, CSS y JavaScript sin librerías.

---

**Manuel Fernández** · [LinkedIn](https://www.linkedin.com/in/manuel-fernandez-rodriguez/) · [GitHub](https://github.com/manuferrod)

Los escudos pertenecen a sus clubes. Bet365 es una marca de su propietario y no tiene relación con este trabajo.
