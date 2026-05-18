# Calculadora de Índice de Calor

Plataforma de escritorio en Python que calcula el **índice de calor** (sensación térmica por temperatura y humedad) utilizando la **fórmula clásica de Steadman (1979)** y las categorías oficiales de riesgo de la NOAA / National Weather Service.

## Funcionalidades

- Entrada de temperatura en °C o °F y humedad relativa con slider interactivo.
- Cálculo inmediato del índice de calor en ambas escalas.
- Clasificación visual del riesgo en cinco categorías (sin riesgo, precaución, precaución extrema, peligro, peligro extremo).
- Recomendaciones de seguridad para cada nivel.
- Mapa de calor interactivo (matplotlib) que muestra la posición exacta del cálculo dentro del rango completo de combinaciones temperatura/humedad.
- Historial de cálculos con tabla y exportación a CSV.

## Instalación

Necesitas Python 3.8 o superior. Instala las dependencias con:

```bash
pip install numpy matplotlib
```

`tkinter` viene incluido con la instalación estándar de Python en macOS y Windows. En Linux puede que necesites instalarlo aparte (`sudo apt install python3-tk`).

## Uso

Desde la carpeta del proyecto:

```bash
python calculadora_indice_calor.py
```

1. Ingresa la temperatura y selecciona la unidad (°C o °F).
2. Ajusta la humedad relativa con el campo numérico o el slider.
3. Presiona **Calcular índice de calor**.
4. El resultado aparece con su categoría de riesgo y recomendación.
5. El mapa de calor muestra dónde se encuentra tu medición.
6. Cada cálculo se guarda en el historial; puedes exportarlo a CSV.

## Fórmula utilizada

Steadman (1979) — versión simple:

```
HI(°F) = 0.5 × (T + 61.0 + (T − 68.0) × 1.2 + RH × 0.094)
```

Donde:
- `T` = Temperatura en °F
- `RH` = Humedad relativa en %

Cuando el promedio `(HI + T)/2 ≥ 80°F`, se utiliza dicho promedio como aproximación al estrés térmico real (criterio NWS).

## Categorías de riesgo (NOAA)

| Rango (°C) | Categoría | Color |
|---|---|---|
| < 27 | Sin riesgo | Verde |
| 27 – 32 | Precaución | Amarillo |
| 32 – 41 | Precaución extrema | Naranja |
| 41 – 54 | Peligro | Rojo |
| > 54 | Peligro extremo | Morado |

## Estructura del proyecto

```
Nuevos proyectos/
├── calculadora_indice_calor.py   # Aplicación principal
└── README_indice_calor.md        # Esta guía
```

## Próximos pasos sugeridos

- Conectar con una API meteorológica (OpenWeatherMap, AccuWeather) para obtener datos automáticos por ubicación.
- Agregar comparación con otras fórmulas (Rothfusz/NWS, Apparent Temperature australiano).
- Generar reportes PDF con gráficas.
- Empacar la app como ejecutable (.exe / .app) con PyInstaller.
