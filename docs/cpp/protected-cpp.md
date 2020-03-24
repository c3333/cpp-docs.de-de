---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 29f57eac7201ac0647275c70c539f9b2f28eb81b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179249"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntax

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Bemerkungen

Das **Protected** -Schlüsselwort gibt den Zugriff auf Klassenmember in der *Mitgliederliste* bis zum nächsten Zugriffsspezifizierer (**Public** oder **private**) oder das Ende der Klassendefinition an. Klassenmember, die als **geschützt** deklariert sind, können nur von folgendem verwendet werden:

- Memberfunktionen der Klasse, die ursprünglich diese Member deklariert hat.

- Friends der Klasse, die ursprünglich diese Member deklariert hat.

- Klassen, die mit öffentlichem oder geschütztem Zugriff von der Klasse abgeleitet werden, die ursprünglich diese Member deklariert hat.

- Direkt privat abgeleitete Klassen, die auch über privaten Zugriff auf geschützte Member verfügen.

Wenn das **Protected** -Schlüsselwort dem Namen einer Basisklasse vorangestellt ist, gibt es an, dass die öffentlichen und geschützten Member der Basisklasse geschützte Member der abgeleiteten Klassen sind.

Geschützte Member sind nicht so privat wie **private** Member, die nur für Member der Klasse zugänglich sind, in der Sie deklariert sind, aber Sie sind nicht so öffentlich wie **öffentliche** Member, auf die in jeder Funktion zugegriffen werden kann.

Geschützte Member, die ebenfalls als **statisch** deklariert werden, sind für alle Friend-oder Member-Funktionen einer abgeleiteten Klasse zugänglich. Geschützte Member, die nicht als **statisch** deklariert werden, sind für Freunde und Element Funktionen in einer abgeleiteten Klasse nur über einen Zeiger auf, einen Verweis auf oder ein Objekt der abgeleiteten Klasse zugänglich.

Weitere Informationen finden Sie unter [Friend](../cpp/friend-cpp.md), [Public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md)und die Element Zugriffs Tabelle Untersteuern des [Zugriffs auf Klassenmember](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können C++ die Schlüsselwörter der Zugriffsspezifizierer (**Public**, **private**und **Protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinflussen. Weitere Informationen finden Sie unter [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Mit [/ln](../build/reference/ln-create-msil-module.md) kompilierte Dateien sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

## <a name="end-clr-specific"></a>"/clr"-spezifisch – Ende

## <a name="example"></a>Beispiel

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Weitere Informationen

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
