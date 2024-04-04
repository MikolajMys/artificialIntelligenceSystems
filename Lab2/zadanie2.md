## Zadanie 2
### Załóżmy, że w pewnej bazie zdefiniowano wyłącznie predykaty: rodzic oraz mężczyzna. Załóżmy ponadto, że zakresem rozważań jest zbiór osób – jako dodatkowy, trzeci predykat. Opierając się na tych trzech predyklatach zdefiniuj w języku Prolog kolejno każdą z poniższych reguł:
```prolog
osoba(Tytus).
osoba(Romek).
osoba(Atomek).
osoba(Tadeusz).
osoba(Adam).
osoba(Konrad).
osoba(Ewa).
osoba(Anna).
osoba(Maria).
osoba(Katarzyna).
osoba(Weronika).
osoba(Alicja).

mezczyzna(Tytus).
mezczyzna(Romek).
mezczyzna(Atomek).
mezczyzna(Tadeusz).
mezczyzna(Adam).
mezczyzna(Konrad).

rodzic(Ewa, Anna).
rodzic(Ewa, Tytus).
rodzic(Tytus, Adam).
rodzic(Alicja, Adam).
rodzic(Weronika, Konrad).
rodzic(Atomek, Konrad).
rodzic(Tadeusz, Maria).

%1. kobieta(X)
kobieta(X) :-
    \+ mezczyzna(X),
    osoba(X).

%2. ojciec(X,Y) – X jest ojcem Y
%3. matka(X,Y) – X jest matką Y
%4. corka(X,Y) – X jest córką Y
%5. brat_rodzony(X,Y) – X jest rodzonym bratem Y
%6. brat_przyrodni(X,Y) – X jest przyrodnim bratem Y
%7. kuzyn(X,Y) – X jest kuzynem Y
%8. dziadek_od_strony_ojca(X,Y) – X jest dziadkiem od strony ojca dla Y
%9. dziadek_od_strony_matki(X,Y) – X jest dziadkiem od strony matki dla Y
%10. dziadek(X,Y) – X jest dziadkiem Y
%11. babcia(X,Y) – X jest babcią Y
%12. wnuczka(X,Y) – Y jest wnuczką X
%13. przodek_do2pokolenia_wstecz(X,Y) – X jest przodkiem Y do drugiego pokolenia wstecz
%14. przodek_do3pokolenia_wstecz(X,Y) - X jest przodkiem Y do trzeciego pokolenia wstecz
```
