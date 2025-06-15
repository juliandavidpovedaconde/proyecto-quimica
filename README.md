# balanceador de ecuaciones quimicas
Este proyecto esta basado en el diseño lógico y técnico de un programa cuyo objetivo es desempeñarse como un balanceador automático de ecuaciones químicas utilizando el lenguaje de programación Python. Para la resolución del sistema de ecuaciones subyacente, se empleará la librería matemática NumPy, especializada en operaciones con matrices y sistemas lineales.
# Objetivo del proyecto
El objetivo es automatizar el proceso de balanceo de ecuaciones químicas, es decir, encontrar los coeficientes estequiométricos adecuados que equilibran los reactivos y productos de una reacción química cumpliendo con la ley de conservación de la masa.
# Fundamento teórico
El balanceo de ecuaciones químicas se basa en el principio de que la cantidad de átomos de cada elemento químico debe ser igual en ambos lados de la ecuación. Esto da lugar a un sistema de ecuaciones lineales donde cada ecuación representa la conservación de un elemento específico.
consiste en transformar una ecuación química en un sistema de ecuaciones lineales, donde cada ecuación representa la conservación de un elemento químico. Los coeficientes que buscamos en la ecuación balanceada se convierten en las incógnitas del sistema. Luego, el sistema puede resolverse usando métodos algebraicos, como los que ofrece NumPy.
Ejemplo : H₂ + O₂ → H₂O
Queremos encontrar los coeficientes a, b, c tal que:
a·H₂ + b·O₂ → c·H₂O

Elementos: H, O
Ecuaciones:
- Hidrógeno: 2a = 2c → a - c = 0
- Oxígeno: 2b = c → 2b - c = 0

Matriz del sistema:
[1, 0, -1]
[0, 2, -1]

Solución: a = 2, b = 1, c = 2
Ecuación balanceada: 2 H₂ + O₂ → 2 H₂O

# Lógica del algoritmo
El algoritmo inicia recibiendo una ecuación química en forma de cadena, por ejemplo:
H2 + O2 -> H2O
Paso 1: Entrada del Usuario
El usuario proporciona la ecuación química sin balancear, por ejemplo:
H2 + O2 → H2O

Paso 2: abstraccion de Fórmulas Químicas
- Separar reactivos y productos.
- Identificar cada elemento químico y contar cuántos átomos de cada uno hay por compuesto.
- Se construye una matriz de coeficientes donde:
- Filas = elementos químicos.
- Columnas = compuestos (reactivos y productos).
Paso 3: Formulación del Sistema Lineal
Se arma una matriz A tal que:
A · x = 0
Donde:
- A representa la conservación de átomos.
- x es el vector de coeficientes estequiométricos.
- Se impone una solución no trivial (evitar que todos los coeficientes sean cero).

Paso 4: Resolución del Sistema
- Se utiliza la librería NumPy, particularmente funciones como:
- numpy.linalg.svd() (para obtener el núcleo de la matriz).
Paso 5: Normalización
- Se convierte el resultado en enteros positivos.
- Se busca el mínimo común múltiplo entre los denominadores si hay fracciones.
- Se simplifica si es necesario.

- Herramienta | Función Principal

----------- | ------------------

-Python | Lenguaje principal del proyecto

-NumPy | Cálculo matricial, resolución de sistemas lineales
![image](https://github.com/user-attachments/assets/b2ebd602-9eda-4beb-b3f9-64bf877d1804)

¿Para qué sirve?:
Se usa para:

Manipular vectores y matrices.

Calcular el mínimo común múltiplo de denominadores.

Representar el sistema de ecuaciones que surge del balanceo.

¿Por qué se usa?:
Es rápida, confiable y bien optimizada para trabajar con álgebra lineal. 
- Regex (re) | Identificación de elementos químicos y cantidades
![image](https://github.com/user-attachments/assets/2df6c228-7a91-4180-98b5-881c3803b273)

Cuando un usuario escribe una ecuación como:
H2 + O2 -> H2O
Necesitamos analizar cada compuesto (por ejemplo, H2O) para:

Detectar qué elementos contiene (H y O)

Saber cuántos átomos de cada elemento hay (2 de H, 1 de O)
Porque los compuestos químicos están escritos en notación compacta, como:

*C6H12O6

*Fe2(SO4)3

*Ca(OH)2

Entonces se necesita una forma flexible para detectar patrones como:
| Componente       | Ejemplo en Regex | Significado                               |
| ---------------- | ---------------- | ----------------------------------------- |
| Elemento químico | `[A-Z][a-z]?`    | Una letra mayúscula + opcional minúscula  |
| Subíndice        | `\d+`            | Uno o más dígitos (cantidad de átomos)    |
| Agrupaciones     | `\((.*?)\)\d*`   | Paréntesis con subíndice, como en `(OH)2` |

- Texttable | Visualización ordenada del sistema y resultados
  
*Hace más fácil depurar y entender el sistema de ecuaciones.

*Ayuda a verificar visualmente si los coeficientes cumplen con la conservación de átomos.

*Mejora la presentación del programa para usuarios o docentes.



![image](https://github.com/user-attachments/assets/56067905-56ce-4690-aef1-11741583ef91)
# cronograma

| **Semana** | **Fecha**               | **Tema**                                                                                                  |
| ---------- | ----------------------- | --------------------------------------------------------------------------------------------------------- |
| Semana 10  | 09/06/2025 - 15/06/2025 | Diseño del preproyecto: definición del problema, objetivos, herramientas a usar (NumPy, Regex), alcances. |
| Semana 11  | 16/06/2025 - 22/06/2025 | Análisis y abstraccion de fórmulas químicas: extracción de elementos y cantidades con `re`.                    |
| Semana 12  | 23/06/2025 - 29/06/2025 | Construcción de la matriz de conservación de átomos a partir del análisis previo.                         |
| Semana 13  | 30/06/2025 - 06/07/2025 | Resolución del sistema lineal con NumPy (`svd`): cálculo del núcleo para obtener coeficientes.            |
| Semana 14  | 07/07/2025 - 13/07/2025 | Validación del balanceador: pruebas con diferentes ecuaciones, corrección de errores.                     |
| Semana 15  | 14/07/2025 - 20/07/2025 | Visualización y mejoras: formateo de resultados, posible integración de PrettyTable.                      |
| Semana 16  | 21/07/2025 - 27/07/2025 | Presentación final del proyecto: documentación, explicación del algoritmo y demostración del balanceador. |
# diagrama de flujo
```mermaid
flowchart TD
    A[Inicio del Programa] --> B[Entrada de ecuación química sin balancear]
    B --> C[Dividir ecuación en reactivos y productos]
    C --> D[Analizar cada compuesto con Regex]
    D --> E[Extraer elementos y cantidades]
    E --> F[Crear lista única de elementos]
    F --> G[Construir matriz de conservación de átomos]
    G --> H["Formular sistema lineal A · x = 0"]
    H --> I["Resolver con NumPy usando SVD"]
    I --> J{"¿Solución válida?"}
    J -- No --> H
    J -- Sí --> K["Obtener vector solución del null space"]
    K --> L[Escalar a coeficientes enteros]
    L --> M[Formatear ecuación balanceada]
    M --> N[Mostrar resultado final]
    N --> O[Fin del Programa]
# bibliografia
# Bibliografía y citas

Este proyecto utiliza los siguientes recursos académicos y técnicos:

- **ScipyPython (2017)**: *Balancing a Chemical Reaction*. Tutorial comprensión de matrices y np.linalg.solve :contentReference[oaicite:1]{index=1}.
- **Sharma, Bhattacharyya & Bora (2025)**: "Matrix method for balancing chemical equations..." – eliminacion gaussiana en reacciones inorgánicas :contentReference[oaicite:2]{index=2}.
- **Gabriel & Onwuka (2015)**: "Balancing of Chemical Equations Using Matrix Algebra" – null‐space y reducción escalonada :contentReference[oaicite:3]{index=3}.
- **Thorne (2011)**: "An Innovative Approach..." – uso de null space para hallar coeficientes :contentReference[oaicite:4]{index=4}.
- **Barrett (2019)**: "Using Matrices to Balance Chemical Reactions..." – enfoque con ecuaciones diofánticas.
- **Chacón & Apte (2023)**: "A Python Code Algorithm..." – implementación con NumPy :contentReference[oaicite:5]{index=5}.
- **chemical‑eq‑balancer (2024)**: paquete PyPI para balancear ecuaciones y exponer matrices :contentReference[oaicite:6]{index=6}.
- **Wikipedia – Chemical equation**: explicación formal del método matricial :contentReference[oaicite:7]{index=7}.
- **Wikipedia – NumPy**: soporte para álgebra lineal y SVD :contentReference[oaicite:8]{index=8}.


