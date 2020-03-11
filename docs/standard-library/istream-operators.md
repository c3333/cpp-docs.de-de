---
title: '&lt;iStream&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874815"
---
# <a name="ltistreamgt-operators"></a>&lt;iStream&gt;-Operatoren

## <a name="op_gt_gt"></a>operator&gt;&gt;

Extrahiert von Zeichenfolgen und Zeichen aus dem Stream.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>Parameter

*Ch* -\
Ein Zeichen.

*ISTR* -\
Ein Datenstrom.

*Str*\
Eine Zeichenfolge.

*Val* -\
Ein Typ.

### <a name="return-value"></a>Rückgabewert

Ein Stream

### <a name="remarks"></a>Bemerkungen

Die `basic_istream`-Klasse definiert außerdem mehrere Extraktionsoperatoren. Weitere Informationen finden Sie unter [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Die Funktions Vorlage:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrahiert bis zu `N - 1` Elemente und speichert Sie im Array, beginnend bei *Str*. Wenn `Istr.`[Breite](../standard-library/ios-base-class.md#width) größer als 0 (null) ist, wird *N* `Istr.width`. Andernfalls ist es die Größe des größten Arrays von `Elem`, das deklariert werden kann. Die Funktion speichert den Wert immer `Elem()`, nachdem alle extrahierten Elemente gespeichert wurden. Die Extraktion hält früh am Ende der Datei an, bei einem Zeichen mit einem Wert `Elem(0)` (das nicht extrahiert wird) oder bei einem Element (das nicht extrahiert wird), das von [WS](../standard-library/istream-functions.md#ws)verworfen würde. Wenn die Funktion keine Elemente extrahiert, ruft Sie `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`auf. In jedem Fall wird `Istr.width(0)` aufgerufen und *ISTR*zurückgegeben.

**Sicherheitshinweis** Die aus dem Eingabestream extrahierte aus null endenden Zeichenfolge darf die Größe des Ziel Puffers *Str*nicht überschreiten. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Die Funktions Vorlage:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrahiert, wenn möglich, ein Element und speichert es in *ch*. Andernfalls wird `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`aufgerufen. In jedem Fall wird *ISTR*zurückgegeben.

Die Funktions Vorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

`Istr >> ( char * ) str` wird zurückgegeben.

Die Funktions Vorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

`Istr >> ( char& ) Ch` wird zurückgegeben.

Die Funktions Vorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

`Istr >> ( char * ) str` wird zurückgegeben.

Die Funktions Vorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

`Istr >> ( char& ) Ch` wird zurückgegeben.

Die Funktions Vorlage:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

gibt `Istr >> val` zurück (und konvertiert einen rvalue-Verweis in `Istr` in einen lvalue im Prozess).

### <a name="example"></a>Beispiel

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[\<istream>](../standard-library/istream.md)
