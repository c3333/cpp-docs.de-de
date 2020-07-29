---
title: Angeben, wann und wo eine Anmerkung gültig ist
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
ms.openlocfilehash: 790a1349c3f4d7dbee878f3eb695d83682a7fa7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216660"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Angeben, wann und wo eine Anmerkung gültig ist

Wenn eine Anmerkung bedingt ist, sind möglicherweise andere Anmerkungen erforderlich, um dies für den Analyzer anzugeben.  Wenn eine Funktion z. b. eine Variable aufweist, die entweder synchron oder asynchron sein kann, verhält sich die Funktion wie folgt: im synchronen Fall ist Sie immer schließlich erfolgreich, aber im asynchronen Fall meldet Sie einen Fehler, wenn Sie nicht sofort ausgeführt werden kann. Wenn die Funktion synchron aufgerufen wird, stellt die Überprüfung des Ergebnis Werts keinen Wert für den Code Analyse Wert dar, da er nicht zurückgegeben hätte.  Wenn die Funktion jedoch asynchron aufgerufen wird und das Ergebnis der Funktion nicht aktiviert ist, kann ein schwerwiegender Fehler auftreten. Dieses Beispiel veranschaulicht eine Situation, in der Sie die-Anmerkung `_When_` – weiter unten in diesem Artikel – zum Aktivieren der Überprüfung verwenden können.

## <a name="structural-annotations"></a>Strukturelle Anmerkungen

Verwenden Sie die folgenden strukturellen Anmerkungen, um zu steuern, wann und wo Anmerkungen angewendet werden.

|Anmerkung|BESCHREIBUNG|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`ein Ausdruck, der einen lvalue ergibt. Die Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von benannt wird `expr` . Für jede Anmerkung in `anno-list` `expr` wird in der Vorbedingung interpretiert, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Post Bedingung, wenn die Anmerkung in der Post-Bedingung interpretiert wird.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`ein Ausdruck, der einen lvalue ergibt. Die Anmerkungen in `anno-list` werden auf das Objekt angewendet, das von benannt wird `expr` . Für jede Anmerkung in `anno-list` `expr` wird in der Vorbedingung interpretiert, wenn die Anmerkung in der Vorbedingung interpretiert wird, und in der Post-Bedingung, wenn die Anmerkung in der nach Bedingung interpretiert wird.<br /><br /> `iter`der Name einer Variablen, die auf die Anmerkung (einschließlich) beschränkt ist `anno-list` . `iter`weist einen impliziten Typ auf **`long`** . Identisch benannte Variablen in jedem einschließenden Bereich werden aus der Auswertung ausgeblendet.<br /><br /> `elem-count`ein Ausdruck, der eine ganze Zahl ergibt.|
|`_Group_(anno-list)`|Die Anmerkungen in `anno-list` werden alle als Qualifizierer betrachtet, die für die Gruppen Anmerkung gelten, die auf jede Anmerkung angewendet wird.|
|`_When_(expr, anno-list)`|`expr`ein Ausdruck, der in konvertiert werden kann **`bool`** . Wenn der Wert ungleich 0 (NULL **`true`** ) ist, gelten die Anmerkungen, die in angegeben sind, `anno-list` als anwendbar.<br /><br /> Standardmäßig wird für jede Anmerkung in `anno-list` `expr` als Verwendung der Eingabewerte interpretiert, wenn die Anmerkung eine Vorbedingung ist, und als die Ausgabewerte verwendet werden, wenn die Anmerkung eine nach Bedingung ist. Um die Standardeinstellung zu überschreiben, können Sie die systeminterne Funktion verwenden, `_Old_` Wenn Sie eine nach Bedingung auswerten, um anzugeben, dass die Eingabewerte verwendet werden sollen. **Hinweis:**  Verschiedene Anmerkungen können als Folge der Verwendung von aktiviert werden `_When_` , wenn ein änderbarer Wert – beispielsweise `*pLength` – beteiligt ist, da das ausgewertete Ergebnis von `expr` in Vorbedingung möglicherweise von dem ausgewerteten Ergebnis in der nach Bedingung abweicht.|

## <a name="see-also"></a>Weitere Informationen

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
