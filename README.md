# telefonica
Este proyecto tiene como objetivo desarrollar un sistema de clasificación capaz de distinguir entre voces humanas reales (bonafide) y ataques generados mediante inteligencia artificial (voces sintéticas). El desarrollo se ha dividido en tres fases experimentales, cada una documentada en su respectivo notebook.

Estructura del Proyecto
Notebook 1: Extracción de Características y Modelos Base (Fase 1)
En la etapa inicial, el foco se centró en la ingeniería de características y la creación de una línea base de clasificación.

Procesamiento: Se transformaron los archivos de audio en coeficientes cepstrales en las frecuencias de Mel (MFCC), capturando la huella acústica única de cada muestra.

Entrenamiento: Se evaluaron modelos iniciales como la Regresión Logística utilizando un conjunto de datos controlado.

Resultado: Se estableció una base técnica sólida, aunque el modelo mostraba una rigidez excesiva que dificultaba la detección en entornos más complejos.

Notebook 2: Evaluación y Detección de Sesgos (Fase 2)
El segundo notebook se dedica a la validación del sistema frente a datos externos (dataset EVAL) para medir su rendimiento en condiciones más realistas.

Conflicto detectado: Al evaluar con datos reales, se observó que el modelo bloqueaba a demasiados usuarios legítimos (falsos positivos).

Análisis: Se identificó la necesidad de rebalancear el entrenamiento, ya que el modelo estaba demasiado especializado en detectar fraude y era incapaz de reconocer la variabilidad de la voz humana real.

Notebook 3: Rebalanceo, Selección de SVM y Optimización (Fase 3)
El último notebook representa la fase de madurez del proyecto, donde se alcanza el equilibrio entre seguridad y accesibilidad.

Estrategia 60/40: Se reconstruyó el dataset de entrenamiento inyectando muestras reales de EVAL para flexibilizar el modelo.

Competencia de Modelos: Se compararon algoritmos de Regresión Logística, Random Forest, XGBoost y SVM. El SVM con Kernel RBF resultó ganador al liderar todas las métricas.

Resultados Finales: En el test blindado, el modelo alcanzó una Balanced Accuracy del 80.93%, logrando rescatar al 82.30% de los usuarios legítimos.

Poda de Características: Se realizó un estudio de importancia por permutación para aligerar el modelo. Se determinó que es posible reducir el sistema a solo 4 variables clave, manteniendo un rendimiento robusto (77.50%) pero con un coste computacional mucho menor.

Conclusiones Técnicas
El proyecto concluye que la proyección dimensional del SVM RBF es la tecnología más eficaz para este problema. La optimización final permite a Telefónica desplegar un sistema ágil que no solo protege contra el fraude sintético, sino que garantiza una experiencia fluida para el cliente real al minimizar los bloqueos innecesarios.

Tecnologías Utilizadas
Lenguaje: Python 3.x

Librerías principales: Scikit-learn, Pandas, NumPy, XGBoost, Matplotlib y Seaborn.

Entorno: Google Colab con integración de Google Drive para la gestión de datasets masivos.
