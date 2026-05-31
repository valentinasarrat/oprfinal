# oprfinal
# Dashboard de Spotify

---

### Mainstream

| Preguntas | Respuestas |
|---|---|
| **Nombre y Rol** | **Felipe, Arquitecto Oyente** — Profesional arquitecto que escucha música como fondo constante durante el trabajo. |
| **Demográficos** | 25 años, Santiago de Chile. Trabaja en una inmobiliaria, ingreso medio-alto. Escucha música durante la jornada laboral y mientras maneja. |
| **Objetivos y Motivaciones** | Quiere descubrir música que todavía no conoce, de forma rápida y sin esfuerzo. Su motivación principal es explorar un catálogo de Spotify para encontrar artistas o canciones que nunca ha escuchado pero que probablemente le van a gustar. También quiere poder armar playlists temáticas por estado de ánimo o actividad (trabajar concentrado, manejar, relajarse) sin tener que buscar canción por canción. No es experto en el ámbito musical, solo quiere escuchar buena música. |
| **Puntos de dolor (Pain points)** | Le cuesta encontrar música nueva porque no sabe por dónde empezar en un catálogo tan grande. Siente que Spotify solo le muestra lo mismo de siempre y no le ayuda a salir de su burbuja. Pierde tiempo armando playlists manualmente porque no tiene una forma rápida de filtrar por lo que está buscando. |



### Un extremo: El Coleccionista Obsesivo

| Preguntas | Respuestas |
|---|---|
| **Nombre y Rol** | **Gonzalo, DJ Amateur** — Coleccionista de música electrónica y beatmaker de fin de semana. Lleva un registro detallado de cada canción que escucha. |
| **Demográficos** | 34 años, Valparaíso. De profesión es técnico informático y durante el día trabaja en ello, de noche mezcla música en su departamento y algunas veces en pequeños bares locales. Ingreso medio-bajo. |
| **Objetivos y Motivaciones** | Quiere analizar patrones técnicos en los datos: distribución de popularidad por género, tendencias por década, duración promedio de canciones. Busca encontrar artistas emergentes con pocos seguidores pero alta popularidad o con buen ritmo para "descubrirlos antes que todos". Valora la profundidad analítica sobre la estética visual. |
| **Puntos de dolor (Pain points)** | Las visualizaciones genéricas no le muestran suficiente detalle. Le frustra no poder filtrar por variables específicas como duración exacta, nivel de popularidad o contenido explícito. Siente que los dashboards están diseñados para oyentes casuales, no para alguien que quiere explorar los datos a fondo. |



### Otro extremo: La Oyente Ocasional

| Preguntas | Respuestas |
|---|---|
| **Nombre y Rol** | **Carmen, Abuela Moderna** — Jubilada que usa Spotify para escuchar música de los 60s y 70s que recuerda de su juventud, guiada por su nieto. |
| **Demográficos** | 73 años, Castro. Jubilada, ingreso fijo por pensión. Usa su celular (Iphone 11) con dificultad, intenta acceder diariamente a Spotify porque le gusta dejar música de fondo durante el día en su casa |
| **Objetivos y Motivaciones** | Solo quiere encontrar canciones que reconoce y escuchar cosas parecidas a lo que ya le gusta. Le gustaría entender de forma simple "qué música hay de los años 70 similar a la que ya escucha" sin tener que leer datos ni navegar interfaces complejas. Y también encontrar con facilidad canciones de su juventud de las que recuerda solo el coro o algunas partes. |
| **Puntos de dolor (Pain points)** | Los dashboards con demasiados gráficos o filtros la abruman. No entiende términos técnicos como "popularidad", "tracks" o "géneros". La letra pequeña y los colores de bajo contraste le dificultan la lectura. Necesita una experiencia extremadamente simple e intuitiva. |



## Segundo, con qué

El dashboard se construye en base al siguiente dataset:

| Archivo | Descripción |
|---|---|
| `spotify.csv` | Base de datos de Spotify con **8.582 canciones**. Contiene información de tracks, artistas, álbumes, géneros, popularidad y fechas de lanzamiento. |

### Columnas disponibles en el dataset

| Columna | Descripción |
|---|---|
| `track_id` | Identificador único de la canción |
| `track_name` | Nombre de la canción |
| `track_number` | Número de pista en el álbum |
| `track_popularity` | Popularidad de 0 a 99 (promedio del dataset: 52) |
| `explicit` | Si la canción tiene contenido explícito (True/False) |
| `artist_name` | Nombre del artista |
| `artist_popularity` | Popularidad del artista (0–100) |
| `artist_followers` | Número de seguidores del artista en Spotify |
| `artist_genres` | Géneros asociados al artista (ej: pop, rock, hip hop) |
| `album_id` | Identificador único del álbum |
| `album_name` | Nombre del álbum |
| `album_release_date` | Fecha de lanzamiento (rango: 1952–2025) |
| `album_total_tracks` | Total de pistas en el álbum |
| `album_type` | Tipo: álbum, single o compilación |
| `track_duration_min` | Duración de la canción en minutos (promedio: 3.49 min) |

### Datos destacados del dataset

-  **8.582 canciones** en total
-  **Artistas más representados:** Taylor Swift (324 tracks), The Weeknd (141), Lana Del Rey (99), Ariana Grande (94), Nirvana (91)
-  **Géneros predominantes:** pop, country, soundtrack, hip hop, indie, folk, rock, rap
-  **Décadas representadas:** desde los 50s hasta 2025, con mayor concentración en 2010s (3.704) y 2020s (3.327)
-  **Contenido explícito:** 2.148 canciones (25%); 6.434 limpias (75%)
-  **Tipos de lanzamiento:** 5.856 álbumes, 2.219 singles, 507 compilaciones



## Tercero, qué

Se propone un **dashboard interactivo en HTML/CSS/JavaScript** titulado **"Descubre lo que no sabías que existía"**, orientado a Felipe: alguien que quiere salir de su burbuja musical sin tener que hacer un análisis complejo.

La propuesta diferenciadora respecto a lo que Spotify ya ofrece es mostrar **relaciones entre datos que la plataforma no te muestra directamente**, en particular:

- **El mapa de los "descubribles":** artistas con pocos seguidores pero canciones de alta popularidad, exactamente los que Felipe debería estar escuchando pero probablemente no conoce todavía
- **Comparador de artistas:** ver lado a lado duración de canciones, popularidad y tipo de seguidores (diferenciándolos según género, rango etario y tipo de oyente: frecuente u ocasional) entre dos o más artistas para entender quién vale la pena explorar
- **Duración de canciones por género:** ¿el pop dura menos que el rock? ¿Ha cambiado con el tiempo? Esto ayuda a Felipe a elegir géneros según cuánto tiempo tiene para escuchar y en que momento del día
- **Géneros por década:** cruzar un género con una época: "dame pop de los 80s" o "rock de los 90s" para entender cómo ha evolucionado lo que le gusta
- **Filtro por contenido explícito:** útil cuando quiere escuchar música mientras trabaja en reuniones o con clientes

El diseño será limpio, de estética moderna, mayormente oscuro y con elementos en verde y con acentos en color lila/violeta, sin tecnicismos, con lenguaje cotidiano que invite a explorar.



### Antecedentes de referencia

---

#### Antecedente 1: [Spotify Wrapped](https://wrapped.spotify.com)

> Pantallazo: <img width="1600" height="900" alt="Spotify-Wrapped" src="https://github.com/user-attachments/assets/8b0cb5b2-83ca-4453-9c78-eeaaa34b3679" />

**Lo positivo a rescatar:**
Spotify Wrapped es el referente máximo de visualización de datos musicales para público general. Usa animaciones suaves, storytelling secuencial ("tu canción más escuchada fue..."), tipografía bold y colores vibrantes que generan conexión emocional. Cada pantalla transmite una sola idea, lo que lo hace extremadamente fácil de entender sin importar el nivel del usuario. Esa claridad de foco "una métrica por pantalla" es directamente aplicable al dashboard.

**Lo negativo a evitar:**
Al ser una experiencia lineal y cerrada, no permite exploración libre ni filtros. El usuario no puede preguntarle al dato. Solo recibe lo que Spotify decidió mostrar. Para este proyecto, donde el objetivo es que Felipe explore y descubra, ese modelo es insuficiente.

---

#### Antecedente 2: [Every Noise at Once](https://everynoise.com)

> Pantallazo: <img width="1131" height="681" alt="Captura de pantalla 2026-05-31 a la(s) 18 10 00" src="https://github.com/user-attachments/assets/68a101a0-626f-4c22-be44-ffe7edb600a5" />

**Lo positivo a rescatar:**
Este proyecto mapea más de 6.000 géneros musicales en un plano 2D interactivo. Permite entender relaciones entre géneros de forma espacial: géneros similares están cerca. Para un usuario como Felipe, que "le gusta un poco de todo", esta idea de ver los géneros como un mapa es poderosa. Se puede rescatar la idea de que el usuario navegue visualmente en lugar de leer listas.

**Lo negativo a evitar:**
La interfaz es extremadamente densa, con tipografía diminuta, poco intuitivo y sin jerarquía visual clara. Para un usuario no experto como Carmen, sería completamente ilegible. El dashboard a desarrollar debe priorizar legibilidad y orientación clara sobre densidad de información.

---

#### Antecedente 3: [Music-Map](https://www.music-map.com)

> Pantallazo: <img width="1131" height="681" alt="Captura de pantalla 2026-05-31 a la(s) 18 10 07" src="https://github.com/user-attachments/assets/23f07265-fff7-4e87-b5be-becbf83d7b6d" />

**Lo positivo a rescatar:**
Music-Map permite ingresar un artista y genera un mapa visual de artistas similares, con los más cercanos al centro. Es un ejemplo de cómo convertir datos complejos de similitud en una experiencia completamente intuitiva. Para Felipe, que "constantemente busca encontrar nueva música", la idea de partir de un artista conocido y descubrir similares es directamente útil y aplicable.

**Lo negativo a evitar:**
La estética es muy básica y anticuada (HTML plano, sin diseño moderno). Funciona como concepto pero no como experiencia visual. El dashboard debe tener un acabado visual contemporáneo que invite a explorar.

---

### Moodboard de Referentes

<img width="3300" height="2550" alt="moodboard web" src="https://github.com/user-attachments/assets/5d340d02-2438-4697-bede-7f0465768352" />



- Paleta oscura con elementos en verde y acentos en lila/violeta
- Tipografías bold y de gran tamaño para datos clave (como en Spotify Wrapped)
- Gráficos de barras redondeadas, gráficos de anillo y "pill tags" para géneros
- Inspiración desde pósters de conciertos con composición asimétrica y uso fuerte del color


