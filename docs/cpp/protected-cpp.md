---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317271"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntax

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Bemerkungen

Das **geschützte** Schlüsselwort gibt den Zugriff auf Klassenmember in der *Memberliste* bis zum nächsten Zugriffsbezeichner **(öffentlich** oder **privat**) oder dem Ende der Klassendefinition an. Als **geschützt** deklarierte Klassenmember können nur wie folgt verwendet werden:

- Memberfunktionen der Klasse, die ursprünglich diese Member deklariert hat.

- Friends der Klasse, die ursprünglich diese Member deklariert hat.

- Klassen, die mit öffentlichem oder geschütztem Zugriff von der Klasse abgeleitet werden, die ursprünglich diese Member deklariert hat.

- Direkt privat abgeleitete Klassen, die auch über privaten Zugriff auf geschützte Member verfügen.

Wenn sie dem Namen einer Basisklasse vorangestellt wird, gibt das **geschützte** Schlüsselwort an, dass die öffentlichen und geschützten Member der Basisklasse geschützte Member ihrer abgeleiteten Klassen sind.

Geschützte Member sind nicht so privat wie **private** Member, die nur für Mitglieder der Klasse zugänglich sind, in der sie deklariert sind, aber sie sind nicht so öffentlich wie **öffentliche** Mitglieder, die in jeder Funktion zugänglich sind.

Geschützte Member, die ebenfalls als **statisch** deklariert werden, sind für jeden Freund oder jede Memberfunktion einer abgeleiteten Klasse zugänglich. Geschützte Member, die nicht als **statisch** deklariert sind, sind für Freunde und Memberfunktionen in einer abgeleiteten Klasse nur über einen Zeiger auf, den Verweis auf oder das Objekt der abgeleiteten Klasse zugänglich.

Weitere Informationen finden Sie unter [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md)und die Memberzugriffstabelle unter Steuern des Zugriffs [auf Klassenmitglieder](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können die C++-Zugriffsbezeichnerschlüsselwörter (**public**, **private**und **protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinträchtigen. Weitere Informationen finden Sie unter [Member Zugriffssteuerung](member-access-control-cpp.md).

> [!NOTE]
> Dateien, die mit [/LN](../build/reference/ln-create-msil-module.md) kompiliert wurden, sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

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

## <a name="see-also"></a>Siehe auch

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
