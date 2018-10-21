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

## Constructeurs

```java
  class CercleConstructeurs {
    public final String couleur;
    public double rayon = 0;

    public CercleConstructeurs() {
      this(0, "NOIR");
    }

    public CercleConstructeurs(double rayon) {
      this(rayon, "NOIR");
    }

    public CercleConstructeurs(String couleur) {
      this(0, couleur);
    }

    public CercleConstructeurs(double rayon, String couleur) {
      this.rayon = rayon;
      this.couleur = couleur;
    }

    public void afficherInformations() {
      System.out.printf(
        "Ceci est un cercle de couleur: %s. Le rayon vaut %.2f.%n",
        this.couleur,
        this.rayon
      );
    }
  }

  class Constructeurs {
    public static void main(String[] args) {
      CercleConstructeurs un = new CercleConstructeurs();
      CercleConstructeurs deux = new CercleConstructeurs(5.0);
      CercleConstructeurs trois = new CercleConstructeurs("BLEU");
      CercleConstructeurs quatre = new CercleConstructeurs(12.0, "ROUGE");

      un.afficherInformations();
      deux.afficherInformations();
      trois.afficherInformations();
      quatre.afficherInformations();
    }
  }
```

## Visibilité (public, private) et final

```java
  class CercleVisibilite {
    public final String couleur;
    private double rayon;

    public CercleVisibilite(double rayon, String couleur) {
      this.rayon = rayon;
      this.couleur = couleur;
    }

    public void doublerRayon() {
      if(peutDoublerRayon()) {
        this.rayon *= 2;
      }
    }

    private boolean peutDoublerRayon() {
      return this.rayon < 10;
    }

    public void afficherInformations() {
      System.out.printf("Cercle(couleur=%s, rayon=%.2f)%n", this.couleur, this.rayon);
    }
  }

  class Visibilite {
    public static void main(String[] args) {
      CercleVisibilite cercle = new CercleVisibilite(3, "ROUGE");

      // Impossible ! rayon est "private"
      // System.out.println(cercle.rayon);

      System.out.println(cercle.couleur); // "ROUGE"

      // Impossilbe ! couleur est "final"
      // cercle.couleur = "MAUVE";

      cercle.afficherInformations(); // Cercle(couleur=ROUGE, rayon=6.00)
      cercle.doublerRayon();  // ok, méthode public, paramètre privé
      cercle.afficherInformations(); // Cercle(couleur=ROUGE, rayon=12.00)
      cercle.doublerRayon(); // ok
      cercle.afficherInformations(); // Cercle(couleur=ROUGE, rayon=12.00)

      // Impossible ! cette méthode est "private"
      // cercle.peutDoublerRayon();
    }
  }
```

## Statics

```java
  class Eleve {
    // statics
    public static int PROMO = 2018;
    private static int NOMBRE_TOTAL = 0;

    // attributs
    public String nom;

    public Eleve(String nom) {
      this.nom = nom;
      NOMBRE_TOTAL++;
    }

    // methodes statiques
    public static int getNombreTotal() {
      return NOMBRE_TOTAL;
    }
  }

  class Statics {
    public static void main(String[] args) {
      System.out.println(Eleve.PROMO); // 2018
      Eleve.PROMO = 2020;
      System.out.println(Eleve.PROMO); // 2020

      System.out.println(Eleve.getNombreTotal()); // 0

      // impossible : c'est privé
      // System.out.println(Eleve.NOMBRE_TOTAL);

      Eleve rene = new Eleve("René");
      Eleve celine = new Eleve("Céline");
      System.out.println(rene.PROMO); // à éviter, ici 12

      System.out.println(Eleve.getNombreTotal()); // 2
    }
  }
```

## Types énumérés

```java
  enum Personne {
    // Les différentes valeurs
    BEBE(0, 3),
    ENFANT(4, 12),
    ADOLESCENT(13, 18),
    ADULTE(18, Integer.MAX_VALUE);

    // Attributs d'instance
    private final int ageMin;
    private final int ageMax;

    // Constructeur
    Personne(int ageMin, int ageMax) {
      this.ageMin = ageMin;
      this.ageMax = ageMax;
    }

    // Méthode
    public boolean isCloserToMaxAge(int age) {
      double middleAge = (this.ageMax + this.ageMin) / 2.0;
      return age >= middleAge;
    }

    // Méthode statique
    public static Personne getPersonneForAge(int age) {
      if (age <= BEBE.ageMax) {
        return BEBE;
      } else if (age <= ENFANT.ageMax) {
        return ENFANT;
      } else if (age <= ADOLESCENT.ageMax) {
        return ADOLESCENT;
      } else {
        return ADULTE;
      }

    }
  }

  class TypesEnumeres {

    public static void main(String[] args) {
      System.out.println(Personne.ENFANT.isCloserToMaxAge(5));  // false
      System.out.println(Personne.ENFANT.isCloserToMaxAge(11)); // true

      Personne personne = Personne.getPersonneForAge(42);
      System.out.println(personne); // ADULTE
    }
  }
```
