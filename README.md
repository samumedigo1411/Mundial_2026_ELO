# Mundial 2026 — Predicción con Modelo Elo + Monte Carlo ⚽🏆

Notebook que predice qué selecciones llegarán a cada fase del Mundial 2026, combinando el **ranking Elo** de fuerza de cada selección con una **simulación Monte Carlo** del torneo completo (10.000 simulaciones), usando los 12 grupos reales del sorteo oficial.

## ¿Qué hace?

1. Asigna un rating **Elo** a cada una de las 48 selecciones clasificadas (actualizado a junio de 2026).
2. Usa la fórmula clásica de Elo para calcular la probabilidad de que un equipo le gane a otro, sumando ventaja de localía a los países anfitriones (México, Estados Unidos, Canadá).
3. Simula la fase de grupos (todos contra todos dentro de cada uno de los 12 grupos), determinando los 2 primeros de cada grupo (clasificación directa) y guardando los terceros para elegir después los 8 mejores.
4. Simula las eliminatorias directas (ronda de 32 hasta la final), resolviendo empates mediante un desempate tipo penales (50/50 ajustado por Elo).
5. Repite todo el proceso **10.000 veces** (Monte Carlo) y cuenta cuántas veces cada selección llega a octavos, cuartos, semifinales, final y título.
6. Genera una tabla de probabilidades por selección y un gráfico de los 10 favoritos al título.

## Fórmula Elo utilizada

$$P(A) = \frac{1}{1 + 10^{-(\Delta R)/400}}$$

Donde $\Delta R$ es la diferencia de Elo entre los dos equipos, con un ajuste de **+100 puntos** al equipo que juega de local.

## Estructura del notebook

| Sección | Contenido |
|---|---|
| Celda 1 | Importación de librerías (`numpy`, `pandas`, `random`, `matplotlib`) y semilla fija para reproducibilidad |
| Celda 2 | Diccionario de ratings Elo de las 48 selecciones |
| Celda 3 | Los 12 grupos reales del sorteo del Mundial 2026 |
| Celda 4 | Función de probabilidad de victoria según Elo |
| Celda 5 | Simulación de la fase de grupos |
| Celda 6 | Simulación de eliminatorias directas |
| Celda 7 | Selección de los 8 mejores terceros lugares |
| Celda 8 | Simulación Monte Carlo completa (10.000 iteraciones) |
| Celda 9 | Tabla de resultados con probabilidades por fase |
| Celda 10 | Predicción final: Top 16, Top 8, Top 4, finalistas y campeón |
| Celda 11 | Gráfico de barras de los favoritos al título |

## Stack

- `numpy`, `pandas` — cálculos y tablas
- `random` — simulación estocástica de partidos
- `collections.defaultdict` — conteo de resultados por fase
- `matplotlib` — visualización de favoritos

## Instalación y uso

```bash
git clone https://github.com/samumedigo1411/Mundial_2026_ELO.git
cd Mundial_2026_ELO
pip install numpy pandas matplotlib jupyter
jupyter notebook Mundial_2026_Elo.ipynb
```

Corre las celdas en orden. Puedes ajustar `N_SIMULACIONES` (por defecto 10.000) para más o menos precisión, y modificar los ratings Elo o los grupos si cambian antes del torneo.

## Notas

- Los resultados son reproducibles gracias a la semilla fija (`random.seed(42)`, `np.random.seed(42)`).
- Es un modelo estadístico simplificado (Elo + azar), no incorpora lesiones, forma reciente puntual, ni otros factores contextuales — sirve como ejercicio predictivo, no como pronóstico garantizado.

## Estado del proyecto

Proyecto predictivo / ejercicio académico ⚽
