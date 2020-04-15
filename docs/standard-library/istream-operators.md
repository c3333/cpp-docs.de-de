---
title: '&lt;iStream&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363039"
---
# <a name="ltistreamgt-operators"></a>&lt;iStream&gt;-Operatoren

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Operator&gt;&gt;

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

*Ch*\
Ein Zeichen.

*Istr*\
Ein Stream

*Str*\
Eine Zeichenfolge.

*Val*\
Ein Typ.

### <a name="return-value"></a>Rückgabewert

Ein Stream

### <a name="remarks"></a>Bemerkungen

Die `basic_istream`-Klasse definiert außerdem mehrere Extraktionsoperatoren. Weitere Informationen finden Sie unter [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

Die Funktionsvorlage:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrahiert Elemente `N - 1` und speichert sie im Array ab *str*. Wenn `Istr.` [die Breite](../standard-library/ios-base-class.md#width) größer als Null ist, ist `Istr.width` *N* ; Andernfalls ist es die Größe des `Elem` größten Arrays, das deklariert werden kann. Die Funktion speichert `Elem()` den Wert immer nach allen extrahierten Elementen, die sie speichert. Die Extraktion stoppt früh am Ende der `Elem(0)` Datei, auf einem Zeichen mit Wert (das nicht extrahiert wird) oder auf einem Element (das nicht extrahiert wird), das von [ws](../standard-library/istream-functions.md#ws)verworfen würde. Wenn die Funktion keine Elemente `Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`extrahiert, ruft sie auf. In jedem Fall `Istr.width(0)` ruft es *Istr*auf und gibt es zurück.

**Sicherheitshinweis** Die null-terminierte Zeichenfolge, die aus dem Eingabestream extrahiert wird, darf die Größe des Zielpuffers *str*nicht überschreiten. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Die Funktionsvorlage:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrahiert ein Element, wenn möglich, und speichert es in *Ch*. Andernfalls ruft `is.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`es auf . In jedem Fall gibt es *Istr*zurück.

Die Funktionsvorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

`Istr >> ( char * ) str` wird zurückgegeben.

Die Funktionsvorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

`Istr >> ( char& ) Ch` wird zurückgegeben.

Die Funktionsvorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

`Istr >> ( char * ) str` wird zurückgegeben.

Die Funktionsvorlage:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

`Istr >> ( char& ) Ch` wird zurückgegeben.

Die Funktionsvorlage:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

gibt `Istr >> val` zurück (und konvertiert einen `Istr` rvalue-Verweis in einen lvalue im Prozess).

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

## <a name="see-also"></a>Siehe auch

[\<istream>](../standard-library/istream.md)
