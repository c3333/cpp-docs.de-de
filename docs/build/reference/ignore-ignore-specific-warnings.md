---
title: /IGNORE (Bestimmte Warnungen ignorieren)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: 4ed87a1a12bea189f56545cf5256351a29977643
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040261"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (Bestimmte Warnungen ignorieren)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parameter

*warning*<br/>
Die Anzahl der zu unterdrückenden Linkerwarnungen liegt im Bereich von 4000 auf 4999.

## <a name="remarks"></a>Bemerkungen

Standardmäßig meldet LINK alle Warnungen. Geben Sie **/Ignore** `warning` an, um den Linker anzuweisen, eine bestimmte Warnungs Nummer zu unterdrücken. Wenn Sie mehrere Warnungen ignorieren, trennen Sie Warnungsnummern jeweils durch Komma.

Der Linker lässt einige Warnungen nicht ignoriert. In dieser Tabelle werden die Warnungen aufgelistet, die von **/Ignore**nicht unterdrückt werden:

| Linker-Warnung | Nachricht |
|--------------------|-|
|LNK4017|`keyword` die-Anweisung wird für die Zielplattform nicht unterstützt. erten|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Unbekannte Option "`option`"; ignoriert|
|LNK4062|'`option`'nicht kompatibel mit dem''`architecture`' Zielcomputer; Option ignoriert|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|Ignoriert "`option1`" aufgrund der "`option2`" Spezifikation|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|Einstiegspunkt '`function`' ist nicht __stdcall mit '`number`' Bytes an Argumenten; Abbild kann möglicherweise nicht ausgeführt werden.|
|LNK4088|Anwendung wurde durch die Option /Force generiert; Abbild kann möglicherweise nicht ausgeführt werden.|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|kein Argument angegeben mit der Option '`option`'; Schalter wird ignoriert|
|LNK4203|Fehler beim Lesen der Programmdatenbank '`filename`'; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' fehlen Debuginformationen für das Verweismodul; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' fehlen aktuelle Debuginformationen für das Verweismodul; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|Vorkompilierte Typinformationen nicht gefunden; '`filename`' nicht verknüpft oder überschrieben; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|LNK4207|'`filename`' kompiliert/Yc/Yu/Z7; PDB kann nicht erstellt werden; Kompilieren Sie mit/ZI; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|LNK4208|Inkompatibles PDB-Format in '`filename`'; Löschen und erneut erstellen; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|LNK4209|Debuginformationen beschädigt; Kompilieren Sie Modul erneut; Objekt wird verknüpft, als ob keine Debuginformationen vorhanden wären|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` wird nicht mehr unterstützt. erten|
|LNK4228|'`option`' ungültig für eine DLL; ignoriert|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Ungültige Anweisung /`directive` gefunden; ignoriert|

Im Allgemeinen repräsentieren Linkerwarnungen, die nicht ignoriert werden können, Buildfehler, Befehlszeilenfehler oder Fehler bei der Konfiguration, die Sie beheben müssen.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im Ordner **Linker** die Eigenschaften Seite **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
