# PhysioSentinel AI v15.5.11

## Cambio exclusivo: animación 3D con cámara realmente libre durante la reproducción

La v15.5.10 resolvía el movimiento del punto usando frames de Plotly con
`redraw=True`. Eso hacía visible la animación, pero cada frame podía reconstruir
la escena 3D y devolver/bloquear la cámara mientras se reproducía.

### Solución v15.5.11
Para el atractor 3D ya no se utilizan frames de `Plotly.animate()`.

El gráfico 3D se renderiza una sola vez y JavaScript actualiza únicamente:
- x del marcador móvil;
- y del marcador móvil;
- z del marcador móvil.

La actualización se realiza con `Plotly.restyle()`.

### Resultado
Mientras el punto está avanzando se puede:
- rotar el atractor con el ratón;
- hacer zoom;
- cambiar la orientación;
- desplazar la cámara;
- mantener la nueva cámara durante toda la reproducción.

La reproducción ya no debe volver a la posición inicial.

Se conservan:
- Reproducir;
- Pausa;
- slider de avance manual;
- velocidad;
- número de frames.

### Sin cambios fisiológicos
No se modifican RRi, corrección de artefactos, τ, embedding m, geometría del
atractor, D2, Lyapunov, RQA, entropías, HRV, Control autonómico, XGBoost,
calibración probabilística ni predicción.
