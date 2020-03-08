---
title: '&lt;istream&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874812"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;-Funktionen

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a> swap

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

*Linker*\
Ein Datenstrom.

*Rechte*\
Ein Datenstrom.

## <a name="ws"></a> ws

Überspringt Leerraum im Datenstrom.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parameter

*_Istr*\
Ein Datenstrom.

### <a name="return-value"></a>Rückgabewert

Der Datenstrom.

### <a name="remarks"></a>Bemerkungen

Der Manipulator extrahiert und verwirft alle Elemente `ch`, für die [Use_facet](../standard-library/basic-filebuf-class.md#open)< **CType**\< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **CType**\< **Elem**>:: **Space**, **ch**) ist true.

Die Funktion ruft [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) auf, wenn sie beim Extrahieren der Elemente auf das Ende der Datei stößt. *_Istr*wird zurückgegeben.

### <a name="example"></a>Beispiel

Unter [Operator>>](../standard-library/istream-operators.md#op_gt_gt) finden Sie ein Beispiel für die Verwendung von `ws`.

## <a name="see-also"></a>Weitere Informationen

[\<istream>](../standard-library/istream.md)
