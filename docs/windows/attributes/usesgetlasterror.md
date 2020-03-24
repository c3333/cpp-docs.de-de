---
title: "\"US-GetLastErrorC++ \" (com-Attribut)"
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: f58929db01a1710e811a973c0559ad29b242b4eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166132"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Teilt dem Aufrufer mit, dass der Aufrufer beim Aufrufen dieser Funktion `GetLastError` aufrufen kann, um den Fehlercode abzurufen.

## <a name="syntax"></a>Syntax

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Bemerkungen

Das **usesgetlasterror** C++ Attribut " [" des](/windows/win32/Midl/usesgetlasterror) Attributs "" ist die gleiche Funktionalität wie das Attribut "" von "" in "".

## <a name="example"></a>Beispiel

Im [idl_module](idl-module.md) Beispiel wird ein Beispiel für **die Verwendung von**"" verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Module** -Attribut|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)
