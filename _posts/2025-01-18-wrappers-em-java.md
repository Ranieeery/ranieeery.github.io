---
title: Wrappers em Java
description: Aprenda o que são e como usar os Wrappers em Java.
author: Raniery
date: 2025-01-18 08:51:00 +0300
categories: [Java, Tutorial]
tags: [Code]
# pin: true
image:
  path: /assets/img/posts/code.png
  alt: Código Java com Integer e equals()
---

<!-- TODO: Acho que posso melhorar essa introdução -->

Se você já utilizou Java por um tempo deve ter percebido que todos os tipos primitivos começam com a inicial minúscula
(como `int`, `float` e `boolean`), porém em algum momento deve ter visto `Integer` ou `Double` com letra maiúscula e que
permitia a utilização de métodos. Isto se deve porque não é um tipo primitivo, é algo chamado de **classe Wrapper** e 
são fundamentais para o desenvolvimento em Java.

## Mas o que são essas classes Wrappers afinal?

Antes de tudo é necessário uma contextualização sobre a linguagem Java. Embora Java possa ser utilizado para outros 
paradigmas de programação como Funcional e Procedural, o cerne dela é a Orientação a Objetos, e portanto, é necessário 
que haja um mecanismo para que tipos primitivos possam ser trados como objetos e consequentemente serem manipulados 
como um. Para o uso em Collections por exemplo: 

Ao colocar `List<int>` para uma lista de inteiros irá acarretar em um erro de compilação uma vez que este método recebe 
`List<E>`, sendo E a representação de um elemento que corresponde ao tipo que a estrutura armazenará (pretendo abordar 
Generics futuramente). Portanto, para uma lista de inteiro é necessário declarar como `List<Integer>`.

Para cada um dos oito tipos primitivos existe uma classe wrapper correspondente, que podem ser importados através do pacote
`java.lang`, sendo eles: 

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

### Mas cadê String?

A classe String é na verdade uma sequência de caracteres e implementa uma interface chamada `CharSequence`[^fn1], por conta disso 
temos métodos como `charAt()`, `length()`(que você provavelmente nunca lembra se é length ou lenght) e `toString()`. As classes 
`StringBuilder` e `StringBuffer` também implementam CharSequence, consequentemente permite o polimorfismo, como por exemplo: 


```java
public void print(CharSequence cs) {
    System.out.println(cs);
}

print("Hello World"); // Uso de String
```

## E porque não usar apenas Wrappers?

Apesar de ser uma grande flexibilidade e inúmeros benefícios, o uso deve ser situacional uma vez que impactam diretamente no desempenho e consumo
de memória da aplicação, principalmente se comparado ao uso direto de tipos primitivos, que são armazenados diretamente na memória, enquanto os 
Wrappers juntamente com Objetos de maior complexidades são alocados no heap

Em construção... 🚧

Passível de mudanças

## Notas de rodapé
[^fn1]: <https://docs.oracle.com/javase/8/docs/api/java/lang/CharSequence.html>
