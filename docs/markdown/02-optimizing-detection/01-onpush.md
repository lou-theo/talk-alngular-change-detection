<!-- .slide: class="with-code" -->

# Detection Strategy

Il en existe 2 :

- `Default` : détection de changement à chaque event
- `OnPush` : détection de changement uniquement si une référence change

<br/><br/>

```typescript
import { ChangeDetectionStrategy, Component } from '@angular/core';

@Component({
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class MyComponent {}
```

<!-- .element: class="big-code block" -->

Notes:

##==##

# Creusons OnPush

Si un composant utilise OnPush, il ne sera vérifié que dans quelques cas :

<br/>

- lorsque l’un des inputs du composant a changé
- Gestion d'un event dans le composant ou l'un de ses enfants quelque soit sa stratégie de détection
- l’utilisation du pipe async
- utilisations explicites de ChangeDetectorRef
<!-- .element: class="list-fragment" -->

Notes:

- détection des inputs se fait sur la ref (mutation des objets/arrays non détectée) => Utilisation de Immutable.js
- subscribe à un observable dans un composant OnPush ne déclenche pas la détection de changement
- ChangeDetectorRef.markForCheck() ou ChangeDetectorRef.detectChanges()

##==##

# OnPush : Explorons quelques cas

<div class="full-center">
 <img class='full-width' src="./assets/images/event-trigger.svg">
</div>

Notes:
Images issues de la doc Angular
https://angular.io/guide/change-detection-skipping-subtrees

En vert les composants qui ont été vérifiés

##==##

# OnPush : Explorons quelques cas

<div class="full-center">
 <img class='full-width' src="./assets/images/on-push-trigger.svg">
</div>

##==##

# OnPush : Explorons quelques cas

<div class="full-center">
 <img style='width: 75%' src="./assets/images/leaf-trigger.svg">
</div>

##==##

# OnPush : Explorons quelques cas

<div class="full-center">
 <img class='full-width' src="./assets/images/on-push-input.svg">
</div>
