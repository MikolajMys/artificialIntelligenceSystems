## Zadanie 0 
### Zapisz reguły dla:nieprzyjazn(X,Y), niby_przyjazn(X,Y), loves(X,Y) 1) może być na zasadzie wzajemności i wyłączności 2) dodaj fakt płeć i true_love(X,Y):
```prolog
%FAKTY:
lubi(jan, pawel).
lubi(pawel, krzysztof).
lubi(pawel, jan).
lubi(jan, bartek).
lubi(bartek, jan).
lubi(kacper, karolina).
lubi(karolina, kacper).
lubi(zosia, asia).
lubi(asia, zosia).

plec(jan, facet).
plec(pawel, facet).
plec(krzysztof, facet).
plec(bartek, facet).
plec(kacper, facet).
plec(karolina, baba).
plec(zosia, baba).
plec(asia, baba).

%REGUŁY:
przyjazn(X,Y) :-
    lubi(X,Y),
    lubi(Y,X).

niby_przyjazn(X,Y) :-
    lubi(X,Y);
    lubi(Y,X).

nieprzyjazn(X,Y) :-
    \+przyjazn(X,Y).

loves(X,Y) :-
    przyjazn(X,Y),
    \+ (lubi(X,Z), Z \= Y),
    \+ (lubi(Y,Z), Z \= X),
    X \= Y.

true_love(X,Y) :-
    loves(X,Y),
    plec(X, facet),
    plec(Y, baba);
    plec(X, baba),
    plec(Y, facet).
```
