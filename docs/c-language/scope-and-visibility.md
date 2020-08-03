---
title: Bereich und Sichtbarkeit
ms.date: 11/04/2016
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
ms.openlocfilehash: 354b354a72b5a96a190ce2322eb160b7d6bff1c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199398"
---
# <a name="scope-and-visibility"></a>Bereich und Sichtbarkeit

Die Sichtbarkeit eines Bezeichners bestimmt die Teile des Programms, in denen ein Bezeichner auf seinen "Bereich" verweisen kann. Ein Bezeichner ist nur in Teilen eines Programms sichtbar (d. h., er kann dort verwendet werden), die von seinem "Bereich" umgeben sind, der (in der Reihenfolge der zunehmenden Beschränkung) auf die Datei, die Funktion, den Block oder den Funktionsprototyp, in der er angezeigt wird, beschränkt sein kann. Der Bereich eines Bezeichners ist der Teil des Programms, in dem der Name verwendet werden kann. Dieser wird manchmal als "lexikalischer Gültigkeitsbereich" bezeichnet. Es gibt vier Arten von Bereichen: Funktion, Datei, Block und Funktionsprototyp.

Der Gültigkeitsbereich aller Bezeichner, abgesehen von Bezeichnungen, wird durch die Ebene bestimmt, auf der die Deklaration erfolgt. Die folgenden Regeln für jede Art von Bereich bestimmen die Sichtbarkeit von Bezeichnern innerhalb eines Programms:

Gültigkeitsbereich der Datei: Der Deklarator oder Typspezifizierer für einen Bezeichner mit Dateigültigkeitsbereich wird außerhalb eines Blocks oder einer Liste von Parametern angezeigt und ist von einer beliebigen Stelle in der Übersetzungseinheit nach seiner Deklaration zugänglich. Bezeichnernamen mit Dateigültigkeitsbereich werden häufig als "global" oder "extern" bezeichnet. Der Gültigkeitsbereich eines globalen Bezeichners beginnt mit dem Punkt seiner Definition oder Deklaration und endet am Ende der Übersetzungseinheit.

Gültigkeitsbereich der Funktion: Eine Bezeichnung ist die einzige Bezeichnerart, die über einen Funktionsgültigkeitsbereich verfügt. Eine Bezeichnung wird implizit durch ihre Verwendung in einer Anweisung deklariert. Bezeichnungsnamen müssen innerhalb einer Funktion eindeutig sein. (Weitere Informationen über Bezeichnungen und Bezeichnungsnamen finden Sie unter [The goto and Labeled Statements](../c-language/goto-and-labeled-statements-c.md) [Die goto- und Labeled-Anweisung].)

Blockbereich: Der Deklarator oder Typspezifizierer für einen Bezeichner mit Blockbereich wird innerhalb eines Blocks oder in der Liste der formalen Parameterdeklarationen in einer Funktionsdefinition angezeigt. Er ist nur vom Zeitpunkt der Deklaration oder Definition bis zum Ende des Blocks sichtbar, der die Deklaration oder Definition enthält. Sein Bereich beschränkt sich auf diesen Block sowie alle Blöcke, die in diesem Block geschachtelt sind, und endet bei der geschweiften Klammer, die den zugeordneten Block schließt. Solche Bezeichner werden manchmal als "lokale Variablen" bezeichnet.

Funktionsprototypbereich: Der Deklarator oder Typspezifizierer für einen Bezeichner mit Funktionsprototypbereich wird in der Liste der Parameterdeklarationen in einem Funktionsprototyp (nicht Teil der Funktionsdeklaration) angezeigt. Sein Bereich endet am Ende des Funktionsdeklarators.

Die entsprechenden Deklarationen zum Sichtbarmachen von Variablen in anderen Quelldateien werden unter [Speicherklassen](../c-language/c-storage-classes.md) beschrieben. Allerdings sind die Variablen und Funktionen, die auf der externen Ebene mit dem **`static`** -Speicherklassenspezifizierer deklariert werden, nur innerhalb der Quelldatei sichtbar, in der sie definiert sind. Alle anderen Funktionen sind global sichtbar.

## <a name="see-also"></a>Siehe auch

[Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md)
