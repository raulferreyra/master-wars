# Big Bang

El **Big Bang** es el proceso de creación de un universo-servidor. Se ejecuta una sola vez al abrir un universo y conserva la semilla utilizada.

## Entrada y resultado

- **Entrada:** identificador del universo, `seed` y versión del generador.
- **Resultado:** 600 sistemas solares numerados, con sus estrellas, órbitas, planetas, lunas y Espacio Lejano.

La misma semilla y la misma versión del generador deben producir exactamente el mismo resultado procedural. Los [[Sistemas Lore]] se insertan después de generar la estructura y siempre reemplazan el resultado de su número reservado.

## Orden de generación

1. Reservar los números de sistemas de Lore.
2. Generar los sistemas procedurales restantes.
3. Asignar una estrella a cada sistema.
4. Distribuir de 3, 4, 5, 7, 9 o 16 planetas en sus 16 [[Órbitas]].
5. Derivar propiedades planetarias, lunas, habitabilidad y recursos.
6. Insertar los sistemas de Lore inmutables.
7. Validar límites y guardar el manifiesto del universo.
