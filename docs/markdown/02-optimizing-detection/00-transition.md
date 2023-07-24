<!-- .slide: class="transition-bg-green-3" -->

# Optimiser le changement de détection

Notes:

La detection de changement est le travail principal d'Angular (ce qui va consommer le plus par le framework) et donc si l'on a besoin de l'optimiser, essayer de la limiter.

D'autant plus que comme vu précédemment généralement inutile de faire une détection de changement de tous les composants à chaque fois.

Warning: la plupart des applications n'auront pas besoin de ces optimisations, et il est préférable de ne pas les utiliser si on ne sait pas pourquoi on le fait.
