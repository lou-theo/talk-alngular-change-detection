# Détacher ses composants du cycle de détection

Avec le Change Detector, on a accès aux méthodes :

- `detach()`
- `reattach()`
- `detectChanges()`
- `markForCheck()`

Notes:

- cran au dessus de NgZone, on gère le cycle à la main
- exemples de cas : webSocket, setInterval, etc très fréquents

- detectChanges() => détection juste composant + enfants
- markForCheck() => avec OnPush
