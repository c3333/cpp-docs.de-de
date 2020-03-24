---
title: Linkertoolwarnung LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 1758fffb72e183e8a186d115b2b3f3b30c32e047
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193875"
---
# <a name="linker-tools-warning-lnk4206"></a>Linkertoolwarnung LNK4206

> vorkompilierte Typinformationen wurden nicht gefunden. "*Dateiname*" ist nicht verknüpft oder überschrieben. Objekt wird verknüpft, als ob keine Debuginformationen

Die Datei mit dem *Namen der Dateinamen* , die mit [/Yc](../../build/reference/yc-create-precompiled-header-file.md)kompiliert wurde, wurde entweder nicht im Link Befehl angegeben oder wurde überschrieben.

Ein häufiges Szenario für diese Warnung ist, wenn sich die mit/Yc kompilierte. obj-Datei in einer Bibliothek befindet und keine Symbol Verweise auf diese obj-Datei aus dem Code vorhanden sind.  In diesem Fall wird die OBJ-Datei vom Linker nicht verwendet (oder sogar angezeigt).  In dieser Situation sollten Sie den Code neu kompilieren und [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) für die Objekte verwenden, die mit [/Yu](../../build/reference/yu-use-precompiled-header-file.md)kompiliert wurden.
