---
title: /DYNAMICBASE (Address Space Layout Randomization verwenden)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170058"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Address Space Layout Randomization verwenden)

Gibt an, ob ein ausführbares Image generiert werden soll, das zur Ladezeit nach dem Zufallsprinzip zur Ladezeit neu erstellt werden kann, indem das ASLR (Address Space Layout Anordnung)-Feature von Windows verwendet wird, das erstmals in Windows Vista

## <a name="syntax"></a>Syntax

> **/DynamicBase**[ **: No**]

## <a name="remarks"></a>Bemerkungen

Die Option **/DynamicBase** ändert den Header eines *ausführbaren Images*, eine DLL-oder exe-Datei, um anzugeben, ob die Anwendung zur Ladezeit nach dem Zufallsprinzip neu erstellt werden soll, und ermöglicht die zufällige Zuordnung von virtuellen Adressen, die sich auf den Speicherort des virtuellen Speichers von Heaps, Stapeln und anderen Betriebssystem Zuordnungen auswirkt. Die **/DynamicBase** -Option gilt sowohl für 32-Bit-als auch für 64-Bit-Images. ASLR wird unter Windows Vista und höheren Betriebssystemen unterstützt. Die Option wird von älteren Betriebssystemen ignoriert.

Standardmäßig ist **/DynamicBase** aktiviert. Verwenden Sie **/DynamicBase: No**, um diese Option zu deaktivieren. Die **/DynamicBase** -Option ist erforderlich, damit die [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) -Option wirksam wird.

### <a name="to-set-this-linker-option-in-visual-studio"></a>So legen Sie diese Linkeroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Eigenschaften** von > **Linker** > **erweitert** aus.

1. Ändern Sie die Eigenschaft **zufällige Basisadresse** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Weitere Informationen

- [MSVC-Linkerreferenz](linking.md)
- [MSVC-Linkeroptionen](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Schutzmaßnahmen für Windows ISV-Software](https://msdn.microsoft.com/library/bb430720.aspx)
