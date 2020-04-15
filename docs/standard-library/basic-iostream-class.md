---
title: basic_iostream-Klasse
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: e2a892525afbbad6d5b42d0b836fee096a70c297
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376819"
---
# <a name="basic_iostream-class"></a>basic_iostream-Klasse

Eine Streamklasse für Ein- und Ausgabe.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das Einfügungen über seine Basisklasse [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem` `Tr` , `Tr`> und Extraktionen über seine Basisklasse [basic_istream](../standard-library/basic-istream-class.md)< `Elem`,> steuert. Die beiden Objekte verwenden eine gemeinsame `Tr` virtuelle Basisklasse [basic_ios](../standard-library/basic-ios-class.md)< `Elem`,>. Außerdem verwalten sie einen gemeinsamen Streampuffer mit Elementen des Typs `Elem`, deren Zeichenmerkmale durch die `Tr`-Klasse bestimmt sind. Der Konstruktor initialisiert seine Basisklassen über `basic_istream`( **strbuf**) und `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_iostream](#basic_iostream)|Erstellen eines `basic_iostream`-Objekts|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[swap](#swap)|Tauscht den Inhalt des bereitgestellten `basic_iostream`-Objekts mit dem Inhalt dieses Objekts aus.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist diesem Objekt den Wert eines angegebenen `basic_iostream`-Objekts zu . Dies ist eine Verschiebezuweisung über einen `rvalue`, die keine Kopie hinterlässt.|

## <a name="requirements"></a>Anforderungen

**Header:** \<istream>

**Namespace:** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a>basic_iostream::basic_iostream

Erstellen eines `basic_iostream`-Objekts

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parameter

*strbuf*\
Ein vorhandenes `basic_streambuf`-Objekt.

*Richting*\
Ein vorhandenes `basic_iostream`-Objekt, das verwendet wird, um ein neues `basic_iostream`-Objekt zu erstellen.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisobjekte über `basic_istream(strbuf)` und `basic_ostream(strbuf)`.

Der zweite Konstruktor initialisiert die `move(right)`Basisobjekte, indem er aufruft.

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a>basic_iostream::operator=

Weisen Sie diesem Objekt den Wert eines angegebenen `basic_iostream`-Objekts zu . Dies ist eine Verschiebezuweisung über einen rvalue, die keine Kopie hinterlässt.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `rvalue`-Verweis auf ein `basic_iostream`-Objekt, aus dem zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator `swap(right)`ruft auf.

## <a name="basic_iostreamswap"></a><a name="swap"></a>basic_iostream::swap

Tauscht den Inhalt des bereitgestellten `basic_iostream`-Objekts mit dem Inhalt dieses Objekts aus.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das auszutauschende `basic_iostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `swap(right)`ruft auf.

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
