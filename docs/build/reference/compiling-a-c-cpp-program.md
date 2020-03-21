---
title: 'MSVC-cC++ /Compilerreferenz: Visual Studio'
description: MSVC-Compilertoolset-Optionen.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077376"
---
# <a name="compiling-a-cc-project"></a>Kompilieren eines C/C++ Projekts

C- C++ und Compileroptionen können entweder in der Visual Studio-IDE oder in der Befehlszeile festgelegt werden.

## <a name="in-visual-studio"></a>In Visual Studio

Sie können die Compileroptionen für jedes Projekt im Dialogfeld Visual Studio- **Eigenschaften Seiten** festlegen. Wählen Sie im linken Bereich **Konfigurations Eigenschaften**, **C/C++**  aus, und wählen Sie dann die Kategorie Compileroptionen aus. In den Themen zu den einzelnen Compileroptionen wird erläutert, wo die jeweilige Option in der Entwicklungsumgebung zu finden ist und wie sie eingestellt werden kann. Eine komplette Liste finden Sie unter [MSVC-Compileroptionen](compiler-options.md) .

## <a name="from-the-command-line"></a>Über die Befehlszeile

Sie können die Optionen für den Compiler (CL.exe) an folgenden Stellen festlegen:

- [In der Befehlszeile](compiler-command-line-syntax.md)

- [In Befehls Dateien](cl-command-files.md)

- [In der CL-Umgebungsvariablen](cl-environment-variables.md)

Die in der CL-Umgebungsvariablen festgelegten Optionen werden bei jedem Aufrufen von CL.EXE verwendet. Wenn eine Befehlsdatei in der CL-Umgebungsvariablen oder in der Befehlszeile angegeben wird, werden die in der Befehlsdatei festgelegten Optionen verwendet. Anders als in der Befehlszeile oder in der CL-Umgebungsvariablen können Sie in einer Befehlsdatei mehrzeilige Optionen und Dateinamen verwenden.

Compileroptionen werden "von links nach rechts" verarbeitet. Wird ein Konflikt erkannt, überwiegt die letzte Option (ganz rechts). Die CL-Umgebungsvariable wird vor der Befehlszeile verarbeitet. Sollte es also zu Konflikten zwischen CL und der Befehlszeile kommen, so hat die Befehlszeile Vorrang.

## <a name="additional-compiler-topics"></a>Weitere Themen zum Compiler

- [MSVC-Compileroptionen](compiler-options.md)

- [Vorkompilierte Headerdateien](../creating-precompiled-header-files.md)

- [CL: Starten des Linkers](cl-invokes-the-linker.md)

Weitere Informationen zum Auswählen des compilerhosts und der Zielarchitektur finden Sie unter [ C++ Configure Projects for 64-Bit, x64 Targets](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Weitere Informationen

[Referenz zur C/C++-Erstellung](c-cpp-building-reference.md)
