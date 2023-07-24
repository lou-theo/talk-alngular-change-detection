<!-- .slide: class="with-code max-height" -->

# Mettre du formatage dans le template

## Ce qui est souvent fait ❌

```typescript
@Component({
  selector: 'app-my-component',
  template: `{{ hello(name) }}`,
})
class MyComponent {
  @Input() name: string;

  hello(name: string) {
    return 'Hello ' + value.toUpperCase();
  }
}
```

<!-- .element: class="big-code block" -->

Notes:
- logique plus ou moins complexe
- ne dois surtout pas avoir d'effet de bord => ExpressionChangedAfterCheckedError

##==##

<!-- .slide: class="two-column-layout" -->

# Mettre du formatage dans le template

## Ce qui est optimisé ✔️

##--##

<br/>
<br/>

<!-- .slide: class="with-code max-height" -->

```typescript
@Component({
  selector: 'app-my-component',
  template: `{{ name | hello }}`,
})
class MyComponent {
  @Input() name: string;
}
```

<!-- .element: class="big-code block" -->

##--##

<br/>

<!-- .slide: class="with-code max-height" -->

```typescript
@Pipe({
  name: 'hello',
  pure: true, // default value
})
export class HelloPipe implements PipeTransform {
  transform(value: string): string {
    return 'Hello ' + value.toUpperCase();
  }
}
```

<!-- .element: class="big-code block" -->

Notes:
- méthode transform du pipe n’est appelée que si la référence de l’objet qu’il transforme a changé ou si celle d’un autre argument de la méthode a changé
- Comme OnPush demande des changements de refs
