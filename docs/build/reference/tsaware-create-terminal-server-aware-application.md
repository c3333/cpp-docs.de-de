---
title: /TSAWARE (Terminalserverfähige Anwendung erstellen)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: c2ec12b0b5fbe241d75acc4bb0d87837371a293e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845730"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Terminalserverfähige Anwendung erstellen)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Bemerkungen

Die Option/TSAWARE legt ein Flag im Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programm Bilds fest. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.

Wenn eine Anwendung nicht mit dem Terminal Server kompatibel ist (auch als ältere Anwendung bezeichnet), führt der Terminal Server bestimmte Änderungen an der Legacy Anwendung aus, damit Sie in einer Umgebung mit mehreren Benutzern ordnungsgemäß funktioniert. Beispielsweise erstellt Terminal Server einen virtuellen Windows-Ordner, sodass jeder Benutzer einen Windows-Ordner erhält, anstatt das Windows-Verzeichnis des Systems zu erhalten. Dies ermöglicht Benutzern den Zugriff auf Ihre eigenen INI-Dateien. Außerdem nimmt Terminal Server einige Anpassungen an der Registrierung für eine Legacy Anwendung vor. Diese Änderungen verlangsamen das Laden der Legacy Anwendung auf dem Terminal Server.

Wenn eine Anwendung Terminal Server fähig ist, muss Sie weder auf ini-Dateien noch auf die **HKEY_CURRENT_USER** Registrierung während des Setups schreiben.

Wenn Sie/TSAWARE verwenden und die Anwendung weiterhin ini-Dateien verwendet, werden die Dateien von allen Benutzern des Systems gemeinsam genutzt. Wenn dies akzeptabel ist, können Sie Ihre Anwendung weiterhin mit/TSAWARE verknüpfen. Andernfalls müssen Sie/TSAWARE: No verwenden.

Die Option/TSAWARE ist für Windows-und Konsolen Anwendungen standardmäßig aktiviert. Weitere Informationen finden Sie unter [/Subsystem](subsystem-specify-subsystem.md) und [/Version](version-version-information.md) .

/TSAWARE ist für Treiber oder DLLs ungültig.

Wenn eine Anwendung mit/TSAWARE verknüpft wurde, zeigt DUMPBIN [/Headers](headers.md) Informationen zu diesem Effekt an.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaften Seite **System** .

1. Ändern Sie die Eigenschaft **Terminal Server** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)<br/>
[Speichern von benutzerspezifischen Informationen](/windows/win32/TermServ/storing-user-specific-information)<br/>
[Legacy Anwendungen in einer Terminaldiensteumgebung](/previous-versions/aa382957(v=vs.85))
