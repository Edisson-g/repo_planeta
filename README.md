# REPO_planeta
__Para reiniciar TODO el progreso (todas las estrellas):__
```js
// REINICIAR TODO - ¡CUIDADO! Esto borra TODAS las estrellas
syncManager.readSet.clear();
localStorage.setItem('readStars', JSON.stringify([]));
syncManager.saveToJSONBin().then(() => {
  console.log('✅ Progreso reiniciado completamente');
  location.reload();
});
```
__Para reiniciar UNA estrella específica:__
```js
// Reemplaza el 0 con el número de la estrella que quieras reiniciar
const estrellaAReiniciar = 0; // 0, 1, 2, etc.

syncManager.readSet.delete(estrellaAReiniciar.toString());
localStorage.setItem('readStars', JSON.stringify([...syncManager.readSet]));
syncManager.saveToJSONBin().then(() => {
  console.log(`✅ Estrella ${estrellaAReiniciar} reiniciada`);
  location.reload();
});
```
__Para ver qué estrellas tienes abiertas antes de reiniciar:__
```js
// Ver estrellas actuales
console.log('Estrellas abiertas AHORA:', [...syncManager.readSet]);
```
