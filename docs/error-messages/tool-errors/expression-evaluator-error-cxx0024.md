---
title: Ausdrucksauswertungsfehler CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195759"
---
# <a name="expression-evaluator-error-cxx0024"></a>Ausdrucksauswertungsfehler CXX0024

der Vorgang benötigt einen l-Wert.

Ein Ausdruck, der nicht als l-Wert ausgewertet wird, wurde für einen Vorgang angegeben, der einen l-Wert erfordert.

Ein l-Wert (wird aufgerufen, weil er auf der linken Seite einer Zuweisungsanweisung angezeigt wird) ist ein Ausdruck, der auf einen Speicherort verweist.

Beispielsweise ist `buffer[count]` ein gültiger l-Wert, da er auf eine bestimmte Speicheradresse verweist. Der logische Vergleichs `zed != 0` ist kein gültiger l-Wert, da er zu "true" oder "false" ausgewertet wird, nicht zu einer Speicheradresse.

Dieser Fehler ist mit CAN0024 identisch.
