---
title: __if_not_exists-Anweisung
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374140"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists-Anweisung

Die **__if_not_exists-Anweisung** testet, ob der angegebene Bezeichner vorhanden ist. Wenn der Bezeichner nicht vorhanden ist, wird der angegebene Anweisungsblock ausgeführt.

## <a name="syntax"></a>Syntax

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Bezeichner*|Der Bezeichner, dessen Vorhandensein Sie überprüfen möchten.|
|*Aussagen*|Eine oder mehrere Anweisungen, die ausgeführt werden sollen, wenn der *Bezeichner* nicht vorhanden ist.|

## <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Um die zuverlässigsten Ergebnisse zu erzielen, verwenden Sie die **__if_not_exists-Anweisung** unter den folgenden Einschränkungen.

- Wenden Sie die **__if_not_exists-Anweisung** nur auf einfache Typen an, nicht auf Vorlagen.

- Wenden Sie die **__if_not_exists-Anweisung** auf Bezeichner innerhalb oder außerhalb einer Klasse an. Wenden Sie die **__if_not_exists-Anweisung** nicht auf lokale Variablen an.

- Verwenden Sie die **__if_not_exists-Anweisung** nur im Textkörper einer Funktion. Außerhalb des Funktionskörpers kann die **__if_not_exists-Anweisung** nur vollständig definierte Typen testen.

- Wenn Sie auf überladene Funktionen testen, können Sie nicht auf eine bestimmte Form der Überladung testen.

Die Ergänzung zur **__if_not_exists-Erklärung** ist die [__if_exists-Erklärung.](../cpp/if-exists-statement.md)

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung **von __if_not_exists**finden Sie unter [__if_exists Anweisung](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Siehe auch

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[__if_exists Erklärung](../cpp/if-exists-statement.md)
