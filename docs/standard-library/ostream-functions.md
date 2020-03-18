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
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425298"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt;-Funktionen

Dies sind die globalen Vorlagen Funktionen, die in &lt;ostream-&gt;definiert sind. Informationen zu Element Funktionen finden Sie in der Dokumentation zur [Basic_ostream-Klasse](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Beendet eine Zeile und leert den Puffer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parameter

*Elem* -\
Der Elementtyp.

*Ostr* -\
Ein Objekt vom Typ **basic_ostream**.

*TR* -\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ **basic_ostream**.

### <a name="remarks"></a>Hinweise

Der Manipulator ruft *Ostr*.[put](../standard-library/basic-ostream-class.md#put)(*Ostr*.[widen](../standard-library/basic-ios-class.md#widen)('\n')) und dann *Ostr*.[flush](../standard-library/basic-ostream-class.md#flush) auf. Sie gibt *Ostr*zurück.

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

*Elem* -\
Der Elementtyp.

*Ostr* -\
Ein Objekt vom Typ `basic_ostream`.

*TR* -\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ `basic_ostream`.

### <a name="remarks"></a>Hinweise

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

*Elem* -\
Der Elementtyp.

*Ostr* -\
Ein Objekt vom Typ `basic_ostream`.

*TR* -\
Zeichenmerkmale.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ `basic_ostream`.

### <a name="remarks"></a>Hinweise

Der Manipulator ruft *Ostr*.[flush](../standard-library/basic-ostream-class.md#flush) auf. Sie gibt *Ostr*zurück.

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

*Elem* -\
Der Elementtyp.

*TR* -\
Zeichenmerkmale.

*Linker*\
Ein lvalue-Verweis auf ein `basic_ostream`-Objekt.

*Rechte*\
Ein lvalue-Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion `swap` führt `left.swap(right)` aus.

## <a name="see-also"></a>Siehe auch

[\<ostream>](../standard-library/ostream.md)
