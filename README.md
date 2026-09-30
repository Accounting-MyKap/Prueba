# Guerra de Varas

Juego de estrategia en tiempo real inspirado en *Stick War: Legacy*, en 3D, hecho en un solo archivo HTML con [Three.js](https://threejs.org/) (r128, cargado desde cdnjs).

Abre `index.html` en el navegador para jugar (necesita conexión para descargar Three.js y las fuentes).

## Diseño de las unidades

Inspirado en el original: palitos de extremidades gruesas y redondeadas con cabeza grande. Tu ejército es negro y las naciones enemigas son granate.

- **Minero:** pico y un gran saco negro a la espalda que se infla al cargar oro.
- **Espadachín:** palito liso con espada (las mejoras añaden hombreras, yelmo y capa).
- **Arquero:** arco y carcaj con flechas a la espalda.
- **Lancero:** casco corintio de bronce con cresta roja de lado a lado, escudo redondo de bronce con anillos rojos y lanza larga.
- **Mago:** sombrero puntiagudo doblado, barba gris larga y bastón.
- **Gigante:** encorvado, con hombros enormes, cabeza pequeña y garrote con púas.

## 3D

- Terreno con relieve, bosques, montañas con niebla atmosférica, nubes y cielo con sol, luna y estrellas.
- Luz del sol con sombras reales que cambia con el ciclo día/noche; de noche iluminan las antorchas, los magos, los cascos de los mineros y las explosiones.
- Los palitos son esqueletos 3D (cilindros y esferas instanciados) que usan las mismas animaciones: IK en las piernas, estelas de arma y ragdolls.
- Cuatro vistas de cámara (`V` o el botón de cámara): clásica, cercana, épica y aérea. Rueda para zoom y clic derecho + arrastrar para girar.

## Lanceros

Inspirados en los espartanos de *300*:

- **Lanzamiento:** al ver un enemigo a media distancia toman impulso con unos pasos, suben la lanza sobre el hombro, echan el brazo atrás y la arrojan por encima de la cabeza como una jabalina (60 de daño, atraviesa 2 enemigos). Después siguen con una espada corta más rápida.
- **Recuperar la lanza:** la lanza queda clavada en el suelo; pasar sobre ella la recoge, y al volver a la estatua se rearman. Las lanzas propias en el suelo se marcan con un anillo dorado.
- **Escudo:** bloqueando de frente reciben ~30% del daño normal (las flechas casi nada; la magia, 60%). Por la espalda no protege. No pueden atacar mientras bloquean y se mueven más lento.
- **IA:** levantan el escudo ante el golpe de un gigante o cuando les llueven flechas, y con la orden *Defender* forman un muro de escudos.
- **Control directo:** `Espacio` o clic ataca cuerpo a cuerpo, `F` lanza la lanza hacia el cursor (botón 🎯 en el móvil) y mantener `Q` bloquea (botón 🛡).

## Magos

La bola de fuego sigue un arco de mortero (unos 45–50°) y cae en el carril del objetivo. La IA apunta adelantándose a los enemigos en movimiento. Al controlar un mago se ve la trayectoria y el círculo de la explosión donde apuntas.

## En el celular

- En pantallas bajas la barra de unidades flota sobre el césped como una franja delgada (solo icono y costo) y el campo de batalla ocupa toda la pantalla.
- La cámara se acerca sola según el tamaño de la pantalla; pellizca con dos dedos para hacer zoom y usa el botón de cámara para cambiar de vista.
- Al controlar un soldado la barra se oculta y quedan los botones de mover, esquivar, saltar, bloquear (lancero), atacar y soltar.
- Menos carga gráfica en móviles (sombras y resolución más bajas). En vertical se sugiere girar el teléfono.

## Guarnición

Detrás de cada estatua hay una empalizada de lanzas afiladas. Con la orden *Guarnición* todas las tropas se retiran detrás de ella, se curan, no pueden ser atacadas y disparan como arqueros (mineros y magos incluidos, como en el original). Los arqueros disparan con su daño normal y alcance de 560 px; el resto dispara flechas más débiles. La IA también se refugia cuando una fuerza mayor llega a sus puertas.

## Sangre y muertes

- Las flechas se clavan en el cuerpo (vivo o muerto) donde impactan, hasta 5 por soldado; las de fuego siguen ardiendo.
- Quien muere por flecha se desploma hacia atrás; los golpes fuertes y explosiones lanzan el cuerpo.
- Los cuerpos sangran y forman un charco que crece; la sangre y los charcos quedan en el campo unos 40 segundos antes de desaparecer.
- Los heridos (menos de 40% de vida) gotean sangre.
- Al recibir un golpe no hay destello: solo salpica sangre.
- Las armas caen al suelo: espadas y lanzas quedan clavadas, arcos y picos tumbados.
- Botón *Sangre: Sí/No* en el menú y en la pausa para desactivarla.

## Profundidad

Las unidades pueden moverse hacia el fondo o el frente del campo; al hacerlo caminan y giran el cuerpo hacia donde van (hasta unos 60°). El cuerpo a cuerpo y los proyectiles solo aciertan a quien está en una franja cercana de profundidad: la IA se alinea con su objetivo y, controlando un soldado, puedes esquivar flechas cambiando de carril.

## Magos: aturdimiento y esbirros

- La bola de fuego aturde 0,8 s a los enemigos alcanzados (salvo gigantes); se ven estrellas girando sobre su cabeza.
- `F` (o la IA cuando se acercan enemigos) invoca 2 esbirros oscuros con espada corta que duran 24 s y pueden bloquear con `Q` si los controlas.

## Poderes y visión

Lluvia de flechas y Meteoro solo se pueden lanzar donde tus tropas ven: cerca de tu estatua o a menos de ~340 px de una de tus unidades. El minimapa oscurece lo que no ves y el círculo de apuntado se pone rojo fuera de la visión. La IA sigue la misma regla, así que no puede bombardear tus minas sin acercarse.

Si un bando se queda sin mineros y sin oro para entrenar uno, su estatua envía un minero de reserva cada 12 segundos para que la economía pueda recuperarse.

## Forja: armas y armaduras

Las mejoras de unidad de la Armería cambian el aspecto de la tropa en cada nivel además de subir sus estadísticas:

| Unidad | Nivel 1 | Nivel 2 | Nivel 3 (efecto especial) |
|---|---|---|---|
| Minero | Casco con lámpara | Pico de acero y bolsa grande | Pico de oro |
| Espada | Hoja de acero y hombrera | Yelmo de hierro | Filo de brasa y capa: los golpes queman |
| Arquero | Arco largo y carcaj | Arco recurvo y manto | Arco dorado: flechas de fuego que queman |
| Lancero | Lanza perforante (atraviesa 3) y escudo con aro | Doble lanza, yelmo cerrado y hombreras | Escudo torre dorado: bloquea 85% y devuelve las flechas |
| Mago | Túnica | Cristal arcano | Orbes guardianes |
| Gigante | Garrote con púas | Martillo de piedra | Mazo de hierro y casco con cuernos |

En la campaña el Caos también mejora su equipo (+5% de vida y daño por nivel): forja 1 desde la batalla 4, forja 2 desde la 6 y forja 3 en la batalla final.

## Qué tiene

- **Economía:** mineros que extraen oro y lo llevan a la estatua.
- **6 unidades:** Minero, Espada, Arquero, Lancero (escudo y armadura), Mago (bola de fuego en área) y Gigante.
- **Órdenes:** Guarnición, Defender y Atacar.
- **Control directo:** toma el mando de cualquier soldado.

## Campaña: conquista de naciones

Como en el original, el mundo está dividido en naciones y cada una se especializa en un tipo de soldado. Al conquistar una nación, su unidad se une a tu ejército para la siguiente batalla. Cada nación tiene su propio monumento: arquero de piedra, espadachín, lancero con escudo, mago con báculo, gigante con garrote o el trono con cuernos del Caos. Tu estatua es el rey coronado del Orden.

| # | Nación | Especialidad enemiga | Qué ganas al vencer |
|---|---|---|---|
| 1 | Arquidonia | Arqueros | Arqueros |
| 2 | Clan de la Espada | Hordas de espadachines | (Furia desde esta batalla) |
| 3 | Lancedonia | Lanceros con muro de escudos | Lanceros |
| 4 | Magocracia | Magos que aturden e invocan esbirros; noche permanente | Magos |
| 5 | Fortaleza Roja | Asedio: monumento con 7000 de vida; +600 de oro inicial | — |
| 6 | Colinas de Hielo | Gigantes | Gigantes (Meteoro desde esta batalla) |
| 7 | Tierra de Nadie | Supervivencia: aguanta 4 minutos contra una horda | — |
| 8 | Trono del Caos | Jefe final: el Rey Gigante aparece al minuto y medio | — |

El enemigo también mejora su forja: nivel 1 en las batallas 5 y 6, nivel 2 en la 7 y nivel 3 en la final.

Cada victoria da hasta 3 estrellas: ganar, terminar con la estatua por encima del 50% y ganar por debajo del tiempo objetivo (en *Tierra de Nadie*, terminar por encima del 80%). Las estrellas nuevas dan coronas; repetir un nivel ya completado da 25.

### Armería

Las coronas se gastan entre batallas en 11 mejoras permanentes (hasta 3 niveles cada una): la Forja de cada unidad (con vista previa 3D del equipo actual y el siguiente), oro inicial, entrenamiento más rápido, estatua más resistente, más maná y la Academia, con la que las tropas nacen con rango ★.

El progreso se guarda en el navegador (`localStorage`). Desde la Armería se puede reiniciar.

La **escaramuza** sigue disponible con todo desbloqueado, sin mejoras y con 3 dificultades.

## Mejoras sobre el original

| Área | Qué cambia |
|---|---|
| 3D | Mundo 3D con luces, sombras y cuatro cámaras |
| Forja | Cada mejora cambia armas y armaduras |
| Animación | Esqueletos procedurales: piernas con IK, balanceo de brazos, inclinación al correr, golpes con anticipación y estela del arma, parpadeo al recibir daño |
| Muertes | Ragdoll con física Verlet: los cuerpos salen despedidos según el golpe |
| Efectos | Sangre que mancha el suelo, chispas en armaduras, explosiones con brasas y humo, temblor de cámara, *hit-stop* en críticos, cámara lenta en meteoros |
| Veteranía | Las unidades ganan experiencia por baja y suben hasta 3 rangos (★): +12% vida y daño por rango |
| Día y noche | Ciclo con sol, luna y estrellas; de noche los arqueros pierden 20% de alcance y las antorchas iluminan |
| Poderes (maná) | Lluvia de flechas (Q), Furia (E, +35% daño y +30% velocidad), Meteoro (R) |
| Control directo | Saltar, esquivar con invulnerabilidad, críticos, cortes a 2 enemigos, arco con carga y trayectoria visible |
| Guarnición | Las tropas se curan dentro de la estatua y los arqueros y magos disparan desde ella |
| IA | Enemigo con economía, composición de ejército, decisiones de ataque/defensa y uso de poderes; 3 dificultades |

## Controles

Basados en la guía de control del original.

| Tecla | Acción |
|---|---|
| `1`–`6` | Entrenar unidades |
| `Z` `X` `C` | Guarnición · Defender · Atacar |
| `Q` `E` `R` | Poderes (apuntan al cursor) cuando no controlas a nadie |
| Clic en soldado / `Tab` | Controlarlo |
| `W` `A` `S` `D` / flechas | Mover la unidad controlada en las cuatro direcciones (también hacia el fondo y el frente del campo); sin unidad, `A` `D` mueven la cámara |
| `Espacio` / clic | Atacar · minar (mantén para cargar el arco) |
| `Q` | Bloquear (espadachín: mitad de daño; lancero: escudo) |
| `F` | Lancero: lanzar la lanza · Mago: invocar 2 esbirros (15 s de recarga) |
| `J` · `Shift` | Saltar · Esquivar |
| `Esc` | Soltar la unidad / cancelar poder |
| `V` | Cambiar vista de cámara |
| Rueda · clic derecho | Zoom · girar la cámara |
| `P` · `M` | Pausa · Sonido |

En pantallas táctiles aparece una cruceta (▲ ◀ ▼ ▶) y botones de esquivar, saltar, bloquear 🛡, habilidad (🎯 lanza / ✦ esbirros), atacar ⚔ y soltar.
