---
title: Ausdrucksauswertungsfehler CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195616"
---
# <a name="expression-evaluator-error-cxx0030"></a>Ausdrucksauswertungsfehler CXX0030

Ausdruck nicht auswerstellbar

Die Ausdrucks Auswertung des Debuggers konnte keinen Wert für den Ausdruck abrufen, wie er geschrieben wurde. Eine wahrscheinliche Ursache ist, dass sich der Ausdruck auf den Speicher bezieht, der sich außerhalb des Adressraums des Programms befindet (Dereferenzierung ein NULL-Zeiger ist ein Beispiel). Windows lässt keinen Zugriff auf Arbeitsspeicher zu, der außerhalb des Adressraums des Programms liegt.

Möglicherweise möchten Sie Ihren Ausdruck mithilfe von Klammern umschreiben, um die Reihenfolge der Auswertung zu steuern.

Dieser Fehler ist mit CAN0030 identisch.
