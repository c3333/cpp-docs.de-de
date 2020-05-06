---
title: Grenzwerte für Gleitkommakonstanten
ms.date: 11/04/2016
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
ms.openlocfilehash: df39ee719a4474f6dfd55d31a2848169a1168390
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325584"
---
# <a name="limits-on-floating-point-constants"></a>Grenzwerte für Gleitkommakonstanten

**Microsoft-spezifisch**

In der folgenden Tabelle sind die Beschränkungen für die Werte von Gleitkommakonstanten aufgeführt. Die Headerdatei FLOAT.H enthält diese Informationen.

### <a name="limits-on-floating-point-constants"></a>Grenzwerte für Gleitkommakonstanten

|Konstante|Bedeutung|Wert|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|Anzahl von Ziffern, *q*, sodass eine Gleitkommazahl mit *q* Dezimalstellen ohne Genauigkeitsverlust auf eine Gleitkommadarstellung und zurück gerundet werden kann.|6<br />15<br />15|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|Kleinste positive Zahl *x*, sodass *x* + 1,0 ungleich 1,0 ist.|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|Anzahl von Ziffern in der Basis, die von **FLT_RADIX** in der Gleitkommamantisse angegeben wird. Die Basis ist 2, daher werden mit diesen Werten Bits angegeben.|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|Darstellbare Höchstgleitkommazahl.|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|Maximal zulässige Ganzzahl, sodass 10 potenziert mit dieser Zahl eine darstellbare Gleitkommazahl ist.|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|Maximal zulässige Ganzzahl, sodass **FLT_RADIX** potenziert mit dieser Zahl eine darstellbare Gleitkommazahl ist.|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|Minimaler positiver Wert.|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|Minimal zulässige negative Ganzzahl, sodass 10 potenziert mit dieser Zahl eine darstellbare Gleitkommazahl ist.|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|Minimal zulässige negative Ganzzahl, sodass **FLT_RADIX** potenziert mit dieser Zahl eine darstellbare Gleitkommazahl ist.|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|Basis der Exponentendarstellung.|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|Rundungsverhalten für Gleitkommaaddition.|1 (ungefähr)<br />1 (ungefähr)<br />1 (ungefähr)|

Beachten Sie, dass sich die Informationen in der obigen Tabelle in zukünftige Implementierungen möglicherweise unterscheiden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Gleitkommakonstanten](../c-language/c-floating-point-constants.md)
