---
title: Helpstringcontext (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: e6d4a6b4ab2381fc9ebe0f237978c92fe0f656c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224447"
---
# <a name="helpstringcontext"></a>helpstringcontext

Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.

## <a name="syntax"></a>Syntax

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parameter

*contextID*<br/>
Ein 32-Bit-Hilfe Kontext Bezeichner in der **Hilfe** Datei.

## <a name="remarks"></a>Bemerkungen

Das **helpstringcontext** C++-Attribut verfügt über die gleiche Funktionalität wie das [helpstringcontext](/windows/win32/Midl/helpstringcontext) -ODL-Attribut.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **Schnittstelle**, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Mond](module-cpp.md)
