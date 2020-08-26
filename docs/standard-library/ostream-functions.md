---
title: '&lt;ostream&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 4db966797202b16911aa67b6fda7c81785d98166
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842636"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt;-Funktionen

Dabei handelt es sich um die in ostream definierten globalen Vorlagen Funktionen &lt; &gt; . Informationen zu Element Funktionen finden Sie in der Dokumentation zur [Basic_ostream-Klasse](basic-ostream-class.md) .

[Endl](#endl)\
[Runden](#ends)\
[Flächen](#flush)\
[swap](#swap)

## <a name="endl"></a>endl

Beendet eine Zeile und leert den Puffer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parameter

*Elem*\
Der Elementtyp.

*Ostr*\
Ein Objekt vom Typ **basic_ostream**.

*Stadtrat*\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ **basic_ostream**.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft *Ostr*auf. [Put](../standard-library/basic-ostream-class.md#put)(*Ostr*).[ Erweitern](../standard-library/basic-ios-class.md#widen)Sie (' \n ')), und rufen Sie dann *Ostr*auf. [flush](../standard-library/basic-ostream-class.md#flush)leeren. Sie gibt *Ostr*zurück.

### <a name="example"></a>Beispiel

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>Ends

Beendet eine Zeichenfolge.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parameter

*Elem*\
Der Elementtyp.

*Ostr*\
Ein Objekt vom Typ `basic_ostream`.

*Stadtrat*\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ `basic_ostream`.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft *Ostr*auf. [Put](../standard-library/basic-ostream-class.md#put)(*Elem*(' \ 0 ')). Sie gibt *Ostr*zurück.

### <a name="example"></a>Beispiel

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

Leert den Puffer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parameter

*Elem*\
Der Elementtyp.

*Ostr*\
Ein Objekt vom Typ `basic_ostream`.

*Stadtrat*\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ `basic_ostream`.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft *Ostr*auf. [flush](../standard-library/basic-ostream-class.md#flush)leeren. Sie gibt *Ostr*zurück.

### <a name="example"></a>Beispiel

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Tauscht die Werte zweier `basic_ostream`-Objekte aus.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parameter

*Elem*\
Der Elementtyp.

*Stadtrat*\
Zeichenmerkmale.

*linken*\
Ein lvalue-Verweis auf ein `basic_ostream`-Objekt.

*Richting*\
Ein lvalue-Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion `swap` führt `left.swap(right)` aus.

## <a name="see-also"></a>Weitere Informationen

[\<ostream>](../standard-library/ostream.md)
