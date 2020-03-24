---
title: Satype (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166275"
---
# <a name="satype"></a>satype

Gibt den Datentyp der `SAFEARRAY` Struktur an.

## <a name="syntax"></a>Syntax

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parameter

*data_type*<br/>
Der Datentyp für die `SAFEARRAY` Datenstruktur, die als Parameter an eine Schnittstellen Methode übergeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellenparameter, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

## <a name="remarks"></a>Bemerkungen

Das **Satype** C++ -Attribut gibt den Datentyp des `SAFEARRAY`an.

> [!NOTE]
> Eine Dereferenzierungsebene wird vom `SAFEARRAY` Zeiger in der generierten IDL-Datei aus der Deklaration in der CPP-Datei gelöscht.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[id](id.md)
