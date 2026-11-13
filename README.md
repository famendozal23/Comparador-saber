# Comparador Saber 11 – Saber Pro

Tablero del Proyecto IVA (Facultad de Ingeniería, Diseño e Innovación y Escuela de Ciencias Básicas, Politécnico Grancolombiano).

Compara los puntajes de Saber 11 y Saber Pro de 732.148 estudiantes que presentaron Saber Pro entre 2022 y 2025, por universidad, modalidad, sede, núcleo básico del conocimiento y programa.

- `index.html`: la página del tablero (funciona sin servidor; todo se calcula en el navegador).
- `datos.b64.txt`: datos por estudiante, comprimidos (gzip + base64).
- `catalogo.json`: nombres de universidades, programas, sedes y núcleos.

Fuente: datos abiertos del ICFES (DataIcfes) y archivo oficial de cruce Saber 11 – Saber Pro (septiembre de 2026). Los puntajes de Saber 11 anteriores a 2014-2 se llevaron a la escala vigente con la recalificación oficial del ICFES (2012-1 a 2014-1) y con una equivalencia estimada (2010-1 a 2011-2). Los datos se preparan con el script `preparacion_datos_IVA.R` del proyecto.

## Ranking de valor agregado (pestaña `#ranking`)

Índice de valor agregado por universidad y por programa, calculado con emparejamiento por puntaje de propensión (propensity score matching). Cada estudiante de una institución se compara con un "gemelo estadístico" de otra institución con igual Saber 11, nivel socioeconómico, estrato, educación de los padres, acceso a internet, zona, edad, género y año de la prueba (más el núcleo del conocimiento para universidades, y la modalidad para programas, cuyos gemelos salen del mismo núcleo en otras instituciones). Vecino más cercano 1:1 con reemplazo, caliper de 0,2 desviaciones estándar del logit del puntaje de propensión; el índice es el efecto promedio sobre los tratados (ATT) estimado con regresión ponderada y errores robustos (HC1).

- `iva.json`: resultados del ranking que lee la pestaña.

## Conflicto y ruralidad (pestaña `#multinivel`)

Modelo lineal mixto de clasificación cruzada (municipio del colegio × institución) que estima la brecha en el avance Saber 11 → Saber Pro de los estudiantes de municipios PDET (Decreto Ley 893 de 2017) y ZOMAC (Decreto 1650 de 2017), y de colegios rurales, frente a estudiantes comparables. Estimado con `lme4` (partes G, H e I de `preparacion_datos_IVA.R`).

- `multinivel.json`: brechas por modelo, componentes de varianza, pruebas de razón de verosimilitud, coeficientes y efectos aleatorios por municipio.
