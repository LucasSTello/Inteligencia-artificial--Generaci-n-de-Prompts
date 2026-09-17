# Marco Metodológico: Fast Prompting e Ingeniería de Prompts en StudyAI

**Proyecto Final:** StudyAI — Asistente Inteligente para la Generación de Planes de Estudio  
**Curso:** IA: Entretejiendo Imaginación y Algoritmos  
**Autor:** Lucas Tello  

---

## 1. Introducción y Enfoque Metodológico

La ingeniería de prompts (*Prompt Engineering*) ha evolucionado desde la formulación empírica de instrucciones informales hacia una disciplina metodológica sistemática y estructurada. En el contexto de modelos fundacionales basados en transformadores (como la familia GPT de OpenAI), el modelo opera como un predictor probabilístico condicionado por el espacio semántico y contextual que define el *prompt*.

El enfoque de **Fast Prompting** adoptado en este proyecto no consiste en redactar directivas apresuradas, sino en aplicar un ciclo rápido, riguroso e iterativo de:
1. **Identificación de Necesidades**: Detección de requerimientos cognitivos y restricciones operativas del estudiante.
2. **Formulación Estructurada**: Selección deliberada de técnicas de estimulación semántica.
3. **Ejecución y Observación**: Evaluación crítica de la respuesta obtenida frente a casos de prueba reales.
4. **Refinamiento Basado en Evidencia**: Corrección de desviaciones, adición de anclas semánticas (*grounding*) y restricciones explícitas.

---

## 2. Catálogo de Técnicas Aplicadas y su Justificación Pedagógica

Cada técnica incorporada en StudyAI responde a un objetivo funcional específico dentro de la solución, evitando la acumulación artificial de conceptos:

### 2.1. Role Prompting (Asignación de Rol)
* **Definición**: Condiciona al modelo a adoptar una identidad profesional, estilo comunicativo y marco ético/técnico específico.
* **Aplicación en StudyAI**: Se define al modelo como *"Asesor Académico de Élite y Especialista en Ciencia del Aprendizaje y Planificación del Estudio Universitario"*.
* **Justificación**: Modula la probabilidad de los tokens para favorecer un tono pedagógico, analítico, empático y estructurado, alejando al modelo de respuestas genéricas o coloquiales.

### 2.2. Context Prompting (Contextualización Situacional)
* **Definición**: Provee la información de entorno que circunscribe el problema del usuario.
* **Aplicación en StudyAI**: Inyección de variables explícitas: materia, lista temática, disponibilidad horaria diaria, total de días, nivel actual, fecha límite, objetivos y preferencias.
* **Justificación**: Reduce la incertidumbre del modelo (*perplexity* contextual) y ancla el razonamiento a la realidad concreta del estudiante.

### 2.3. Instruction Prompting (Instrucciones Directivas)
* **Definición**: Directrices explícitas sobre qué tareas procesar secuencialmente.
* **Aplicación en StudyAI**: Mandatos claros de clasificar la dificultad, desglosar las sesiones día por día y estructurar los tiempos.

### 2.4. Few-Shot Prompting (Demostración por Ejemplos)
* **Definición**: Presentación de uno o más pares de entrada-salida o micro-patrones estructurales dentro del contexto.
* **Aplicación en StudyAI**: Se introduce un micro-ejemplo de bloque diario (desglose horario en minutos: 15 min repaso activo, 40 min bloque teórico, 10 min pausa activa, 40 min práctica deliberada, 15 min autoevaluación).
* **Justificación**: Demuestra al modelo el formato sintáctico y el nivel de granularidad esperado sin necesidad de describir prolijamente cada detalle, garantizando coherencia formal.

### 2.5. Structured Prompting (Estructuración Sintáctica)
* **Definición**: Uso de delimitadores visuales (===, ###, viñetas, tablas Markdown) para segmentar el prompt.
* **Aplicación en StudyAI**: Separación nítida entre datos de entrada, restricciones, ejemplos y las 9 secciones obligatorias de salida.
* **Justificación**: Facilita la atención cruzada (*cross-attention*) del modelo, evitando que las restricciones se diluyan en párrafos densos.

### 2.6. Restricciones Explícitas y Negative Constraints (Grounding y Anti-alucinación)
* **Definición**: Reglas prohibitivas y de validación de límites.
* **Aplicación en StudyAI**:
  - Prohibición estricta de incorporar materias o conceptos no brindados por el estudiante.
  - Obligación matemática de que la suma de minutos de cada día sea idéntica al presupuesto diario declarado (ej. 2 horas = 120 minutos).
* **Justificación**: Erradica dos de los fallos más comunes en planificación por IA: la sobrecarga del estudiante con agendas irreales y la invención de contenidos.

### 2.7. Task Decomposition (Descomposición Modular de Tareas)
* **Definición**: División de una tarea compleja en subtareas manejables ejecutadas en secuencia lógica.
* **Aplicación en StudyAI**: El plan no se solicita en un solo paso difuso; se descompone en 9 fases:
  1. Diagnóstico situacional.
  2. Matriz de priorización.
  3. Desglose cronológico por día.
  4. Tabla de presupuesto temporal minuto a minuto.
  5. Objetivos de aprendizaje operativos.
  6. Técnicas de estudio activo aplicadas.
  7. Estrategia de repaso espaciado.
  8. Autoevaluaciones prácticas.
  9. Gestión del descanso previo al examen.

### 2.8. Iteración y Refinamiento Progresivo
* **Definición**: Desarrollo empírico comparando versiones progresivas (V1 -> V2 -> V3) para validar ganancias incrementales de calidad.

---

## 3. Matriz Cualitativa de Evaluación

Para evitar la invención de puntuaciones numéricas ficticias no respaldadas por pruebas psicométricas o estadísticas, se establece un marco de **evaluación cualitativa multidimensional** basado en 6 criterios:

1. **Claridad**: Legibilidad del lenguaje, comprensión inmediata de las instrucciones y ausencia de ambigüedad.
2. **Organización**: Jerarquía visual, uso de Markdown, tablas de tiempo y secuenciación lógica de los días.
3. **Personalización**: Ajuste explícito al nivel del estudiante (intermedio), preferencias declaradas (bloques cortos, práctica, repaso) y materia.
4. **Cumplimiento de Instrucciones**: Adherencia rigurosa a las restricciones, presupuesto horario y los 9 bloques solicitados.
5. **Utilidad para el Estudiante**: Valor práctico y aplicabilidad inmediata del plan sin requerir reordenamiento manual.
6. **Consistencia de la Respuesta**: Estabilidad estructural y ausencia de contradicciones temporales o conceptuales.

---

## 4. Sinergia Multimodal (Texto e Imagen)

La integración del modelo texto-imagen se fundamenta en la **Teoría de la Doble Codificación de Paivio (Dual Coding Theory)**:
* La información procesada mediante canales verbales (plan textual detallado con minutos y ejercicios) y canales no verbales (infografía visual del calendario semanal) se almacena en subsistemas cognitivos separados pero interconectados.
* El texto aporta la **precisión operativa** (qué hacer en el minuto 45), mientras que la imagen proporciona el **mapa cognitivo global** (visión holística de los 7 días, hitos y ritmo de avance), reduciendo la ansiedad y la fatiga mental del estudiante.