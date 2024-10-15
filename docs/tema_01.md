# Guía del Proyecto: Análisis y Diseño de Algoritmos 📘

Bienvenid@ a la guía oficial del proyecto de **Análisis y Diseño de Algoritmos**. Este documento servirá como una referencia clave a lo largo del curso y te proporcionará las herramientas necesarias para abordar los retos algorítmicos que se presentarán.

### Objetivo del Proyecto

El proyecto se centra en conceptos avanzados relacionados con la **transición de estados** en sistemas binarios. A través de este documento, podrás comprender, aplicar y desarrollar soluciones eficientes a problemas algorítmicos complejos. Los temas principales incluyen:

- **Matriz de Transición de Probabilidad (TPM)**
- **Marginalización y descomposición matricial**
- **Probabilidad condicional**
- **Distancias métricas** y su aplicación en distribuciones de probabilidad

Cada uno de estos temas será abordado tanto desde un punto de vista teórico como práctico, aplicando ejemplos de código en **Python** para resolver problemas reales.

---

## 📖 Vista Previa del Proyecto en PDF

A continuación puedes visualizar el documento guía del proyecto directamente desde esta página. Si por alguna razón no puedes verlo, también tienes la opción de descargarlo más abajo.

<iframe src="../docs/_static/Guía_Proyecto_ADA24B___V1_1_0.pdf" width="100%" height="600px">
    Tu navegador no soporta la vista previa del PDF.
    [Haz clic aquí para descargar el PDF.](../docs/_static/Guía_Proyecto_ADA24B___V1_1_0.pdf)
</iframe>

---

## Descarga del Documento 📂

Si no puedes visualizar el PDF embebido, puedes descargar el archivo completo del proyecto aquí:

<!-- [Descargar PDF con los detalles del proyecto](../docs/_static/pdf/Guía_Proyecto_ADA24B___V1_1_0.pdf){:target="_blank"} -->
[Descargar PDF Guía del proyecto](../docs/_static/pdf/Guía_Proyecto_ADA24B___V1_1_0.pdf)
---

## 🧠 Ejemplo de Código Python

En el siguiente código, implementamos la métrica **Earth Mover's Distance (EMD)** usando la **Distancia de Hamming** como base. Este código es esencial para comparar distribuciones de probabilidad dentro del contexto de los problemas planteados en el proyecto.

```python
import numpy as np
from pyemd import emd
from numpy.typing import NDArray

def emd_pyphi(u: NDArray[np.float64], v: NDArray[np.float64]) -> float:
    """
    Calcula la Earth Mover's Distance (EMD) entre dos distribuciones de probabilidad u y v.
    La distancia de Hamming es utilizada como métrica de base.
    """
    n: int = len(u)
    costs: NDArray[np.float64] = np.empty((n, n))

    for i in range(n):
        costs[i, :i] = [hamming_distance(i, j) for j in range(i)]
        costs[:i, i] = costs[i, :i]
    np.fill_diagonal(costs, 0)

    cost_matrix: NDArray[np.float64] = np.array(costs, dtype=np.float64)
    return emd(u, v, cost_matrix)

def hamming_distance(a: int, b: int) -> int:
    return (a ^ b).bit_count()
```

El objetivo es que puedas enfrentarte a problemas complejos, entendiendo el comportamiento de los algoritmos y optimizando soluciones para obtener los mejores resultados posibles.

---

¡Manos a la obra!
