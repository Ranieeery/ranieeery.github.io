---
title: Wrappers em Java
description: Aprenda o que são e como usar os Wrappers em Java.
author: Raniery
date: 2025-04-29 08:51:00 +0300
categories: [Java, Tutorial]
tags: [Code]
# pin: true
image:
  path: /assets/img/posts/code.png
  alt: Código Java com Integer e equals()
---

<!-- TODO: Acho que posso melhorar essa introdução -->

Imagine a seguinte situação: você está desenvolvendo em Java e precisa armazenar uma lista de números inteiros. Em um primeiro contato possa ser que tente usar `ArrayList<int>`, porém isto terá um erro de compilação uma vez que *ArrayList* apenas armazenas objetos. Para prosseguir com o desenvolvimento, você terá que buscar alguma forma de armazenar valores em um objeto e é aqui que os **Wrappers** entram.

## O que são Wrappers afinal?

Antes de tudo é necessário uma contextualização sobre a linguagem Java. Embora Java possa ser utilizado para outros paradigmas de programação como Funcional e Procedural, o cerne dela é a Orientação a Objetos, e portanto, é necessário que haja um mecanismo para que tipos primitivos possam ser trados como objetos e consequentemente serem manipulados como um. Para o uso em Collections, o *ArrayList* tratado inicialmente seria declarado como `ArrayList<Integer>`.

Além disso, por serem objetos as classes Wrapper fornecem uma gama de métodos utilitários para trabalhar com os valores primitivos encapsulados, tal qual métodos de conversão de tipo como `Integer.toString()` pra retornar o valor em *String*. Outra vantagem é a possibilidade de usar *null* para representar ausência de um valor, algo que não é possível utilizando tipos primitivos.

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

A classe String, embora possa parecer um Wrapper, é na verdade uma sequência de caracteres e implementa uma interface chamada `CharSequence`[^fn1]. Por conta desta interface temos métodos como `charAt()`, `length()`(que você provavelmente nunca lembra se é length ou lenght) e `toString()`. As classes `StringBuilder` e `StringBuffer` também implementam CharSequence, consequentemente permitindo o polimorfismo.

## E porque não usar apenas Wrappers?

Apesar de ser uma grande flexibilidade e inúmeros benefícios, o uso deve ser situacional uma vez que impactam diretamente no desempenho e consumo
de memória da aplicação, principalmente se comparado ao uso direto de tipos primitivos, que são armazenados diretamente na memória, enquanto os 
Wrappers juntamente com Objetos de maior complexidades são alocados no heap

## Autoboxing

## Equals (titulo provisorio)

Em construção... 🚧

Passível de mudanças

## Notas de rodapé
[^fn1]: <https://docs.oracle.com/javase/8/docs/api/java/lang/CharSequence.html>
