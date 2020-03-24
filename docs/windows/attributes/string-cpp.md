---
title: String (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 96d5e609130b34a4a5f35109ce691c2de470e537
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166159"
---
# <a name="string-c"></a>string (C++)

Gibt an, dass das eindimensionale **char**-, **wchar_t**-, `byte` (oder äquivalente) Array oder der Zeiger auf ein solches Array als Zeichenfolge behandelt werden muss.

## <a name="syntax"></a>Syntax

```cpp
[string]
```

## <a name="remarks"></a>Bemerkungen

Das **String** C++ -Attribut verfügt über die gleiche Funktionalität wie das-Attribut der- [Zeichenfolge](/windows/win32/Midl/string) .

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie Sie die **Zeichenfolge** für eine Schnittstelle und für eine typedef verwenden:

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Array oder Zeiger auf ein Array, Schnittstellenparameter, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Arrayattribute](array-attributes.md)<br/>
[export](export.md)
