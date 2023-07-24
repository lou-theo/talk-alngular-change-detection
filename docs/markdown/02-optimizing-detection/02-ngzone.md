<!-- .slide: class="with-code max-height" -->

# Exécution en dehors de ngZone

```typescript
import { Component, NgZone, OnInit } from '@angular/core';
@Component(...)
class AppComponent implements OnInit {
  constructor(private ngZone: NgZone) {}
  ngOnInit() {
    this.ngZone.runOutsideAngular(() =>
      setInterval(pollForUpdates, 500)
    );
  }
}
```

<!-- .element: class="big-code block" -->

Notes:
- `ngZone.runOutsideAngular` permet d'exécuter une fonction en dehors de la zone Angular
- particulièrement utile / indispensable pour les libs qui ne sont pas Angular-aware (charts, etc.) qui utilisent beaucoup addEventListener et setTimeout

Pour les libs qui ne sont pas Angular-aware, lorsque les utilisateurs vont ne serait-ce que survoler le graphique, des centaines d’événements DOM se déclencheront
