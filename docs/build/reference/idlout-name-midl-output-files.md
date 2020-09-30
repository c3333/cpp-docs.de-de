---
title: /IDLOUT (Namen der MIDL-Ausgabedateien)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 8dc26a0564a979c918d1eb1eb85e63e9c73caba0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506932"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Namen der MIDL-Ausgabedateien)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Parameter

*path*<br/>
Eine absolute oder relative Pfadspezifikation. Wenn Sie einen Pfad angeben, wirkt sich dies nur auf den Speicherort einer IDL-Datei aus. alle anderen Dateien werden im Projektverzeichnis abgelegt.

*filename*<br/>
Gibt den Namen der IDL-Datei an, die vom-Mittell-Compiler erstellt wurde. Es wird keine Dateierweiterung angenommen. Geben Sie *filename*. idl an, wenn Sie eine IDL-Erweiterung wünschen.

## <a name="remarks"></a>Bemerkungen

Die Option/IDLOUT gibt den Namen und die Erweiterung der IDL-Datei an.

Der-compilercompiler wird vom MSVC-Linker aufgerufen, wenn Projekte verknüpft werden, die über das [Module](../../windows/attributes/module-cpp.md) -Attribut verfügen.

/IDLOUT gibt auch die Dateinamen der anderen Ausgabedateien an, die dem mittlerer l-Compiler zugeordnet sind:

- *Dateiname*. tlb

- *Dateiname*_P. c

- *Dateiname*_i. c

- *Dateiname*. h

*Dateiname* ist der Parameter, den Sie an/IDLOUT. übergeben. Wenn [/TLBOUT](tlbout-name-dot-tlb-file.md) angegeben wird, erhält die TLB-Datei ihren Namen aus/TLBOUT *filename*.

Wenn Sie weder/IDLOUT noch/TLBOUT angeben, erstellt der Linker vc70. tlb, vc70. idl, vc70_p. c, vc70_i. c und vc70. h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die **eingebettete IDL** -Eigenschaften Seite.

1. Ändern Sie die Eigenschaft **IDL-Basis Dateiname zusammenführen** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)<br/>
[/IGNOREIDL (Attribute nicht in Mittel l verarbeiten)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Optionen für die Mittell-Befehlszeile angeben)](midl-specify-midl-command-line-options.md)<br/>
[Erstellen eines attributierten Programms](../../windows/attributes/cpp-attributes-com-net.md)
