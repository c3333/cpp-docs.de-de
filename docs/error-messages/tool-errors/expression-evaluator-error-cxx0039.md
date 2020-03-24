---
title: Ausdrucksauswertungsfehler CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185125"
---
# <a name="expression-evaluator-error-cxx0039"></a>Ausdrucksauswertungsfehler CXX0039

Symbol ist mehrdeutig

Die C-Ausdrucks Auswertung kann nicht bestimmen, welche Instanz eines Symbols in einem Ausdruck verwendet werden soll. Das Symbol tritt mehrmals in der Vererbungs Struktur auf.

Sie müssen den Bereichs Auflösungs Operator (`::`) verwenden, um die Instanz explizit anzugeben, die im Ausdruck verwendet werden soll.

Dieser Fehler ist mit CAN0039 identisch.
