---
title: Standardnamespace
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: 5696730bcef08ad11be4a2b689e95eb3c13e11eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845704"
---
# <a name="default-namespace"></a>Standardnamespace

Der `default` Namespace erstellt die integrierten Typen, die von C++ unterstützt werden/CX.

## <a name="syntax"></a>Syntax

```
namespace default;
```

### <a name="members"></a>Member

Alle integrierte Typen erben die folgenden Member.

| Name | Beschreibung |
|--|--|
| [default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md) | Bestimmt, ob das angegebene Objekt gleich dem aktuellen Objekt ist. |
| [default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md) | Gibt den Hashcode für diese Instanz zurück. |
| [default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md) | Gibt eine Zeichenfolge zurück, die den aktuellen Typ darstellt. |
| [default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md) | Gibt eine Zeichenfolge zurück, die den aktuellen Typ darstellt. |

### <a name="built-in-types"></a>Integrierte Typen

|Name|Beschreibung|
|----------|-----------------|
|`char16`|Ein nicht numerischer 16-Bit-Wert, der einen Unicode-Codepunkt (UTF-16) darstellt.|
|`float32`|Eine 32-Bit-IEEE 754-Gleitkommazahl.|
|`float64`|Eine 64-Bit-IEEE 754-Gleitkommazahl.|
|`int16`|Eine 16-Bit-Ganzzahl mit Vorzeichen.|
|`int32`|Eine 32-Bit-Ganzzahl mit Vorzeichen.|
|`int64`|Eine 64-Bit-Ganzzahl mit Vorzeichen.|
|`int8`|Eine numerischer 8-Bit-Wert mit Vorzeichen.|
|`uint16`|Eine 16-Bit-Ganzzahl ohne Vorzeichen.|
|`uint32`|Eine 32-Bit-Ganzzahl ohne Vorzeichen.|
|`uint64`|Eine 64-Bit-Ganzzahl ohne Vorzeichen.|
|`uint8`|Eine numerischer 8-Bit-Wert ohne Vorzeichen.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** vccorlib.h

## <a name="see-also"></a>Weitere Informationen

[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)
