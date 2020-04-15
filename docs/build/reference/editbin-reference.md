---
title: EDITBIN-Referenz
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328346"
---
# <a name="editbin-reference"></a>EDITBIN-Referenz

Der Microsoft COFF Binary File Editor (EDITBIN. EXE) ändert COFF-Binärdateien (Common Object File Format). Sie können EDITBIN verwenden, um Objektdateien, ausführbare Dateien und DLL (Dynamic Link Libraries) zu ändern.

> [!NOTE]
> Sie können dieses Tool nur über die Eingabeaufforderung für die Eingabeaufforderung Visual Studio starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

EDITBIN ist für die Verwendung von Dateien, die mit der Compileroption [/GL](gl-whole-program-optimization.md) erstellt wurden, nicht verfügbar. Alle Änderungen an Binärdateien, die mit /GL erzeugt werden, müssen durch Neukompilieren und Verknüpfen erreicht werden.

- [EDITBIN-Befehlszeile](editbin-command-line.md)

- [EDITBIN-Optionen](editbin-options.md)

## <a name="see-also"></a>Siehe auch

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)
