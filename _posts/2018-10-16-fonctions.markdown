---
layout: post
title: 'Fonctions'
date: 2018-10-16 01:00
---

## Exemple de fonction

```java
  class MaClasse {
    public static int carre(int i) {
      return i*i;
    }

    public static void main(String[] args) {
      int x = 3;

      System.out.println(carre(x));
    }
  }
```

## Passage par valeur

```java
  public class PassageParValeur {
    public static void echange(int i, int j) {
      // i et j : copies locales
      // Toute modification ne change QUE i et j au sein
      // de cette fonction
      int tmp = i;
      i = j;
      j = tmp;
    }

    public static void main(String[] args) {
      int a = 1, b = 2;

      // Java fait une copie de a, une copie de b,
      // et passe ces copies à la fonctions. Quoique
      // la fonction fasse, à la ligne 19, a et b
      // ne seront pas modifiés
      echange(a, b);

      // a et b ne sont pas modifiés
      System.out.printf("a: %d, b: %d%n", a, b);
    }
  }
```

## Passage par référence

```java
  public class PassageParReference {
    public static void miseAuCarre(int[] tableau) {
      // Néanmoins, toute modification des objets référencés,
      // elle, se reflétera dans la fonction appelante.
      for (int i = 0; i < tableau.length; i++) {
        tableau[i] = tableau[i] * tableau[i];
      }
    }

    public static void main(String[] args) {
      int[] a = { 1, 2, 3 };

      miseAuCarre(a);

      // le CONTENU de a est modifié
      System.out.printf("a: %s%n", Arrays.toString(a));
    }
  }
```

## Récursivité

```java
  public static void somme(int i) {
    if(i == 0) {
      return 0;
    }

    return i + somme(i - 1);
  }
```

## Overloading

```java
  class NomClasse {
    // pour les String
    public static int longueur(String s) {
      return s.length();
    }

    // Pour les entiers
    public static int longueur(int i) {
      String si = String.valueOf(i);
      return si.length();
    }

    public static void main(String[] args) {
      int k = 12345;
      int lk = longueur(k); // lk vaut 5
      String s = "oui";
      int ls = longueur(s); // ls vaut 3
    }
  }
```

## Variadic arguments (varags)

```java
  class VarArgs {
    public static int max(int... nombres) {
      int currentMax = Integer.MIN_VALUE;
      for(int i: nombres) {
        if(currentMax < i) {
          currentMax = i;
        }
      }

      return currentMax;
    }

    public static void main(String[] args) {
      max();
      max(1, 2, 4);
      max(5, 8, 42, 0);
    }
  }
```
