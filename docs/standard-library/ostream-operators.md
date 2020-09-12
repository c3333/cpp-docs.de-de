---
title: '&lt;ostream&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: a4dfee6c70f068e5a61294e6b2863a8a12a9c378
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039767"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt;-Operatoren

[KOM&lt;&lt;](#op_lt_lt)

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> KOM&lt;&lt;

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
Ein `basic_ostream`-Objekt.

*SRT*\
Eine Zeichenfolge.

*_Tr*\
Zeichenmerkmale.

*ster*\
Der Typ

### <a name="return-value"></a>Rückgabewert

Der Datenstrom.

### <a name="remarks"></a>Bemerkungen

Die `basic_ostream`-Klasse definiert außerdem mehrere Einfügeoperatoren. Weitere Informationen finden Sie unter [basic_ostream:: Operator &lt; &lt; ](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

bestimmt die Länge N = `traits_type::` [length](../standard-library/char-traits-struct.md#length)( `str` ) der Sequenz, beginnend bei *Str*, und fügt die Sequenz ein. Wenn N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), fügt die Funktion auch eine Wiederholung von `_Ostr.width`-N-Füllzeichen ein. Die Wiederholung geht der Sequenz voraus, wenn ( `_Ostr` . [flags](../standard-library/ios-base-class.md#flags)  &  Flags `adjustfield` ! = [left](../standard-library/ios-functions.md#left). Andernfalls folgt die Wiederholung der Sequenz. Die Funktion gibt *_Ostr*zurück.

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

fügt das Element `_Ch` ein. Wenn 1 < `_Ostr.width`, dann fügt die Funktion auch eine Wiederholung von `_Ostr.width`-1 Füllzeichen hinzu. Die Wiederholung geht der Sequenz voraus, wenn ( `_Ostr.flags & adjustfield != left`. Andernfalls folgt die Wiederholung der Sequenz. *_Ostr*wird zurückgegeben.

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

mit dem Unterschied, dass jedes Element *_Ch* der Sequenz, beginnend bei *Str* , in ein Objekt vom Typ konvertiert wird, `Elem` indem `_Ostr.` [Put](../standard-library/basic-ostream-class.md#put)(- `_Ostr.` [Erweiterung](../standard-library/basic-ios-class.md#widen)( `_Ch` )) aufgerufen wird.

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

mit der Ausnahme, dass *_Ch* in ein Objekt vom Typ konvertiert wird, `Elem` indem aufgerufen wird `_Ostr.put( _Ostr.widen( _Ch ))` .

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

(Die *_Ch* muss vor dem Einfügen nicht erweitert werden.)

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

`_Ostr << (const char *)str` wird zurückgegeben.

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

`_Ostr << (char)_Ch` wird zurückgegeben.

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

`_Ostr << (const char *)str` wird zurückgegeben.

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

`_Ostr << (char)_Ch` wird zurückgegeben.

Die Vorlagenfunktion:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

gibt `_Ostr << val` zurück (und konvertiert einen [RValue-Verweis](../cpp/rvalue-reference-declarator-amp-amp.md) zu `_Ostr` zu einem lvalue im Prozess).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator<<` finden Sie unter [flush](../standard-library/ostream-functions.md#flush).

## <a name="see-also"></a>Weitere Informationen

[\<ostream>](../standard-library/ostream.md)
