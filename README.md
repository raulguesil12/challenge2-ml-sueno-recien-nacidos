# Challenge 1 (Individual): Pipeline de Machine Learning
**Caso asignado: Tipo C – Sueño en los Recién Nacidos (0–3 meses)**

- Curso: Machine Learning – Universidad Peruana Cayetano Heredia (UPCH)
- Docente: Yannick Patrick Carrasco Merma
- Unidad: Fundamentos de Machine Learning
- Estudiante: _(tu nombre completo)_

---

## 1. Presentación del caso

El caso proviene de la infografía **"El Sueño en los Primeros Meses de Vida"** (Examen Parcial, Estudio de Caso III). La infografía resume evidencia científica sobre el sueño infantil de 0 a 3 meses:

| Elemento de la infografía | Dato reportado |
|---|---|
| Estudio científico | 162 bebés y 100 padres (Zúrich, Suiza) |
| Registro | > 25 000 horas de sueño registradas con actigrafía |
| Seguimiento | Longitudinal a los 3, 6 y 12 meses |
| Hallazgo 1 | Los ciclos de sueño duran ~40 minutos en bebés (más cortos que en adultos) |
| Hallazgo 2 | Los ciclos aumentan ~10 minutos entre los 3 y 12 meses |
| Fuente divulgativa | Los recién nacidos duermen ~16 horas al día, de forma fragmentada e impredecible |
| Variables observables | Edad del bebé, duración de ciclos de sueño, actividad motora, cantidad total de sueño, lactancia, ubicación del sueño, años de observación, recomendaciones prácticas |
| Aspectos no reportados | Impacto a largo plazo en el desarrollo cognitivo, causalidad directa de la lactancia, efectividad comparativa de cada intervención, diferencias por contexto geográfico/social/cultural, factores clínicos y médicos adicionales |

## 2. Planteamiento del problema

> **¿Cómo podemos modelar y predecir la evolución del sueño de un recién nacido (duración del ciclo de sueño y horas totales de sueño) a partir de su edad y de variables observables, para identificar patrones típicos y orientar a las familias en la creación de rutinas de sueño?**

Problema formal:

- **Entrada:** edad del bebé (semanas), actividad motora, lactancia, ubicación del sueño, rutina del ambiente.
- **Salida:** duración esperada del ciclo de sueño (min) y horas de sueño por día.
- **Objetivo:** (a) explorar qué acciones llevan a un patrón de sueño más consolidado (búsqueda en espacio de estados) y (b) estimar la tendencia de maduración del sueño (regresión).

## 3. ¿Por qué se puede abordar con IA y Machine Learning?

1. **Hay datos secuenciales y masivos:** más de 25 000 horas de actigrafía son demasiado para analizarlas manualmente; los algoritmos detectan patrones en señales de movimiento.
2. **Existe una tendencia aprendible:** la duración del ciclo crece con la edad (≈ +10 min entre 3 y 12 meses). Esto es una relación que un modelo de **regresión** puede capturar.
3. **El sueño es fragmentado e impredecible a nivel individual:** un modelo estadístico permite estimar la tendencia general y la variabilidad entre bebés.
4. **Hay decisiones que tomar:** las intervenciones (rutinas, ambiente, señales de cansancio) se pueden representar como **operadores** sobre estados del sueño, y una **búsqueda** (BFS, A*) puede explorar qué secuencia de acciones consolida mejor el sueño.
5. **La infografía lo sugiere explícitamente:** _"Estos datos pueden utilizarse para construir modelos de Machine Learning que predigan, clasifiquen o agrupen patrones de sueño infantil."_

**Tipo de aprendizaje:** supervisado (regresión sobre edad → duración del ciclo). Posible extensión no supervisada: agrupar patrones de sueño (clustering).

**Limitaciones y ética:** los datos reportados son de una sola población (Zúrich), no se reporta causalidad ni efectos a largo plazo; el modelo es orientativo y **no sustituye** la evaluación de un pediatra.

## 4. Contenido del repositorio

| Archivo | Descripción | Puntaje |
|---|---|---|
| `README.md` | Presentación del caso y problema | 5 |
| `espacio_de_estados.md` + `espacio_de_estados.jpeg` | Estados, operadores, restricciones y representación visual | 5 |
| `01_pipeline_razonamiento_busqueda.ipynb` | Problema → Espacio de Estados → Exploración → Búsqueda → Resultado | 5 |
| `02_pipeline_modelo_prediccion.ipynb` | Regresión, datos sintéticos y gráfico interpretativo | 5 |

## 5. Cómo ejecutar
1. Sube el repositorio a GitHub.
2. Abre cada notebook en Google Colab (`Archivo → Abrir cuaderno → GitHub`) o usa el botón *Open in Colab*.
3. Ejecuta `Entorno de ejecución → Ejecutar todo`.

Dependencias: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `networkx` (todas ya vienen en Colab).

## 6. Fuentes
- Infografía "El Sueño en los Primeros Meses de Vida" (Examen Parcial – ML, UPCH).
- Estudio científico citado en la infografía (Zúrich, actigrafía, seguimiento a 3, 6 y 12 meses).
