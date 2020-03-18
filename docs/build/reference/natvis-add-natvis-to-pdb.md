---
title: /NATVIS (Natvis zu PDB hinzufügen)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: a16e320a2f8f946912fef6a354f27f6514a67e29
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439278"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (Natvis zu PDB hinzufügen)

> /NATVIS:*Dateiname*

## <a name="parameters"></a>Parameter

*filename*<br/>
Eine natvis-Datei, die der PDB-Datei hinzugefügt werden soll. Sie bettet die Debugger-Visualisierungen in der natvis-Datei in die PDB ein.

## <a name="remarks"></a>Bemerkungen

Die Option/NATVIS bettet die Debuggervisualisierungen, die in der natvis-Datei *Dateiname* definiert sind, in die von Link generierte PDB-Datei ein. Dadurch kann der Debugger die Visualisierungen unabhängig von der natvis-Datei anzeigen. Sie können mehrere/NATVIS-Optionen verwenden, um mehr als eine natvis-Datei in die generierte PDB-Datei einzubetten.

Link ignoriert/NATVIS, wenn keine PDB-Datei mit einer [/Debug](debug-generate-debug-info.md) -Option erstellt wird. Informationen zum Erstellen und Verwenden von natvis-Dateien finden Sie unter [Erstellen benutzerdefinierter Ansichten von systemeigenen Objekten im Visual Studio-Debugger](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im Ordner **Linker** die Eigenschaften Seite **Befehlszeile** aus.

1. Fügen Sie dem Textfeld **zusätzliche Optionen** die Option/NATVIS hinzu.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Diese Option hat keine programmgesteuerte Entsprechung.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
