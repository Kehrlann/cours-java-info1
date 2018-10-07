---
layout: post
title: 'Chaînes de caractères'
date: 2018-10-09 02:00
---

## Création, concaténation

```java
  String maChaine = "Je m'appelle";
  maChaine = maChaine + " Toto. J'ai " + 8 + " ans.";

  System.out.println(maChaine);  // Je m'appelle Toto. J'ai 8 ans.
```

## Comparaison

```java
  String one = "alpha";

  // Recopie manuelle
  String two = "";
  for (char c : one.toCharArray()) {
    two += c;
  }

  System.out.println(one == two); // false, ce sont deux références différents

  System.out.println(one.equals(two));  // true !

  // comparaison lexicographique
  // Attention aux majuscules et minuscules
  // "alpha" plus petit que "omega", mais plus grand que "Omega"
  System.out.println("alpha".compareTo("omega"));
  System.out.println("alpha".compareTo("Omega"));
```

## Méthodes utiles

```java
  "alpha".contains("ph");       // true
  "OMEGA".toLowerCase();        // "omega"
  "toto".replaceAll("o", "a");  // "tata"
  "".isEmpty();                 // true
  "abcde".length();             // 5
  //...
  // et bien d'autres ! Ctrl + Espace dans Eclipse
```

## StringBuffer: chaînes de caractères performantes

```java
  int nombreDeCaracteres = 100_000;
  long start = System.currentTimeMillis();
  String myString = "";
  for (int i = 0; i < nombreDeCaracteres; i++) {
    myString += "a";
  }
  System.out.printf(
      "100_000 concaténations: %dms\n",
      System.currentTimeMillis() - start
  ); // plusieurs secondes

  start = System.currentTimeMillis();
  StringBuffer myBuffer = new StringBuffer();
  for (int i = 0; i < nombreDeCaracteres; i++) {
    myBuffer.append("a");
  }
  myBuffer.toString();
  System.out.printf(
      "String Buffer de 100_000 caractères: %dms\n",
      System.currentTimeMillis() - start
  ); // quelques millisecondes
```
