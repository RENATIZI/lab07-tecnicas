# Tarea: Mi prompt avanzado

## Tarea elegida
Diseñar una suite de casos de prueba unitarios y funcionales para un módulo de registro de usuarios (validación de correo electrónico, contraseña segura y verificación de duplicados en base de datos) en una aplicación backend escrita en Java.

## Version 1: prompt basico

```text
Genera casos de prueba para el registro de usuarios de mi sistema.
```

* **Técnica agregada:** Ninguna (Zero-shot básico).
* **Por qué:** Sirve como línea base para observar cómo responde el modelo sin restricciones de rol, contexto ni formato.
* **Qué mejoró:** Al ser la primera versión, entregó una lista genérica en texto corrido mezclando pruebas visuales con lógica de negocio, sin valores de entrada concretos ni resultados esperados claros.

## Version 2

```text
Actúa como un Ingeniero de QA Senior especializado en pruebas automatizadas de aplicaciones backend en Java con JUnit 5.

Genera casos de prueba para el método `registrarUsuario(String email, String password)` de un sistema de registro. Incluye casos válidos, inválidos y valores límite.

Formato de salida: Presenta los casos únicamente en una tabla Markdown con las columnas: ID, Escenario, Datos de Entrada, Resultado Esperado.
```

* **Técnica agregada:** Role Prompting (rol específico de Ingeniero de QA Senior) y Prompt Estructurado (formato de salida definido en tabla Markdown con columnas exactas).
* **Por qué:** La versión 1 era demasiado ambigua y desordenada; necesitaba acotar la respuesta al entorno backend de Java y obligar a la IA a estructurar los datos de prueba de forma legible.
* **Qué mejoró:** Eliminó las pruebas de interfaz innecesarias, separó claramente los datos de entrada del resultado esperado y organizó todo en una tabla limpia. Sin embargo, omitió casos críticos de seguridad (como valores nulos o espacios en blanco) y no explicó por qué eligió cada caso límite.

## Version 3: prompt final

```text
Actúa como un Ingeniero de QA Senior especializado en pruebas automatizadas de aplicaciones backend en Java con JUnit 5.

Tu objetivo es diseñar casos de prueba exhaustivos para el método `registrarUsuario(String email, String password)` cuyas reglas de negocio son:
1. El email debe tener formato válido y no existir previamente en la base de datos.
2. La contraseña debe tener entre 8 y 16 caracteres, al menos una mayúscula y un número.

Sigue este proceso paso a paso:
- Paso 1 (Descomposición): Identifica primero las particiones de equivalencia y valores límite para cada regla de negocio.
- Paso 2 (Chain of Thought): Razona brevemente qué fallos comunes suelen ocurrir en cada partición antes de escribir los casos.
- Paso 3 (Generación con ejemplos): Genera al menos 6 casos de prueba siguiendo exactamente la estructura de este ejemplo:

Ejemplo:
| ID | Tipo | Escenario | Entrada (email / password) | Resultado Esperado |
|---|---|---|---|---|
| TC-01 | Positivo | Registro exitoso con datos estándar | usuario@dominio.com / Clave123 | Retorna HTTP 201 y usuario guardado |

- Paso 4 (Autocrítica): Al final de la tabla, revisa tus propios casos generados y señala si falta algún caso borde crítico (ej. valores nulos o espacios) agregándolo si es necesario.
```

* **Técnica agregada:** Descomposición, Chain of Thought (Cadena de pensamiento), Few-shot (un ejemplo guía) y Autocrítica.
* **Por qué:** Para asegurar cobertura total en producción, no basta con pedir una tabla; el modelo debe analizar primero las reglas de negocio, guiarse por un estándar exacto de redacción y auditar su propia respuesta para no olvidar valores nulos (`null`).
* **Qué mejoró:** La respuesta incluyó el análisis previo de particiones, respetó al 100% la nomenclatura `TC-XX` del ejemplo, cubrió casos borde complejos (`null`, contraseñas de 7 y 17 caracteres, correos duplicados) y añadió una verificación final de calidad.

## Tecnicas usadas en el prompt final

| Parte del prompt final | Técnica aplicada | Función dentro del prompt |
|---|---|---|
| *"Actúa como un Ingeniero de QA Senior especializado en pruebas automatizadas de aplicaciones backend en Java con JUnit 5."* | **Role Prompting** | Define un perfil técnico concreto (evitando el genérico "experto") para usar terminología de JUnit y backend. |
| *"Paso 1 (Descomposición): Identifica primero las particiones de equivalencia y valores límite..."* | **Descomposición** | Divide el problema complejo de probar un registro completo en sub-reglas manejables (email y contraseña). |
| *"Paso 2 (Chain of Thought): Razona brevemente qué fallos comunes suelen ocurrir..."* | **Chain of Thought** | Obliga al modelo a analizar posibles errores antes de redactar los casos, evitando respuestas superficiales. |
| *"Ejemplo: \| TC-01 \| Positivo \| Registro exitoso..."* | **Few-shot Prompting** | Muestra el formato exacto de tabla, columnas y nivel de detalle esperado para los datos de entrada. |
| *"Paso 4 (Autocrítica): Al final de la tabla, revisa tus propios casos generados y señala si falta algún caso borde..."* | **Autocrítica** | Hace que la IA audite su propia tabla y corrija omisiones (como entradas `null`) antes de dar por terminada la respuesta. |

## Evaluacion del resultado

| Criterio de evaluación | Cumple (Sí / No) | Observación |
|---|---|---|
| ¿El rol asignado es específico y acorde a la tarea de software? | Sí | Se definió como Ingeniero de QA Senior en Java/JUnit 5,
