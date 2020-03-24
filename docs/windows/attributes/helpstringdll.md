---
title: Helpstringdll (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 4ec0d959b2fc10fc34bfc7050a1970359dae5bbc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168121"
---
# <a name="helpstringdll"></a>helpstringdll

Gibt den Namen der dll an, die verwendet werden soll, um die Suche nach Dokument Zeichenfolgen (Lokalisierung) auszuführen.

## <a name="syntax"></a>Syntax

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Parameter

*string*<br/>
Die DLL-Datei, die für die Suche nach Dokument Zeichenfolgen verwendet wird

## <a name="remarks"></a>Bemerkungen

Das **Helpstringdll** C++ -Attribut verfügt über die gleiche Funktionalität wie das-Attribut von [Helpstringdll](/windows/win32/Midl/helpstringdll) .

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Schnittstelle**, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methodenattribut](method-attributes.md)
