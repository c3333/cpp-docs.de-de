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
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320322"
---
# <a name="pointers-to-members"></a>Zeiger auf Member

Deklarationen von Zeigern auf Member sind Sonderfälle von Zeigerdeklarationen.  Sie werden mit der folgenden Reihenfolge deklariert:

> *storage-class-specifiers*<sub>opt</sub> *cv-qualifiers*<sub>opt</sub> *type-specifier* *ms-modifier*<sub>opt</sub> *qualified-name* **`::*`** *cv-qualifiers*<sub>opt</sub> *identifier* *pm-initializer*<sub>opt</sub>**`;`**

1. Der Deklarationsbezeichner:

   - Ein optionaler Speicherklassenbezeichner.

   - Optionale **const-** und volatile-Bezeichner. **volatile**

   - Der Typspezifizierer: der Name eines Typs Es ist der Typ des Members, auf den verwiesen werden soll, nicht die Klasse.

1. Der Deklarator:

   - Ein optionaler Microsoft-spezifischer Modifizierer. Weitere Informationen finden Sie unter [Microsoft-Spezifische Modifikatoren](../cpp/microsoft-specific-modifiers.md).

   - Der qualifizierte Name der Klasse, die die Member enthält, auf die gezeigt werden muss.

   - Der __`::`__ Operator.

   - Der __`*`__ Operator.

   - Optionale **const-** und volatile-Bezeichner. **volatile**

   - Der Bezeichner, der den Zeiger auf ein Member benennt.

1. Ein optionaler Zeiger-zu-Member-Initialisierungsmittel:

   - Der **`=`** Operator.

   - Der **`&`** Operator.

   - Der qualifizierte Name der Klasse.

   - Der __`::`__ Operator.

   - Der Name eines nicht statischen Members der Klasse des entsprechenden Typs.

Wie immer sind mehrere Deklaratoren (sowie alle zugeordneten Initialisierer) in einer einzelnen Deklaration zulässig. Ein Zeiger auf Member darf nicht auf einen statischen Member der **`void`** Klasse, einen Member des Verweistyps oder verweisen.

Ein Zeiger auf einen Member einer Klasse unterscheidet sich von einem normalen Zeiger: Er enthält sowohl Typinformationen für den Typ des Members als auch für die Klasse, zu der der Member gehört. Ein normaler Zeiger identifiziert nur ein einzelnes Objekt im Arbeitsspeicher (hat nur die Adresse dieses Objekts). Ein Zeiger auf einen Member einer Klasse identifiziert den Member in jeder Instanz der Klasse. Im folgenden Beispiel werden die Klasse `Window` und mehrere Zeiger auf Memberdaten deklariert.

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

Im vorherigen Beispiel `pwCaption` ist ein Zeiger auf `Window` jeden Member einer `char*`Klasse vom Typ . Der Typ von `pwCaption` lautet `char * Window::*`. Im nächsten Codefragment werden Zeiger auf die Memberfunktionen `SetCaption` und `GetCaption` deklariert.

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

Der Unterschied **`.*`** zwischen **`->*`** den und Operatoren (zeiger-zu-Element-Operatoren) besteht darin, dass **`.*`** der **`->*`** Operator Elemente auswählt, die einen Objekt- oder Objektverweis erhalten, während der Operator Elemente über einen Zeiger auswählt. Weitere Informationen zu diesen Operatoren finden Sie unter [Ausdrücke mit Zeiger-zu-Member-Operatoren](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Das Ergebnis der Zeiger-zu-Member-Operatoren ist der Typ des Members. In diesem Fall ist dies `char *`.

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

Die Adresse eines statischen Elements ist kein Zeiger auf ein Element. Es ist ein regelmäßiger Zeiger auf die eine Instanz des statischen Elements. Für alle Objekte einer bestimmten Klasse ist nur eine Instanz eines statischen Members vorhanden. Das bedeutet, dass Sie die**&** normalen Adress-von<strong>\*</strong>- und Dereferenzierungsoperatoren ( ) verwenden können.

## <a name="pointers-to-members-and-virtual-functions"></a>Zeiger auf Member und virtuelle Funktionen

Das Aufrufen einer virtuellen Funktion über eine Zeiger-zu-Member-Funktion funktioniert so, als ob die Funktion direkt aufgerufen worden wäre. Die richtige Funktion wird in der v-Tabelle nachgeschlagen und aufgerufen.

Entscheidend für das Funktionieren von virtuellen Funktionen ist immer, dass sie durch einen Zeiger auf eine Basisklasse aufgerufen werden. (Weitere Informationen zu virtuellen Funktionen finden Sie unter [Virtuelle Funktionen](../cpp/virtual-functions.md).)

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
