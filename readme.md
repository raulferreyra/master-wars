# Master Wars

Master Wars es un juego de estrategia multijugador para navegador inspirado en títulos como **OGame, Ikariam, Forge of Empires y Tribal Wars**, pero construido alrededor de un universo procedural, un Lore fijo y una simulación que evoluciona a partir de las decisiones de los jugadores.

El proyecto busca combinar:

- Generación procedural de universos.
- Estrategia y administración de recursos.
- Colonización espacial.
- Facciones y razas con identidades propias.
- Exploración y expansión.
- Progresión mediante títulos y logros.
- Un Lore común para todos los universos.
- Una historia emergente diferente en cada servidor.

---

## Concepto central

Cada **universo es un servidor independiente**.

Todos los universos parten del mismo punto histórico y contienen los mismos elementos definidos por el Lore. Sin embargo, gran parte del espacio disponible se genera proceduralmente mediante un **Big Bang**, utilizando una semilla (`seed`) que permite producir un universo único y reproducible.

La premisa inicial es:

> La humanidad acaba de iniciar su expansión espacial gracias al conocimiento recibido de los marcianos y a la tecnología venusiana. Al mismo tiempo, las demás civilizaciones también comienzan su propia expansión.

A partir de ese instante, las acciones de los jugadores determinan la historia particular de cada universo.

---

## Estructura general

```text
Master Wars
│
├── Obsidian/
│   └── Diseño, reglas, Lore y documentación
│
├── Go/
│   └── Backend, motor de juego y generación del universo
│
└── React/
    └── Interfaz web y representación visual del universo
```

La documentación se define primero en **Obsidian**. El código deberá implementar las reglas establecidas en esa documentación.

---

## Universo

Cada universo:

- Es un servidor independiente.
- Tiene un máximo de **600 sistemas solares**.
- No interactúa con otros universos.
- Se genera mediante un **Big Bang** al inicializarse.
- Utiliza una semilla para permitir generación reproducible.
- Mantiene una estructura espacial común.
- Contiene sistemas procedurales y sistemas definidos por el Lore.

Los sistemas están numerados:

```text
001 → 002 → 003 → ... → 598 → 599 → 600
```

La navegación del visor será circular:

```text
600 → 001
001 → 600
```

Esto representa la continuidad espacial del universo dentro de la representación del juego.

---

## Sistemas solares

Cada sistema solar contiene:

- Una única estrella.
- Exactamente **16 órbitas**.
- Entre **3, 4, 5, 7, 9 o 16 planetas**.
- Entre 0 y 3 lunas por planeta.
- Un Espacio Lejano.
- Planetas procedurales o elementos definidos por el Lore.

Un sistema con tres planetas sigue teniendo las 16 órbitas:

```text
Órbita 01 → vacía
Órbita 02 → planeta
Órbita 03 → vacía
Órbita 04 → vacía
...
Órbita 07 → planeta
...
Órbita 14 → planeta
...
Órbita 16 → vacía
```

Las órbitas ocupadas por sistemas procedurales se determinan aleatoriamente.

---

## Estrellas

Inicialmente existen tres tipos:

1. **Enana Blanca**
2. **Mediana Amarilla**
3. **Gigante Roja**

El tipo de estrella podrá influir en las características y probabilidades de generación de su sistema.

---

## Planetas

Los planetas se generan a partir de diferentes propiedades físicas y ambientales.

Entre las propiedades previstas se encuentran:

- Masa.
- Tamaño.
- Temperatura.
- Composición.
- Agua.
- Atmósfera.
- Vegetación.
- Actividad geológica.
- Radiación.
- Habitabilidad.
- Densidad mineral.
- Otras propiedades que se definirán durante el diseño.

Estas propiedades deberán utilizarse para derivar las características económicas del planeta.

La intención es evitar un sistema arbitrario donde los recursos simplemente "aparezcan". La producción deberá tener una relación lógica con las condiciones del planeta.

---

## Habitabilidad

No todos los planetas son colonizables.

Existirán planetas:

- Habitables.
- Hostiles pero colonizables.
- No habitables.

Por ejemplo, un planeta tóxico puede ser colonizado mediante procesos y tecnología adecuados.

En cambio, un planeta definido como no habitable, como determinados planetas completamente gaseosos o de agua, no podrá ser colonizado bajo las reglas normales del juego.

---

## Lunas

Cada planeta puede tener:

```text
0 → 1 → 2 → 3 lunas
```

Nunca se generarán más de tres.

El tamaño y otras características del planeta podrán influir en la probabilidad de generación de sus lunas.

---

## Nombres procedurales

Los nombres de planetas generados proceduralmente no utilizarán caracteres aleatorios.

Cada raza tendrá un conjunto controlado de **sílabas válidas**.

Los nombres tendrán entre **2 y 8 sílabas**.

El sistema podrá utilizar deliberadamente:

- Vocales.
- Consonantes.
- Tildes.
- Diéresis.
- Otros elementos lingüísticos definidos para cada idioma.

El objetivo es generar nombres extraños pero coherentes con la identidad lingüística de cada raza.

Los nombres serán posteriormente modificables por el jugador cuando un planeta sea colonizado.

Se deberá conservar el nombre original generado para mantener la identidad histórica del planeta.

---

## Planetas y sistemas del Lore

Los elementos del Lore son **inmutables**.

Todos los universos tienen la misma historia inicial y los mismos sistemas definidos por el Lore.

Ejemplos:

```text
Sistema 025 → Animalias
Sistema 052 → Robotas
Sistema 137 → Sistema Solar / Tierra
```

El sistema de numeración es fijo.

La generación funciona de la siguiente manera:

```text
001–024 → Procedural
025      → Lore: Animalias
026–051 → Procedural
052      → Lore: Robotas
053–136 → Procedural
137      → Lore: Sistema Solar
138–600 → Procedural
```

Los sistemas Lore:

- Siempre aparecen.
- Mantienen su número.
- Mantienen su posición.
- Mantienen sus planetas.
- Mantienen sus razas.
- Mantienen sus facciones.
- No pueden ser modificados por el jugador.
- No pueden ser destruidos.
- No pueden ser renombrados.
- No pueden ser sustituidos por generación procedural.

Los sistemas Lore también respetan la estructura de 16 órbitas, pero la configuración de sus planetas está definida por el Lore y no por el generador aleatorio.

---

## Espacio Lejano

Cada sistema solar dispone de una zona denominada **Espacio Lejano**.

Será utilizada posteriormente para:

- Exploración.
- Minería de asteroides.
- Obtención de recursos.
- Misiones.
- Otros eventos espaciales.

Su función inicial es ofrecer actividades fuera de los planetas y permitir operaciones con un nivel de riesgo diferente al de las zonas habitadas.

---

## Facciones y razas

Los jugadores deberán seleccionar:

```text
Facción
   ↓
Raza
```

Cada facción tendrá tres razas.

Las razas poseen:

- Identidad cultural.
- Idioma.
- Sistema de nombres.
- Terminología propia.
- Lore.
- Posibles características y tecnologías propias.

La definición exacta de las tres facciones y sus nueve razas se documentará posteriormente.

---

## Jugadores

Cada jugador tendrá dos identificadores.

### ID interno

Identificador técnico de la aplicación.

Ejemplo:

```text
00001
00002
00003
```

Será independiente de la raza y servirá para identificar internamente al jugador.

### Identificador público

El jugador recibirá un número público asociado a su raza.

La denominación cambia según la raza.

Ejemplo:

```text
Humanos:
Misión 69

Lupernos:
Camada 14

Rinocerontias:
Cría 37
```

El número indica el orden de incorporación de jugadores de esa raza dentro del universo.

El identificador público se genera **únicamente cuando el jugador finaliza correctamente su creación**.

Se registrará fecha y hora de creación para determinar el orden histórico de incorporación.

Los números no se reutilizan. Por tanto, pueden existir huecos:

```text
Misión 68
Misión 70
```

La ausencia de la Misión 69 es válida.

---

## Capital

Después de seleccionar facción y raza, el jugador recibirá un planeta capital.

La ubicación será asignada de manera que los nuevos jugadores puedan aparecer dentro de zonas adecuadas para la interacción con otros jugadores, evitando que el universo inicial coloque aleatoriamente a todos a distancias extremas.

El algoritmo concreto de distribución de jugadores será definido posteriormente.

---

## Títulos

Los títulos no serán elegidos libremente al comenzar.

Se desbloquearán mediante acciones, progreso o logros.

Ejemplos conceptuales:

```text
Alcanzar determinada cantidad de tropas
→ Capitán

Almacenar determinada cantidad de recursos
→ Administrador

Otros logros
→ Nuevos títulos
```

Un jugador podrá desbloquear múltiples títulos y posteriormente utilizar uno de ellos como título visible.

El catálogo definitivo y las condiciones de desbloqueo se definirán posteriormente.

---

## Arquitectura tecnológica

### Backend

**Go**

Responsabilidades previstas:

- API.
- Generación procedural.
- Motor de juego.
- Reglas de simulación.
- Economía.
- Jugadores.
- Colonización.
- Persistencia.
- Procesamiento de eventos.
- Seguridad y validaciones.

### Frontend

**React**

Responsabilidades previstas:

- Interfaz del jugador.
- Visor del universo.
- Visor de sistemas solares.
- Administración de planetas.
- Gestión de recursos.
- Construcción.
- Investigación.
- Flotas.
- Representación visual de las propiedades planetarias.

### Persistencia

Se contempla inicialmente una base de datos **NoSQL**.

La elección concreta del motor y el modelo definitivo de persistencia se establecerán durante el diseño técnico.

---

## Generación procedural

El universo comenzará mediante un proceso denominado **Big Bang**.

Conceptualmente:

```text
Seed
  ↓
Universe
  ↓
600 Solar Systems
  ↓
Star
  ↓
16 Orbits
  ↓
Planet Distribution
  ↓
Planet Properties
  ↓
Moons
  ↓
Resources / Derived Properties
  ↓
Far Space
```

Los sistemas definidos por el Lore se insertan en las posiciones correspondientes y no son sustituidos por resultados aleatorios.

La misma semilla deberá producir el mismo universo.

Esto permitirá:

- Reproducibilidad.
- Pruebas.
- Depuración.
- Recuperación.
- Análisis de generación.

---

## Filosofía del proyecto

Master Wars no pretende generar un universo completamente aleatorio sin restricciones.

La generación procedural debe utilizar:

> **Reglas + restricciones + aleatoriedad controlada.**

El objetivo es que cada universo sea diferente, pero que siga siendo coherente con las reglas del mundo.

La historia inicial es fija.

La configuración espacial procedural es variable.

Las acciones de los jugadores son variables.

El resultado final de cada universo será, por tanto, una historia diferente.

---

## Estado del proyecto

Actualmente el proyecto se encuentra en fase de **diseño y definición de reglas**.

No se debe comenzar la implementación principal hasta establecer suficientemente:

- Lore.
- Facciones.
- Razas.
- Sistemas.
- Planetas.
- Propiedades físicas.
- Recursos.
- Economía.
- Colonización.
- Jugadores.
- Progresión.
- Combate.
- Exploración.
- Diplomacia.
- Reglas temporales.
- Modelo de persistencia.

La documentación de Obsidian será la fuente de verdad del diseño del juego.

---

## Próximos pasos

1. Definir la estructura definitiva del Lore.
2. Definir las tres facciones.
3. Definir las nueve razas.
4. Definir los sistemas y planetas Lore.
5. Definir las propiedades de las estrellas.
6. Definir las propiedades planetarias.
7. Definir el sistema de generación procedural.
8. Definir los recursos.
9. Definir cómo las propiedades planetarias afectan la producción.
10. Definir colonización.
11. Definir jugadores y distribución inicial.
12. Definir progresión y títulos.
13. Diseñar el modelo de datos.
14. Implementar el generador de universo en Go.
15. Implementar persistencia.
16. Implementar API.
17. Construir el frontend en React.

---

## Principio fundamental

**Primero se define el mundo. Después se construye el motor. Finalmente se construye la interfaz.**

```text
OBSIDIAN
   ↓
Diseño + Lore + Reglas
   ↓
GO
   ↓
Simulación + Backend
   ↓
REACT
   ↓
Experiencia del jugador
```
