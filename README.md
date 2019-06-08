# Crystal

Crystal és un llenguatge de programació creat per Manas Technology Solutions, i dissenyat i desenvolupat per Ary Borenszweig, Juan Wajnerman, Brian Cardiff, juntament amb més de 300 contribuidors, nascut de voler un llenguatge que combini la facilitat d'escriure, entendre, i atractiu visual de llenguatges de scripting com Ruby, amb la eficiencia, i beneficis de seguretat de tipus de llenguatges compilats com C.

# Paradigma de programació

Crystal és un llenguatge caracteritzat per:

- Un **tipat fort i estàtic**, gràcies a l'ús d'un compilador per a generar binaris i un algorisme d'inferencia de tipus.
- Una programació **orientada a objectes** , on qualsevol component de Crystal és un objecte que sempre compleix amb:
  - Tenir un tipus.
  - Respondre a métodes.
- Preséncia de eines de **concurrència**.
- Un estil d'escriptura imperatiu, on gràcies a la herència de Ruby, resulta en codi llegible i molt semblant a llenguatges d'scripting.

## Sistema de Tipus

Una de les característiques de Crystal és que implementa un sistema de tipat on s'emplea un algorisme que infereix els tipus de cada objecte en temps de compilació. La herència de llenguatges llegibles resulta en la manca de necessitat de declarar els tipus de variables. En altres llenguatges, el programa s'executava i, en cas de trobar un error de tipus, paraba la execució llençant una excepció.

Crystal s'aprofita de utilitzar un compilador per, en temps de compilador, inferir el tipus o els possibles tipus que pot tenir una variable, i evaluar la possibilitat d'errors.

Una consequencia que ha convertit en capabilitat remarcable es la no existencia d'errors de tipus Nil. En Crystal, cap tipus pot ser Nil, i les variables que poden prendre per valor Nil resulten amb un tipus que és la unió dels altres tipus que pot prendre i Nil. D'aquesta manera, el compilador pot saber si una operació donada pot generar excepcions de tipus, i alertar d'aquestes.

```crystal
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

```python
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

Un problema que sembla aparent és el tractament de tipus com els de per exemple arxius JSON, els quals poden contenir una àmplia varietat de tipus diferents i potencialment provocar multitud d'errors de tipus. La sol·lució empleada pels desenvolupadors de Crystal es introduir un tipus anomenat *Any*, el qual suporta tots els possibles tipus dels arxius JSON.

## Tipus

Al ser un llenguatge de programació de propòsit general, incorpora la majoria de tipus coneguts:

- Bool

- Integer

- Float

- Char

- String

- Array: Representa un vector clàssic, amb la característica que els tipus dels elements poden variar

  - ```crystal
    arrayNormal = [1,2,3]			# => Array(Int32)
    arrayVariable = [1,"2",3] 		# => Array(Int32 | String)
    arrayAmbPossiblesTipusDiferents = [1,2,3] of Int32 | String
    ```

    

- Tuple: Representa una llista de valors de tamany fix. Similar a un `Array`

  - ```crystal
    tuple = {1, "String", 'Char'}
    tuple[0]	#Retorna el primer element
    ```

    

- Hash: Mapejat de claus a valors

  - ```crystal
    dict = {"clau1" => 3, "clau2" => "valor"}
    ```

    

També incorpora altres tipus més especifics com:

- Array-like

- Hask-like

- Range: Representa una llista de valors entre `n` i `m`

  - ```crystal
    (n..m)			#Genera els valors entre n i m
    (n...m)			#Genera els valors entre n i  m-1 
    (0..5).to_a 	# => [0, 1, 2, 3, 4, 5]
    (0...5).to_a 	# => [0, 1, 2, 3, 4]
    ```

- Regex: Representa una expressió regex

  - ```crystal
    var = /\'([a-zA-Z]*)\'/			#Detecta paraules dintre de cometes
    var.match "Test de 'Regex'."	#Retorna els matches de la expressió
    "Test de 'Regex'.".match var	#Sintaxis alternativa
    ```

    

- NamedTuple: Similar a `Hash`, pero inmutable, es a dir, mapeja un conjunt fixe de claus a valors

- Command: Representa una comanda de consola

  - ```crystal
    'echo foo'
    ```

- Proc: Representa un punter a una funció, la qual pot estar definida previament o definida en la declaració de la variable

  - ```crystal
    proc1 = ->{1}					#Punter a una funció sense arguments que retorna 1
    proc2 = ->(x : Int32) {x.to_s}	#Punter a una funció que pren com a argument un 								 Int32 i retorna la representació d'aquest en 									 string
    Array(Int32, String -> Char)	#Crea un array de procs que prenen com a arguments 									un Int32 i un String i retornen un Char
    ```

    Una dada curiosa a remarcar és la similitud de sintaxis que tenen les definicions dels procs en Crystal amb les definicions dels tipus a Haskell. Mentre que a haskell els arguments s'uneixen amb ```->```, a Crystal es separen amb ```,```. Aquesta similitud es merament visual, ja que els dos llenguatges tracten arguments de maneres completament diferents.





# Llenguatges similars

Crystal és un llenguatge derivat de **Ruby**, la qual cosa implica que les similituds haurien de ser altes; són tant semblants, que molt codi escrit en Ruby pot ser executat directament en Crystal, tot i que aquesta no és la intenció dels desenvolupadors.

Un altre llenguatge similar és **Python**, un llenguatge de scripting força conegut i que té una sintaxis força semblant a Crystal.

Tot i que tots dos són força semblants, Crystal es promociona com a un llenguatge fàcil d'aprendre per a gent que coneix Ruby, ja que pren inspiració d'aquest, al contrari que amb Python, el qual proporciona als seus usuaris una certa familiaritat per a poder adaptar-se més ràpidament a Crystal.

# Característiques Particulars

Crystal té certs aspectes i característiques particularment interessants que cal mencionar.

- Una de les maneres que intenta combinar llenguatges de scripting i compilats és amb la capabilitat del seu compilador per a poder tant generar un arxiu binari o executar directament el codi. Internament, el funcionament no té més misteri que, al executar el codi directament, genera un arxiu binari temporal, i executa aquest.
- Està majoritariament programat en Crystal. Només una petita part del seu codi base està escrita en C, mentre que la resta s'implementa en Crystal.
- Incorpora certs aspectes de C directament. És capaç d'utilitzar llibreries de C nativament, i pren inspiració de les macros de C per a fer la seva pròpia implementació.
- Encara no proporciona suport natiu a Windows. L'única manera de fer-ho servir es amb un subsistema per a Linux.
- No disposa de paral·lelisme natiu. El mecanisme més semblant que té són els *Fibers*, que són bàsicament *Threads* lleugers.

## Bibliografia

*Crystal-Lang*: <https://crystal-lang.org/>

*Crystal reference*: <https://crystal-lang.org/reference/overview/>

*Crystal By Example*, Repositori GitHub: <https://github.com/askn/crystal-by-example>

*Crystal API*: <https://crystal-lang.org/api/0.29.0>

