---
title: Compilerwarnung (Stufe 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199567"
---
# <a name="compiler-warning-level-1-c4650"></a>Compilerwarnung (Stufe 1) C4650

Debuginformationen nicht in vorkompiliertem Header; Es sind nur globale Symbole aus dem Header verfügbar.

Die vorkompilierte Header Datei wurde nicht mit symbolischen Debuginformationen von Microsoft kompiliert.

Wenn die resultierende ausführbare Datei oder die Datei mit der Dynamic Link Library verknüpft ist, enthält Sie keine Debuginformationen für lokale Symbole, die im vorkompilierten Header enthalten sind.

Diese Warnung kann vermieden werden, indem die vorkompilierte Header Datei mit der [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) -Befehlszeilenoption neu kompiliert wird.
