## Zadanie 2
### Załóżmy, że w pewnej bazie zdefiniowano wyłącznie predykaty: rodzic oraz mężczyzna. Załóżmy ponadto, że zakresem rozważań jest zbiór osób – jako dodatkowy, trzeci predykat. Opierając się na tych trzech predyklatach zdefiniuj w języku Prolog kolejno każdą z poniższych reguł:
```prolog
osoba(tytus).
osoba(romek).
osoba(atomek).
osoba(tadeusz).
osoba(adam).
osoba(konrad).
osoba(ewa).
osoba(anna).
osoba(maria).
osoba(katarzyna).
osoba(weronika).
osoba(alicja).

mezczyzna(tytus).
mezczyzna(romek).
mezczyzna(atomek).
mezczyzna(tadeusz).
mezczyzna(adam).
mezczyzna(konrad).

rodzic(weronika, ewa).
rodzic(ewa, anna).
rodzic(ewa, tytus).
rodzic(romek, anna).
rodzic(romek, tytus).
rodzic(ewa, tadeusz).
rodzic(atomek, tadeusz).
rodzic(tytus, adam).
rodzic(alicja, adam).
rodzic(weronika, konrad).
rodzic(atomek, konrad).
rodzic(tadeusz, maria).
rodzic(anna, maria).

%1. kobieta(X)
kobieta(X) :-
    \+ mezczyzna(X),
    osoba(X).

%2. ojciec(X,Y) – X jest ojcem Y
ojciec(X,Y) :-
    mezczyzna(X),
    rodzic(X,Y).

%3. matka(X,Y) – X jest matką Y
matka(X,Y) :-
    kobieta(X),
    rodzic(X,Y).

%4. corka(X,Y) – X jest córką Y
corka(X,Y) :-
    kobieta(X),
    rodzic(Y,X).

%5. brat_rodzony(X,Y) – X jest rodzonym bratem Y
brat_rodzony(X,Y) :-
    mezczyzna(X),
    rodzic(A,X),
    rodzic(A,Y),
    rodzic(B,X),
    rodzic(B,Y),
    mezczyzna(A),
    kobieta(B),
    A \= B,
    X \= Y.

%6. brat_przyrodni(X,Y) – X jest przyrodnim bratem Y
brat_przyrodni(X,Y) :-
    mezczyzna(X),
    rodzic(A,X),
    rodzic(A,Y),
    rodzic(B,X),
    rodzic(C,Y),
    B \= C,
    A \= B,
    A \= C,
    X \= Y.
    
%7. kuzyn(X,Y) – X jest kuzynem Y
kuzyn(X,Y) :-
    mezczyzna(X),
    rodzic(A,X),
    rodzic(B,Y),
    rodzic(C,A),
    rodzic(C,B),
    A \= B,
    C \= B,
    C \= A,
    X \= Y.

%8. dziadek_od_strony_ojca(X,Y) – X jest dziadkiem od strony ojca dla Y
dziadek_od_strony_ojca(X,Y) :-
    mezczyzna(X),
    rodzic(X,A),
    rodzic(A,Y),
    mezczyzna(A),
    X \= A,
    Y \= A,
    X \= Y.
    

%9. dziadek_od_strony_matki(X,Y) – X jest dziadkiem od strony matki dla Y
dziadek_od_strony_matki(X,Y) :-
    mezczyzna(X),
    rodzic(X,A),
    rodzic(A,Y),
    kobieta(A),
    X \= A,
    Y \= A,
    X \= Y.

%10. dziadek(X,Y) – X jest dziadkiem Y
dziadek(X,Y) :-
    mezczyzna(X),
    rodzic(X,A),
    rodzic(A,Y),
    X \= A,
    Y \= A,
    X \= Y.

%11. babcia(X,Y) – X jest babcią Y
babcia(X,Y) :-
    kobieta(X),
    rodzic(X,A),
    rodzic(A,Y),
    X \= A,
    Y \= A,
    X \= Y.

%12. wnuczka(X,Y) – Y jest wnuczką X
wnuczka(X,Y) :-
    kobieta(X),
    corka(X,A),
    corka(A,Y),
    X \= A,
    Y \= A,
    X \= Y.

%13. przodek_do2pokolenia_wstecz(X,Y) – X jest przodkiem Y do drugiego pokolenia wstecz
przodek_do2pokolenia_wstecz(X,Y) :-
    babcia(X,Y);
    dziadek(X,Y),
    X \= Y.

%14. przodek_do3pokolenia_wstecz(X,Y) - X jest przodkiem Y do trzeciego pokolenia wstecz
przodek_do3pokolenia_wstecz(X,Y) :-
    rodzic(X,A),
	przodek_do2pokolenia_wstecz(A,Y),
    X \= A,
    Y \= A,
    X \= Y.
```
