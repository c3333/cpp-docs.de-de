---
title: Ausdrucksauswertungsfehler CXX0052
ms.date: 11/04/2016
f1_keywords:
- CXX0052
helpviewer_keywords:
- CXX0052
- CAN0052
ms.assetid: 5060d479-d0a4-4682-b858-c8b9a4f324e6
ms.openlocfilehash: 5b9596313a80cb555f7daf4b65eda54a1d23a1ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184800"
---
# <a name="expression-evaluator-error-cxx0052"></a>Ausdrucksauswertungsfehler CXX0052

Member-Funktion nicht vorhanden

Eine Member-Funktion wurde als Haltepunkt angegeben, konnte jedoch nicht gefunden werden. Dieser Fehler kann verursacht werden, wenn ein Haltepunkt bei einer Funktion festgelegt wird, die als Inline festgelegt wurde.

Kompilieren Sie die Datei mit Inlining Forced Off (/Ob0) neu, um in dieser Funktion einen Haltepunkt festzulegen.

Ein Ausdruck, der als Funktion bezeichnet wird, die nicht definiert wurde.

Dieser Fehler ist mit CAN0052 identisch.
