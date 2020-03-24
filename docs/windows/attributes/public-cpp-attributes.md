---
title: Public (C++ Attribute) (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: 6912117ad05d6b608c45425ebec27cd49c0e5dc4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214713"
---
# <a name="public-c-attributes"></a>public (C++-Attribute)

Stellt sicher, dass eine typedef in die Typbibliothek wechselt, auch wenn in der IDL-Datei nicht auf Sie verwiesen wird.

## <a name="syntax"></a>Syntax

```cpp
[public]
```

## <a name="remarks"></a>Bemerkungen

Das **Public** C++ -Attribut verfügt über die gleiche Funktionalität wie das [öffentliche](/windows/win32/Midl/public) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das **Public** -Attribut verwendet wird:

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**typedef**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
