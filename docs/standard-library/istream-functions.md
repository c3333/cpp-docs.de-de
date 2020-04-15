---
title: '&lt;istream&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363079"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;-Funktionen

|||
|-|-|
|[swap](#istream_swap)|[Ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>Swap

Tauscht die Elemente zweier Streamobjekte.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Stream

*Richting*\
Ein Stream

## <a name="ws"></a><a name="ws"></a>Ws

Überspringt Leerraum im Datenstrom.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parameter

*_Istr*\
Ein Stream

### <a name="return-value"></a>Rückgabewert

Der Datenstrom.

### <a name="remarks"></a>Bemerkungen

Der Manipulator extrahiert und verwirft alle Elemente, `ch` für die [use_facet](../standard-library/basic-filebuf-class.md#open)< **Ctype** \< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**(**ctype**\< **Elem**>:: **space**, **ch**) ist TRUE.

Die Funktion ruft [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) auf, wenn sie beim Extrahieren der Elemente auf das Ende der Datei stößt. Es gibt *_Istr zurück.*

### <a name="example"></a>Beispiel

Unter [Operator>>](../standard-library/istream-operators.md#op_gt_gt) finden Sie ein Beispiel für die Verwendung von `ws`.

## <a name="see-also"></a>Siehe auch

[\<istream>](../standard-library/istream.md)
