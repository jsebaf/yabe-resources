# OpenCode: diseño, desarrollo y despliegue

## Sesión 1

### Panorama de la IA en el desarrollo y ciclo de vida de un producto de software

Evolución reciente de la IA aplicada al desarrollo de software y distintos niveles de implicación de la IA, desde el autocompletado de código hasta los agentes autónomos y el *vibe coding*. Análisis del *trade-off* entre el control y la comprensión por parte del desarrollador, y la velocidad y el grado de delegación.

Repaso muy breve de las principales técnicas de IA y evolución hacia los grandes modelos de lenguaje (LLM).

### LLM y agentes de IA

Introducción al funcionamiento básico de los LLM: tokenización, predicción del siguiente token y contexto. Concepto del LLM como sistema sin estado y necesidad de proporcionar el contexto en cada interacción.

Ejemplo de utilización de un chatbot web como asistencia al desarrollo y análisis de las limitaciones de este enfoque.

- Concepto de contexto.
- Concepto de herramienta.
- El agente como un sistema que combina modelo, contexto y herramientas en un ciclo iterativo de decisión y acción.

### Introducción a OpenCode

- OpenCode como agente de IA para el desarrollo de software.
- Conceptos de *prompt*, contexto, modelo y herramientas.
- Tokens de entrada y salida y coste de las interacciones.
- Relación entre cantidad de contexto y coste.
- Selección de proveedores y modelos.
- Flujos de interacción con el modelo: interacciones simples y procesos de varios pasos.

### Primeros pasos

- Trabajo sobre un proyecto existente.
- Exploración del proyecto mediante el agente.
- Modificación del proyecto y ejecución de acciones mediante herramientas.
- Análisis de las interacciones entre el agente y el modelo.
- Trabajo en un proyecto nuevo.
- Planificación e implementación.
- Ejemplo simple de una iteración.

|                                          | Artefacto                                                      |
| ---------------------------------------- | -------------------------------------------------------------- |
| ¿Qué es un agente de IA y cómo funciona? | OpenCode instalado y primer proyecto modificado por el agente. |

---

## Sesión 2

### Introducción al proyecto de ejemplo

- Explicación del proyecto desde un punto de vista funcional: un motor de reservas de hotel. Listado de requisitos funcionales.
- Explicación de la arquitectura propuesta: un servicio en Laravel que expone una API autenticada para la creación, modificación y consulta de reservas de hotel.
- Ejemplo de interfaz de usuario: una aplicación web sencilla en React con Tailwind CSS.
- Esquema de seguridad para la comunicación entre la UI y la API.
- Persistencia mediante una base de datos PostgreSQL.

### Definición del flujo de trabajo

Explicación de un modelo de trabajo en el que las *features* se documentarán en GitHub Issues y, a partir de estas, se desencadenará un flujo de análisis, implementación y pruebas asistido por el agente.

### Reglas e instrucciones

- Explicación de los conceptos de reglas e instrucciones del agente.
- Primera aproximación a la implementación del flujo de trabajo definido anteriormente mediante reglas de OpenCode.
- Implementación de un conjunto inicial de *features* utilizando la aproximación anterior.

| Tema                                                           | Artefacto                                                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| ¿Cómo hacemos que el agente trabaje dentro de nuestro proceso? | Proyecto Laravel, flujo de trabajo definido y primeras *features* implementadas. |

---

## Sesión 3

### Comandos y habilidades

- Explicación de los conceptos de comandos y habilidades (*skills*).
- Diferencias entre instrucciones generales, comandos y *skills*, y papel de cada mecanismo dentro del flujo de trabajo.
- Automatización del flujo de trabajo mediante comandos y *skills*.
- Evolución del flujo definido en la sesión anterior hacia un proceso más sistemático y reutilizable.
- Implementación de las *features* restantes del backend utilizando el flujo de trabajo automatizado.

### MCP

- Concepto de MCP y necesidad de ampliar las capacidades del agente mediante herramientas y fuentes de información externas.
- Configuración de servidores MCP en OpenCode.
- Utilización de MCP dentro del flujo de trabajo.
- Implementación de las *features* correspondientes a la UI con la asistencia de MCP.

| Tema                                                        | Artefacto                                                                     |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------- |
| ¿Cómo automatizamos y ampliamos las capacidades del agente? | Flujo de trabajo automatizado y aplicación completa, incluyendo backend y UI. |

---

## Sesión 4

### Implementación de un agente para el análisis de datos

Planteamiento de una necesidad de negocio que requiera obtener información de la aplicación y analizarla.

- Planteamiento de la necesidad y definición de los datos necesarios.
- Diseño de una arquitectura basada en un agente y herramientas externas.
- Diseño e implementación de un servidor MCP para la extracción de datos.
- Incorporación de capacidades de análisis al agente.
- Diseño e implementación de una herramienta para la presentación de los resultados.
- Utilización del agente para realizar el análisis y obtener información a partir de los datos.

### Aprovisionamiento y despliegue

Aplicación de las herramientas y conceptos trabajados en las sesiones anteriores para extender el uso del agente al ciclo de vida de despliegue de la aplicación.

- Descripción de la infraestructura necesaria para ejecutar la aplicación.
- Definición del aprovisionamiento de la infraestructura como código.
- Utilización del agente para analizar, diseñar e implementar la infraestructura.
- Automatización del proceso de construcción y despliegue de la aplicación.
- Integración del despliegue en el flujo de trabajo del proyecto.
- Análisis de la capacidad del agente para trabajar sobre sistemas que van más allá del código de la aplicación.

| Tema                                                                                   | Artefacto                                                                                                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ¿Hasta dónde podemos extender el uso del agente fuera del desarrollo de la aplicación? | Aplicación desplegada automáticamente e infraestructura gestionada mediante código. Agente de análisis de datos con acceso a las fuentes de información del sistema. |

---

## Sesión 5

### Troubleshooting y observabilidad

Aplicación del agente al diagnóstico y resolución de problemas sobre un sistema desplegado.

- Concepto de observabilidad y principales fuentes de información: logs, métricas y trazas.
- Instrumentación básica de la aplicación para obtener información útil para el diagnóstico.
- Generación de tráfico y situaciones controladas que permitan observar el comportamiento del sistema.
- Recogida y visualización de métricas mediante herramientas de observabilidad.
- Análisis de errores y anomalías a partir de la información disponible.
- Utilización del agente como asistente para el diagnóstico de problemas.
- Relación entre observabilidad, troubleshooting y ciclo de desarrollo.

| Tema                                                                                | Artefacto                                                                                                 |
| ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| ¿Cómo utilizamos un agente para entender y solucionar problemas en un sistema real? | Sistema desplegado con observabilidad básica y un flujo de generación, detección y análisis de problemas. |
