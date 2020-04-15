---
title: Grenzwerte für Gleitkommakonstanten
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: ccd395eef319e57cecffad8a5278b6df1397f4cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373369"
---
# <a name="floating-limits"></a>Grenzwerte für Gleitkommakonstanten

**Microsoft Specific**

In der folgenden Tabelle sind die Limits für die Werte von Gleitkommakonstanten aufgeführt. Diese Grenzwerte sind auch in \<der Standardheaderdatei float.h> definiert.

## <a name="limits-on-floating-point-constants"></a>Grenzwerte für Gleitkommakonstanten

|Konstante|Bedeutung|Wert|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Anzahl von Ziffern q, sodass eine Gleitkommazahl mit q Dezimalstellen ohne Genauigkeitsverlust auf eine Gleitkommadarstellung und zurück gerundet werden kann.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Kleinste positive Zahl x, sodass x + 1,0 ungleich 1,0 ist.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Anzahl der Ziffern im Radix, die durch `FLT_RADIX` im Gleitkomma-Signifikand angegeben werden. Der Radix ist 2; daher geben diese Werte Bits an.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Maximale darstellbare Gleitkommazahl.|3.402823466e+38F<br/>1,7976931348623158e+308<br/>1,7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Maximale ganzzahlige Zahl, so dass 10, die auf diese Zahl angehoben wird, eine darstellbare Gleitkommazahl ist.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Die maximale ganzzahlige Zahl, die `FLT_RADIX` auf diese Zahl angehoben wird, ist eine darstellbare Gleitkommazahl.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Minimaler positiver Wert.|1.175494351e-38F<br/>2,2250738585072014e-308<br/>2,2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Minimale negative ganze Zahl, so dass 10, die auf diese Zahl angehoben wird, eine darstellbare Gleitkommazahl ist.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Minimale negative ganzzahlige `FLT_RADIX` Zahl, die auf diese Zahl angehoben wird, ist eine darstellbare Gleitkommazahl.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Basis der Exponentendarstellung.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Rundungsmodus für Gleitkommaaddition.|1 (ungefähr)<br/>1 (ungefähr)<br/>1 (ungefähr)|

> [!NOTE]
> Die Informationen in der Tabelle können sich in zukünftigen Versionen des Produkts unterscheiden.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Ganzzahlgrenzen](../cpp/integer-limits.md)
