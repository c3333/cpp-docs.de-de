---
title: Case (C++-com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: 23330b7b220873725dc566df947f3f3596160029
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232806"
---
# <a name="case-c"></a>case (C++)

Wird mit dem [Switch_type](switch-type.md) -Attribut in einer verwendet **`union`** .

## <a name="syntax"></a>Syntax

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parameter

*value*<br/>
Ein möglicher Eingabe Wert, für den Sie die Verarbeitung bereitstellen möchten. Der **Werttyp** kann einer der folgenden Typen sein:

- **`int`**

- **`char`**

- `boolean`

- **`enum`**

oder einen Bezeichner eines solchen Typs.

## <a name="remarks"></a>Bemerkungen

Das **Case** C++-Attribut verfügt über die gleiche Funktionalität wie das Mittel l-Attribut für den **Fall** . Dieses Attribut wird nur mit dem [Switch_type](switch-type.md) -Attribut verwendet.

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung des **Case** -Attributs:

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|Member von **`class`** oder**`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
