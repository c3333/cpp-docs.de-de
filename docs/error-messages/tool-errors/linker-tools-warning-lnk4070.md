---
title: Linkertoolwarnung LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194004"
---
# <a name="linker-tools-warning-lnk4070"></a>Linkertoolwarnung LNK4070

/Out: filename-Direktive in. Das Exp unterscheidet sich vom Ausgabe Dateinamen "filename". Direktive wird ignoriert

Der `filename`, der in der Anweisung " [Name](../../build/reference/name-c-cpp.md) " oder " [Library](../../build/reference/library.md) " beim Erstellen der EXP-Datei angegeben wurde, unterscheidet sich vom Ausgabe `filename`, der entweder standardmäßig angenommen oder mit der [/out](../../build/reference/out-output-file-name.md) -Option angegeben wurde.

Diese Warnung wird angezeigt, wenn Sie den Namen einer Ausgabedatei in der Entwicklungsumgebung ändern und die DEF-Datei des Projekts nicht aktualisiert wurde. Aktualisieren Sie die DEF-Datei manuell, um diese Warnung zu beheben.

Bei einem Client Programm, das die resultierende DLL verwendet, treten möglicherweise Probleme auf.
