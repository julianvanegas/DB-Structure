# 🌳 Árboles ABB y B+

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/julianvanegas/DB-Structure/blob/main/Arboles%20ABB%20y%20B%2B/Arboles_ABB_B%2B.ipynb)

Este proyecto implementa y compara tres estructuras de datos para búsquedas por ID en Python: una lista simple, un Árbol Binario de Búsqueda (ABB) y un Árbol B+. El experimento se ejecuta sobre 10.000 estudiantes generados aleatoriamente para observar, de forma práctica, cómo cambia el rendimiento según la estructura elegida. En sistemas de información, la elección de la estructura de datos impacta directamente los tiempos de consulta, por lo que aquí se contrastan enfoques con comportamientos distintos: la lista lineal con búsqueda de $O(n)$, el ABB con costo promedio de $O(\log n)$ (y peor caso $O(n)$ si se desbalancea), y el Árbol B+ con $O(\log n)$ garantizado gracias a su balance estructural.

| Estructura | Complejidad | Descripción |
|---|---|---|
| Lista simple | $O(n)$ | Recorrido lineal elemento a elemento. |
| ABB | $O(\log n)$ promedio $O(n)$ peor caso | Árbol binario con partición izquierda/derecha. |
| B+ | $O(\log n)$ garantizado | Árbol balanceado con hojas enlazadas. |

&nbsp;

## 📁 Estructura del repositorio

```
DB-Structure/
└── Arboles ABB y B+/
    ├── Arboles_ABB_B+.ipynb    # Notebook principal con el código en Python.
    └── README.md               # Este archivo, como instructivo.
```

&nbsp;

## ⚙️ Requisitos

Necesitas Python 3.8 o superior y la librería [faker](https://faker.readthedocs.io/) para la generación de datos sintéticos. La instalación mínima es:

```bash
pip install faker
```

Los módulos `random`, `time` y `bisect` pertenecen a la biblioteca estándar de Python.

&nbsp;

## 🚀 Ejecución

### Opción 1 — Google Colab

Puedes abrir el notebook directamente en Google Colab haciendo clic en el siguiente botón:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/julianvanegas/DB-Structure/blob/main/Arboles%20ABB%20y%20B%2B/Arboles_ABB_B%2B.ipynb)

### Opción 2 — Local con Jupyter

Si prefieres trabajar en tu entorno, clona el repositorio y ejecútalo con Jupyter:

```bash
git clone https://github.com/julianvanegas/DB-Structure.git
cd "DB-Structure/Arboles ABB y B+"
jupyter notebook Arboles_ABB_B+.ipynb
```

### Opción 3 — Ejecutar como script

También es posible convertir el notebook a script y correrlo como un archivo de Python:

```bash
jupyter nbconvert --to script Arboles_ABB_B+.ipynb
python Arboles_ABB_B+.py
```

&nbsp;

## 🧩 Funcionamiento del código

### 1. Generación de datos.

Se generan 10.000 estudiantes con datos ficticios en español usando `Faker`. Después, esos registros se cargan en las estructuras para ejecutar las comparaciones de búsqueda.

### 2. Lista simple (`ListSystem`).

Funciona como línea base y recorre los elementos de manera secuencial hasta hallar el ID solicitado. Su costo es lineal y crece proporcionalmente al tamaño del conjunto.

### 3. Árbol Binario de Búsqueda (`ABB`).

Organiza los IDs en un árbol con menores a la izquierda y mayores a la derecha. Esta estructura mejora la búsqueda en promedio al descartar ramas, aunque puede degradarse si el árbol queda desbalanceado.

### 4. Árbol B+ (`BPlusTree`).

Guarda los datos en nodos hoja y usa nodos internos como guía de navegación. Como se mantiene balanceado y las hojas están enlazadas, conserva búsquedas en $O(\log n)$ y facilita consultas por rango; en este proyecto se usa `order=100` con divisiones (split) cuando se supera ese límite.

&nbsp;

## 📈 Benchmark

La función `benchmark(qty, structures)` mide tiempos en milisegundos para una cantidad dada de búsquedas bajo dos patrones de acceso: IDs en orden aleatorio e IDs en orden ascendente. Esto permite observar diferencias tanto en acceso general como en acceso secuencial. Se hacen tres pruebas: con `100`, `1000` y `5000` búsquedas.

&nbsp;

## 🛠️ Tecnologías utilizadas

- **Python 3** lenguaje principal.
- **Faker** generación de datos sintéticos en español colombiano.
- **bisect** búsqueda e inserción binaria eficiente dentro de los nodos B+.
- **time** medición de tiempos de alta precisión.
- **Google Colab** o **Jupyter** entorno de ejecución.

&nbsp;

---

Copyright © 2026 Julian Vanegas López