---
title: /HEAP (Heapgröße festlegen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439521"
---
# <a name="heap-set-heap-size"></a>/HEAP (Heapgröße festlegen)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Bemerkungen

Die Option/Heap legt die Größe des Heaps in Bytes fest. Diese Option ist nur für die Verwendung beim Aufbau einer exe-Datei vorgesehen.

Das *Reserve* Argument gibt die gesamte Heap Zuordnung im virtuellen Speicher an. Die Standard Heap Größe beträgt 1 MB. Der Linker rundet den angegebenen Wert auf die nächsten 4 Bytes auf.

Das optionale `commit`-Argument gibt die Menge an physischem Speicher an, die gleichzeitig belegt werden soll. Die Zusicherung von virtuellem Speicher bewirkt die Belegung von Speicher in der Auslagerungsdatei. Ein höherer `commit` Wert spart Zeit, wenn die Anwendung mehr Heap Speicher benötigt, erhöht jedoch die Arbeitsspeicher Anforderungen und möglicherweise die Startzeit.

Geben Sie die *Reserve* -und `commit` Werte in der Notation Decimal oder C-Language an.

Diese Funktionalität ist auch über eine Modul Definitionsdatei mit [HEAPSIZE](heapsize.md)verfügbar.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **Linker**.

1. Klicken Sie auf die Eigenschaften Seite **System** .

1. Ändern Sie die Eigenschaft **Heap-Commitgröße** .

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Prüfen Sie <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
