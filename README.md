# REPO_planeta
__Para reiniciar TODO el progreso (todas las estrellas):__
```js
// ⚠️ ESTO BORRA TODAS LAS ESTRELLAS ABIERTAS
syncManager.readSet.clear();
localStorage.setItem('readStars', JSON.stringify([]));
syncManager.saveToJSONBin().then(() => {
    console.log('✅ Todas las estrellas han sido reiniciadas');
    location.reload();
});
```
__Para reiniciar UNA estrella específica:__
```js
// Reemplaza el 0 con el número de la estrella que quieras reiniciar
const estrellaAReiniciar = 0; // 0, 1, 2, 3, 4 (para tus 5 estrellas)

syncManager.readSet.delete(estrellaAReiniciar.toString());
localStorage.setItem('readStars', JSON.stringify([...syncManager.readSet]));
syncManager.saveToJSONBin().then(() => {
    console.log(`✅ Estrella ${estrellaAReiniciar} reiniciada`);
    location.reload();
});
```
__Para ver qué estrellas tienes abiertas antes de reiniciar:__
```js
// Para saber qué estrellas tienes abiertas actualmente
console.log('📊 Estrellas abiertas AHORA:', [...syncManager.readSet]);
console.log('🔢 Números de estrellas abiertas:', [...syncManager.readSet].map(Number));
```
___Si quieres hacer una copia de seguridad antes:__
```js
// 1. GUARDAR RESPALDO
const respaldo = [...syncManager.readSet];
console.log('💾 Respaldo guardado:', respaldo);

// 2. REINICIAR (elige la Opción 1 o 2 arriba)

// 3. Si te arrepientes, RESTAURAR:
syncManager.readSet = new Set(respaldo);
localStorage.setItem('readStars', JSON.stringify(respaldo));
syncManager.saveToJSONBin().then(() => location.reload());
```
__Para tu caso específico (5 estrellas):__
```js
// Ver qué estrellas tienes abiertas
console.log('Estrellas abiertas:', [...syncManager.readSet]);

// Reiniciar TODO (todas las estrellas)
syncManager.readSet.clear();
localStorage.setItem('readStars', JSON.stringify([]));
syncManager.saveToJSONBin().then(() => location.reload());
```
__Explicación del color (HSL):__
El color usa HSL (Hue, Saturation, Lightness):

__h (Hue - Matiz):__ Valor de 0 a 1 que determina el color base

- 0.00 = Rojo
- 0.10 = Naranja/Dorado (como tu primer mensaje)
- 0.33 = Verde
- 0.56 = Azul/Cian (como tu segundo mensaje)
- 0.66 = Azul más intenso
- 0.82 = Violeta/Rosa (como tu tercer mensaje)
- 1.00 = Vuelve al rojo

__s (Saturation - Saturación):__ De 0 a 1, intensidad del color

- 0.00 = Gris
- 0.85 = Muy saturado (colores vivos)
- 1.00 = Saturado máximo

__l (Lightness - Luminosidad):__ De 0 a 1, brillo del color

- 0.00 = Negro
- 0.50 = Color normal
- 0.72 = Bastante brillante (como usas)
- 1.00 = Blanco

__Ejemplos de colores que puedes usar:__
```js
// Colores para tus mensajes:
color:{h:0.00, s:0.90, l:0.72}  // Rojo romántico
color:{h:0.05, s:0.85, l:0.70}  // Naranja cálido
color:{h:0.12, s:0.88, l:0.75}  // Dorado brillante
color:{h:0.30, s:0.80, l:0.70}  // Verde esmeralda
color:{h:0.50, s:0.90, l:0.72}  // Azul cielo
color:{h:0.60, s:0.85, l:0.70}  // Azul profundo
color:{h:0.75, s:0.90, l:0.72}  // Violeta
color:{h:0.85, s:0.88, l:0.75}  // Rosa
color:{h:0.95, s:0.80, l:0.70}  // Magenta
```
__Sobre la fecha:__
```js
// Mensaje disponible desde el 15 de marzo de 2026
fecha: new Date('2026-03-15')

// Mensaje disponible desde el 1 de abril de 2026
fecha: new Date('2026-04-01')

// Mensaje disponible desde hoy
fecha: new Date()  // ← Fecha actual
```
