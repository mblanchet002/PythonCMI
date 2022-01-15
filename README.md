# PythonCMI

## Projet numérique Python CMI


### Projet XPS

La spectrométrie photoélectronique X ou spectrométrie de photoélectrons induits par rayons (XPS) est une méthode qualitative sensible à la surface et non invasive qui permet d’identifier les éléments existants dans un matériau. Elle permet également de donner l’état chimique, la structure chimique et la densité électronique de l’élément dans le matériau.
Lors d’une expérience XPS, l’échantillon est bombardé par des rayons X d’une certaine longueur d’onde, qui émet un électron qui est ensuite détecté. Les électrons éjectés ont des énergies propres à chaque atome, ce qui permet donc de déterminer la composition de l’échantillon. 
La XPS est très utilisée pour l’analyse des composés inorganiques, des alliages métalliques, semiconducteurs, catalyseurs, céramiques, etc. La méthode est moins utilisée pour des composés dans sa forme hydratée comme des hydrogels car la XPS ne détecte pas l’hydrogène ou l’hélium.

L'objectif de ce projet était de réussir à modéliser l'enveloppe d'un signal XPS (intensité en fonction de l'énergie de liaison).

#### Principe de la XPS

La XPS est une application de l’effet photoélectrique décrit pas Einstein en 1905. Dans cet effet, les électrons sont émis par des atomes en réponse à l’impact d’un rayonnement électromagnétique.
Einstein prédit que des photoélectrons seraient produits à partir d’un matériau lorsque l’énergie des photons incidents dépasse l’énergie de liaison des électrons dans ce matériau. L’énergie est proportionnelle à la fréquence des photons (ℎν).  
L'énergie cinétique de l’électron émis est liée à l'énergie de liaison de chaque électron, et comme les atomes ont plusieurs orbitales à différents états d'énergie, la réponse résultante sera une gamme d'électrons émis avec différentes énergies de liaison (et énergies cinétiques) produisant ainsi un spectre XPS.

                        ℎν=EL+EC+φ

Où ℎν est l’énergie du photon avec h la constante de Planck et ν la fréquence de la radiation. EL est l’énergie de liaison, EC l’énergie cinétique et φ la fonction de travail.

Comme les rayons X ont des énergies entre 0 et 100 eV, ce sont les électrons de cœur qui sont émis. Ces électrons de cœur ont des énergies caractéristiques à chaque atome, ce qui permet d’identifier l’élément dans un matériau.

#### Instrumentation

L'appareil XPS est composé d’une source de rayons X, une chambre d’irradiation, un canon ionique, un neutralisateur de charges, des pompes, un analyseur d’électrons et un analyseur.

##### Source de rayons X
Les sources de rayons X sont la partie de l’appareillage qui nous permet d’avoir les rayons X. Le choix du type de source se fait selon les critères suivants :
-	La résolution de l’énergie du rayon X,
-	L’énergie des photons émis, il faut une énergie suffisante pour éjecter les électrons

##### Chambre d'irradiation
La chambre d’irradiation ou chambre d’ultravide est la chambre où l’échantillon est déposé afin d’être irradié. Elle sert à faire l’ultravide et l’environnement dans la chambre doit être exempt de champ magnétique externe.

##### Canon ionique
Un canon ionique est utilisé pour nettoyer la surface de l’échantillon qui a pu être contaminée par de la poussière et des gaz résiduels de l’atmosphère. Le canon ionique permet aussi de faire un profilage de profondeur, en enregistrant des profils de profondeur et donc analyser la composition de l’échantillon en profondeur.

Les caractéristiques d’un canon sont définies selon :
-	L’énergie et le courant du faisceau d’ions,
-	La distribution du courant dans la zone
-	La taille du point


![image](https://user-images.githubusercontent.com/93384155/149346726-c319c2bc-f56b-487f-9a45-23d535299892.png)


#### Contenu du notebook Projet_XPS

Pour réaliser ce projet nous avons travailler sur un seul notebook nommé Projet_XPS. 

Sur ce notebook, nous avons tout d'abord tenté un première technique permettant de créer l'enveloppe du signal, il s'agit de découper la courbe en plusieurs morceaux afin d'isoler les pics du signal, sur chacun de ses moreceaux on créé une fonction gaussienne approximative en fonction de trois valeurs : la valeur sur l'axe des abscisses du sommet du pic (mu), la hauteur du pic (a) et sa largeur (sigma), ensuite on utilise la fonction curv_fit sur cette fonction pour trouver la gaussienne qui se rapproche au mieux du signal, enfin on concatène les différents morceaux. 

La première technique n'étant pas totalement satisfaisante, nous en avons essayé une deuxième qui utilise la fonction curv_fit sur la somme de gaussiennes ce qui nous permet d'avoir une courbe plus réaliste sans coupure.
