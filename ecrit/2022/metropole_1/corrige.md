# Métropole 2022

## Exercice 1

### Partie A : Expression correctement parenthésée 

#### Question 1.
« les éléments sont maintenant retirés (pour être lus) de cette structure de données
dans le même ordre qu’ils y ont été ajoutés lors de l’enregistrement »

Pile --> filo (first in last out)
File --> fifo (first in first out)

Ici nous sommes dans le cas d'une FILE.

-----------------------------
Exemple : On considère l’expression simplifiée A : "( )( ( ) )" 
Lors de l’analyse de l’expression A, controleur (initialement égal à 0)
prend successivement pour valeur 1, 0, 1, 2, 1, 0. Le parenthésage est correct. 
----------------------------

#### Question 2

Expression simplifiée B : " ((( )( )"
(initialement égal à 0)
----> 1, 2, 3, 2, 3, 2

Expression simplifiée C : "(( )))("
(initialement égal à 0)
----> 1, 2, 1, 0, -1, 0

#### Question 3
```Python
 def parenthesage_correct(expression):
    """ fonction retournant True si l'expression arithmétique simplifiée (str) est correctement parenthésée, False  sinon. 
    Condition: expression ne contient que des parenthèses  ouvrantes et fermantes """
    controleur = 0 
    for parenthese in expression: #pour chaque parenthèse
        if parenthese == '(': 
            controleur = controleur + 1 
        else: # parenthese == ')' 
            controleur = controleur - 1 
            if controleur < 0  : # test 1 (à recopier et compléter)
                #parenthèse fermante sans parenthèse ouvrante 
                return False
    if controleur == 0 : # test 2 (à recopier et compléter) 
        return True #le parenthésage est correct 
    else:    
        return False #parenthèse(s) fermante(s) manquante(s)
```
### Partie B : Texte correctement balisé 

On peut faire l’analogie entre le texte simplifié des fichiers HTML (uniquement constitué de balises ouvrantes <nom>
et fermantes </nom>) et les expressions parenthésées : 
Par exemple, l’expression HTML simplifiée : 
"<p><strong><em></em></strong></p>" est correctement balisée. 
On ne tiendra pas compte dans cette partie des balises ne comportant pas de fermeture comme <br> ou <img …>.  

#### Question 4
<p><em></em></p>

a.
<p>  -->  <p><em> --> <p> --> valide

b. La pile est vide.

#### Question 5

Une expression HTML correctement balisée contient 12 balises.
Indiquer le nombre d’éléments que pourrait contenir au maximum la pile lors de son analyse.

<b1><b2><b3><b4><b5><b6></b6></b5></b4></b3></b2></b1>
Maximum 6 éléments.
--------------------------------------------------------------------------------------------------------------

## Exercice 2

On pourra utiliser les mots clés SQL suivants :
SELECT, FROM, WHERE, JOIN, ON, INSERT, INTO, VALUES, UPDATE, SET, AND. 

- la relation individu (id_ind, nom, prenom, naissance)
- la relation realisation (id_rea, titre, annee, type)
- la relation emploi (id_emp, description, #id_ind, #id_rea)
- 
### Question 1

#### a.

```sql
SELECT nom, prenom, naissance FROM individu 
WHERE nom = 'Crog'; 
```
Sur l'extrait ça retourne ça :
Crog Daniel 07-07-1968
Plus généralement cela retourne le nom, le prénom et la date de naissance de tous les individus qui ont pour nom 'Crog'

#### b.
```sql
SELECT titre, id_rea FROM realisation 
WHERE annee > 2020;
```

### Question 2

#### a.

La clé primaire doit être unique. On nous dira que la l'individu d'id_ind 688 existe déjà

#### b.

Oui, du moment que la clé primaire est différente

### Question 3

#### a.

```sql
INSERT INTO emploi 
VALUES (5400, 'Acteur(James Bond)', 688, 105); 
INSERT INTO emploi 
VALUES (5401, 'Acteur(James Bond)', 688, 325);
```
#### b.
Il faut d'abord créer la réalisation ! Pour que la clé primaire #id_rea fasse référence à quelque chose qui existe !!
Pas demandé mais cela serait :
```sql
INSERT INTO realisation 
VALUES (951, 'Docteur Yes', 2048, 'action'); 
INSERT INTO emploi 
VALUES (5402, 'Acteur(James Bond)', 688, 951);
```

### Question 4

#### a.
https://www.w3schools.com/sql/sql_join.asp
https://sql.sh/cours/jointures
https://sql.sh/cours/jointures/inner-join

```sql
SELECT nom, titre, annee 
FROM emploi 
JOIN individu ON emploi.id_ind=individu.id_ind
JOIN realisation ON realisation.id_rea=emploi.id_rea
WHERE emploi.description = 'Acteur(James Bond)';
```
#### b.
Fournir une requête SQL permettant de trouver toutes les descriptions des
emplois de Denis Johnson (Denis est son prénom et Johnson est son nom).
On veillera à n’afficher que la description des emplois et non les films associés à ces emplois.


```sql
SELECT emploi.description
FROM emploi 
JOIN individu ON emploi.id_ind=individu.id_ind
WHERE individu.nom = 'Johnson' AND individu.prenom = 'Denis';
```

-----------------------------------------------------------------------------------------------------------------------

## Exercice 3





## Exercice 4







## Exercice 5
