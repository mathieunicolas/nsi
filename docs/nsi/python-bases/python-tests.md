---
icon: octicons/info-24
hide:
  - footer
---
# Python : conditions et tests
## if, elif, else

`if` { .def }

:   Signifie _si_ en anglais : permet de réaliser un bloc d'instructions si l'évaluation du test est positive.

`elif` { .def }

:   Contraction de _else_ et _if_, signifie _sinon, si_ : permet d'ajouter d'autres conditions dans un bloc de plusieurs tests.

`else` { .def }

:   Signifie _sinon_, permet de réaliser un bloc d'instructions dans tous les autres cas non traités par les `if` et `elif` précédents.

## Structure d'un bloc
Pour écrire un bloc d'instructions conditionnelles, la structure est précisément définie.

<div class="grid" markdown>
```python
if TEST:
  instruction1
  instruction2
  ...
elif TEST2:
  instruction3
  ...
else:
  instruction4
  ...
```

!!! info inline end
    Remarquez que chaque instruction d'un même bloc est décalée d'une **tabulation** (++tab++)

    On appelle cela l'indentation du code.

</div>

Les mots-clés `elif` et `else` ne sont pas obligatoires, leur utilisation doit être motivée par les besoins de l'algorithme.

## Effectuer un test

Pour effectuer un test, ou créer une condition, on utilise le mot-clé `if` qui signifie "si" en anglais.

Le mot-clé `elif`, contraction de **else if**, qui signifie "sinon, si" en anglais, permet d'ajouter une ou plusieurs conditions supplémentaires.


| Symbole | Signification                              | Exemple                 |
|:-------:| ------------------------------------------ | ----------------------- |
|    ==   | égalité (pour des nombres ou des chaînes)  | `ìf var == 12:`         |
|    !=   | inégalité (pour des nombres ou des chaînes | `if word != "château":` |
|    <    | est inférieur à                            | `if temperature < 15:`  |
|    >    | est supérieur à                            | `elif price > 199:`     |
|    <=   | est inférieur ou égal à                    |                         |
|    >=   | est supérieur ou égal à                    |                         |


```python title="exemple : mettre en place un choix d'options"
choix = input("Voulez-vous convertir en degrés Celsius (1) ou en Kelvin (2) ? \n")
if choix == "1":
  print("Vous avez choisi l'option 1")
elif choix == "2":
  print("Vous avez choisi l'option 2")
else:
  print("Vous avez indiqué un choix non valable.")
```

Si l'utilisateur indique "1" ou "2", alors la réponse correspondante sera affichée. Pour toute autre valeur tapée par l'utilisateur, le programme indiquera que le choix n'est pas valable.

!!!tip "astuce"
    Attention, lorsque l'utilisateur donne une réponse via la commande **input**, c'est un type **str** (chaîne de caractère) qui est créé, il faut donc penser à modifier le type de la variable si on veut manipuler des valeurs numériques entières, comme des opérations mathématiques ou de comparaison : `int(input())`.

## Les booléens
Jusqu'à présent, nous avons principalement utilisé deux types de données : les nombres (`#!python int` et `#!python float`) et les chaînes de caractère (le type `#!python str`). Il existe un troisième type tout aussi important que les deux premiers : les **booléens**. Un booléen est un type de données qui ne peut prendre que deux valeurs : vrai (`#!python True`) ou faux (`#!python False`).

À chaque fois que vous réalisez un test, le résultat est exprimé sous la forme d'un booléen. En effet, si vous testez l'égalité entre deux valeurs, on ne peut que répondre par vrai ou faux. Les booléens sont donc indirectement présents à chaque fois que vous utiliserez des tests. On peut d'ailleurs le vérifier facilement.

``` python
a = 2
b = 3
print("Soit l'expression a == b :", type(a == b), ", valeur :", a == b)
print("Soit l'expression 3 == 3 :", type(3 == 3), ", valeur :", 3 == 3)
```
<div class="result" markdown>
``` title="Résultat"
Soit l'expression a == b : <class 'bool'> , valeur : False
Soit l'expression 3 == 3 : <class 'bool'> , valeur : True
```
</div>

Notez bien l'utilisation de `==` : pour comparer l'égalité de deux valeurs, on écrit bien deux fois le signe égal. L'utilisation d'un seul `=` est utilisé pour l'affectation de variables. C'est une erreur courante qu'il faut éviter de commettre.

### and, or, not
Nous savons donc désormais que l'utilisation de la structure `if TEST:` consister à exécuter des instructions si le résultat du test est égal au booléen `True`.

Il existe trois opérateurs qui permettent de créer des structures logiques à l'aide de booléens : `and`, `or` et `not`. Grâce à ces opérateurs, on peut combiner plusieurs tests, plusieurs expressions, dans une évaluation globale.

`and` { .def }

:    _et_ en anglais : `TEST1 and TEST2` sera `True` si chaque test est égal à `True`.

`or` { .def }

:    _ou_ en anglais : `TEST1 or TEST2` sera `True` si au moins un test est égal à `True`.

`not` { .def }

:    _non_, permet d'inverser un booléen.

Le comportement de ces trois opérateurs est résumé dans ce que l'on appelle des tables de vérité.

--8<-- "docs/nsi/tables-verite.md"

On trouve aussi le *not* comme opérateur logique avec la table de vérité suivante :

| exp   | not (exp) |
| ----- | --------- |
| True  | False     |
| False | True      |

``` python title="Exemples d'utilisation" linenums="1"
a = 2
b = 3
c = 3

if a == 2 and b == 3:
  print("Oui, a == 2 et b == 3")
if a == 3 or b == c:
  print("Je peux affirmer que a == 3 OU que b == c")
if not b == a:
  print("L'expression est évaluée comme True, donc le test est False : b n'est pas égal à a.")
```
<div class="result" markdown>
``` title="Résultat"
Oui, a == 2 et b == 3
Je peux affirmer que a == 3 OU que b == c
L'expression entière est évaluée comme True, donc le test est False : b n'est pas égal à a.
```
</div>