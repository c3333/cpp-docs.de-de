---
title: LCID (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: bb9e44d34c675e4f5d955c5f422a6dd35259ec8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214798"
---
# <a name="lcid"></a>lcid

Ermöglicht es Ihnen, einen Gebiets Schema Bezeichner an eine Funktion zu übergeben.

## <a name="syntax"></a>Syntax

```cpp
[lcid]
```

## <a name="remarks"></a>Bemerkungen

Das **LCID** C++ -Attribut implementiert die Funktionalität des [LCID](/windows/win32/Midl/lcid) -Attributs "Mittel l". Wenn Sie das Gebiets Schema für einen Bibliotheks Block implementieren möchten, verwenden Sie den **LCID =** `lcid`-Parameter für das [Module](module-cpp.md) -Attribut.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
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

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)
