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

Imagine a seguinte situação: você está desenvolvendo em Java e precisa armazenar uma lista de números inteiros. Inicialmente pode ser que você tente usar `ArrayList<int>`, porém isto acarretará um erro de compilação uma vez que *ArrayList* apenas armazena objetos. Para resolver isso, você precisa de uma forma de tratar valores primitivos como objetos. Como fazer isso? Através das classes **Wrapper**.

## O que são Wrappers afinal?

Antes de tudo é necessária uma contextualização sobre a linguagem Java. Embora Java suporte outros paradigmas de programação como Funcional e Procedural, o seu cerne é a Orientação a Objetos, e, portanto, é necessário que haja um mecanismo para que tipos primitivos possam ser tratados como objetos e serem consequentemente manipulados como tal. Para o uso em Collections, o *ArrayList* tratado inicialmente seria declarado como `ArrayList<Integer>`.

```java
ArrayList<int> = ... // Erro: Type argument cannot be of a primitive type
ArrayList<Integer> list = ... // Ok: Usa a classe Wrapper Integer
ArrayList<int[]> list = ... // Ok: int[] é um tipo de referência (objeto array de int), não um primitivo isolado. Confira a nota de rodapé abaixo para mais detalhes
```

> Sobre Reference Type[^fn1]

Além disso, por serem objetos, as classes Wrapper fornecem uma gama de métodos utilitários para trabalhar com os valores primitivos encapsulados, tais como métodos de conversão de tipo como `Integer.toString()` para retornar o valor como *String*. Outra vantagem é a possibilidade de usar *null* para representar ausência de um valor, algo que não é possível utilizando tipos primitivos.

```java
Integer valor = 25;
String valorStr = valor.toString();

System.out.println(valorStr) // "25"
```

Para cada um dos oito tipos primitivos existe uma classe wrapper correspondente, disponíveis no pacote `java.lang`, sendo:

| Tipo Primitivo | Wrapper   |
| :------------- | :-------- |
| boolean        | Boolean   |
| char           | Character |
| byte           | Byte      |
| short          | Short     |
| int            | Integer   |
| long           | Long      |
| float          | Float     |
| double         | Double    |

## Autoboxing e Unboxing

Por ser um objeto, normalmente teríamos que passar o tipo primitivo em um construtor para atribuição como no exemplo abaixo:

```java
Integer number = new Integer(25); // Método depreciado

Integer number = Integer.valueOf(25); // Prefira valueOf() pois ele pode reutilizar objetos do cache para valores comuns, otimizando a memória
```

Se fosse necessário sempre realizar conversões explícitas para trabalhar com Wrappers, o código se tornaria mais verboso e com uma complexidade desnecessária. Para evitar isso, o Java oferece recursos de autoboxing e unboxing para que essas conversões sejam realizadas de maneira automática.

Autoboxing é o nome do processo no qual o compilador converte o tipo primitivo para uma classe Wrapper quando necessário, evitando que o valor tenha que ser convertido manualmente. No exemplo abaixo, ao passar um *int* automaticamente o compilador converterá para um *Integer*.

```java
Integer number = 10;
```

Já o unboxing é o processo inverso, onde uma classe Wrapper é automaticamente convertida para seu tipo primitivo correspondente. Conforme o exemplo abaixo, o compilador converterá *Integer* para seu valor em *int*.

```java
Integer number = 25;
int intNumber = number;
```

## Comparação de Wrappers

Ao trabalhar com Wrappers, é fundamental entender como a comparação funciona. O operador `==` compara as referências dos objetos (se apontam para o mesmo local na memória), enquanto o método `equals()` compara os valores encapsulados.

```java
Integer a = 100;
Integer b = 100;
Integer c = 1000;
Integer d = 1000;

System.out.println(a == b);      // true
System.out.println(c == d);      // false
System.out.println(a.equals(b)); // true
System.out.println(c.equals(d)); // true
```

O código acima levanta uma questão: por que `a == b` é `true` mas `c == d` é `false`?

Isso acontece porque o Java mantém um *cache* (pool) de objetos para certos valores de Wrappers para otimizar o uso de memória. Por padrão, esses caches cobrem os seguintes valores:

- **Boolean**: `true` e `false` são sempre os mesmos objetos.
- **Byte**: Todos os valores de -128 a 127.
- **Short** e **Integer**: Valores de -128 a 127.
- **Character**: Valores de `\u0000` a `\u007F` (0 a 127).

Quando você utiliza o autoboxing ou `valueOf()` para valores dentro dessas faixas, o Java retorna um objeto já existente na memória do cache. Porém, para valores fora do range, como 1000, um novo objeto é criado. Portanto, para comparar os *valores* de objetos Wrapper, é importante utilizar o método `equals()` ou utilizar o operador `==` ciente dessas limitações de cache.

Este comportamento associado ao cache pode ser observado pelo seguinte trecho de código:

```java
Integer a = 127;
Integer b = 127;
Integer c = 128;
Integer d = 128;

System.out.println(a == b);
System.out.println(c == d);
```

## Mas e String?

A classe *String*, embora possa parecer um Wrapper, é na verdade uma sequência de caracteres e implementa uma interface chamada *CharSequence*[^fn2]. Por conta desta interface temos métodos como `charAt()`, `length()`(que você provavelmente nunca lembra se é length() ou lenght()) e `toString()`. As classes `StringBuilder` e `StringBuffer` também implementam CharSequence, consequentemente permitindo o polimorfismo.

```java
public final class String implements java.io.Serializable, Comparable<String>, CharSequence, Constable, ConstantDesc {...}
```

## Por que não usar apenas Wrappers?

Apesar de terem uma grande flexibilidade e uma gama de benefícios, o uso deve ser situacional uma vez que impacta diretamente no desempenho e consumo de memória da aplicação, principalmente se comparado ao uso direto de tipos primitivos, que são armazenados diretamente na memória, enquanto os Wrappers, como outros objetos, são alocados no heap.

Em resumo, use Wrappers quando precisar tratar primitivos como objetos, como em Collections, aproveitar seus métodos utilitários ou representar a ausência de valor com *null*. Para máxima performance em cálculos intensivos, prefira os tipos primitivos (atento para questões de precisão em pontos flutuantes também).

## Notas de rodapé

[^fn1]: <https://docs.oracle.com/javase/8/docs/jdk/api/jpda/jdi/com/sun/jdi/ReferenceType.html>
[^fn2]: <https://docs.oracle.com/javase/8/docs/api/java/lang/CharSequence.html>
