---
title: Ausdrucksauswertungsfehler CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184423"
---
# <a name="expression-evaluator-error-cxx0065"></a>Ausdrucksauswertungsfehler CXX0065

Variable benötigt Stapel Rahmen

Ein Ausdruck enthielt eine Variable, die im aktuellen Bereich vorhanden ist, aber noch nicht erstellt wurde.

Dieser Fehler kann auftreten, wenn Sie in den Prolog einer Funktion eingetreten sind, den Stapel Rahmen für die Funktion jedoch noch nicht eingerichtet haben, oder wenn Sie den Exitcode für die Funktion abgecheckt haben.

Schrittweises Durchlaufen des Prolog-Codes, bis der Stapel Rahmen eingerichtet wurde, bevor der Ausdruck ausgewertet wird.

Dieser Fehler ist mit CAN0065 identisch.
