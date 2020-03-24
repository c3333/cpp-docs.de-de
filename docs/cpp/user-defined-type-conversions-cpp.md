---
title: Benutzerdefinierte Typkonvertierungen (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: 055b5bd5c82e4f0be449d548de25267eabef47bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187933"
---
# <a name="user-defined-type-conversions-c"></a>Benutzerdefinierte Typkonvertierungen (C++)

Eine *Konvertierung* erzeugt einen neuen Wert eines Typs aus einem Wert eines anderen Typs. *Standard Konvertierungen* sind in der C++ Sprache integriert und unterstützen die integrierten Typen. Sie können auch *benutzerdefinierte Konvertierungen* erstellen, um Konvertierungen in, aus oder zwischen benutzerdefinierten Typen auszuführen.

Die Standardkonvertierungen konvertieren zwischen integrierten Typen, zwischen Zeigern oder Verweisen auf Typen, die durch Vererbung verwandt sind, von und zu void-Zeigern und zum NULL-Zeiger. Weitere Informationen finden Sie unter [Standard Konvertierungen](../cpp/standard-conversions.md). Benutzerdefinierte Konvertierungen konvertieren zwischen benutzerdefinierten Typen oder zwischen benutzerdefinierten Typen und integrierten Typen. Sie können als [konvertierungskonstruktoren](#ConvCTOR) oder als [Konvertierungs Funktionen](#ConvFunc)implementiert werden.

Konvertierungen können entweder explizit sein—wenn ein Programmierer einen Typen z. B. durch eine Umwandlung oder direkte Initialisierung in einen anderen Typen konvertiert—oder implizit—wenn die Sprache oder das Programm einen anderen Typen als den vom Programmierer angegeben verlangt.

Implizite Konvertierungen werden in den folgenden Fällen ausgeführt:

- Wenn ein Argument einer Funktion nicht vom gleichen Typ ist wie der entsprechende Parameter.

- Wenn ein Rückgabewert einer Funktion nicht vom gleichen Typ ist wie der Rückgabetyp der Funktion.

- Wenn ein Initialisiererausdruck nicht vom gleichen Typ ist wie das initialisierte Objekt.

- Wenn ein Ausdruck, der eine Bedingungsanweisung, ein Schleifenkonstrukt oder einen Switch kontrolliert, nicht den richtigen Ergebnistyp für diese Kontrolle hat.

- Wenn ein an einen Operator übergebener Operand nicht vom gleichen Typ ist wie der entsprechende Operand-Parameter. Für integrierte Operatoren müssen beide Operanden vom gleichen Typ sein und werden in einen gemeinsamen Typen konvertiert, der beide Operanden darstellen kann. Weitere Informationen finden Sie unter [Standard Konvertierungen](standard-conversions.md). Für benutzerdefinierte Operatoren müssen alle Operanden vom gleichen Typ sein wie der entsprechende Operand-Parameter.

Wenn eine Standardkonvertierung eine implizite Konvertierung nicht ausführen kann, kann der Compiler eine benutzerdefinierte Konvertierung verwenden, optional gefolgt von einer zusätzlichen Standardkonvertierung zur Vervollständigung.

Wenn zwei oder mehrere benutzerdefinierte Konvertierungen mit derselben Konvertierung an einem Konvertierungsort verfügbar sind, wird die Konvertierung auch als "Mehrdeutig" bezeichnet. Solche Mehrdeutigkeiten führen zu einem Fehler, da der Compiler nicht ermitteln kann, welche der verfügbaren Konvertierungen ausgeführt werden soll. Die Definition mehrerer Wege für dieselbe Konvertierung ist jedoch nicht zwangsläufig ein Fehler, da sich die Konvertierungen an unterschiedlichen Stellen im Quellcode befinden können, z. B. in Abhängigkeit von den Headerdateien der jeweiligen Quelldatei. Sofern an jedem Konvertierungsort nur eine Konvertierung verfügbar ist, liegt keine Mehrdeutigkeit vor. Mehrdeutige Konvertierungen können auf verschiedene Arten entstehen. Die gängigsten Arten sind:

- Mehrfachvererbung. Die Konvertierung ist in mehr als einer Basisklasse definiert.

- Mehrdeutige Funktionsaufrufe. Die Konvertierung ist gleichzeitig als Konvertierungskonstruktor des Zieltyps und als Konvertierungsfunktion des Quelltyps definiert. Weitere Informationen finden Sie unter [Konvertierungs Funktionen](#ConvFunc).

Mehrdeutigkeiten können normalerweise aufgelöst werden, in dem der Name des betreffenden Typs vollständiger angegeben wird, oder durch eine explizite Umwandlung zur Klarstellung Ihrer Absicht.

Sowohl Konvertierungskonstruktoren als auch Konvertierungsfunktionen folgen den Regeln für die Memberzugriffssteuerung. Die Zugänglichkeit der Konvertierungen wird jedoch nur berücksichtigt, wenn eine eindeutige Konvertierung ermittelt werden kann. Eine Konvertierung kann also auch dann mehrdeutig sein, wenn die Zugriffsebene einer konkurrierenden Konvertierung deren Ausführung verhindern würde. Weitere Informationen zur Barrierefreiheit von Membern finden Sie unter [Member Access Control](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Das Schlüsselwort explicit und Probleme mit impliziter Konvertierung

Wenn Sie eine benutzerdefinierte Konvertierung erstellen, kann der Compiler diese standardmäßig für implizite Konvertierungen verwenden. Manchmal ist dies erwünscht, aber in anderen Fällen können die einfachen Regeln des Compilers für implizite Konvertierungen dazu führen, dass dieser unerwünschten Code akzeptiert.

Ein bekanntes Beispiel für eine implizite Konvertierung, die Probleme verursachen kann, ist die Konvertierung in **bool**. Es gibt viele Gründe, warum Sie einen Klassentyp erstellen können, der in einem booleschen Kontext verwendet werden kann, z. –. zum Steuern einer **if** -Anweisung oder einer Schleife – aber wenn der Compiler eine benutzerdefinierte Konvertierung in einen integrierten Typ ausführt, kann der Compiler später eine zusätzliche Standard Konvertierung anwenden. Der Zweck dieser zusätzlichen Standard Konvertierung besteht darin, Dinge wie die herauf Stufung von **kurz** nach **int**zu ermöglichen, aber auch die Tür für weniger offensichtliche Konvertierungen zu öffnen, z. –. von **bool** zu **int**, sodass Ihr Klassentyp in ganzzahligen Kontexten verwendet werden kann, die Sie nie vorgesehen haben. Dieses spezielle Problem wird als *sicheres boolescher Problem*bezeichnet. Bei dieser Art von Problem kann das **explizite** Schlüsselwort helfen.

Das **explizite** Schlüsselwort teilt dem Compiler mit, dass die angegebene Konvertierung nicht zum Ausführen impliziter Konvertierungen verwendet werden kann. Wenn Sie vor der Einführung des **expliziten** Schlüssel Worts die syntaktische Bequemlichkeit impliziter Konvertierungen wollten, mussten Sie entweder die unbeabsichtigten Folgen akzeptieren, die manchmal von der impliziten Konvertierung erstellt wurden, oder weniger praktische, benannte Konvertierungs Funktionen als Problem Umgehung verwenden. Mit dem **expliziten** Schlüsselwort können Sie nun bequeme Konvertierungen erstellen, die nur zum Ausführen expliziter Umwandlungen oder direkter Initialisierung verwendet werden können. Dies führt nicht zu der Art von Problemen, die durch das sichere boolesche Problem verdeutlicht werden.

Das **explizite** Schlüsselwort kann seit c++ 98 auf konvertierungskonstruktoren und Konvertierungs Funktionen seit c++ 11 angewendet werden. Die folgenden Abschnitte enthalten weitere Informationen zur Verwendung des **expliziten** Schlüssel Worts.

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Konvertierungskonstruktoren

Konvertierungskonstruktoren definieren Konvertierungen von benutzerdefinierten oder integrierten Typen zu einem benutzerdefinierten Typ. Das folgende Beispiel veranschaulicht einen konvertierungskonstruktor, der vom integrierten Typ **Double** in einen benutzerdefinierten Typ konvertiert wird `Money`.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

Beachten Sie, dass der erste Aufruf der Funktion `display_balance`, die ein Argument vom Typ `Money` entgegennimmt, keine Konvertierung erfordert, da das Argument bereits vom korrekten Typ ist. Beim zweiten `display_balance`-Aufrufe wird jedoch eine Konvertierung benötigt, da der Typ des Arguments, ein **Double** mit dem Wert `49.95`, nicht von der Funktion erwartet wird. Die Funktion kann diesen Wert nicht direkt verwenden, aber da eine Konvertierung vom Typ des Arguments –**Double**– in den Typ des entsprechenden Parameters –`Money`– wird ein temporärer Wert des Typs `Money` aus dem-Argument erstellt und zum Vervollständigen des Funktions Aufrufes verwendet. Beachten Sie im dritten `display_balance`-, dass das-Argument kein **Double**ist, sondern stattdessen ein **float** -Wert mit dem Wert `9.99`– ist und der Funktions Aufrufvorgang dennoch abgeschlossen werden kann, da der Compiler eine Standard Konvertierung durchführen kann – in diesem Fall von **float** auf **Double**– und die benutzerdefinierte Konvertierung von **Double** in `Money` durchführen, um die erforderliche Konvertierung abzuschließen.

### <a name="declaring-conversion-constructors"></a>Deklarieren von Konvertierungskonstruktoren

Beim Deklarieren von Konvertierungskonstruktoren gelten die folgenden Regeln:

- Der Zieltyp der Konvertierung ist der benutzerdefinierte Typ, der konstruiert wird.

- Konvertierungskonstruktoren erwarten normalerweise genau ein Argument, das vom Quelltyp ist. Konvertierungskonstruktoren können jedoch zusätzliche Parameter definieren, wenn jeder dieser zusätzlichen Parameter einen Standardwert hat. Der Quelltyp ist weiterhin der Typ des ersten Parameters.

- Konvertierungskonstruktoren definieren wie auch alle anderen Konstruktoren keinen Rückgabetyp. Die Angabe eines Rückgabetyps bei der Deklaration führt zu einem Fehler.

- Konvertierungskonstruktoren können explizit sein.

### <a name="explicit-conversion-constructors"></a>Explizite Konvertierungskonstruktoren

Durch Deklarieren eines konvertierungskonstruktors, der **explizit**ist, kann er nur verwendet werden, um die direkte Initialisierung eines Objekts auszuführen oder eine explizite Umwandlung auszuführen. Damit wird verhindert, dass Funktionen, die ein Argument vom Klassentyp erwarten, ebenfalls implizit Argument vom Quelltyp des Konvertierungskonstruktors akzeptieren. Außerdem wird verhindert, dass der Klassentyp aus einem Wert des Quelltyps durch Kopieren initialisiert wird. Das folgende Beispiel zeigt die Definition eines expliziten Konvertierungskonstruktors und dessen Auswirkungen auf die Wohlgeformtheit des Codes.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

In diesem Beispiel können Sie den expliziten Konvertierungskonstruktor weiterhin für die direkte Initialisierung von `payable` verwenden. Falls Sie jedoch `Money payable = 79.99;` durch Kopieren initialisieren, erhalten Sie einen Fehler. Der erste Aufruf von `display_balance` ist nicht betroffen, da das Argument vom korrekten Typ ist. Der zweite Aufruf von `display_balance` führt zu einem Fehler, da der Konvertierungskonstruktor nicht für implizite Konvertierungen verwendet werden kann. Der dritte `display_balance`-ist aufgrund der expliziten Umwandlung in `Money`zulässig. Beachten Sie jedoch, dass der Compiler trotzdem geholfen hat, die Umwandlung abzuschließen, indem Sie eine implizite Umwandlung von **float** in **Double**eingefügt haben.

Obwohl die Vorzüge impliziter Konvertierungen verlockend sind, können diese zu schwer auffindbaren Bugs führen. Als Standardregel sollten alle Konvertierungskonstruktoren explizit sein, es sei denn, Sie möchten eine bestimmte Konvertierung implizit erlauben.

##  <a name="conversion-functions"></a><a name="ConvFunc"></a>Konvertierungs Funktionen

Konvertierungsfunktionen definieren Konvertierungen von einem benutzerdefinierten Typ zu anderen Typen. Diese Funktionen werden manchmal auch als "Umwandlungsoperatoren" bezeichnet, da sie zusammen mit Konvertierungskonstruktoren aufgerufen werden, wenn ein Wert zu einem anderen Typ umgewandelt wird. Das folgende Beispiel veranschaulicht eine Konvertierungs Funktion, die vom benutzerdefinierten Typ, `Money`, in den integrierten Typ **Double**konvertiert:

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

Beachten Sie, dass die Member-Variable `amount` als privat und eine öffentliche Konvertierungs Funktion in den Typ **Double** eingeführt wird, um den Wert von `amount`zurückzugeben. In der Funktion `display_balance` erfolgt eine implizite Konvertierung, wenn der Wert von `balance` durch den Operator zum Einfügen des Datenstroms `<<` in die Standardausgabe geschrieben wird. Da kein Stream-Einfügungs Operator für den benutzerdefinierten Typ `Money`definiert ist, aber einen für den integrierten Typ **Double**gibt, kann der Compiler die Konvertierungs Funktion von `Money` verwenden, **um den** Operator für das Einfügen von Daten zu erfüllen.

Konvertierungsfunktionen werden an abgeleitete Klassen vererbt. Konvertierungsfunktionen in abgeleiteten Klassen überschreiben geerbte Konvertierungsfunktionen nur dann, wenn diese zum exakt gleichen Typ konvertieren. Beispielsweise überschreibt eine benutzerdefinierte Konvertierungs Funktion des abgeleiteten Klassen **Operators int** weder – noch einen Einfluss – eine benutzerdefinierte Konvertierungs Funktion des Basisklassen **Operators Short**, auch wenn die Standard Konvertierungen eine Konvertierungs Beziehung zwischen **int** und **Short**definieren.

### <a name="declaring-conversion-functions"></a>Deklarieren von Konvertierungsfunktionen

Beim Deklarieren von Konvertierungsfunktionen gelten die folgenden Regeln:

- Der Zieltyp der Konvertierung muss vor der Deklaration der Konvertierungsfunktion deklariert werden. Klassen, Strukturen, Enumerationen und typedefs können nicht innerhalb der Deklaration der Konvertierungsfunktion deklariert werden.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Konvertierungsfunktionen akzeptieren keine Argumente. Die Angabe von Parametern bei der Deklaration führt zu einem Fehler.

- Der Rückgabetyp einer Konvertierungsfunktion wird durch deren Namen festgelegt, der gleichzeitig der Name des Zieltyps der Konvertierung ist. Die Angabe eines Rückgabetyps bei der Deklaration führt zu einem Fehler.

- Konvertierungsfunktionen können virtual sein.

- Konvertierungsfunktionen können explizit sein.

### <a name="explicit-conversion-functions"></a>Explizite Konvertierungsfunktionen

Wenn eine Konvertierungsfunktion als explizit deklariert wird, kann diese nur für explizite Umwandlungen verwendet werden. Damit wird verhindert, dass Funktionen, die ein Argument vom Zieltyp der Konvertierungsfunktion erwarten, ebenfalls implizit Argument vom Klassentyp akzeptieren. Außerdem wird verhindert, dass Instanzen des Zieltyps aus einem Wert des Klassentyps durch Kopieren initialisiert werden. Das folgende Beispiel zeigt die Definition einer expliziten Konvertierungsfunktion und deren Auswirkungen auf die Wohlgeformtheit des Codes.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

Hier wurde der Konvertierungs Funktions **Operator "Double** " explizit erstellt, und in der Funktion `display_balance` eine explizite Umwandlung in den Typ " **Double** " eingeführt, um die Konvertierung auszuführen. Ohne diese Umwandlung wäre der Compiler nicht in der Lage, den geeigneten Operator zum Einfügen des Datenstroms `<<` für den Typ `Money` zu ermitteln, und ein Fehler wäre die Folge.
