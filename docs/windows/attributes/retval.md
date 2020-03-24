---
title: retval (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 5aded4588614eb4171e31a588f125ea8aa8de7ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166340"
---
# <a name="retval"></a>retval

Gibt den Parameter an, der den Rückgabewert des Members empfängt.

## <a name="syntax"></a>Syntax

```cpp
[retval]
```

## <a name="remarks"></a>Bemerkungen

Das **retval** C++ -Attribut verfügt über die gleiche Funktionalität wie das " [retval](/windows/win32/Midl/retval) "-Attribut "Mittel l".

**retval** muss für das letzte Argument in der Deklaration einer Funktion angezeigt werden.

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **retval**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellenparameter, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|**out**|
|**Ungültige Attribute**|**in**|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methodenattribut](method-attributes.md)
