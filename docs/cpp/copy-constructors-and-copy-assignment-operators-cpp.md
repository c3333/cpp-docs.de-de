---
title: Kopierkonstruktoren und Kopierzuweisungsoperatoren (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189529"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Kopierkonstruktoren und Kopierzuweisungsoperatoren (C++)

> [!NOTE]
> Ab c++ 11 werden zwei Arten von Zuweisungen in der Sprache unterstützt: *Kopier Zuweisung* und *Bewegungs Zuweisung*. In diesem Artikel bedeutet "Zuweisung" immer "Kopierzuweisung", sofern nicht explizit anders angegeben. Weitere Informationen zur Verschiebungs Zuweisung finden Sie unter [bewegungskonstruktoren und BewegungsC++Zuweisungs Operatoren ()](move-constructors-and-move-assignment-operators-cpp.md).
>
> Objekte können sowohl mit dem Zuordnungsvorgang als auch dem Initialisierungsvorgang kopiert werden.

- **Zuweisung**: Wenn ein Objektwert einem anderen Objekt zugewiesen wird, wird das erste Objekt in das zweite Objekt kopiert. Deshalb gilt Folgendes:

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   dazu, den Wert von `b` nach `a` zu kopieren.

- **Initialisierung**: die Initialisierung tritt auf, wenn ein neues Objekt deklariert wird, wenn Argumente als Wert an Funktionen übermittelt werden oder wenn Werte von Funktionen nach Wert zurückgegeben werden.

Sie können die Semantik von "kopieren" für Objekte des Klassentyps definieren. Betrachten Sie z. B. diesen Code:

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

Der vorhergehende Code kann "Den Inhalt von FILE1.DAT auf FILE2.DAT kopieren" oder "FILE2.DAT ignorieren und `b` als zweiten Ziehpunkt für FILE1.DAT erstellen" bedeuten. Jeder Klasse muss wie folgt eine entsprechende Kopiersemantik beigefügt werden.

- Mithilfe des Zuweisungs Operator **Operators =** zusammen mit einem Verweis auf den Klassentyp als Rückgabetyp und dem Parameter, der durch den **Konstanten** Verweis übergeben wird – z. b. `ClassName& operator=(const ClassName& x);`.

- Durch Verwendung des Kopierkonstruktors.

Wenn Sie keinen Kopierkonstruktor deklarieren, generiert der Compiler einen memberweisen Kopierkonstruktor für Sie.  Wenn Sie keinen Kopierkonstruktoroperator deklarieren, generiert der Compiler einen memberweisen Kopierkonstruktoroperator für Sie. Das Deklarieren eines Kopierkonstruktors unterdrückt nicht den vom Compiler generierten Kopierzuweisungsoperator (und umgekehrt). Wenn Sie einen implementieren, sollten Sie auch den anderen implementieren, damit die Codebedeutung eindeutig ist.

Der Kopierkonstruktor nimmt ein Argument vom Typ <em>Class-Name</em> <strong>&</strong>auf, wobei *Class-Name* der Name der Klasse ist, für die der Konstruktor definiert ist. Beispiel:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> Legen Sie den Typ des- **Arguments für** den Typ des Kopierkonstruktors, den <em>Klassennamen</em> , nach Möglichkeit<strong>&</strong> . Dadurch wird verhindert, dass der Kopierkonstruktor fälschlicherweise das Objekt ändert, aus dem er kopiert. Außerdem wird das Kopieren aus **Konstanten** Objekten ermöglicht.

## <a name="compiler-generated-copy-constructors"></a>Vom Compiler generierte Kopierkonstruktoren

Vom Compiler generierte Kopierkonstruktoren, wie benutzerdefinierte Kopierkonstruktoren, verfügen über ein einzelnes Argument vom Typ "Verweis auf *Class-Name*". Eine Ausnahme besteht darin, dass für alle Basisklassen und Element Klassen Kopierkonstruktoren deklariert sind, die als ein einzelnes Argument vom Typ " **Konst** <em>Class-Name</em> <strong>&</strong>" gelten. In einem solchen Fall ist das vom Compiler generierte Argument des Kopierkonstruktors ebenfalls **konstant**.

Wenn der Argumenttyp für den Kopierkonstruktor nicht **konstant**ist, generiert die Initialisierung durch Kopieren eines **Konstanten** Objekts einen Fehler. Umgekehrt ist dies nicht der Fall: Wenn das Argument **konstant**ist, können Sie initialisieren, indem Sie ein Objekt kopieren, das nicht **konstant**ist.

Vom Compiler generierte Zuweisungs Operatoren folgen dem gleichen Muster in Bezug auf **Konstanten.** Sie verwenden ein einzelnes Argument vom Typ " <em>Class-Name</em> <strong>&</strong> ", es sei denn, die Zuweisungs Operatoren in allen Basis-und Element Klassen akzeptieren Argumente des Typs " **Konstanten** <em>Klassenname</em> "<strong>&</strong>. In diesem Fall nimmt der generierte Zuweisungs Operator der Klasse ein **Konstanten** Argument an.

> [!NOTE]
> Wenn virtuelle Basisklassen von Kopierkonstruktoren – vom Compiler generiert oder benutzerdefiniert – initialisiert werden, werden sie nur einmal initialisiert: bei der Erstellung.

Die Auswirkungen ähneln denen beim Kopierkonstruktor. Wenn der Argumenttyp nicht **konstant**ist, generiert die Zuweisung eines **Konstanten** Objekts einen Fehler. Umgekehrt ist dies nicht der Fall: Wenn **einem Wert,** der nicht **konstant**ist, ein konstanter Wert zugewiesen wird, ist die Zuweisung erfolgreich.

Weitere Informationen zu überladenen Zuweisungs Operatoren finden Sie unter [Zuweisung](../cpp/assignment.md).
