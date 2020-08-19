---
title: wbuffer_convert-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: ba8c98075741ae6cb8db0ecdfcb1e18cf4f4f89c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561114"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert-Klasse

Beschreibt einen Streampuffer, der die Übertragung von Elementen in einen bzw. aus einem Streampuffer steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parameter

*Codecvt*\
Das Facet [locale](../standard-library/locale-class.md), das das Konvertierungsobjekt darstellt.

*Elem*\
Der Breitzeichen-Elementtyp.

*Aufweisen*\
Die mit *Elem* verknüpften Merkmale.

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage beschreibt einen Streampuffer, der die Übertragung von Elementen des Typs steuert `_Elem` , dessen Zeichen Merkmale durch die Klasse beschrieben werden `Traits` , zu und von einem bytestreampuffer des Typs `std::streambuf` .

Konvertierung zwischen einer Sequenz von `Elem`-Werten und Multibytesequenzen erfolgt durch ein Objekt der Klasse `Codecvt<Elem, char, std::mbstate_t>`, das die Anforderungen des Facets `std::codecvt<Elem, char, std::mbstate_t>` für die Standardcodekonvertierung erfüllt.

Ein Objekt dieser Klassen Vorlagen Speicher:

- Ein Zeiger auf den entsprechenden zugrunde liegenden Bytestreampuffer

- Ein Zeiger auf das zugeordnete Konvertierungsobjekt (das freigegeben wird, wenn das [wbuffer_convert](../standard-library/wbuffer-convert-class.md)-Objekt
