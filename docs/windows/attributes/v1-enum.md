---
title: v1_enum (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 1a189f6f1c5ef9d4ae77df9f1eda3f3671ddaf52
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166106"
---
# <a name="v1_enum"></a>v1_enum

Leitet, dass der angegebene Enumerationstyp als 32-Bit-Entität und nicht als 16-Bit-Standardwert übertragen wird.

## <a name="syntax"></a>Syntax

```cpp
[v1_enum]
```

## <a name="remarks"></a>Bemerkungen

Das **v1_enum** C++ -Attribut verfügt über die gleiche Funktionalität wie das [v1_enum](/windows/win32/Midl/v1-enum) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung von **v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Enumerierter Typ|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
