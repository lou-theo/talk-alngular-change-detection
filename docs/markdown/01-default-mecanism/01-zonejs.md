<!-- .slide: class="with-code" -->

# Rappel sur la nature JavaScript

Les fonctions / prototypes sont overridables

<br/>

```js
var _ = window.setTimeout;
window.setTimeout = function (delay, fn) {
  return typeof delay == 'number' ? _(fn, delay) : _(delay, fn);
};
```

<!-- .element: class="big-code block" -->

<br/>

[lien du gist](https://gist.github.com/mislav/e6d8eaa76dab5baf7dd1)

<div class="fragment">
⚠️ Cette cascade a été réalisée par un professionnel, n'essayez surtout pas de la reproduire chez vous.
</div>

##==##

# Introduction à Zone.js

Librairie qui permet de créer des zones d'exécution

Angular est exécuté dans une zone

<br/>

Notes:

Concept simple: une grande partie de l'API du DOM est surchargée pour être interceptée par Zone.js

Créé par l'équipe Angular mais peut être utilisé avec n'importe quel framework

##==##

# Les hooks de Zone.js

Différents hooks sont disponibles pour intercepter les événements asynchrones :

- **onInvoke** qui sera appelé avant l’exécution du code encapsulé dans la zone
- **onHasTask** qui sera appelé après l’exécution du code encapsulé dans la zone
- **onHandleError** qui sera appelé dès que l’exécution du code encapsulé dans la zone lance une erreur
- **onFork** qui sera appelé à la création de la zone

Notes:

Permet (entre autres):

- change detection
- profiling
