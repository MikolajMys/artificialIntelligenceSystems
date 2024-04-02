```prolog
%A)
%rodzic(a,x).
%rodzic(a,y).
%rodzic(b,x).
%rodzic(b,y).

dziecko(X,Y) :-
    rodzic(Y,X).

rodzenstwo(X,Y) :-
    rodzic(Z,X),
    rodzic(Z,Y),
    X \= Y.

%B)


```
