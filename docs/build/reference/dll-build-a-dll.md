---
title: /DLL (DLL erstellen)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 5f7907d659ee3bedc590b88320df03edce005b06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293757"
---
# <a name="dll-build-a-dll"></a>/DLL (DLL erstellen)

```
/DLL
```

## <a name="remarks"></a>Hinweise

Die/DLL-Option erstellt eine DLL als Hauptausgabedatei. Eine DLL-Datei enthält in der Regel die Exporte, die von einem anderen Programm verwendet werden können. Es gibt drei Methoden zum Angeben von Exports, aufgelistet in empfohlener Reihenfolge von Nutzen:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) im Quellcode

1. Ein [EXPORTE](exports.md) -Anweisung in DEF-Datei

1. Ein [/EXPORT](export-exports-a-function.md) Spezifikation in einem LINK-Befehl

Ein Programm kann mehr als eine Methode verwenden.

Eine weitere Möglichkeit zum Erstellen einer DLL wird mit der **Bibliothek** Moduldefinitionsdatei-Anweisung. Die Optionen/Base "und" / DLL zusammen entsprechen den **Bibliothek** Anweisung.

Angegeben Sie diese Option in der Entwicklungsumgebung nicht werden, Diese Option ist für die Verwendung nur in der Befehlszeile. Diese Option wird festgelegt, wenn Sie ein DLL-Projekt mit einer Anwendungs-Assistenten erstellen.

Beachten Sie, dass wenn Sie die Importbibliothek in einem vorherigen Schritt erstellen, bevor Sie die DLL-Datei erstellen, den gleichen Satz von Objektdateien müssen beim Erstellen der DLL-Datei übergeben werden wie bei der Erstellung der Importbibliothek.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen finden Sie unter [Festlegen von C++-Compiler und die Build-Eigenschaften in Visual Studio](../working-with-project-properties.md).

1. Klicken Sie auf die **Konfigurationseigenschaften** Ordner.

1. Klicken Sie auf die **allgemeine** Eigenschaftenseite.

1. Ändern der **Konfigurationstyp** Eigenschaft.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
