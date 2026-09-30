# Guerra de Varas

Juego de estrategia en tiempo real inspirado en *Stick War: Legacy*, en 3D, hecho en un solo archivo HTML con [Three.js](https://threejs.org/) (r128, cargado desde cdnjs).

Abre `index.html` en el navegador para jugar (necesita conexión para descargar Three.js y las fuentes).

## 3D

- Terreno con relieve, bosques, montañas con niebla atmosférica, nubes y cielo con sol, luna y estrellas.
- Luz del sol con sombras reales que cambia con el ciclo día/noche; de noche iluminan las antorchas, los magos, los cascos de los mineros y las explosiones.
- Los palitos son esqueletos 3D (cilindros y esferas instanciados) que usan las mismas animaciones: IK en las piernas, estelas de arma y ragdolls.
- Cuatro vistas de cámara (`V` o el botón de cámara): clásica, cercana, épica y aérea. Rueda para zoom y clic derecho + arrastrar para girar.

## Lanceros

Inspirados en los espartanos de *300*:

- **Lanzamiento:** al ver un enemigo a media distancia lanzan su lanza (60 de daño, atraviesa 2 enemigos). Después siguen con una espada corta más rápida.
- **Recuperar la lanza:** la lanza queda clavada en el suelo; pasar sobre ella la recoge, y al volver a la estatua se rearman. Las lanzas propias en el suelo se marcan con un anillo dorado.
- **Escudo:** bloqueando de frente reciben ~30% del daño normal (las flechas casi nada; la magia, 60%). Por la espalda no protege. No pueden atacar mientras bloquean y se mueven más lento.
- **IA:** levantan el escudo ante el golpe de un gigante o cuando les llueven flechas, y con la orden *Defender* forman un muro de escudos.
- **Control directo:** clic o `Espacio` lanza la lanza hacia el cursor si no hay nadie al alcance (si lo hay, ataca cuerpo a cuerpo). Mantén `S` o `↓` (botón 🛡 en el móvil) para bloquear.

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

## Campaña

8 batallas en orden. Cada nivel desbloquea unidades o poderes y cambia las reglas del enemigo:

| # | Nivel | Novedad |
|---|---|---|
| 1 | Primer filo | Mineros y espadas |
| 2 | Arcos en la colina | Arqueros y Furia |
| 3 | Muro de escudos | Lanceros y Lluvia de flechas |
| 4 | Noche eterna | Magos; siempre es de noche |
| 5 | Asedio | La estatua enemiga tiene 7000 de vida; +600 de oro inicial |
| 6 | El despertar | Gigantes y Meteoro |
| 7 | Resistir | Supervivencia: aguanta 4 minutos contra una horda |
| 8 | Trono del Caos | Jefe final: el Rey Gigante aparece al minuto |

Cada victoria da hasta 3 estrellas: ganar, terminar con la estatua por encima del 50% y ganar por debajo del tiempo objetivo (en *Resistir*, terminar por encima del 80%). Las estrellas nuevas dan coronas; repetir un nivel ya completado da 25.

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

| Tecla | Acción |
|---|---|
| `1`–`6` | Entrenar unidades |
| `Z` `X` `C` | Guarnición · Defender · Atacar |
| `Q` `E` `R` | Poderes (apuntan al cursor) |
| Clic en soldado / `Tab` | Controlarlo |
| Minero controlado | Pica junto a una mina con `Espacio` o clic y lleva la bolsa a tu estatua para entregar el oro |
| `A` `D` / flechas | Mover unidad o cámara |
| `W` · `Shift` | Saltar · Esquivar |
| `S` / `↓` | Bloquear con el escudo (lancero controlado) |
| `Espacio` / clic | Atacar (mantén para cargar el arco) |
| `Esc` | Soltar la unidad / cancelar poder |
| `V` | Cambiar vista de cámara |
| Rueda · clic derecho | Zoom · girar la cámara |
| `P` · `M` | Pausa · Sonido |

En pantallas táctiles aparecen botones de movimiento al controlar una unidad.
