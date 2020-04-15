---
title: '&lt;ostream&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: d8b6f4e0f0b5bca41f8d895415fff4003231ad1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373606"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt;-Operatoren

||
|-|
|[Operator&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operator&lt;&lt;

Schreibt verschiedene Typen in den Stream.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Ein Zeichen.

*_Elem*\
Der Elementtyp.

*_Ostr*\
Ein `basic_ostream` -Objekt.

*Str*\
Eine Zeichenfolge.

*_Tr*\
Zeichenmerkmale.

*Val*\
Der Typ

### <a name="return-value"></a>Rückgabewert

Der Datenstrom.

### <a name="remarks"></a>Bemerkungen

Die `basic_ostream`-Klasse definiert außerdem mehrere Einfügeoperatoren. Weitere Informationen finden Sie [unter&lt;basic_ostream::operator](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

bestimmt die Länge `traits_type::`N`str`= [Länge](../standard-library/char-traits-struct.md#length)( ) der Sequenz, die bei *str*beginnt, und fügt die Sequenz ein. Wenn N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), fügt die Funktion auch eine Wiederholung von `_Ostr.width`-N-Füllzeichen ein. Die Wiederholung geht der Sequenz`_Ostr`voran, wenn ( . [flags](../standard-library/ios-base-class.md#flags) &  Flags`adjustfield` != [links](../standard-library/ios-functions.md#left). Andernfalls folgt die Wiederholung der Sequenz. Die Funktion gibt *_Ostr*zurück.

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

fügt das Element `_Ch` ein. Wenn 1 < `_Ostr.width`, dann fügt die Funktion auch eine Wiederholung von `_Ostr.width`-1 Füllzeichen hinzu. Die Wiederholung geht der Sequenz voraus, wenn ( `_Ostr.flags & adjustfield != left`. Andernfalls folgt die Wiederholung der Sequenz. Es gibt *_Ostr*zurück.

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

verhält sich so wie

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

außer, dass jedes Element *_Ch* der Sequenz, die an `_Ostr.` *str* beginnt, durch Aufrufen von [put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[widen](../standard-library/basic-ios-class.md#widen)(`_Ch`)) in ein Objekt des Typs `Elem` konvertiert wird.

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

verhält sich so wie

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

außer, dass *_Ch* durch Aufrufen `Elem` `_Ostr.put`( `_Ostr.widen`( `_Ch`)) in ein Objekt des Typs konvertiert wird.

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

verhält sich so wie

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Sie muss die Elemente nicht erweitern, bevor sie eingefügt werden.)

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

verhält sich so wie

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Es muss *_Ch* nicht erweitern, bevor es eingefügt wird.)

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

gibt `_Ostr` << `const char *` `str`zurück( ) .

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

gibt `_Ostr` << `char` `_Ch`zurück( ) .

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

gibt `_Ostr` << `const char *` `str`zurück( ) .

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

gibt `_Ostr` << `char` `_Ch`zurück( ) .

Die Vorlagenfunktion:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

gibt `_Ostr` `<<` `val` zurück (und konvertiert einen [RValue-Verweis](../cpp/rvalue-reference-declarator-amp-amp.md) zu `_Ostr` zu einem lvalue im Prozess).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator<<` finden Sie unter [flush](../standard-library/ostream-functions.md#flush).

## <a name="see-also"></a>Siehe auch

[\<ostream>](../standard-library/ostream.md)
