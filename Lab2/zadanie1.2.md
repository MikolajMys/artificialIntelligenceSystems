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

%C) x i y są dziadkami

%D) y jest przybranym rodzicem x

%E) x jest przybranym rodzeństwem y

%F) x jest partnerem/ką rodzeństwa y

%G) x jest dzieckiem dziadka i rodzica y 



```
