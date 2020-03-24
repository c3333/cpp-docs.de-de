---
title: Linkertoolwarnung LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183487"
---
# <a name="linker-tools-warning-lnk4075"></a>Linkertoolwarnung LNK4075

Ignorieren von "Option1" aufgrund der Angabe von "option2"

Die zweite Option überschreibt das erste.

Es werden sich gegenseitig ausschließende Linker-Optionen angegeben.  Überprüfen Sie die Linkeroptionen.  Wo die Linkeroptionen angegeben werden, hängt davon ab, wie Sie Ihr Projekt entwickeln.

- Wenn Sie in der Entwicklungsumgebung entwickeln, sehen Sie sich die Linker-Eigenschaften Seiten für Ihr Projekt an, und sehen Sie, wo beide Linkeroptionen angegeben werden.  Weitere Informationen finden Sie unter [Set Compiler and Build Properties](../../build/working-with-project-properties.md) .

- Wenn Sie in der Befehlszeile erstellen, sehen Sie sich die hier angegebenen Linker-Optionen an.

- Wenn Sie mit Buildskripts erstellen, überprüfen Sie die Skripts, um zu sehen, wo diese Linkeroptionen angegeben werden.

Wenn Sie feststellen, wo die sich gegenseitig ausschließenden Linker-Optionen angegeben sind, entfernen Sie eine der Linkeroptionen.

Einige spezifische Beispiele:

- Wenn Sie ein Modul verknüpfen, das mit **/Zi**kompiliert wurde, das eine interne Linkeroption namens/EDITANDCONTINUE und ein Modul impliziert, das mit/OPT: ref,/OPT: ICF oder/Incremental: No kompiliert wurde, das kein/EDITANDCONTINUE impliziert, erhalten Sie LNK4075.  Weitere Informationen finden Sie unter [/Z7,/Zi,/Zi (Debuginformationsformat)](../../build/reference/z7-zi-zi-debug-information-format.md) .
