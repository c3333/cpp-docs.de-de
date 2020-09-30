---
title: /TLBOUT (TLB-Datei benennen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 62913eaadd0f0a88f05ce347a6778062a1e66f17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509341"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (TLB-Datei benennen)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Argumente

*path*<br/>
Eine absolute oder relative Pfadspezifikation für den Speicherort, an dem die TLB-Datei erstellt werden soll.

*filename*<br/>
Gibt den Namen der TLB-Datei an, die vom-Mittell-Compiler erstellt wurde. Es wird keine Dateierweiterung angenommen. Geben Sie *filename*. tlb an, wenn Sie eine TLB-Erweiterung wünschen.

## <a name="remarks"></a>Bemerkungen

Die Option/TLBOUT gibt den Namen und die Erweiterung der TLB-Datei an.

Der-compilercompiler wird vom MSVC-Linker aufgerufen, wenn Projekte verknüpft werden, die über das [Module](../../windows/attributes/module-cpp.md) -Attribut verfügen.

Wenn/TLBOUT nicht angegeben ist, erhält die TLB-Datei ihren Namen aus [/IDLOUT](idlout-name-midl-output-files.md) *filename*. Wenn/IDLOUT nicht angegeben ist, wird die TLB-Datei vc70. tlb genannt.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die **eingebettete IDL** -Eigenschaften Seite.

1. Ändern Sie die Eigenschaft **Typbibliothek** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

1. Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)<br/>
[/IGNOREIDL (Attribute nicht in Mittel l verarbeiten)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Optionen für die Mittell-Befehlszeile angeben)](midl-specify-midl-command-line-options.md)<br/>
[Erstellen eines attributierten Programms](../../windows/attributes/cpp-attributes-com-net.md)
