# Documentación Técnica: Eficiencia de Consultas con GraphQL

## 1. Objetivo
Demostrar la capacidad de **GraphQL** para optimizar la obtención de datos, permitiendo al cliente solicitar exactamente lo que necesita y obtener recursos relacionados en una única transacción,.

## 2. Detalles del Experimento
- **Entorno de prueba:** GraphQL Pokémon API Playground,.
- **Endpoint:** `https://graphql-pokemon2.vercel.app/`,.
- **Método:** Consulta anidada (Relaciones),.

## 3. Consulta Ejecutada (Query)
Para evitar la sobre-recuperación de datos y obtener información vinculada de forma eficiente, se diseñó la siguiente consulta:

```graphql
query {
  pokemon(id: "UG9rZW1vbjowMDE=") {
    name
    weight
    height
    evolutions {
      name
    }
  }
}