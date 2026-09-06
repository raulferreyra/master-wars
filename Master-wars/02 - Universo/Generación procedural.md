# Generación procedural

La generación procedural crea variedad reproducible sin romper el Lore. Usa `seed`, versión de generador y reglas de distribución; nunca nombres o valores aleatorios sin contexto.

## Restricciones obligatorias

- 600 sistemas por universo.
- Una estrella y 16 órbitas por sistema.
- Solo 3, 4, 5, 7, 9 o 16 planetas por sistema.
- De 0 a 3 lunas por planeta.
- Los números reservados por [[Sistemas Lore]] no se alteran.
- Toda propiedad derivada debe poder reconstruirse desde los datos guardados.

El generador debe conservar tanto los valores base como sus resultados derivados. Así se puede explicar por qué un planeta produce un recurso o por qué requiere tecnología para ser colonizado.
