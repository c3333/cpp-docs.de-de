---
title: Syntax für die MSVC-Compilerbefehlszeile
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320550"
---
# <a name="compiler-command-line-syntax"></a>Syntax für die Compilerbefehlszeile

Die CL-Befehlszeile verwendet die folgende Syntax:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

In der folgenden Tabelle wird die Eingabe in den CL-Befehl beschrieben.

|Eintrag|Bedeutung|
|-----------|-------------|
|*Option*|Eine oder mehrere [CL-Optionen](compiler-options.md). Beachten Sie, dass alle Optionen für alle angegebenen Quelldateien gelten. Optionen werden entweder durch einen Schrägstrich (/) oder einen Bindestrich (-) angegeben. Wenn eine Option ein Argument annimmt, dokumentiert die Beschreibung der Option, ob ein Leerzeichen zwischen der Option und den Argumenten zulässig ist. Optionsnamen (mit Ausnahme der Option /HELP) werden die Groß-/Kleinschreibung beachtet. Weitere Informationen finden Sie unter [Reihenfolge der CL-Optionen.](order-of-cl-options.md)|
|`file`|Der Name einer oder mehrerer Quelldateien, .obj-Dateien oder Bibliotheken. CL kompiliert Quelldateien und übergibt die Namen der .obj-Dateien und -Bibliotheken an den Linker. Weitere Informationen finden Sie unter [CL Filename Syntax.](cl-filename-syntax.md)|
|*Lib*|Ein oder mehrere Bibliotheksnamen. CL übergibt diese Namen an den Linker.|
|*Befehlsdatei*|Eine Datei, die mehrere Optionen und Dateinamen enthält. Weitere Informationen finden Sie unter [CL-Befehlsdateien.](cl-command-files.md)|
|*link-opt*|Eine oder mehrere [MSVC-Linker-Optionen](linker-options.md). CL übergibt diese Optionen an den Linker.|

Sie können eine beliebige Anzahl von Optionen, Dateinamen und Bibliotheksnamen angeben, solange die Anzahl der Zeichen in der Befehlszeile 1024 nicht überschreitet, dem vom Betriebssystem vorgegebenen Grenzwert.

Informationen zum Rückgabewert von cl.exe finden Sie unter [Rückgabewert von cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> Das Befehlszeilen-Eingabelimit von 1024 Zeichen wird in zukünftigen Versionen von Windows nicht garantiert gleich bleiben.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)
