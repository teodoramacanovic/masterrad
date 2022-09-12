# masterrad
ARXPY tool  

Alat ArxPy je razvijen kako bi olakšao i ubrzao procenu bezbednosti ARX blok šifara. ArxPy je oruđe-instrument za pronalaženje optimalnih RX karakteristika ARX blok šifara. ArxPy koristi Python implementaciju ARX blok šifri kao ulaz i primenjuje SAT-zasnovanu metodu za pronalaženje tih karakteristika. Kada nam je data Python implementacija ARX blok šifre, ArxPy se izršava jednostavnom shell komandom, te je stoga jedino potrebno uložiti trud za implementaciju ARX šifri u Python-u. S obzirom na to da ArxPy ima otvoreni izvorni kod i modularnu arhitekturu, moguće je lako ga prilagoditi za neku specifičnu potrebu.  

ArxPy očekuje određenu strukturu u Python implementaciji ARX blok šifri. Python implementacija ARX blok šifre koja zadovoljava traženu strukturu naziva se ARX implementacija.  

Minimalna ARX implementacija se sastoji od globalne promenljive wordsize, i dve funkcije: key_schedule i encryption. Globalna promenljiva wordsize sadrži veličinu reči (u bitovima) ARX blok šifre.  

Funkcija key_schedule implementira algoritam proširivanja ključa ARX blok šifre. Ova funkcija ima m argumenata, koji reprezentuju m reči ključa. Ova funkcija nema povratnu vrednost – potključevi se čuvaju u objektu nalik na listu, round_keys.  

Funkcija encryption implementira algoritam šifrovanja ARX blok šifre. Argumenti ove funkcije predstavljaju reči teksta. Izlaz svake runde se čuva u objektu nalik na listu, rounds, osim poslednjeg izlaza, koji se koristi kao povratna vrednost. Ova funkcija može da sadrži rundne ključeve iz objekta round_keys.
Kako bi se implementirali algoritmi šifrovanja i proširivanja ključa, Python operatori $+$, $\ggg$ , $\lll$ i $\oplus$ se koriste kao sabiranje po modulu, desna i leva rotacija i XOR, tim redosledom.   

Osim promenljive wordsize i funkcija key_schedule i encryption, moguće je definisati dodatne promenljive i funkcije, kako bi se poboljšala preglednost i modularnost implementacije.   

Postoji nekoliko ograničenja u vezi sa objektima rounds i round_keys:  

 -Oni nisu kreirani niti deklarisani u ARX implementaciji, nego su kreirani od strane parsera ArxPy  
 
 -Podržavaju jedino operator [ ] za pristup svojim elementima (negativni indeksi nisu dozvoljeni)  
 
 -Mogu da čuvaju ili jednu vrednost ili listu vrednosti, ali svaka pozicija može biti dodeljena samo jednom.
