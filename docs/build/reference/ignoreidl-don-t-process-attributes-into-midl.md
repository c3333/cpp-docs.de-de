---
title: /IGNOREIDL (Don&#39;t Attribute in Mittel l verarbeiten)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: eac6209e0c34562254117d6ab9db5f47545037ea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506885"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t Attribute in Mittel l verarbeiten)

```
/IGNOREIDL
```

## <a name="remarks"></a>Bemerkungen

Die/IGNOREIDL-Option gibt an, dass alle [IDL-Attribute](../../windows/attributes/idl-attributes.md) im Quellcode nicht in einer IDL-Datei verarbeitet werden sollen.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die **eingebettete IDL** -Eigenschaften Seite.

1. Ändern Sie die Eigenschaft **eingebettete IDL ignorieren** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)<br/>
[/IDLOUT (Name der Mittell-Ausgabedateien)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (Name. TLB-Datei)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (Optionen für die Mittell-Befehlszeile angeben)](midl-specify-midl-command-line-options.md)<br/>
[Erstellen eines attributierten Programms](../../windows/attributes/cpp-attributes-com-net.md)
