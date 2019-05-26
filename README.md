Crystal
===========

Crystal és un llenguatge de programació nascut de voler un llenguatge fàcil d'escriure, entendre, i visualment atractiu, a la vegada que ràpid. Així doncs, agafant com a principals referents, Ruby per la seva alta productivitat dels programadors degut a la facilitat d'escriptura i entesa, i C pel seu alt rendiment i eficiencia.

Paradigma de programació
=============
Crystal és un llenguatge caracteritzat per:
- Un **tipat fort i estàtic**, gràcies a l'ús d'un compilador per a generar binaris i un algorisme d'inferencia de tipus
- Una programació **orientada a objectes**, on qualsevol component de Crystal és un objecte que sempre compleix amb:
	- Tenir un tipus
	- Respondre a métodes
- Un estil d'escriptura imperatiu, on gràcies a la herència de Ruby, resulta en codi llegible i molt semblant a llenguatges d'scripting

Sistema de Tipus
-------
Una de les característiques de Crystal és que implementa un sistema de tipat on s'emplea un algorisme que infereix els tipus de cada objecte en temps de compilació. La herència de llenguatges llegibles resulta en la manca de necessitat de declarar els tipus de variables. En altres llenguatges, el programa s'executava i, en cas de trobar un error de tipus, paraba la execució llençant una excepció.

Crystal s'aprofita de utilitzar un compilador per, en temps de compilador, inferir el tipus o els possibles tipus que pot tenir una variable, i evaluar la possibilitat d'errors.

Una consequencia que ha convertit en capabilitat remarcable es la no existencia d'errors de tipus Nil. En Crystal, cap tipus pot ser Nil, i les variables que poden prendre per valor Nil resulten amb un tipus que és la unió dels altres tipus que pot prendre i Nil. D'aquesta manera, el compilador pot saber si una operació donada pot generar excepcions de tipus, i alertar d'aquestes.

```Crystal
# Crystal
condicio = true
if condicio
  i = 1
else
  i = "a"
end
print "La variable i té valor " + i
-----------------------------------------------
Output:
Error in testing.cr:9 no overload matches ‘String#+’ with type (Int32 | String)
```
En aquest code snippet es veu l'error generat pel compilador de Crystal, on detecta la possibilitat de que la variable i sigui un Int32, i per consequent, la funció print no es pugui executar correctament degut a un error de tipus.

```Python
# Python
condicio = true
if condicio:
  i = 1
else:
  i = "a"
print("La variable i té valor " + i)
-----------------------------------------------
Output:
condicio = true
TypeError: must be str, not int
condicio = false
La variable i té valor a
```
En canvi, en un llenguatge com Python, aquest error només es genera quan en una execució es compleix que i té un valor que provoca error de tipus en la funció print.

Tot i així, es pot observar que el codi de Crystal resulta força similar al de Python, amb l'avantatge de tenir més seguretat de tipus.

Llenguatges similars
====================


## Bibliografia

H. Wickham, *Advanced R*
Souce: <http://adv-r.had.co.nz/>

*Statistics with R*. Source: <http://zoonek2.free.fr/UNIX/48_R/all.html>

L. Lamport, *LATEX: a document preparation system: user’s guide and
reference manual* (Addison-Wesley Pub. Co., cop. 1994)

*An introduction to R* (W. N. Venables, D. M. Smith and the R Core Team)
Source:<https://cran.r-project.org/doc/manuals/R-intro.pdf>

*What is R programming used for?*
Source: <https://www.quora.com/What-is-R-programming-used-for>

*R, llenguatge de programació*.  Source:
<https://ca.wikipedia.org/wiki/R_llenguatgeprogramacio>

*R, Docs*. Source:(https://cran.r-project.org/doc/manuals/r-release/R-lang.html)

*Apply, lapply, sapply functions in R*,
 Source:<https://www.r-bloggers.com/apply-lapply-rapply-sapply-functions-in-r/>

*R Classes and Objects*,  Source:
<https://www.datamentor.io/r-programming/object-class-introduction/>
