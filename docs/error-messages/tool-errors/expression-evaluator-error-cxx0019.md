---
title: Ausdrucksauswertungsfehler CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195889"
---
# <a name="expression-evaluator-error-cxx0019"></a>Ausdrucksauswertungsfehler CXX0019

Ungültige Typumwandlung.

Die C-Ausdrucks Auswertung kann die Typumwandlung nicht wie geschrieben ausführen.

Dieser Fehler ist mit CAN0019 identisch.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Der angegebene Typ ist unbekannt.

1. Es gab zu viele Ebenen von Zeiger Typen. Beispielsweise die Typumwandlung

    ```
    (char **)h_message
    ```

   kann nicht von der C-Ausdrucks Auswertung ausgewertet werden.
