```prolog
%A) x jest rodzeństwem y
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

%B) x jest kuzynem y
%rodzic(a,b).
%rodzic(a,c).
%rodzic(b,x).
%rodzic(c,y).

kuzyn(X, Y) :-
    rodzic(Z, X),
    rodzic(W, Y),
    rodzenstwo(Z, W),
    X \= Y.

%C) x i y są dziadkami
%rodzic(x,a).
%rodzic(y,b).
%rodzic(a,c).
%rodzic(b,c).

dziadkowie(X, Y) :-
    rodzic(X, A),
    rodzic(Y, B),
    rodzic(A, C),
    rodzic(B, C),
    X \= Y.

%D) y jest przybranym rodzicem x
rodzic(a,x).
rodzic(a,b).
rodzic(y,b).

%E) x jest przybranym rodzeństwem y

%F) x jest partnerem/ką rodzeństwa y

%G) x jest dzieckiem dziadka i rodzica y 

```
