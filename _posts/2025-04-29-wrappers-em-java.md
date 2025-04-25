---
title: Wrappers em Java
description: Aprenda o que são e como usar os Wrappers em Java.
author: Raniery
date: 2025-04-25 08:51:00 +0300
categories: [Java, Tutorial]
tags: [Code]
# pin: true
image:
  path: /assets/img/posts/code.png
  alt: Código Java com Integer e equals()
---

Imagine a seguinte situação: você está desenvolvendo em Java e precisa armazenar uma lista de números inteiros. Em um primeiro contato pode ser que você tente usar `ArrayList<int>`, porém isto terá um erro de compilação uma vez que *ArrayList* apenas armazena objetos. Para prosseguir com o desenvolvimento, você terá que buscar alguma forma de armazenar valores em um objeto então qual seria a forma de resolver este problema? Através das classes **Wrapper**.

## O que são Wrappers afinal?

Antes de tudo é necessário uma contextualização sobre a linguagem Java. Embora Java possa ser utilizado para outros paradigmas de programação como Funcional e Procedural, o cerne dela é a Orientação a Objetos, e portanto, é necessário que haja um mecanismo para que tipos primitivos possam ser tratados como objetos e consequentemente serem manipulados como um. Para o uso em Collections, o *ArrayList* tratado inicialmente seria declarado como `ArrayList<Integer>`.

```java
ArrayList<int> = ... //Type argument cannot be of a primitive type
ArrayList<Integer> list = ... // Ok
ArrayList<int[]> list = ... // Ok, Reference Type 
``` 
[Reference Type ^fn1]

Além disso, por serem objetos as classes Wrapper fornecem uma gama de métodos utilitários para trabalhar com os valores primitivos encapsulados, tais como métodos de conversão de tipo como `Integer.toString()` para retornar o valor como *String*. Outra vantagem é a possibilidade de usar *null* para representar ausência de um valor, algo que não é possível utilizando tipos primitivos.

Para cada um dos oito tipos primitivos existe uma classe wrapper correspondente, que podem ser importados através do pacote `java.lang`, sendo: 

| Tipo Primitivo   | Wrapper    |
| :--------------- | :--------- |
| boolean          | Boolean    |
| byte             | Byte       |
| short            | Short      |
| int              | Integer    |
| long             | Long       |
| float            | Float      |
| double           | Double     |
| char             | Character  |

### Mas e String?

A classe String, embora possa parecer um Wrapper, é na verdade uma sequência de caracteres e implementa uma interface chamada `CharSequence`[^fn2]. Por conta desta interface temos métodos como `charAt()`, `length()`(que você provavelmente nunca lembra se é length ou lenght) e `toString()`. As classes `StringBuilder` e `StringBuffer` também implementam CharSequence, consequentemente permitindo o polimorfismo.

## E porque não usar apenas Wrappers?

Apesar de ser uma grande flexibilidade e inúmeros benefícios, o uso deve ser situacional uma vez que impacta diretamente no desempenho e consumo de memória da aplicação, principalmente se comparado ao uso direto de tipos primitivos, que são armazenados diretamente na memória, enquanto os Wrappers juntamente com objetos de maior complexidades são alocados no heap

## Autoboxing

## Equals (titulo provisorio)

Em construção... 🚧

Passível de mudanças

## Notas de rodapé
[Reference Type ^fn1]: <https://docs.oracle.com/javase/8/docs/jdk/api/jpda/jdi/com/sun/jdi/ReferenceType.html>
[^fn2]: <https://docs.oracle.com/javase/8/docs/api/java/lang/CharSequence.html>
