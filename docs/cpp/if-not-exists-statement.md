---
title: __if_not_exists-Anweisung
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 3e0eb550830a1689d440e3b471759a98f1eef0ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187256"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists-Anweisung

Die- **`__if_not_exists`** Anweisung testet, ob der angegebene Bezeichner vorhanden ist. Wenn der Bezeichner nicht vorhanden ist, wird der angegebene Anweisungsblock ausgeführt.

## <a name="syntax"></a>Syntax

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*identifier*|Der Bezeichner, dessen Vorhandensein Sie überprüfen möchten.|
|*Äußerungen*|Eine oder mehrere auszuführende Anweisungen, wenn der *Bezeichner* nicht vorhanden ist.|

## <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Um die zuverlässigsten Ergebnisse zu erzielen, verwenden Sie die- **`__if_not_exists`** Anweisung unter den folgenden Einschränkungen.

- Wenden Sie die- **`__if_not_exists`** Anweisung nur auf einfache Typen, nicht auf Vorlagen an.

- Wenden Sie die- **`__if_not_exists`** Anweisung auf Bezeichner innerhalb oder außerhalb einer Klasse an. Wenden Sie die- **`__if_not_exists`** Anweisung nicht auf lokale Variablen an.

- Verwenden Sie die- **`__if_not_exists`** Anweisung nur im Text einer Funktion. Außerhalb des Texts einer Funktion kann die- **`__if_not_exists`** Anweisung nur vollständig definierte Typen testen.

- Wenn Sie auf überladene Funktionen testen, können Sie nicht auf eine bestimmte Form der Überladung testen.

Das Komplement der- **`__if_not_exists`** Anweisung ist die [__if_exists](../cpp/if-exists-statement.md) -Anweisung.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **`__if_not_exists`** finden Sie unter [__if_exists-Anweisung](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Weitere Informationen

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[__if_exists-Anweisung](../cpp/if-exists-statement.md)
