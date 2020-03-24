---
title: Range (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 380f7c9e15a3682b486217c842f00c944251e631
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214616"
---
# <a name="range-c"></a>range (C++)

Gibt einen Bereich zulässiger Werte für Argumente oder Felder an, deren Werte zur Laufzeit festgelegt werden.

## <a name="syntax"></a>Syntax

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Parameter

*low*<br/>
Der niedrige Bereichs Wert.

*high*<br/>
Der Wert für den hohen Bereich.

## <a name="remarks"></a>Bemerkungen

Das **Range** C++ -Attribut verfügt über die gleiche Funktionalität [wie das-](/windows/win32/Midl/range) bereichsmittell-Attribut.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellen Methode, Schnittstellenparameter|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Datenmemberattribute](data-member-attributes.md)
