Popescu Alexandru Iulian

Conway’s Game Of Life

Enunt

  Game of Life, cunoscut și sub numele de Life, este un automat celular conceput de matematicianul britanic John Horton Conway în 1970. Este un joc cu zero jucători, ceea ce înseamnă că evoluția sa este determinată de starea sa inițială, care nu necesită intrări suplimentare. 
Se interacționează cu Jocul Vieții prin crearea unei configurații inițiale și observarea modului în care evoluează.

Variante

- Varianta secvențială va fi create folosind C#.
- Variantele paralele vor folosi: Fire de executie si Linq.
Pentru firele de execuție voi încerca sa impart liniile și/sau coloanele pe anumite thread-uri pentru a mari viteza simularii.

Informatii platforma
Windows 10
Procesor: Ryzen 5
Numar nuclee
6
Numar thread-uri
12
Frecventa
3,7 GHz
Frecventa turbo
4,6 GHz
Cache level 2
3 MB
Cache level 3
32 MB

RAM: 16GB
Placa video: (nu este utilizata) NVidia RTX 3060ti

- Benchmark pentru varianta secvențială
https://live.amcharts.com/5MDkx/
Cel mai mare input a durat 84 minute. Se poate observa o creștere semnificativă a timpului de execuție atât cand crestem numarul de iteratii dar și cand crestem dimensiunile plansei de joc.
Se poate observa ca timpul este mai afectat de dublarea dimensiunii matricii decat de dublarea numărului de iterații.

- Benchmark pentru varianta paralelizata (Threading.Tasks)
https://live.amcharts.com/lkODd/

Se poate observa ca cel mai mare input, care a durat 83 de minute pe varianta secvențială, a fost redus la aproximativ 15 minute. 
Varianta paralelizata folosește un Parallel.For pentru a înlocui un nested for din funcția UpdateState(), astfel fiecare proces v-a lucra pe o alta linie din matrice simultan.

- Benchmark pentru varianta paralelizata (Linq)
https://live.amcharts.com/5Nzk3/
Pentru aceasta varianta am folosit libraria Linq pentru a paraleliza un query care contine o lista de valori de la 0 la gridHeight: list.AsParallel().ForAll(...). (20 min).
Putem observa ca și aceasta varianta este mai rapidă decat cea secvențială dar mai inceata decat cea originală, folosind Threading.Tasks,  cam cu 20%. De obicei aceasta metoda este folosita pentru query uri.

- Varianta modificata
Variabilele au fost mutate în afara funcției UpdateState pentru a fi inițializare o singura data. Se observa ca aceasta varianta este mai rapidă pe inputuri mici, deoarece pe cel mai mare input timpul este tot de ~15 minute ca si cealalta metoda de paralalizare.


Referințe gasite momentan

https://www.geeksforgeeks.org/program-for-conways-game-of-life/
http://www.jeremybytes.com/Downloads.aspx#ConwayTDD
https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life
https://www.youtube.com/watch?v=FWSR_7kZuYg&ab_channel=TheCodingTrain
https://stackoverflow.com/questions/12405938/save-time-with-parallel-for-loop
https://devblogs.microsoft.com/pfxteam/is-it-ok-to-use-nested-parallel-for-loops/
https://en.delphipraxis.net/topic/1296-nested-parallel-for-loops-bad-idea/






