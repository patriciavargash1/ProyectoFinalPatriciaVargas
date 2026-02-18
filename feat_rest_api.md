# Análisis de Arquitectura REST: El Problema del Over-fetching

## 1. Objetivo
Documentar la eficiencia de la arquitectura REST mediante la solicitud de un recurso específico y analizar la cantidad de datos innecesarios recibidos en comparación con los requerimientos mínimos del sistema.

## 2. Detalles de la Petición
- **Herramienta utilizada:** ReqBin (Cliente REST en línea).
- **Método HTTP:** `GET`.
- **Endpoint:** `https://pokeapi.co/api/v2/pokemon/1/` (Recurso: Bulbasaur).

## 3. Análisis de Resultados
Al realizar la consulta del recurso completo, el servidor respondió con un **JSON masivo y complejo** que contiene toda la información disponible del Pokémon.

### Requerimientos del Sistema:
Para el diseño de nuestra interfaz, solo necesitamos los siguientes campos:
1. `name`
2. `weight`
3. `height`

### Evidencia de Over-fetching:
A pesar de solo requerir 3 campos, la respuesta REST devolvió cientos de líneas de datos adicionales. Se identificaron las siguientes secciones como **irrelevantes** para nuestra necesidad actual:
- **`moves`**: Una lista extensa de todos los movimientos que el Pokémon puede aprender.
- **`abilities`**: Detalles técnicos de las habilidades.
- **`game_indices`**: Referencias a versiones específicas de los juegos.
- **`sprites`**: Múltiples URLs de imágenes que no fueron solicitadas.

## 4. Conclusión Técnica
La arquitectura REST, al no permitir filtrar campos desde la consulta, obliga al cliente a descargar un volumen de datos significativamente mayor al necesario. Esto impacta directamente en el consumo de ancho de banda y en los tiempos de procesamiento del lado del cliente..