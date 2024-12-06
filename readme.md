# Ninja Monkey Function Blocks 🐒🍭

Welcome to the **Ninja Monkey Function Blocks** repository! This is the companion source code for the fun and insightful [Ninja Monkey](https://www.youtube.com/@ninjamonkeystutorials) video series on **OOP in PLC programming** using [TwinCAT 3 4026](https://www.beckhoff.com/en-en/products/automation/twincat/twincat-3-build-4026/). 🎥


## Table-Of-Contents

1. [🍬 What’s Inside?](#what-is-inside)
2. [Why You’ll Love It ❤️](#why-you-will-love-it)
3. [🎨 Diagrams](#diagrams)
4. [Version Log](#version-log)

## What is inside

In this video, you’ll learn how to build a **candy vending machine** 🍭 with **candies** 🍬 and **consumers** 🧍‍♀️🧍‍♂️. Along the way, the code and video will guide you through key concepts of **Object-Oriented Programming (OOP)** in PLCs:

- 🏛️ **Classes, Methods, and Properties**
- 🔒 **Access Specifiers** (who can access what!)
- 🔄 **Inheritance** (like family traits for code)
- 🌐 **Abstraction** (simplifying complexity)
- 🛠️ **Dynamic Object Creation** (objects on the fly!)
- 🤝 **Techniques** like **delegation** and **dependency injection**.

> ⚠️ **Note:** This video does **not** cover `Interface`s—that’s reserved for another tutorial. Stay tuned!

## Why You Will Love It

Whether you're just starting out with PLC programming or looking to expand your OOP skills, this project is designed to teach and inspire. With clear explanations and practical examples, you’ll be able to take your PLC programming to the next level.
So grab some candy 🍬, dive in, and let’s build something sweet!

## Diagrams

```mermaid 
classDiagram
    AnyToTArgConverter <|-- AbstractCandy
    AbstractCandy *-- CandyTypes
    AbstractCandy *-- CandyName
    AbstractCandy *-- CandyAmountInGram
    AbstractCandy *-- AbstractCandyDispatcher
    AbstractCandyConsumer *-- SatisfactionLevelInPercent
    AbstractCandyConsumer *-- ConsumerName
    AbstractCandy .. AbstractCandyConsumer
    AbstractCandyDispatcher -- AbstractCandyConsumer
    class AnyToTArgConverter{
        <<Abstract>>
        # AnyToArg(in :ANY) Tc2_Utilities.T_Arg
        - typeClassToArgType(S typeClass :__SYSTEM.TYPE_CLAS, size :UDINT) Tc2_Utilities.E_ArgType
        - dereferenceAnys(in :__SYSTEM.AnyType, out :__SYSTEM.AnyType)
        - AnyTypeToArg(in :__SYSTEM.AnyType) Tc2_Utilities.T_Arg
    }
    class AbstractCandy{
        <<Abstract>>
        + amountOfCandy :CandyAmountInGram
        + nameOfCandy :CandyName
        + typeOfCandy :CandyTypes
        + initializeDispatchers()
        + FB_exit(bInCopyCode :BOOL) BOOL
        + eatMe(consumer :REFERENCE TO AbstractCandyConsumer) POINTER TO AbstractCandy
        # destruct() POINTER TO AbstractCandy
        # addNewDispatcher(candyType :CandyTypes) 
        # logCandyConsume(consumer :REFERENCE TO AbstractCandyConsumer) 
        - freeDispatchers()

    }
    class CandyTypes{
        <<Enumeration>>
        CANDY_BARS :WORD = 1
        CAND_CORN :WORD = 2
        CANDY_STICKS :WORD = 4
        CARAMEL_CANDY :WORD = 8
        CHOCOLATE_CANDY :WORD = 16
        GUMMY_CANDY :WORD = 32
        MINTS :WORD = 64
        LOLLIPOPS :WORD = 128
        JAWBREAKERS :WORD = 256
        HARDCANDY :WORD = 512
        LICORICE_CANDY :WORD = 1024
        SOUR_CANDY :WORD = 2048
    }
    class CandyName{
        <<Alias>>
        Tc2_System.T_MaxString
    }
    class CandyAmountInGram{
        <<Alias>>
        UINT 0..500
    }
    class AbstractCandyConsumer{
        <<Abstract>>
        + levelOfSatisfaction :SatisfactionLevelInPercent
        + name :ConsumerName
        + eatCandyBars(amount :CandyAmountInGram)
        + eatCandyCorn(amount :CandyAmountInGram)
        + eatCandySticks(amount :CandyAmountInGram)
        + eatCaramelCandy(amount :CandyAmountInGram)
        + eatChoclateCandy(amount :CandyAmountInGram)
        + eatGummyCandy(amount :CandyAmountInGram)
        + eatHardCandy(amount :CandyAmountInGram)
        + eatJawbreakers(amount :CandyAmountInGram)
        + eatLicoriceCandy(amount :CandyAmountInGram)
        + eatLollipops(amount :CandyAmountInGram)
        + eatMints(amount :CandyAmountInGram)
        + eatSourCandy(amount :CandyAmountInGram)
    }
    class ConsumerName{
        <<Alias>>
        Tc2_System.T_MaxString
    }
    class SatisfactionLevelInPercent{
        <<Alias>>
        UINT 0..100
    }
    class AbstractCandyDispatcher{
        <<Abstract>>
        + destruct() POINTER TO AbstractCandyDispatcher
        + eat(consumer :REFERENCE TO AbstractCandyConsumer, amount :CandyAmountInGram)
        # eatCandiesIsImpossible(consumer :REFERENCE TO AbstractCandyConsumer, amount :CandyAmountInGram) :BOOL
    }
 ```

## Folder-Structure

*   **.\\**
*   **src\\** _root folder for all project sources_
*   **.gitignore**  _the git ignore file for this project_
*   **.gitattributes** _the git attribute file for the LFS support_
*   **README.md** _the file you read right now_

## Version-Log

### Versions 

1.	[0.0.0.0](#0000)

### 0.0.0.0 
_initial commit_


