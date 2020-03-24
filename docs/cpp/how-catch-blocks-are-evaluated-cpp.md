---
title: Auswerten von Catch-Blöcken (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 11804c48631659b84006abb824837efea3902416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188636"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Auswerten von Catch-Blöcken (C++)

C++ ermöglicht Ihnen das Auslösen von Ausnahmen eines beliebigen Typs, obwohl im Allgemeinen empfohlen wird, Typen auszulösen, die von der std::exception abgeleitet sind. Eine C++ -Ausnahme kann von einem **catch** -Handler abgefangen werden, der den gleichen Typ wie die ausgelöste Ausnahme angibt, oder durch einen Handler, der einen beliebigen Ausnahmetyp abfangen kann.

Wenn der Typ der ausgelösten Ausnahme eine Klasse ist, die auch eine Basisklasse (oder Klassen) besitzt, kann sie durch Handler abgefangen werden, die Basisklassen des Ausnahmetyps oder Verweise auf Basen des Ausnahmetyps akzeptieren. Beachten Sie, dass wenn eine Ausnahme durch einen Verweis abgefangen wird, sie an das tatsächlich ausgelöste Ausnahmeobjekt gebunden ist; andernfalls ist es eine Kopie (nahezu identisch mit einem Argument für eine Funktion).

Wenn eine Ausnahme ausgelöst wird, kann Sie von den folgenden Typen von **catch** -Handlern abgefangen werden:

- Ein Handler, der jeden Typ akzeptieren kann (mit der Auslassungszeichensyntax).

- Ein Handler, der den gleichen Typ wie das Ausnahme Objekt akzeptiert. Da es sich um eine Kopie handelt, werden **Konstanten** und **flüchtige** modifiziererer ignoriert.

- Ein Handler, der einen Verweis auf den gleichen Typ wie das Ausnahmeobjekt akzeptiert.

- Ein Handler, der einen Verweis auf eine **Konstante oder** **flüchtige** Form desselben Typs wie das Ausnahme Objekt akzeptiert.

- Ein Handler, der eine Basisklasse des gleichen Typs wie das Ausnahme Objekt akzeptiert. Da es sich um eine Kopie handelt, werden **Konstanten** und **flüchtige** modifiziererer ignoriert. Der **catch** -Handler für eine Basisklasse darf nicht dem **catch** -Handler für die abgeleitete Klasse vorangestellt sein.

- Ein Handler, der einen Verweis auf eine Basisklasse des gleichen Typs wie das Ausnahmeobjekt akzeptiert.

- Ein Handler, der einen Verweis auf eine **Konstante oder** **flüchtige** Form einer Basisklasse des gleichen Typs wie das Ausnahme Objekt akzeptiert.

- Ein Handler, der einen Zeiger akzeptiert, in den ein ausgelöstes Zeigerobjekt über Standardzeigerkonvertierungsregeln konvertiert werden kann.

Die Reihenfolge, in der die **catch** -Handler angezeigt werden, ist signifikant, da Handler für einen bestimmten **try** -Block in der Reihenfolge ihrer Darstellung überprüft werden. Beispielsweise ist es einem Fehler, den Handler einer Basisklasse vor dem Handler einer abgeleiteten Klasse zu platzieren. Nachdem ein entsprechender **catch** -Handler gefunden wurde, werden nachfolgende Handler nicht untersucht. Folglich muss ein Ellipsen **catch** -Handler der letzte Handler für den **try** -Block sein. Beispiel:

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

In diesem Beispiel ist der Auslassungs Zeichen- **catch** -Handler der einzige Handler, der untersucht wird.

## <a name="see-also"></a>Weitere Informationen

[Moderne C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)
