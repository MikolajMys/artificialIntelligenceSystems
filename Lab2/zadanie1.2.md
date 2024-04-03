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
%rodzic(a,x).
%rodzic(a,b).
%rodzic(y,b).

przybrany_rodzic(X, Y) :-
    rodzic(X,B),
    rodzic(A,B),
    rodzic(A,Y),
    \+ rodzic(X,Y),
	X \= Y.

%E) x jest przybranym rodzeństwem y
%rodzic(a,x).
%rodzic(b,x).
%rodzic(b,y).
%rodzic(c,y).

przybrane_rodzenstwo(X,Y):-
    rodzic(A,X),
    rodzic(A,Y),
    \+ (rodzic(B,X), rodzic(B,Y), B \= A),
    X \= Y.

%F) x jest partnerem/ką rodzeństwa y
%rodzic(a,y).
%rodzic(a,b).
%rodzic(b,c).
%rodzic(x,c).

partner_ka_rodzenstwa(X,Y) :-
    rodzenstwo(Y,B),
    dziecko(A,X),
    dziecko(A,B),
    X \= Y.

%G) x jest dzieckiem dziadka i rodzica y 
rodzic(a,x).
rodzic(b,x).
rodzic(a,c).
rodzic(b,y).
rodzic(c,y).

dziadek(X,Y) :-
    rodzic(A,Y),
    dziecko(A,X),
    X \= Y.

dziecko_dziadka_rodzica(X,Y) :-
    dziadek(A,Y),
    rodzic(B,Y),
    dziecko(X,A),
    dziecko(X,B),
    X \= Y.
```
