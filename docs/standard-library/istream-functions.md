---
title: '&lt;istream&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 6d1fede2726d3d8f5dd678b95fd7a22a301ea95a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840972"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;-Funktionen

[Wechsel](#istream_swap)\
[Gefangener](#ws)

## <a name="swap"></a><a name="istream_swap"></a> Wechsel

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

*linken*\
Ein Stream

*Richting*\
Ein Stream

## <a name="ws"></a><a name="ws"></a> Gefangener

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

Der Manipulator extrahiert und verwirft alle Elemente `ch` , für die [Use_facet](../standard-library/basic-filebuf-class.md#open) <  **CType** \< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)) ist. **is**( **CType** \< **Elem**> :: **Space**, **ch**) ist true.

Die Funktion ruft [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) auf, wenn sie beim Extrahieren der Elemente auf das Ende der Datei stößt. *_Istr*wird zurückgegeben.

### <a name="example"></a>Beispiel

Unter [Operator>>](../standard-library/istream-operators.md#op_gt_gt) finden Sie ein Beispiel für die Verwendung von `ws`.

## <a name="see-also"></a>Weitere Informationen

[\<istream>](../standard-library/istream.md)
