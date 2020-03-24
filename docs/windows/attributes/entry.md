---
title: Entry (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167094"
---
# <a name="entry"></a>entry

Gibt eine exportierte Funktion oder Konstante in einem Modul an, indem der Einstiegspunkt in der DLL identifiziert wird.

## <a name="syntax"></a>Syntax

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parameter

*id*<br/>
Die ID des Einstiegs Punkts.

## <a name="remarks"></a>Bemerkungen

Das **Entry** C++ -Attribut verfügt über die gleiche Funktionalität wie das- [Eintrags](/windows/win32/Midl/entry) -Attribut.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Entry**finden Sie im Beispiel für [idl_module](idl-module.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|`idl_module`-Attribut|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)
