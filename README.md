# Comparador Saber 11 – Saber Pro

Tablero del Proyecto IVA (Facultad de Ingeniería, Diseño e Innovación y Escuela de Ciencias Básicas, Politécnico Grancolombiano).

Compara los puntajes de Saber 11 y Saber Pro de 732.148 estudiantes que presentaron Saber Pro entre 2022 y 2025, por universidad, modalidad, sede, núcleo básico del conocimiento y programa.

- `index.html`: la página del tablero (funciona sin servidor; todo se calcula en el navegador).
- `datos.b64.txt`: datos por estudiante, comprimidos (gzip + base64).
- `catalogo.json`: nombres de universidades, programas, sedes y núcleos.

Fuente: datos abiertos del ICFES (DataIcfes) y archivo oficial de cruce Saber 11 – Saber Pro (septiembre de 2026). Los puntajes de Saber 11 anteriores a 2014-2 se llevaron a la escala vigente con la recalificación oficial del ICFES (2012-1 a 2014-1) y con una equivalencia estimada (2010-1 a 2011-2). Los datos se preparan con el script `preparacion_datos_IVA.R` del proyecto.
