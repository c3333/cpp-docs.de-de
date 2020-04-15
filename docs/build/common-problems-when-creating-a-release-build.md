---
title: Häufig auftretende Probleme beim Erstellen eines Releasebuilds
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328864"
---
# <a name="common-problems-when-creating-a-release-build"></a>Häufig auftretende Probleme beim Erstellen eines Releasebuilds

Während der Entwicklung erstellen und testen Sie in der Regel mit einem Debugbuild Ihres Projekts. Wenn Sie dann Ihre Anwendung für einen Releasebuild erstellen, erhalten Sie möglicherweise eine Zugriffsverletzung.

Die folgende Liste zeigt die primären Unterschiede zwischen einem Debug- und einem Release-Build (nondebug). Es gibt noch andere Unterschiede, aber im Folgenden sind die primären Unterschiede, die dazu führen würden, dass eine Anwendung in einem Release-Build fehlschlägt, wenn sie in einem Debugbuild funktioniert.

- [Heap-Layout](#_core_heap_layout)

- [Kompilierung](#_core_compilation)

- [Pointer-Unterstützung](#_core_pointer_support)

- [Optimierungen](#_core_optimizations)

Informationen zum Abfangen von Releasebuildfehlern in Debugbuilds finden Sie in der Compileroption [/GZ (Catch Release-Build Errors in Debug Build).](reference/gz-enable-stack-frame-run-time-error-checking.md)

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Heap-Layout

Heap-Layout wird die Ursache für etwa neunzig Prozent der offensichtlichen Probleme sein, wenn eine Anwendung im Debuggen arbeitet, aber nicht veröffentlicht wird.

Wenn Sie das Projekt für das Debuggen erstellen, verwenden Sie den Debugspeicherzuweisungser. Dies bedeutet, dass alle Speicherzuweisungen Schutzbytes um sie herum platziert haben. Diese Wächterbytes erkennen eine Speicherüberschreibung. Da sich das Heaplayout zwischen Release- und Debugversionen unterscheidet, verursacht ein Speicherüberschreiben möglicherweise keine Probleme in einem Debugbuild, hat jedoch möglicherweise katastrophale Auswirkungen in einem Releasebuild.

Weitere Informationen finden Sie unter [Überprüfen auf Speicherüberschreiben](checking-for-memory-overwrites.md) und [Verwenden des Debugbuilds zum Überprüfen auf Speicherüberschreibung](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Kompilierung

Viele der MFC-Makros und ein Großteil der MFC-Implementierung ändert sich, wenn Sie für die Veröffentlichung erstellen. Insbesondere wird das ASSERT-Makro in einem Releasebuild zu nichts ausgewertet, sodass keiner der in ASSERTs gefundenen Codes ausgeführt wird. Weitere Informationen finden Sie unter Prüfen von [ASSERT-Anweisungen](using-verify-instead-of-assert.md).

Einige Funktionen sind für eine höhere Geschwindigkeit im Release-Build vorgesehen. Optimierungen werden in der Regel in einem Releasebuild aktiviert. Es wird auch ein anderer Speicherallokator verwendet.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Pointer-Unterstützung

Das Fehlen von Debuginformationen entfernt den Abstand aus der Anwendung. In einem Releasebuild haben streunende Zeiger eine größere Chance, auf nicht initialisierten Speicher zu verweisen, anstatt auf Debuginformationen zu verweisen.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optimierungen

Je nach Art bestimmter Codesegmente kann der Optimierende Compiler unerwarteten Code generieren. Dies ist die am wenigsten wahrscheinliche Ursache für Release-Build-Probleme, aber es tritt gelegentlich auf. Eine Lösung finden Sie unter [Optimieren Ihres Codes](optimizing-your-code.md).

## <a name="see-also"></a>Siehe auch

[Releasebuilds](release-builds.md)<br/>
[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
