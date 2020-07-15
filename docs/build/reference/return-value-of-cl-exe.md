---
title: Rückgabewert von cl.exe
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 627d20a85b8f31ab881588533840a888334e9847
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373774"
---
# <a name="return-value-of-clexe"></a>Rückgabewert von cl.exe

cl.exe gibt 0 (null) für Erfolg (keine Fehler) und andernfalls einen Wert ungleich 0 (null) zurück.

Der Rückgabewert von cl.exe kann nützlich sein, wenn Sie mit einer Skript-, PowerShell-, CMD- oder BAT-Datei kompilieren. Es wird empfohlen, die Ausgabe des Compilers aufzuzeichnen, um mögliche Fehler oder Warnmeldungen beheben zu können.

Es gibt weitaus mehr mögliche Exitcodes bei Fehlern, als cl.exe auflisten könnte. Sie können in den Dateien "Winerror. h" oder "NTSTATUS. h", die im Windows Software Development Kit enthalten sind, in dem Verzeichnis "% Program Files (x86)% \ Windows Kits \\ <em>Version</em>\include\shared\" einen Fehlercode nachschlagen. Im Dezimalformat zurückgegebene Fehlercodes müssen für die Suche in das Hexadezimalformat konvertiert werden. Beispiel: Der Fehlercode -1073741620 entspricht im Hexadezimalformat 0xC00000CC. Dieser Fehler befindet sich in der Datei "ntstatus.h" mit der entsprechenden Meldung "Der angegebene Freigabename wurde auf dem Server nicht gefunden". Eine herunterladbare Liste der Windows-Fehlercodes finden Sie unter [&#91;MS-erref&#93;: Windows-Fehlercodes](https://docs.microsoft.com/openspecs/windows_protocols/MS-ERREF).

Sie können die Bedeutung einer Fehlermeldung des Compilers auch mit dem Hilfsprogramm für die Fehlersuche von Visual Studio herausfinden. Geben Sie in einer Visual Studio-Befehlsshell **errlook.exe** ein, um das Hilfsprogramm zu starten. oder **Wählen Sie**in der Visual Studio-IDE in der Menüleiste Extras und **Fehlersuche**aus. Geben Sie den Fehlerwert ein, um den beschreibenden Text zu finden, der mit dem Fehler verknüpft ist. Weitere Informationen finden Sie unter [ERRLOOK-Referenz](errlook-reference.md).

## <a name="remarks"></a>Hinweise

Bei dem folgenden Beispiel handelt es sich um eine BAT-Datei, die den Rückgabewert von cl.exe verwendet.

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>Weitere Informationen

[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
