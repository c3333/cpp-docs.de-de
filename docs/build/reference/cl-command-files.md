---
title: CL-Befehlsdateien
description: Mit dem MSVC-Compiler können Sie Befehls Dateien angeben, die Befehlszeilenoptionen enthalten.
ms.date: 07/08/2020
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 6deab4b11dcc6c53beb5b4fa8b014a56020c3420
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180941"
---
# <a name="cl-command-files"></a>CL-Befehlsdateien

Eine Befehlsdatei ist eine Textdatei, die Compileroptionen und Dateinamen enthält. Sie gibt Optionen an, die Sie andernfalls in der [Befehlszeile](compiler-command-line-syntax.md)eingeben oder mithilfe der [CL-Umgebungsvariablen](cl-environment-variables.md)angeben. CL akzeptiert eine Compilerbefehlsdatei als Argument, entweder in der CL-Umgebungsvariablen oder in der Befehlszeile. Anders als bei der Befehlszeile oder der CL-Umgebungsvariablen können Sie mehrere Zeilen mit Optionen und Dateinamen in einer Befehlsdatei verwenden.

Optionen und Dateinamen in einer Befehlsdatei werden verarbeitet, wenn ein Befehls Dateiname innerhalb der CL-Umgebungsvariablen oder in der Befehlszeile angezeigt wird. Wenn die Option jedoch **`/link`** in der Befehlsdatei angezeigt wird, werden alle Optionen im Rest der Zeile an den Linker weitergeleitet. Optionen in späteren Zeilen in der Befehlsdatei und Optionen in der Befehlszeile nach dem Aufruf der Befehlsdatei werden weiterhin als Compileroptionen akzeptiert. Weitere Informationen zur Auswirkung der Reihenfolge der Optionen auf die Interpretation finden Sie unter [Reihenfolge der CL-Optionen](order-of-cl-options.md).

Eine Befehlsdatei darf keinen CL-Befehl enthalten. Jede Option muss in derselben Zeile beginnen und enden. Sie können den umgekehrten Schrägstrich ( **`\`** ) nicht verwenden, um eine Option über zwei Zeilen hinweg zu kombinieren.

Eine Befehlsdatei wird durch ein @-Zeichen ( **`@`** ) gefolgt von einem Dateinamen angegeben. Der Dateiname kann einen absoluten oder relativen Pfad angeben.

Wenn sich beispielsweise der folgende Befehl in einer Datei namens "\" befindet:

```cmd
/Ot /link LIBC.LIB
```

und geben Sie den folgenden CL-Befehl an:

```cmd
CL /Ob2 @RESP MYAPP.C
```

der Befehl für cl lautet wie folgt:

```cmd
CL /Ob2 /Ot MYAPP.C /link LIBC.LIB
```

Hier können Sie sehen, wie die Befehlszeile und die Befehlsdatei Befehle effektiv kombiniert werden.

## <a name="see-also"></a>Weitere Informationen

[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)
