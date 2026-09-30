# Guerra de Varas

Juego de estrategia en tiempo real inspirado en *Stick War: Legacy*, hecho en un solo archivo HTML5 (canvas + JavaScript, sin dependencias).

Abre `index.html` en el navegador para jugar.

## Qué tiene

- **Economía:** mineros que extraen oro y lo llevan a la estatua.
- **6 unidades:** Minero, Espada, Arquero, Lancero (escudo y armadura), Mago (bola de fuego en área) y Gigante.
- **Órdenes:** Guarnición, Defender y Atacar.
- **Control directo:** toma el mando de cualquier soldado.

## Mejoras sobre el original

| Área | Qué cambia |
|---|---|
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
| `A` `D` / flechas | Mover unidad o cámara |
| `W` · `Shift` | Saltar · Esquivar |
| `Espacio` / clic | Atacar (mantén para cargar el arco) |
| `Esc` | Soltar la unidad / cancelar poder |
| `P` · `M` | Pausa · Sonido |

En pantallas táctiles aparecen botones de movimiento al controlar una unidad.
