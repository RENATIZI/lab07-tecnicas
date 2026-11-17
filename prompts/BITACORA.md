



# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting. Herramienta de IA usada: GEMINI

## Ejercicio 2:
Zero-shot, one-shot y few-shot
| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot |3 | libre|no |
| One-shot | 4|libre | si|
| Few-shot |3 |libre | no|
## Ejercicio 3:
Chain of Thought
| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
| --- | --- | --- | --- |
| Directo | | | |
| Paso a paso | S/ 318.60 | Si | Si |
## Ejercicio 4:
Role prompting
| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---|---|---|---|
| A. Sin rol | Neutro y general (equilibrio entre sencillo y técnico) | Sí, usa analogías cotidianas (como una caja) y ejemplos genéricos de pseudocódigo o lenguajes populares | A cualquier persona que busca una definición rápida y estándar por primera vez |
| B. Rol docente | Muy sencillo, didáctico y estructurado paso a paso | Sí, usa ejemplos cotidianos muy simples y ejercicios básicos para asegurar la comprensión | A estudiantes principiantes o personas sin experiencia previa en programación |
| C. Rol senior | Técnico pero práctico (usa términos de Java como RAM, *camelCase*, tipado estático y `final`, combinados con la metáfora de la bodega) | Sí, incluye un bloque de código real en Java con buenas prácticas y consejos de producción para evitar *bugs* | A desarrolladores junior o compañeros de equipo que ya tienen nociones básicas y necesitan aplicar el concepto en proyectos reales |
Descomposicion
## Ejercicio 5:

## Ejercicio 6:
Prompt estructurado y autocritica
### 4. Evaluar. Revisa la tabla final y anota en tu bitácora:

| Qué revisar | Cumple (Sí / No) |
| :--- | :--- |
| ¿Tiene las 4 columnas pedidas? | **Sí** *(ID, Escenario, Datos de entrada, Resultado esperado)* |
| ¿Incluye el bloqueo después de 3 intentos? | **Sí** *(Caso CP-03)* |
| ¿Incluye casos con campos vacíos? | **Sí** *(Caso CP-07)* |
| ¿Indica qué casos agregó en la autocrítica? | **Sí** *(Se detallaron CP-06 desglosado y CP-07 al CP-09 nuevos)* |
| ¿Hay algún caso repetido o que no tenga sentido? | **No** *(Cada caso evalúa una condición única y coherente)* |

- [Bitacora de tecnicas avanzadas](prompts/BITACORA.md)
