---
layout: post
title: 'Object Oriented Programming'
date: 2018-10-23 01:00
---

## Exemple de classe

```java
  class Cercle {
    // Attribut
    public double rayon = 0;

    // Constructeur
    public Cercle(double rayon) {
      this.rayon = rayon;
    }

    // Méthode
    public double calculerAire() {
      return Math.PI * this.rayon * this.rayon;
    }
  }

  class ExempleClasse {
    public static void main(String[] args) {
      Cercle cercle = new Cercle(5.0);
      System.out.println("rayon : " + cercle.rayon); // rayon : 5
      cercle.rayon = 12;
      System.out.println("rayon : " + cercle.rayon); // rayon : 12
      System.out.println("aire : " + cercle.calculerAire()); // aire : ...
    }
  }
```
