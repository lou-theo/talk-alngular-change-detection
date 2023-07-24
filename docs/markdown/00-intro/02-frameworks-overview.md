# Rapide tour d'horizon

Comment se débrouille la concurrence ?

- On fait à la main ou on fait pas
- Utilisation de méthodes / objets spécifiques / ES proxies
- binding au DOM
- DOM virtuel
- dirty checking
<!-- .element: class="list-fragment" -->

Notes:

- Je n'ai pas creusé en détails les autres frameworks, je ne fais que les survoler
- 2eme point => quand lancer la détection de changement
- les suivants => faire la détection de changement

##==##

# Et pour Angular ?

Postulat de départ : les changements proviennent...

- directement de l'utilisateur
- de la résolution d'un code asynchrone
<!-- .element: class="list-fragment" -->

Notes:

- clic / saisie utilisateur / scroll...
- requête HTTP / setTimeout / setInterval / Promise / Observable...

##==##

# Et pour LES Angular ?

<div class="full-center">
 <img src="./assets/images/angularjs-to-angular.png">
</div>

Notes:
Avec AngularJs :

- directives specifiques (ng-click, ng-model, ...)
- services ($http, $timeout, $interval, ...)
- appel direct au change detection acs non gérés par AngularJs (requetes hors $http, ...)
- système de watchers avec digest cycle => tant qu'il y a des modifs dans les watchers, on relance le digest cycle

=> tout ça permet de savoir s'il y a eu un changement mais pas ce qui a changé
