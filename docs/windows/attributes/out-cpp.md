---
title: Out (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 6ab8fdf691e2220087f5c5d64bb70c5deb27675c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214667"
---
# <a name="out-c"></a>out (C++)

Gibt die Zeigerparameter an, die von der aufgerufenen Prozedur an die aufrufende Prozedur zurückgegeben werden (vom Server an den Client).

## <a name="syntax"></a>Syntax

```cpp
[out]
```

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut **out** hat die gleiche Funktion wie das MIDL-Attribut [out](/windows/win32/Midl/out-idl) .

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von [bindable](bindable.md) finden Sie im Beispiel für **out**.

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
[Parameterattribute](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)
