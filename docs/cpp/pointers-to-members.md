---
title: Zeiger auf Member
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: 3238cd801763c72e96ccd93eee9640e672a5fbf5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150781"
---
# <a name="pointers-to-members"></a>Zeiger auf Member

Deklarationen von Zeigern auf Member sind Sonderfälle von Zeigerdeklarationen.  Sie werden mit der folgenden Sequenz deklariert:

> *Storage-Class-Specifiers*<sub>opt</sub> *CV-Qualifizierer*<sub>opt</sub> *type-specifier* *MS-Modifier*<sub>opt</sub> *Qualified-Name* **`::*`** *CV-Qualifizierer*<sub>opt</sub> *Identifier* *pm-initializer*<sub>opt</sub> **`;`**

1. Der Deklarationsbezeichner:

   - Ein optionaler Speicherklassenbezeichner.

   - Optionale **Konstanten** und **flüchtige** Bearbeiter.

   - Der Typspezifizierer: der Name eines Typs Dabei handelt es sich um den Typ des Members, auf den verwiesen werden soll, nicht um die Klasse.

1. Der Deklarator:

   - Ein optionaler Microsoft-spezifischer Modifizierer. Weitere Informationen finden Sie unter [Microsoft-spezifische modifiziererer](../cpp/microsoft-specific-modifiers.md).

   - Der qualifizierte Name der Klasse, die die Member enthält, auf die gezeigt werden muss.

   - Der __`::`__ -Operator.

   - Der __`*`__ -Operator.

   - Optionale **Konstanten** und **flüchtige** Bearbeiter.

   - Der Bezeichner, der den Zeiger auf ein Member benennt.

1. Ein optionaler Pointer-to-Member-Initialisierer:

   - Der **`=`** -Operator.

   - Der **`&`** -Operator.

   - Der qualifizierte Name der Klasse.

   - Der __`::`__ -Operator.

   - Der Name eines nicht statischen Members der Klasse des entsprechenden Typs.

Wie immer sind mehrere Deklaratoren (sowie alle zugeordneten Initialisierer) in einer einzelnen Deklaration zulässig. Ein Zeiger auf einen Member darf nicht auf einen statischen Member der Klasse, einen Member des Verweis Typs oder **`void`** zeigen.

Ein Zeiger auf einen Member einer Klasse unterscheidet sich von einem normalen Zeiger: Er verfügt sowohl über Typinformationen für den Typ des Members als auch über die Klasse, zu der der Member gehört. Ein normaler Zeiger identifiziert nur ein einzelnes Objekt im Arbeitsspeicher (hat nur die Adresse dieses Objekts). Ein Zeiger auf einen Member einer Klasse identifiziert den Member in jeder Instanz der Klasse. Im folgenden Beispiel werden die Klasse `Window` und mehrere Zeiger auf Memberdaten deklariert.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

Im vorherigen Beispiel ist `pwCaption` ein Zeiger auf einen beliebigen Member der-Klasse `Window` der vom Typ `char*`ist. Der Typ von `pwCaption` lautet `char * Window::* `. Im nächsten Codefragment werden Zeiger auf die Memberfunktionen `SetCaption` und `GetCaption` deklariert.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Die Zeiger `pfnwGC` und `pfnwSC` zeigen auf `GetCaption` bzw. `SetCaption` der Klasse `Window`. Mithilfe des Zeigers auf den Member `pwCaption` kopiert der Code Informationen direkt in die Fensterbeschriftung:

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

Der Unterschied zwischen den Operatoren **`.*`** und **`->*`** (die Zeiger-zu-Member-Operatoren) besteht darin, dass der **`.*`** -Operator bei einem Objekt-oder Objekt Verweis Member auswählt, während der **`->*`** -Operator Member durch einen Zeiger auswählt. Weitere Informationen zu diesen Operatoren finden [Sie unter Ausdrücke mit Zeiger-zu-Member-Operatoren](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Das Ergebnis der Zeiger-auf-Member-Operatoren ist der Typ des Members. In diesem Fall ist dies `char *`.

Im folgenden Codefragment werden die Memberfunktionen `GetCaption` und `SetCaption` mithilfe der Zeiger auf Member aufgerufen:

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>Einschränkungen für Zeiger auf Member

Die Adresse eines statischen Members ist kein Zeiger auf einen Member. Es ist ein regulärer Zeiger auf eine Instanz des statischen Members. Nur eine Instanz eines statischen Members ist für alle Objekte einer bestimmten Klasse vorhanden. Dies bedeutet, dass Sie die normalen address-of-Operatoren ( **&** ) und Dereferenzierungsoperatoren (<strong>\*</strong>) verwenden können.

## <a name="pointers-to-members-and-virtual-functions"></a>Zeiger auf Member und virtuelle Funktionen

Das Aufrufen einer virtuellen Funktion über eine Pointer-to-Member-Funktion funktioniert so, als wäre die Funktion direkt aufgerufen worden. Die korrekte Funktion wird in der v-Tabelle gesucht und aufgerufen.

Entscheidend für das Funktionieren von virtuellen Funktionen ist immer, dass sie durch einen Zeiger auf eine Basisklasse aufgerufen werden. (Weitere Informationen zu virtuellen Funktionen finden Sie unter [virtuelle Funktionen](../cpp/virtual-functions.md).)

Der folgende Code zeigt, wie eine virtuelle Funktion durch einen Zeiger auf eine Memberfunktion aufgerufen werden kann:

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```
