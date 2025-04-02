```Prolog
nocuidatemplo(apolo, fuego).
nocuidatemplo(apolo, tierra).
nocuidatemplo(hecate, aire).
nocuidatemplo(ares, agua).
nocuidatemplo(ares, aire).

cuidatemplo(hermes, fuego).
cuidatemplo(hermes, agua).

cuida(X, Y):- nocuidatemplo(X,Y).  

```