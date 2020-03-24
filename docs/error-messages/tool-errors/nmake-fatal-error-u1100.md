---
title: 'NMAKE: Schwerwiegender Fehler U1100'
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193263"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE: Schwerwiegender Fehler U1100

das Makro "macroname" ist im Kontext der Batch Regel "Rule" unzulässig.

NMAKE generiert diesen Fehler, wenn der Befehls Block einer Batch Modus-Regel direkt oder indirekt auf ein spezielles Datei Makro verweist, das nicht $ < ist.

$ < ist das einzige zulässige Makro für Regeln im Batch Modus.
