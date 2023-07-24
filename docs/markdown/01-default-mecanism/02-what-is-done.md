# Et maintenant, ça se passe comment ?

Avant tout, 1 rappel / 2 contraintes :

- Les composants sont organisés en arbre
- Pas de changement de modèle / effet de bord lors de la détection de changement
- Interdiction de modifier un composant parent

Notes:

- On sait quand est déclenché la détection de changement, mais pas en quoi il consiste

- En mode dev on a 2 détections de changement qui se suivent pour vérifier les effets de bord

- Permet de largement simplifier la détection de changement (coucou AngularJs et les digest cycles)

##==##

# Lors de la détection de changement

- L'ENSEMBLE des composants est parcouru de manière séquentielle
- On exécute les **lyfecycle hooks**
- Pour chaque expression dans le template, on **compare la valeur actuelle / précédente**
- Si la valeur a changé, on **déclenche le rendu du composant**
<!-- .element: class="list-fragment" -->

Notes:

- On part du composant root et on descend dans l'arbre
- on fait tout ça pour le moindre petit event (scroll, setTimeout, etc.)

- Lifecycles : ngOnChanges, ngDoCheck, ngAfterContentChecked, ngAfterViewChecked

##==##

<!-- .slide: class="two-column-layout" -->

# La comparaison du modèle d'un composant en pratique

##--##

<!-- .slide: class="with-code" -->

```typescript
@Component({
  selector: 'app-my-component',
  template: `Hello {{ name }}`,
})
class MyComponent {
  @Input() name: string;
}
```

<!-- .element: class="big-code block" -->

##--##

Notes:

- warning: pas d'info dans la doc, blogs et conférences anciens sur le sujet
- Le JS est exécuté dans des VMs sur navigateur, la mécanique des VMs demande au code de ne pas être trop générique pour être optimisé et mis en cache
- Le changeDetector fait partie de chaque composant, on a un arbre de changeDetector

##==##

<!-- .slide: class="two-column-layout" -->

# La comparaison du modèle d'un composant en pratique

##--##

<!-- .slide: class="with-code" -->

```typescript
@Component({
  selector: 'app-my-component',
  template: `Hello {{ name }}`,
})
class MyComponent {
  @Input() name: string;
}
```

<!-- .element: class="big-code block" -->

##--##

<!-- .slide: class="with-code" -->

```typescript
class MyComponent_ChangeDetector {
  detectChanges() {
    if (this.name !== this.previousName) {
      this.previousName = this.name;
      hasChanged = true;
    }
  }
}
```

<!-- .element: class="big-code block" -->
