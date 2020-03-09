---
title: Speicherklassen (C++)
description: In C++geben die Schlüsselwörter "static", "extern" und "thread_local" die Lebensdauer, die Verknüpfung und den Speicherort einer Variablen oder Funktion an.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- extern_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: ab00a5c64a32dc1dab5fef4bc15b722587bc2d6b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856897"
---
# <a name="storage-classes"></a>Speicherklassen

Eine *Speicher Klasse* im Kontext von C++ Variablen Deklarationen ist ein Typspezifizierer, der die Lebensdauer, die Verknüpfung und den Speicherort von Objekten steuert. Ein angegebenes Objekt kann nur eine Speicherklasse haben. Variablen, die innerhalb eines Blocks definiert sind, verfügen über automatischen Speicher, sofern Sie nicht anderweitig mithilfe der **extern**, **static**oder **thread_local** Spezifizierer angegeben werden Automatische Objekte und Variablen haben keine Bindung; sie sind für Code außerhalb des Blocks nicht sichtbar. Arbeitsspeicher wird automatisch zugewiesen, wenn die Ausführung in den Block Eintritt und die Zuordnung aufgehoben wird, wenn der Block beendet wird.

**Hinweise**

1. Das [änderbare](../cpp/mutable-data-members-cpp.md) -Schlüsselwort kann als Speicherklassenspezifizierer angesehen werden. Es ist jedoch nur in der Memberliste einer Klassendefinition verfügbar.

1. **Visual Studio 2010 und höher:** Das Schlüsselwort " **Auto** " ist C++ kein Speicherklassenspezifizierer mehr, und das **Register** -Schlüsselwort ist veraltet. **Visual Studio 2017 Version 15,7 und höher:** (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): das **Register** -Schlüsselwort wird aus C++ der Sprache entfernt.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a>Kum

Das **static** -Schlüsselwort kann zum Deklarieren von Variablen und Funktionen im globalen Gültigkeitsbereich, im Namespace Bereich und im Klassen Bereich verwendet werden. Statische Variablen können auch im lokalen Gültigkeitsbereich deklariert werden.

Statische Dauer bedeutet, dass das Objekt oder die Variable zugewiesen wird, wenn das Programm gestartet wird. Die Zuweisung wird wieder aufgehoben, wenn das Programm beendet wird. Externe Verknüpfung bedeutet, dass der Name der Variablen von außerhalb der Datei sichtbar ist, in der die Variable deklariert wird. Umgekehrt bedeutet interne Verknüpfung, dass der Name nicht außerhalb der Datei sichtbar ist, in der die Variable deklariert wird. Standardmäßig verfügt ein Objekt oder eine Variable, das bzw. die im globalen Namespace definiert wird, über eine statische Dauer und externe Verknüpfung. Das **static** -Schlüsselwort kann in den folgenden Situationen verwendet werden.

1. Wenn Sie eine Variable oder Funktion im Datei Gültigkeitsbereich deklarieren (globaler und/oder Namespace-Gültigkeitsbereich), gibt das **static** -Schlüsselwort an, dass die Variable oder Funktion eine interne Verknüpfung aufweist. Wenn Sie eine Variable deklarieren, hat die Variable eine statische Dauer und wird vom Compiler mit dem Wert 0 initialisiert, solange Sie keinen anderen Wert angeben.

1. Wenn Sie eine Variable in einer Funktion deklarieren, gibt das **static** -Schlüsselwort an, dass die Variable ihren Zustand zwischen Aufrufen dieser Funktion beibehält.

1. Wenn Sie einen Datenmember in einer Klassen Deklaration deklarieren, gibt das **static** -Schlüsselwort an, dass eine Kopie des Members von allen Instanzen der Klasse gemeinsam genutzt wird. Ein statischer Datenmember muss im Dateibereich definiert sein. Ein integraler Datenmember, den Sie als " **Konstanten static** " deklarieren, kann einen Initialisierer aufweisen.

1. Wenn Sie eine Member-Funktion in einer Klassen Deklaration deklarieren, gibt das **static** -Schlüsselwort an, dass die Funktion von allen Instanzen der Klasse gemeinsam genutzt wird. Eine statische Member-Funktion kann nicht auf einen Instanzmember zugreifen, da die Funktion keinen impliziten **this** -Zeiger hat. Um auf einen Instanzmember zuzugreifen, deklarieren Sie die Funktion mit einem Parameter, der ein Instanzzeiger oder -verweis ist.

1. Sie können die Member einer Union nicht als statisch deklarieren. Eine global deklarierte anonyme Union muss jedoch explizit als **statisch**deklariert werden.

Dieses Beispiel zeigt, wie eine Variable, die in einer Funktion als **statisch** deklariert wurde, ihren Status zwischen Aufrufen dieser Funktion beibehält.

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

Dieses Beispiel zeigt die Verwendung von **static** in einer-Klasse.

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

Dieses Beispiel zeigt eine lokale Variable, die in einer Member-Funktion als **statisch** deklariert ist. Die statische Variable ist im gesamten Programm verfügbar. Alle Instanzen des Typs verwenden dieselbe Kopie der statischen Variable.

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

Ab C++11 ist eine statische lokale Variableninitialisierung auf jeden Fall threadsicher. Diese Funktion wird manchmal als *Magic Statics*bezeichnet. Allerdings müssen alle nachfolgende Zuweisungen in einer Multithreadanwendung synchronisiert werden. Die Thread sichere statische Initialisierungsfunktion kann mit dem [/Zc: threadsafeinit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) Flag deaktiviert werden, um zu vermeiden, dass eine Abhängigkeit von der CRT besteht.

## <a name="extern"></a>Extern

Objekte und Variablen, die als **extern** deklariert sind, deklarieren ein Objekt, das in einer anderen Übersetzungseinheit oder in einem einschließenden Bereich als externe Verknüpfung definiert ist. Weitere Informationen finden Sie unter [externe](extern-cpp.md) und [Übersetzungseinheiten und Verknüpfungen](program-and-linkage-cpp.md).

## <a name="thread_local"></a>thread_local (c++ 11)

Auf eine Variable, die mit dem **thread_local** -Spezifizierer deklariert wird, kann nur auf dem Thread zugegriffen werden, für den Sie erstellt wurde Die Variable wird erstellt, wenn der Thread erstellt, und zerstört, wenn der Thread zerstört wird. Jeder Thread verfügt über eine eigene Kopie der Variable. Unter Windows ist **thread_local** funktionell gleichwertig mit dem Microsoft-spezifischen [__declspec (Thread)](../cpp/thread.md) -Attribut.

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

Hinweise zum **thread_local** Spezifizierer:

- Dynamisch initialisierte Thread lokale Variablen in DLLs können nicht für alle aufrufenden Threads ordnungsgemäß initialisiert werden. Weitere Informationen finden Sie unter [Thread](thread.md).

- Der **thread_local** Spezifizierer kann mit **static** oder **extern**kombiniert werden.

- Sie können **thread_local** nur auf Datendeklarationen und-Definitionen anwenden. **thread_local** kann nicht für Funktions Deklarationen oder-Definitionen verwendet werden.

- Sie können **thread_local** nur für Datenelemente mit statischer Speicherdauer angeben. Hierzu zählen globale Datenobjekte (sowohl **statische** als auch **extern**), lokale statische Objekte sowie statische Datenmember von Klassen. Alle lokalen Variablen, die **thread_local** deklariert sind, sind implizit statisch, wenn keine andere Speicher Klasse bereitgestellt wird. Anders ausgedrückt: bei Block Bereich **thread_local** gleich `thread_local static`.

- Sie müssen **thread_local** sowohl für die Deklaration als auch für die Definition eines lokalen Thread Objekts angeben, unabhängig davon, ob die Deklaration und Definition in der gleichen Datei oder in separaten Dateien auftreten.

Unter Windows ist **thread_local** funktionell äquivalent zu [__declspec (Thread)](../cpp/thread.md) , mit dem Unterschied, dass **__declspec (Thread)** auf eine Typdefinition angewendet werden kann und in C-Code gültig ist. Verwenden Sie nach Möglichkeit **thread_local** , da es Teil des C++ Standards ist und daher besser portabel ist.

##  <a name="register"></a>sich

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): das **Register** -Schlüsselwort ist keine unterstützte Speicher Klasse mehr. Das Schlüsselwort ist nach wie vor im Standard für die zukünftige Verwendung reserviert.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Beispiel: automatische und statische Initialisierung

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

In diesem Beispiel wird veranschaulicht, wie und wann die Objekte `I1`, `I2`und `I3` initialisiert und zerstört werden.

Zum Programm gibt es mehrere Punkte zu beachten:

- Erstens werden `I1` und `I2` automatisch zerstört, wenn die Ablaufsteuerung den Block beendet, in dem sie definiert sind.

- Zweitens ist es in C++ nicht notwendig, Objekte oder Variablen am Anfang eines Blocks zu deklarieren. Außerdem werden diese Objekte nur initialisiert, wenn die Ablaufsteuerung deren Definitionen erreicht. (`I2` und `I3` sind Beispiele für solche Definitionen.) Die Ausgabe wird genau angezeigt, wenn Sie initialisiert werden.

- Des Weiteren behalten statische lokale Variablen wie `I3` ihre Werte für die Dauer des Programms bei, werden jedoch zerstört, sobald das Programm beendet wird.

## <a name="see-also"></a>Weitere Informationen

[Deklarationen und Definitionen](../cpp/declarations-and-definitions-cpp.md)