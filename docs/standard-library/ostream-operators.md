---
title: '&lt;ostream&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874811"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt;-Operatoren

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>operator&lt;&lt;

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

*Val* -\
Der Typ

### <a name="return-value"></a>Rückgabewert

Der Datenstrom.

### <a name="remarks"></a>Bemerkungen

Die `basic_ostream`-Klasse definiert außerdem mehrere Einfügeoperatoren. Weitere Informationen finden Sie unter [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

bestimmt die Länge N = `traits_type::`[Länge](../standard-library/char-traits-struct.md#length)(`str`) der Sequenz, beginnend bei *Str*, und fügt die Sequenz ein. Wenn N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), fügt die Funktion auch eine Wiederholung von `_Ostr.width`-N-Füllzeichen ein. Die Wiederholung geht der Sequenz voraus, wenn (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left). Andernfalls folgt die Wiederholung der Sequenz. Die Funktion gibt *_Ostr*zurück.

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

verhält sich so

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

mit dem Unterschied, dass jedes Element *_Ch* der Sequenz, beginnend bei *Str* , in ein Objekt des Typs `Elem` konvertiert wird, indem `_Ostr.`[Put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[ausgedehnt](../standard-library/basic-ios-class.md#widen)(`_Ch`)) aufgerufen wird.

Die Vorlagenfunktion

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

verhält sich so

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

mit der Ausnahme, dass *_Ch* in ein Objekt vom Typ `Elem` durch Aufrufen von `_Ostr.put`(`_Ostr.widen`(`_Ch`)) konvertiert wird.

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

verhält sich so

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

verhält sich so

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

gibt `_Ostr` < < (`const char *``str`) zurück.

Die Vorlagenfunktion

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

gibt `_Ostr` < < (`char``_Ch`) zurück.

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

gibt `_Ostr` < < (`const char *``str`) zurück.

Die Vorlagenfunktion:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

gibt `_Ostr` < < (`char``_Ch`) zurück.

Die Vorlagenfunktion:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

gibt `_Ostr` `<<` `val` zurück (und konvertiert einen [rvalue-Verweis](../cpp/rvalue-reference-declarator-amp-amp.md) , um in einen lvalue im Prozess `_Ostr`).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von [ finden Sie unter ](../standard-library/ostream-functions.md#flush)flush`operator<<`.

## <a name="see-also"></a>Weitere Informationen

[\<ostream>](../standard-library/ostream.md)
