# 💻 Análisis de Métodos de Comunicación Interna en Computadores Paralelos para Sistemas LLM

[![Status](https://img.shields.io/badge/Estado-Investigación%20Finalizada-success)](https://github.com/TuUsuario/NombreDelRepo)
[![License](https://img.shields.io/badge/License-MIT-blue)](https://opensource.org/licenses/MIT)

## 👤 Autoría y Afiliación

| Rol | Nombre | Institución | Contacto |Asignatura| Año |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Autor** | Anyi Cristina Ruano Adrada | Fundación Universitaria Internacional de la Rioja | cristina1adrada@gmail.com | Estructura de Computadores |2025 |

---

## Introducción

El desarrollo exponencial de los grandes modelos de lenguaje (LLMs), como *ChatGPT*, *Gemini* y *Claude*, ha sido posible gracias a los avances en computación paralela y arquitecturas de alto rendimiento [3], [10]. Estos sistemas requieren infraestructuras capaces de procesar billones de parámetros de manera eficiente, donde la comunicación interna entre procesadores y nodos constituye un factor crítico [1], [2], [14].  

La revolución de los LLMs no radica únicamente en innovaciones algorítmicas, sino en una revolución de escala impulsada por arquitecturas de cómputo paralelo de última generación [3], [10], [18]. En este contexto, resulta esencial analizar los métodos de comunicación empleados en computadores paralelos, las topologías de interconexión, las estrategias de enrutamiento y los diseños de multiprocesadores que sostienen a los LLMs contemporáneos [2].  

Los objetivos principales de este trabajo son:  

1. Analizar la relación entre los fundamentos de la arquitectura de computadores y las necesidades de infraestructura para el entrenamiento y la operación de LLMs [7].  
2. Evaluar comparativamente la capacidad de distintos LLMs para generar conocimiento técnico especializado [10].  
3. Reflexionar sobre la utilidad y las limitaciones de los LLMs como fuente de investigación en arquitectura de computadores [11].  

---

## Marco Teórico

### Modelos de paralelismo (Taxonomía de Flynn)

- **SISD (Single Instruction, Single Data):** Arquitectura secuencial clásica de Von Neumann [1], inadecuada para LLMs [2].  
- **SIMD (Single Instruction, Multiple Data):** Propia de GPUs modernas, permite ejecutar operaciones vectoriales masivas, optimizando cálculos matriciales [2], [14].  
- **MISD (Multiple Instruction, Single Data):** Poco usado; su aplicación en LLMs es marginal [10], [18].  
- **MIMD (Multiple Instruction, Multiple Data):** Base de supercomputadores y clusters actuales, clave para implementar paralelismo híbrido en LLMs [9], [14].  

### Topologías de red

- **Bus compartido:** Simple pero con escalabilidad limitada [4], [24].  
- **Malla (Mesh):** Escalable y usada en clusters GPU; la latencia aumenta con la distancia [4], [5].  
- **Hipercubo:** Alta conectividad, útil en sistemas a gran escala [25].  
- **Torus y Dragonfly:** Predominantes en supercomputadores modernos. Dragonfly minimiza latencia y diámetro de red, siendo ideal para *All-Reduce* en LLMs [3], [25].  

### Estrategias de enrutamiento

- **Determinístico (XY):** Simplicidad, pero riesgo de congestión [2].  
- **Adaptativo:** Selección dinámica según congestión; preferido en HPC [5].  
- **Aleatorio:** Menos común, pero puede evitar bloqueos [24].  

### Diseño de multiprocesadores

- **UMA (Uniform Memory Access):** Acceso uniforme a memoria, baja escalabilidad [14].  
- **NUMA (Non-Uniform Memory Access):** Mejora la escalabilidad, pero requiere coherencia de caché [2].  
- **Híbridos (clusters de nodos NUMA):** Predominantes en supercomputadores modernos [3].  

---

## Metodología

Se realizó un análisis comparativo consultando a tres LLMs —ChatGPT, Gemini y Claude— mediante un conjunto de **preguntas técnicas** sobre:  

1. Arquitecturas MIMD.  
2. Topologías de red.  
3. Estrategias de enrutamiento.  
4. Diseño de multiprocesadores.  

Las respuestas fueron documentadas en tablas, comparadas y evaluadas en términos de:  

- **Precisión técnica.**  
- **Nivel de detalle.**  
- **Coherencia y limitaciones.**  

---

## Resultados: Respuestas de los LLMs

### Pregunta 1: ¿Qué es una arquitectura MIMD?

| Modelo    | Respuesta resumida                                                                 |
|-----------|------------------------------------------------------------------------------------|
| ChatGPT   | Explica MIMD como múltiples procesadores ejecutando instrucciones diferentes sobre datos distintos. Relación con supercomputadores y clusters. |
| Gemini    | Similar a ChatGPT, enfatiza flexibilidad y ejemplos de uso en sistemas distribuidos. |
| Claude    | Precisión conceptual, incluye limitaciones prácticas y menciona paralelismo híbrido. |

---

### Pregunta 2: ¿Cuáles son las topologías de red más usadas en computadores paralelos?

| Modelo    | Respuesta resumida                                                                 |
|-----------|------------------------------------------------------------------------------------|
| ChatGPT   | Malla, hipercubo, anillo, torus, Dragonfly.                                        |
| Gemini    | Incluye mismas topologías y ejemplos de uso industrial.                            |
| Claude    | Detalla ventajas/desventajas de cada topología.                                    |

---

### Pregunta 3: ¿Qué estrategias de enrutamiento se utilizan?

| Modelo    | Respuesta resumida                                                                 |
|-----------|------------------------------------------------------------------------------------|
| ChatGPT   | Enrutamiento determinístico y adaptativo.                                          |
| Gemini    | Añade ejemplos de implementaciones prácticas.                                      |
| Claude    | Explica impacto en latencia, escalabilidad y confiabilidad.                        |

---

### Pregunta 4: ¿Cómo se diseñan los multiprocesadores modernos?

| Modelo    | Respuesta resumida                                                                 |
|-----------|------------------------------------------------------------------------------------|
| ChatGPT   | UMA, NUMA, coherencia de caché.                                                    |
| Gemini    | Similar, añade NUMA distribuido.                                                   |
| Claude    | Más completo, integra NUMA + clusters + coherencia avanzada.                       |

---

## Análisis Comparativo y Crítico

1. **Consistencia técnica:** Todos los modelos ofrecen respuestas correctas, aunque con diferente profundidad.  
2. **Nivel de detalle:** Claude tiende a ser más completo y crítico; Gemini destaca en ejemplos aplicados; ChatGPT ofrece explicaciones claras y accesibles.  
3. **Limitaciones:** Ningún modelo ofrece referencias explícitas ni ejemplos de casos reales a gran escala. Esto confirma que los LLMs sirven como punto de partida, pero requieren verificación bibliográfica [3], [7].  

---

## Aplicaciones en el contexto de LLMs

- El entrenamiento distribuido de LLMs depende de redes como **InfiniBand** y topologías **Dragonfly**, que permiten minimizar la latencia [3].  
- Estrategias de enrutamiento adaptativo son esenciales para evitar congestión durante operaciones colectivas [5].  
- Los sistemas híbridos (clusters NUMA + GPUs) constituyen la infraestructura predominante en proyectos como GPT-4 y Gemini [10].  

---

## Conclusiones

1. La arquitectura paralela y la comunicación interna son pilares esenciales en el desarrollo de LLMs.  
2. Las topologías Dragonfly y torus, junto a enrutamiento adaptativo, representan la base tecnológica más prometedora.  
3. Los LLMs pueden apoyar la investigación técnica como **herramienta inicial de exploración**, pero no sustituyen el rigor académico ni las fuentes primarias [11].  
4. La complementariedad de ChatGPT, Gemini y Claude sugiere que el uso combinado de varios modelos puede enriquecer la investigación.  

---
📄 [Descargar informe completo en PDF](Trabajo. Análisis de Métodos de Comunicación Interna en Computadores Paralelos_EC_RuanoAnyi_.pdf)

## 📚 Referencias Bibliográficas

* **[1]**	Asociación Española de Arquitectura de Computadores, "Actas de las jornadas técnicas anuales", 2021-2023.
* **[2]**	Barcelona Supercomputing Center, "Curso de programación paralela con MPI y OpenMP", Materiales del curso, 2023. [En línea]. Disponible: https://www.bsc.es/education
* **[3]**	C. Rodríguez León y M. P. González Vidal, "Diseño de clusters optimizados para el entrenamiento de grandes modelos de lenguaje", en Actas de las Jornadas de Paralelismo, Almería, España, 2023, pp. 234-245.
* **[4]**	Consulta a ChatGPT-4 Turbo. (24 de mayo de 2024). OpenAI. [Transcripción completa de las respuestas técnicas sobre arquitectura paralela].
* **[5]**	Consulta a Claude 3 Opus. (24 de mayo de 2024). Anthropic. [Transcripción completa de las respuestas técnicas sobre HPC y LLMs].
* **[6]**	Consulta a Gemini Advanced. (24 de mayo de 2024). Google. [Transcripción completa de las respuestas técnicas sobre sistemas distribuidos].
* **[7]**	E. Fernández Martínez y R. Torres Rodríguez, "Evaluación comparativa de estrategias de enrutamiento en redes de interconexión para HPC", en Congreso Español de Informática, Granada, España, 2022, pp. 112-125.
* **[8]**	E. González Castro, "Optimización de comunicaciones en sistemas paralelos para aplicaciones de deep learning", Tesis doctoral, Universidad de Málaga, 2023.
* **[9]**	European Processor Initiative, "Arquitecturas de procesadores para computación exascale", Documento técnico, 2023. [En línea]. Disponible: https://www.european-processor-initiative.eu/
* **[10]**	F. García Sánchez, Computación de Alto Rendimiento: Arquitecturas Paralelas y Distribuidas. Madrid: McGraw-Hill, 2021.
* **[11]**	Google AI, "Arquitectura de sistemas TPU para entrenamiento de modelos a escala", Documentación técnica, 2023. [En línea]. Disponible: https://cloud.google.com/tpu/docs/system-architecture
* **[12]**	IEEE Spain Section, "Boletín de arquitectura de computadores y sistemas paralelos", Publicación trimestral, 2022-2023.
* **[13]**	J. Díaz Martín et al., "Estado del arte en arquitecturas paralelas para inteligencia artificial: desafíos y tendencias", Revista de Procesamiento Paralelo y Distribuido, vol. 30, núm. 4, pp. 201-218, 2023.
* **[14]**	J. L. Hennessy y D. A. Patterson, Arquitectura de Computadores: Un Enfoque Cuantitativo, 6ª ed. Barcelona: Elsevier, 2018.
* **[15]**	J. M. Cecilia et al., "Optimización de operaciones colectivas en entornos MPI para el entrenamiento de modelos de deep learning", Journal of Computer Science and Technology, vol. 18, núm. 1, pp. 23-35, 2023.
* **[16]**	L. García Hernández y P. Sánchez López, "Análisis de escalabilidad en arquitecturas paralelas para aplicaciones de machine learning a gran escala", en Simposio Internacional de Arquitectura de Computadores, Málaga, España, 2023, pp. 78-92.
* **[17]**	M. A. Pérez Sánchez, "Diseño y evaluación de topologías de interconexión para computación exascale", Tesis doctoral, Universidad Politécnica de Madrid, 2022.
* **[18]**	M. Valero Cortés y E. Zapata Marcos, Arquitecturas Paralelas: De los Multiprocesadores a los Clusters. Barcelona: Edicions UPC, 2019.
* **[19]**	Mellanox Technologies, "InfiniBand para aplicaciones de inteligencia artificial y HPC", White Paper, 2022. [En línea]. Disponible: https://www.mellanox.com/products/infiniband
* **[20]**	Ministerio de Ciencia e Innovación, "Estrategia Nacional de Inteligencia Artificial", Gobierno de España, 2022. [En línea]. Disponible: https://www.ciencia.gob.es/estrategias/IA
* **[21]**	MPI Forum, "Estándar MPI 4.0: Especificación completa", 2021. [En línea]. Disponible: https://www.mpi-forum.org/docs/
* **[22]**	NVIDIA Corporation, "Guía de optimización de NCCL para clusters de IA", Documentación técnica, 2023. [En línea]. Disponible: https://docs.nvidia.com/deeplearning/nccl
* **[23]**	OpenMP Architecture Review Board, "Especificación OpenMP 5.2", 2021. [En línea]. Disponible: https://www.openmp.org/specifications/
* **[24]**	P. López García y M. J. Acosta López, "Análisis de topologías de interconexión para clusters de computación de altas prestaciones", Revista Iberoamericana de Informática Educativa, vol. 25, núm. 2, pp. 45-62, 2022.
* **[25]**	R. Sánchez García y M. L. Pérez Martínez, "Evaluación de tecnologías emergentes en interconexión para HPC", Journal of Supercomputing, vol. 79, núm. 8, pp. 8912-8935, 2023.
* **[26]**	R. Suppi y E. Luque, Sistemas Distribuidos y Paralelos: Conceptos y Aplicaciones. Madrid: Pearson Educación, 2020.
* **[27]**	Red Española de Supercomputación, "Guía de mejores prácticas para computación de altas prestaciones", Documentación técnica, 2023. [En línea]. Disponible: https://www.res.es/documentacion
* **[28]**	A. Gómez Martínez y S. Ramos Pollán, "Arquitecturas híbridas CPU-GPU para inteligencia artificial: retos y oportunidades", Inteligencia Artificial: Revista Iberoamericana de Inteligencia Artificial, vol. 26, núm. 72, pp. 67-82, 2023.
  
---
