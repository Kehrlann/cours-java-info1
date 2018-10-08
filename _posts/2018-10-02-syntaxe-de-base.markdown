---
layout: post
title: 'Syntaxe de base'
date: 2018-10-02 01:00
---

## Squelette pour écrire un programme

```java
  public class MonProgramme {
    public static void main(String[] args) {
      // Votre code ici !
    }
  }
```

## Afficher du texte

```java
  // Afficher du texte et aller à ligne
  System.out.println("Hello, world !");

  String nom = "Toto";
  int age = 8;
  double fortune = 8.5;

  System.out.printf("%s a %d ans et possède %+.2f euros.", nom, age, fortune);
  // affiche "Toto a 8 ans et possède +8.50 euros."
```

## Lire des entrées clavier par l'utilisateur

```java
  import java.util.Scanner;

  public class MonProgramme {
    public static void main(String[] args) {
      Scanner monScanner = new Scanner(System.in);

      System.out.println("Choisir un nombre entre 1 et 10:");

      // Attention, si l'utilisateur tape autre chose qu'un entier, le programme plante
      int input = monScanner.nextInt();

      if (input == 7) {
        System.out.println("Gagné !");
      } else {
        System.out.println("Perdu ...");
      }
    }
  }
```

## Lire des entrées clavier par l'utilisateur jusqu'à ce qu'il tape un entier

```java
  import java.util.Scanner;

  public class MonProgramme {
    public static void main(String[] args) {
      int monEntier;
      Scanner monScanner = new Scanner(System.in);

      System.out.println("Choisir un nombre entre 1 et 10:");

      while (true) {
        if (monScanner.hasNextInt()) {
          // Si l'entrée est un entier, le stocker dans monEntier et arrêter la boucle
          monEntier = monScanner.nextInt();
          break;
        }

        // Sinon, lire la ligne, la jeter, et afficher un message à l'utilisateur
        monScanner.nextLine();
        System.out.println("Ceci n'est pas un entier ...");
      }

      if (input == 7) {
        System.out.println("Gagné !");
      } else {
        System.out.println("Perdu ...");
      }
    }
  }
```
