---
title: /ENTRY (Symbol für Einstiegspunkt)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 80833980b64e8fdd2a2f57b2dc40eb21c784b6f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232702"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbol für Einstiegspunkt)

```
/ENTRY:function
```

## <a name="arguments"></a>Argumente

*function*<br/>
Eine Funktion, die eine benutzerdefinierte Startadresse für eine exe-Datei oder eine DLL-Datei angibt.

## <a name="remarks"></a>Bemerkungen

Die Option/Entry gibt eine Einstiegspunkt Funktion als Startadresse für eine exe-Datei oder eine DLL-Datei an.

Die-Funktion muss für die Verwendung der **`__stdcall`** Aufruf Konvention definiert werden. Die Parameter und der Rückgabewert hängen davon ab, ob es sich bei dem Programm um eine Konsolenanwendung, eine Windows-Anwendung oder eine DLL handelt. Es wird empfohlen, dass Sie den Linker den Einstiegspunkt festlegen lassen, damit die C-Lauf Zeit Bibliothek ordnungsgemäß initialisiert wird, und C++-Konstruktoren für statische Objekte ausführen.

Standardmäßig handelt es sich bei der Startadresse um einen Funktionsnamen aus der C-Lauf Zeit Bibliothek. Der Linker wählt ihn gemäß den Attributen des Programms aus, wie in der folgenden Tabelle dargestellt.

|Funktionsname|Standardwert für|
|-------------------|-----------------|
|**mainCRTStartup** (oder **wmainCRTStartup**)|Eine Anwendung, die/Subsystem: Console; verwendet Aufrufe `main` (oder `wmain` )|
|**WinMainCRTStartup** (oder **wWinMainCRTStartup**)|Eine Anwendung, die/Subsystem verwendet:**Windows**; Ruft `WinMain` (oder `wWinMain` ) auf, die für die Verwendung von definiert werden müssen.**`__stdcall`**|
|**_DllMainCRTStartup**|eine DLL. Ruft `DllMain` auf, falls vorhanden, die für die Verwendung von definiert werden muss.**`__stdcall`**|

Wenn die [/dll](dll-build-a-dll.md) -Option oder die [/Subsystem](subsystem-specify-subsystem.md) -Option nicht angegeben ist, wählt der Linker ein Subsystem und einen Einstiegspunkt aus, je nachdem, ob `main` oder `WinMain` definiert ist.

Die Funktionen `main` , `WinMain` und `DllMain` sind die drei Formen des benutzerdefinierten Einstiegs Punkts.

Wenn Sie ein verwaltetes Image erstellen, muss die für/Entry angegebene Funktion über eine Signatur von (LPVOID *var1*, DWORD *var2*, LPVOID *var3*) verfügen.

Informationen dazu, wie Sie einen eigenen `DllMain` Einstiegspunkt definieren, finden Sie unter [DLLs und Verhalten der Visual C++ Lauf Zeit Bibliothek](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaften Seite **erweitert** .

1. Ändern Sie die Eigenschaft **Einstiegspunkt** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
