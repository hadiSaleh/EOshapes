Разработать программу, которая с консоли должна принимать на вход в единый контейнер (одномерный массив или список) различные альтернативные геометрические фигуры (для начала треугольники со сторонами a, b, c и прямоугольники со сторонами x, y). После записи в контейнер вывести список введенных геометрических фигур. Отдельным циклом вывести периметры геометрических фигур. Каждая фигура - отдельный объект. Количество вводимых фигур можно ограничить 10.

Особенности реализации:
1. В runtime.jar добавлен объект string.toFloat
2. При реализации объекта треугольника возникала ошибка "The object ... has too many free attributes".
   Причем возникла она при добавлении аттрибута area, который не является свободным. Похоже на то, что ошибка возникает при проверке не только свободных аттрибутов.
   В файле eo-parser/src/main/resources/org/eolang/parser/errors/many-free-attributes.xsl увеличено максимальное значение свободных аттрибутов с 4 до 5.
   <xsl:for-each select="//o[count(o[@name and not(@base) and not(@atom)]) &gt; 5]">
   
## Examples for Eolang objects

<img src="https://www.yegor256.com/images/books/elegant-objects/cactus.svg" height="100px" />

[![Maven Central](https://img.shields.io/maven-central/v/org.eolang/eo-maven-plugin.svg)](https://maven-badges.herokuapp.com/maven-central/org.eolang/eo-maven-plugin)

You can play with EOLANG here, in a few simple steps:

First, clone this repo to your local machine and go
to the `sandbox` directory (you will need
[Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
installed):

```bash
$ git clone https://github.com/cqfn/eo.git
$ cd eo/sandbox
```

Then, compile the code (you will need
[Maven 3.3+](https://maven.apache.org/)
and [Java SDK 8+](https://www.java.com/en/download/) installed):

```bash
$ mvn compile
```

Intermediary `*.xml` files will be generated in the `target` directory (it will
be created). Also, there will be `*.java` and `*.class` files. Feel free to analyze
them: EO is parsed into XML, then translated to Java, and then compiled
by Java SDK to Java bytecode. Finally, just run the bytecode program through JRE:

```bash
$  ./run.sh 1 3.0 4.0 5.0 2 2.0 4.0 1 25.3 31.3 22.6 0
Triangle:
  Perimeter: 79.200000
  Area: 282.669609 
Rectangle:
  Perimeter: 12.000000
  Area: 8.000000 
Triangle:
  Perimeter: 12.000000
  Area: 6.000000 
```

Should work.

Then, you can modify `*.eo` files, run `mvn compile` to compile them
again and `run.sh` to run it again.

[Have fun!](https://www.elegantobjects.org)