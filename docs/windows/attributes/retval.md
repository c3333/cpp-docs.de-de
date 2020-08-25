---
title: retval (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: f90893390bc67cb495e646f61e3d61a994e42e50
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845990"
---
# <a name="retval"></a>retval

Gibt den Parameter an, der den Rückgabewert des Members empfängt.

## <a name="syntax"></a>Syntax

```cpp
[retval]
```

## <a name="remarks"></a>Bemerkungen

Das **retval** -C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut " [retval](/windows/win32/Midl/retval) " in der Mitte.

**retval** muss für das letzte Argument in der Deklaration einer Funktion angezeigt werden.

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **retval**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**out**|
|**Ungültige Attribute**|**in**|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)
