## Zadanie 1
### a) Przedstaw w języku logiki predykatów poniższe stwierdzenia – zacznij od zidentyfikowania w nich tzw. stałych indywiduowych oraz określeniawystępujących predykatów:

Stałe indywidualne:
  - markus
  - cezar

Predykaty:
1. Markus był człowiekiem:
    czlowiek(markus)
2. Markus był pompejańczykiem (obywatelem Pompejów):
    pompejczyk(markus)
3. Wszyscy pompejańczycy byli Rzymianami:
   ∀x(pompejczyk(a)) -> rzymianie(a)
4. Cezar był władcą:
   wladca(cezar)
5. Wszyscy Rzymianie albo byli lojalni wobec Cezara, albo go nienawidzili:
   ∀x(rzymianie(a) -> (lojalnosc(a, cezar) ∨ nienawisc(a, cezar)))
6. Każdy jest lojalny wobec kogoś.
   ∀x ∃y(lojalnosc(a, y))
7. Ludzie próbują dokonać zamachu tylko na tych władców, wobec których nie są lojalni:
   zamachowiec(a, b) ∧ wladca(b) ∧ czlowiek(a) -> ∼lojalnosc(a, b)
8. Markus próbował dokonać zamachu na Cezara:
   zamachowiec(markus, cezar)

### b) Posługując się powyższymi predykatami spróbuj odpowiedzieć na pytanie, czy Markus był lojalny wobec Cezara. Czy są one wystarczające/kompletne, by można było przeprowadzić formalny dowód takiego stwierdzenia? Jeżeli nie, uzupełnij powyższą listę i podaj dowód:
zamachowiec(markus, cezar) ∧ wladca(cezar) ∧ czlowiek(markus) -> ∼lojalnosc(markus, cezar)
Nie musimy dopisywać większej ilosci predykatów jestesmy w stanie udowodnic brak lojalnosci markusa wobec cezara.

### c) Przekształć skonstruowane przez siebie formuły do postaci koniunkcyjnej normalnej (CNF):
### d) Przeprowadź dowód z punktu b) metodą rezolucji.
