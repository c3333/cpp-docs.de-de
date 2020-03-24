---
title: Ausdrucksauswertungsfehler CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: 5858ce936acfb8b949351c9263f3a9379c73648e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195824"
---
# <a name="expression-evaluator-error-cxx0022"></a>Ausdrucksauswertungsfehler CXX0022

Funktionsaufrufe vor _main

Die C-Ausdrucks Auswertung kann eine Funktion nicht auswerten, bevor der Debugger die Funktion **_main**eingegeben hat. Das Programm wird erst ordnungsgemäß initialisiert, wenn **_main** aufgerufen wurde.

Dieser Fehler ist mit CAN0022 identisch.
