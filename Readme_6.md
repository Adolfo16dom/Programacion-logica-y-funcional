> ### Problemas con Predicados Mitológicos
1. Aplanar una lista de listas anidadas

* Utiliza el predicado flatten para transformar una estructura anidada en una lista plana.
* Problema: Dada una lista como [1, [2, [3, 4], 5], [6]], genera [1, 2, 3, 4, 5, 6].
* Predicado: `flatten/2`.

```Prolog
% Convierte una lista con estructuras anidadas en una lista plana.
flatten([], []).
flatten([H|T], R) :-
    flatten(H, RH),
    flatten(T, RT),
    append(RH, RT, R).
flatten(X, [X]) :-
    X \= [],
    X \= [_|_].

% Ejemplo: Aplanar una lista.

% ?- flatten([1, [2, [3, 4], 5],[6]], R).
% R = [1, 2, 3, 4, 5, 6].
```