> ### Problemas de programación Lógica 
Problema 1: Los guardianes de los templos
Cuatro guardianes (Apolo, Hécate, Ares y Hermes) custodian templos mitológicos asociados con diferentes elementos (fuego, agua, tierra y aire). Sabemos que:

- Apolo no cuida el templo de fuego ni el de tierra.
- Hécate no cuida el templo de aire.
- Ares no cuida el templo de agua ni de aire.
- Hermes cuida el templo de fuego o de agua.

Pregunta: ¿Qué templo cuida cada guardián?
```Prolog

cuida(apolo, aire).
cuida(apolo, agua).
cuida(hecate, tierra).
cuida(hecate, fuego).
cuida(hecate, agua).
cuida(ares, tierra).
cuida(ares, fuego).
cuida(hermes, fuego).
cuida(hermes, agua).


templo_de(X, Y) :- cuida(X, Y).


```