---
title: optional (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.optional
helpviewer_keywords:
- optional attribute
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
ms.openlocfilehash: 6a4fdcd0b8466d2dbf2c034fc4a3ee9ae2df8d0a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214659"
---
# <a name="optional-c"></a>optional (C++)

Gibt einen optionalen Parameter für eine Member-Funktion an.

## <a name="syntax"></a>Syntax

```cpp
[optional]
```

## <a name="remarks"></a>Bemerkungen

Das **optionale** C++ -Attribut verfügt über die gleiche Funktionalität wie das [optionale](/windows/win32/Midl/optional) Mittel l-Attribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie **optional** verwendet werden kann:

```cpp
// cpp_attr_ref_optional.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellenparameter|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)
