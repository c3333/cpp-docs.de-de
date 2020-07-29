---
title: appobject (com-Attribut C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: ae3547a32e6d5984a9ef95e495ba119c3a2ed385
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222159"
---
# <a name="appobject"></a>appobject

Identifiziert die Co-Klasse als Anwendungs Objekt, das einer Full. exe-Anwendung zugeordnet ist, und gibt an, dass die Funktionen und Eigenschaften der Co-Klasse in dieser [Typbibliothek](../../mfc/automation-clients-using-type-libraries.md)global verfügbar sind.

## <a name="syntax"></a>Syntax

```cpp
[appobject]
```

## <a name="remarks"></a>Bemerkungen

Das **appobject** C++-Attribut verfügt über die gleiche Funktionalität wie das " [appobject](/windows/win32/Midl/appobject) "-Attribut "mittlerer l".

## <a name="example"></a>Beispiel

Der folgende Code zeigt eine einfache Klassendefinition mit vorangestelltem Attribut Block, der **appobject**umfasst:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|`coclass`|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
