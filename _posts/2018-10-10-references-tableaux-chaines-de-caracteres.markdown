---
layout: post
title: 'Tableaux et chaînes de caractères'
---

## Déclaration & instanciation

```java
  // Standard, un tableau de 5 entiers
  // Toutes les cases sont intialisées à une valeur 0 !
  int[] monTableau = new int[5];

  // Fonctionne également, un tableau de 10 entiers
  int monAutreTableau[] = new int[10];

  // Initialisation et remplissage
  // Pas besoin d'expliciter la taille
  int monTableauRempli[] = new int[] { 1, 2, 3, 4 };
```

## Adressage et affichage

```java
  int[] myArray = new int[5];

  myArray[0] = 42;

  System.out.println(myArray[0]);   // affiche 42
  System.out.println(myArray[1]);   // affiche 0

  System.out.println(myArray);  // affiche la référence

  String contents = Arrays.toString(myArray);
  System.out.println(contents);   // affiche [42, 0, 0, 0, 0]
```

## Erreur d'indice

```java
  int[] myArray = new int[5];

  myArray[5] = 8;   // Erreur! C'est le 6ème élément d'un tableau à 5 cases.
```

## Parcours

```java
  int[] myArray = new int[] { 42, 43, 44, 45, 46 };

  // Première version : par indice
  for (int i = 0; i < myArray.length; i++) {
    System.out.println(myArray[i]);
  }

  // Seconde possibilité : par valeur
  for (int nombre: myArray) {
    System.out.println(nombre);
  }
```

## Affectation

```java
  int[] premier = {1,2,3,4,5};
  int[] deuxieme = {6,7,8,9,10};

  deuxieme = premier;

  // deuxième et premier sont des références vers le même tableau
  // modifier le contenu de deuxième == modifier le contenu de premier
  deuxieme[0] = 42;
  System.out.println(premier[0]); // affiche 42

  deuxieme = {1,1,1,1};

  // deuxième ne référence plus le même tableau que premier
  deuxieme[0] = 1337;
  System.out.println(premier[0]); // affiche toujours 42
```

## Recopie

```java
  // copier src[0..49] => dst[2..51]
  System.arraycopy(src, 0, dst, 2, 50);

  // copie les 10 premières cases de t dans t2 :
  int[] t2 = Arrays.copyOf(t, 10);

   // copie les cases 5,6..79 de t dans t3 :
  int[] t3 = Arrays.copyOfRange(t, 5, 80);
  // ATTENTION : copie les cases d'indice [5..80[

  int[] copie = t.clone();
```

## Tableaux de tableaux

```java
  // [ [0,0,0,0], [0,0,0,0] ]
  int[][] matrix = new int[2][4];
  for (int i=0 ; i<matrix.length ; i++) {
    for (int j=0 ; j<matrix[i].length ; j++) {
      matrix[i][j] = i*j;
    }
  }

  // Affichage
  System.out.println(Arrays.deepToString(matrix));
```

## Tableaux de tableaux, formes non rectangulaires

```java
  //  [? , ? , ?]
  int[] triangle = new int[3][];

  // [
  //  [0],
  //  [0, 0],
  //  [0, 0, 0],
  // ]
  triangle[0] = new int[1];
  triangle[1] = new int[2];
  triangle[2] = new int[3];
```
