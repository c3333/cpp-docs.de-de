---
title: Speicherklassen (C++)
description: In C++ geben die Schlüsselwörter "Static", "extern" und "thread_local" die Lebensdauer, Verknüpfung und Speicherortposition einer Variablen oder Funktion an.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365346"
---
# <a name="storage-classes"></a>Speicherklassen

Eine *Speicherklasse* im Kontext von C++-Variablendeklarationen ist ein Typbezeichner, der die Lebensdauer, Verknüpfung und Speicherposition von Objekten steuert. Ein angegebenes Objekt kann nur eine Speicherklasse haben. Variablen, die innerhalb eines Blocks definiert sind, verfügen über automatischen Speicher, sofern nicht anders mit den **externen**, **statischen**oder thread_local-Bezeichnern angegeben. **thread_local** Automatische Objekte und Variablen haben keine Bindung; sie sind für Code außerhalb des Blocks nicht sichtbar. Der Speicher wird ihnen automatisch zugewiesen, wenn die Ausführung in den Block eintritt, und beim Beenden des Blocks abzugewiesen.

**Hinweise**

1. Das [veränderbare](../cpp/mutable-data-members-cpp.md) Schlüsselwort kann als Speicherklassenbezeichner betrachtet werden. Es ist jedoch nur in der Memberliste einer Klassendefinition verfügbar.

1. **Visual Studio 2010 und höher:** Das **auto** Auto-Schlüsselwort ist kein C++-Speicherklassenbezeichner mehr, und das **Registerschlüsselwort** ist veraltet. **Visual Studio 2017 Version 15.7 und höher:** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Das **Register-Schlüsselwort** wird aus der C++-Sprache entfernt.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>Statische

Das **static** static-Schlüsselwort kann verwendet werden, um Variablen und Funktionen im globalen Bereich, im Namespacebereich und im Klassenbereich zu deklarieren. Statische Variablen können auch im lokalen Gültigkeitsbereich deklariert werden.

Statische Dauer bedeutet, dass das Objekt oder die Variable zugewiesen wird, wenn das Programm gestartet wird. Die Zuweisung wird wieder aufgehoben, wenn das Programm beendet wird. Externe Verknüpfung bedeutet, dass der Name der Variablen von außerhalb der Datei sichtbar ist, in der die Variable deklariert wird. Umgekehrt bedeutet interne Verknüpfung, dass der Name nicht außerhalb der Datei sichtbar ist, in der die Variable deklariert wird. Standardmäßig verfügt ein Objekt oder eine Variable, das bzw. die im globalen Namespace definiert wird, über eine statische Dauer und externe Verknüpfung. Das **static** static-Schlüsselwort kann in den folgenden Situationen verwendet werden.

1. Wenn Sie eine Variable oder Funktion im Dateibereich (globaler **static** und/oder Namespacebereich) deklarieren, gibt das static-Schlüsselwort an, dass die Variable oder Funktion über eine interne Verknüpfung verfügt. Wenn Sie eine Variable deklarieren, hat die Variable eine statische Dauer und wird vom Compiler mit dem Wert 0 initialisiert, solange Sie keinen anderen Wert angeben.

1. Wenn Sie eine Variable in **static** einer Funktion deklarieren, gibt das static-Schlüsselwort an, dass die Variable ihren Status zwischen Aufrufen dieser Funktion beibehält.

1. Wenn Sie einen Datenmember in einer **static** Klassendeklaration deklarieren, gibt das static-Schlüsselwort an, dass eine Kopie des Members von allen Instanzen der Klasse gemeinsam genutzt wird. Ein statischer Datenmember muss im Dateibereich definiert sein. Ein integraler Datenmember, den Sie als **const static** deklarieren, kann einen Initialisierer haben.

1. Wenn Sie eine Memberfunktion in einer **static** Klassendeklaration deklarieren, gibt das static-Schlüsselwort an, dass die Funktion von allen Instanzen der Klasse gemeinsam genutzt wird. Eine statische Memberfunktion kann nicht auf ein Instanzmember zugreifen, da die Funktion keinen impliziten **Zeiger** hat. Um auf einen Instanzmember zuzugreifen, deklarieren Sie die Funktion mit einem Parameter, der ein Instanzzeiger oder -verweis ist.

1. Sie können die Member einer Union nicht als statisch deklarieren. Eine global deklarierte anonyme Union muss jedoch explizit als **statisch**deklariert werden.

Dieses Beispiel zeigt, wie eine in einer Funktion **deklarierte** Variable ihren Status zwischen Aufrufen dieser Funktion beibehält.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

Dieses Beispiel zeigt die Verwendung von **static** in einer Klasse.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

Dieses Beispiel zeigt eine lokale Variable, die in einer Memberfunktion **als statisch** deklariert wurde. Die statische Variable ist im gesamten Programm verfügbar. Alle Instanzen des Typs verwenden dieselbe Kopie der statischen Variable.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

Ab C++11 ist eine statische lokale Variableninitialisierung auf jeden Fall threadsicher. Diese Funktion wird manchmal als *magische Statik*bezeichnet. Allerdings müssen alle nachfolgende Zuweisungen in einer Multithreadanwendung synchronisiert werden. Die threadsichere statische Initialisierungsfunktion kann mithilfe des [/Zc:threadSafeInit-Flags](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) deaktiviert werden, um eine Abhängigkeit von der CRT zu vermeiden.

## <a name="extern"></a><a name="extern"></a>extern

Objekte und Variablen, die als **extern** deklariert wurden, deklarieren ein Objekt, das in einer anderen Übersetzungseinheit oder in einem einschließenden Bereich definiert ist, als externe Verknüpfung. Weitere Informationen finden Sie unter [Extern-](extern-cpp.md) und [Übersetzungseinheiten und Verknüpfung](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++11)

Auf eine Variable, die mit dem thread_local-Bezeichner deklariert wurde, kann nur auf den Thread zugegriffen werden, auf dem sie erstellt wird. **thread_local** Die Variable wird erstellt, wenn der Thread erstellt, und zerstört, wenn der Thread zerstört wird. Jeder Thread verfügt über eine eigene Kopie der Variable. Unter Windows ist **thread_local** funktional dem Microsoft-spezifischen [__declspec(Thread)-Attribut](../cpp/thread.md) entspricht.

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Dinge, die **thread_local** Sie über den thread_local-Bezeichner beachten sollten:

- Dynamisch initialisierte threadlokale Variablen in DLLs werden möglicherweise nicht für alle aufrufenden Threads korrekt initialisiert. Weitere Informationen finden Sie unter [Thread](thread.md).

- Der thread_local-Bezeichner kann mit **statischen** oder **externen**. **thread_local**

- Sie können **thread_local** nur auf Datendeklarationen und Definitionen anwenden; **thread_local** kann nicht für Funktionsdeklarationen oder Definitionen verwendet werden.

- Sie können **thread_local** nur für Datenelemente mit statischer Speicherdauer angeben. Dazu gehören globale Datenobjekte (sowohl **statische** als auch **externe),** lokale statische Objekte und statische Datenmember von Klassen. Jede lokale Variable, **die thread_local** deklariert wurde, ist implizit statisch, wenn keine andere Speicherklasse bereitgestellt wird. Mit anderen Worten, im Blockbereich `thread_local static`entspricht **thread_local** der .

- Sie müssen **thread_local** sowohl für die Deklaration als auch für die Definition eines lokalen Threadobjekts angeben, unabhängig davon, ob die Deklaration und Definition in derselben Datei oder in separaten Dateien erfolgt.

Unter Windows ist **thread_local** funktional [__declspec(Thread)](../cpp/thread.md) gleichwertig, mit der Ausnahme, dass **__declspec(Thread)** auf eine Typdefinition angewendet werden kann und im C-Code gültig ist. Verwenden Sie nach Möglichkeit **thread_local,** da sie Teil des C++-Standards ist und daher tragbarer ist.

## <a name="register"></a><a name="register"></a>Registrieren

**Visual Studio 2017 Version 15.3 und höher** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Das **Register-Schlüsselwort** ist keine unterstützte Speicherklasse mehr. Das Schlüsselwort ist im Standard weiterhin für die zukünftige Verwendung reserviert.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Beispiel: Automatische vs. statische Initialisierung

Ein lokales automatisches Objekt oder eine lokale automatische Variable wird jedes Mal initialisiert, wenn die Ablaufsteuerung ihre Definition erreicht. Ein lokales automatisches Objekt oder eine lokale automatische Variable wird erstmalig initialisiert, wenn die Ablaufsteuerung ihre Definition erreicht.

Betrachten Sie das folgende Beispiel, in dem eine Klasse definiert wird, die die Initialisierung und Beschädigung von Objekten protokolliert und dann drei Objekte, `I1`, `I2` und `I3`, definiert:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

In diesem Beispiel wird `I1`veranschaulicht, wie und wann die Objekte , `I2`und `I3` initialisiert werden und wenn sie zerstört werden.

Es gibt mehrere Punkte über das Programm zu beachten:

- Erstens werden `I1` und `I2` automatisch zerstört, wenn die Ablaufsteuerung den Block beendet, in dem sie definiert sind.

- Zweitens ist es in C++ nicht notwendig, Objekte oder Variablen am Anfang eines Blocks zu deklarieren. Außerdem werden diese Objekte nur initialisiert, wenn die Ablaufsteuerung deren Definitionen erreicht. `I2` (und `I3` sind Beispiele für solche Definitionen.) Die Ausgabe zeigt genau an, wann sie initialisiert werden.

- Des Weiteren behalten statische lokale Variablen wie `I3` ihre Werte für die Dauer des Programms bei, werden jedoch zerstört, sobald das Programm beendet wird.

## <a name="see-also"></a>Siehe auch

[Deklarationen und Definitionen](../cpp/declarations-and-definitions-cpp.md)
