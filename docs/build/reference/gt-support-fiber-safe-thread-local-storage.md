---
title: /GT (Fibersicheren lokalen Threadspeicher unterstützen)
description: Die MSVC-Compileroption/gt ermöglicht sichere Optimierungen für Thread lokale Speicherdaten.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 1b1d9f6514cec8c3d247f86be063f2ac3e0dfe72
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180811"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>`/GT`(Fiber-sicheren lokalen Thread Speicher unterstützen)

Unterstützt die Fiber-Sicherheit für Daten, die mit statischem lokalen Thread Speicher zugewiesen werden, d. h. mit zugeordneten Daten `__declspec(thread)` .

## <a name="syntax"></a>Syntax

> **`/GT`**

## <a name="remarks"></a>Bemerkungen

Auf Daten, die mit deklariert werden, `__declspec(thread)` wird durch ein TLS-Array (Thread-Local Storage) verwiesen. Das TLS-Array ist ein Array von Adressen, die vom System für jeden Thread verwaltet werden. Jede Adresse in diesem Array gibt den Speicherort der Thread lokalen Speicherdaten an.

Eine Fiber ist ein Lightweight-Objekt, das aus einem Stapel und einem Register Kontext besteht und für verschiedene Threads geplant werden kann. Eine Fiber kann in jedem Thread ausgeführt werden. Da eine Fiber möglicherweise ausgetauscht und später in einem anderen Thread neu gestartet wird, kann der Compiler die Adresse des TLS-Arrays nicht zwischenspeichern oder Sie als allgemeinen Teil Ausdruck für einen Funktions Aufruhe optimieren. **`/GT`** verhindert solche Optimierungen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Optimierung** aus.

1. Ändern Sie die Eigenschaft **Fiber-sichere Optimierungen aktivieren** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
