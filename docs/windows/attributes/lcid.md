---
title: LCID (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 7533cd9b269a879c5c2f061dcdfc632b1b27c871
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834179"
---
# <a name="lcid"></a>lcid

Ermöglicht es Ihnen, einen Gebiets Schema Bezeichner an eine Funktion zu übergeben.

## <a name="syntax"></a>Syntax

```cpp
[lcid]
```

## <a name="remarks"></a>Bemerkungen

Das **LCID** C++-Attribut implementiert die Funktionalität des [LCID](/windows/win32/Midl/lcid) -Attributs "Mittel l". Wenn Sie das Gebiets Schema für einen Bibliotheks Block implementieren möchten, verwenden Sie den **LCID =** - `lcid` Parameter für das [Module](module-cpp.md) -Attribut.

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

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenparameter|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)
