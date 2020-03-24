---
title: Ausdrucksauswertungsfehler CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196065"
---
# <a name="expression-evaluator-error-cxx0015"></a>Ausdrucksauswertungsfehler CXX0015

Ausdruck zu komplex (Stapelüberlauf)

Der eingegebene Ausdruck war zu komplex oder zu tief geschachtelt für die Menge an Speicher, die der Ausdrucks Auswertung von C zur Verfügung steht.

Ein Überlauf tritt normalerweise auf, weil zu viele ausstehende Berechnungen ausgeführt werden.

Ordnen Sie den Ausdruck so an, dass jede Komponente des Ausdrucks so ausgewertet werden kann, wie er gefunden wird, anstatt zu warten, bis andere Teile des Ausdrucks berechnet werden.

Unterbrechen Sie den Ausdruck in mehrere Befehle.

Dieser Fehler ist mit CAN0015 identisch.
