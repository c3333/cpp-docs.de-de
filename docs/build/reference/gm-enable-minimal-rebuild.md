---
title: /Gm (Minimale Neuerstellung aktivieren)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439641"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Minimale Neuerstellung aktivieren)

Veraltet. Aktiviert die minimale Neuerstellung, die bestimmt, ob C++-Quelldateien, die geänderte C++-Klassendefinitionen enthalten (gespeichert in Headerdateien (.h)) neu kompiliert werden müssen.

## <a name="syntax"></a>Syntax

```
/Gm
```

## <a name="remarks"></a>Bemerkungen

**/GM** ist veraltet. Möglicherweise löst Sie keinen Build für bestimmte Arten von Header Dateiänderungen aus. Sie können diese Option in Ihren Projekten problemlos entfernen. Um Buildzeiten zu verbessern, sollten Sie stattdessen vorkompilierte Header und inkrementelle und parallele Buildoptionen verwenden. Eine Liste der veralteten Compileroptionen finden Sie im Abschnitt " **veraltete und entfernte Compileroptionen** " unter [Compileroptionen nach Kategorie aufgelistet](compiler-options-listed-by-category.md).

Der Compiler speichert Abhängigkeitsinformationen zwischen Quelldateien und Klassendefinitionen während der ersten Kompilierung in der .idb-Datei des Projekts. (Abhängigkeitsinformationen teilen mit, welche Quelldatei von welcher Klassendefinition abhängt und in welcher .h-Datei sich die Definition befindet.) Nachfolgende Kompilierungen verwenden die in der .idb-Datei gespeicherten Informationen, um zu bestimmen, ob eine Quelldatei kompiliert werden muss, selbst wenn sie eine geänderte .h-Datei enthält.

> [!NOTE]
> Die minimale Neuerstellung basiert auf Klassendefinitionen, die sich zwischen Includedateien nicht ändern. Klassendefinitionen müssen für ein Projekt global sein (es sollte nur eine Definition für eine bestimmte Klasse vorhanden sein), da die Abhängigkeitsinformationen in der .idb-Datei für das gesamte Projekt erstellt werden. Wenn Sie mehr als eine Definition für eine Klasse in Ihrem Projekt haben, deaktivieren Sie die minimale Neuerstellung.

Da der inkrementelle Linker die in OBJ-Dateien enthaltenen Windows-Metadaten nicht mithilfe der Option [/ZW (Windows-Runtime Kompilierung)](zw-windows-runtime-compilation.md) unterstützt, ist die **/GM** -Option nicht mit **/ZW**kompatibel.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C/ > C++ -** **Code Generierung** aus.

1. Ändern Sie die Eigenschaft minimale Neuerstellung **aktivieren** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
