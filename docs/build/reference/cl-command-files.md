---
title: CL-Befehlsdateien
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440265"
---
# <a name="cl-command-files"></a>CL-Befehlsdateien

Eine Befehlsdatei ist eine Textdatei, die Optionen und Dateinamen enthält, die Sie andernfalls in der [Befehlszeile](compiler-command-line-syntax.md) eingeben oder mithilfe der [CL-Umgebungsvariablen](cl-environment-variables.md)angeben. Cl akzeptiert eine Compilerbefehlsdatei als Argument in der CL-Umgebungsvariablen oder in der Befehlszeile. Anders als in der Befehlszeile oder in der CL-Umgebungsvariablen können Sie in einer Befehlsdatei mehrzeilige Optionen und Dateinamen verwenden.

Optionen und Dateinamen in einer Befehlsdatei werden entsprechend dem Speicherort eines Befehls Dateinamen innerhalb der CL-Umgebungsvariablen oder in der Befehlszeile verarbeitet. Wenn jedoch die/Link-Option in der Befehlsdatei angezeigt wird, werden alle Optionen im Rest der Zeile an den Linker weitergeleitet. Optionen in nachfolgenden Zeilen in der Befehlsdatei und Optionen in der Befehlszeile nach dem Aufruf der Befehlsdatei werden weiterhin als Compileroptionen akzeptiert. Weitere Informationen zur Auswirkung der Reihenfolge der Optionen auf die Interpretation finden Sie unter [Reihenfolge der CL-Optionen](order-of-cl-options.md).

Eine Befehlsdatei darf keinen CL-Befehl enthalten. Jede Option muss in derselben Zeile beginnen und enden. Sie können den umgekehrten Schrägstrich ( **\\** ) nicht verwenden, um eine Option über zwei Zeilen hinweg zu kombinieren.

Eine Befehlsdatei wird durch ein @-Zeichen ( **\@** ) gefolgt von einem Dateinamen angegeben. der Dateiname kann einen absoluten oder relativen Pfad angeben.

Wenn sich beispielsweise der folgende Befehl in einer Datei namens "\" befindet:

```
/Og /link LIBC.LIB
```

und geben Sie den folgenden CL-Befehl an:

```
CL /Ob2 @RESP MYAPP.C
```

der Befehl für cl lautet wie folgt:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Beachten Sie, dass die Befehlszeile und die Befehlsdatei Befehle effektiv kombiniert werden.

## <a name="see-also"></a>Weitere Informationen

[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)
