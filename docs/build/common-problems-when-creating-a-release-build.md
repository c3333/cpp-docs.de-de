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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328864"
---
# <a name="common-problems-when-creating-a-release-build"></a>Häufig auftretende Probleme beim Erstellen eines Releasebuilds

Während der Entwicklung verwenden Sie in der Regel einen Debugbuild des Projekts zum Erstellen und Testen. Wenn Sie Ihre Anwendung dann für einen Releasebuild erstellen, wird möglicherweise ein Zugriffsverstoß zurückgegeben.

In der nachstehenden Liste sind die Hauptunterschiede zwischen einem Debug- und einem Releasebuild (nicht für das Debugging) aufgeführt. Es gibt zwar weitere Unterschiede, die folgenden sind jedoch die wichtigsten, die dazu führen können, dass eine Anwendung in einem Releasebuild fehlschlägt, obwohl sie im Debugbuild funktioniert hat.

- [Heaplayout](#_core_heap_layout)

- [Kompilierung](#_core_compilation)

- [Zeigerunterstützung](#_core_pointer_support)

- [Optimierungen](#_core_optimizations)

Weitere Informationen zum Abfangen von Releasebuildfehlern in Debugbuilds finden Sie unter [/GZ (Aktivieren der Fehlerüberprüfung zur Laufzeit für den Stapelrahmen)](reference/gz-enable-stack-frame-run-time-error-checking.md).

## <a name="heap-layout"></a><a name="_core_heap_layout"></a> Heaplayout

Das Heaplayout ist die Ursache von ungefähr 90 % der auftretenden Probleme, wenn eine Anwendung im Debugbuild funktioniert, aber nicht im Releasebuild.

Wenn Sie Ihr Projekt für das Debuggen erstellen, verwenden Sie die Debugspeicherzuweisung. Dies bedeutet, dass der Speicher um alle Speicherbelegungen herum mit Schutzbytes belegt wird. Diese Schutzbytes erkennen eine Speicherüberschreibung. Da sich das Heaplayout zwischen der Release- und der Debugversion unterscheidet, verursacht eine Speicherüberschreibung möglicherweise keine Probleme in einem Debugbuild, hat dann jedoch schwerwiegende Auswirkungen in einem Releasebuild.

Weitere Informationen finden Sie unter [Überprüfen auf Speicherüberschreibungen](checking-for-memory-overwrites.md) und [Verwenden des Debugbuilds für die Überprüfung auf Speicherüberschreibungen](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a> Kompilierung

Viele der MFC-Makros und der Großteil der MFC-Implementierung ändern sich, wenn Sie einen Releasebuild erstellen. Das ASSERT-Makro wird in einem Releasebuild beispielsweise zu nichts ausgewertet. Es wird also kein Code ausgeführt, der in einem ASSERT-Makro enthalten ist. Weitere Informationen finden Sie unter [Verwenden von VERIFY anstelle von ASSERT](using-verify-instead-of-assert.md).

Einige Funktionen sind Inlinefunktionen, um die Erstellung des Releasebuilds zu beschleunigen. Optimierungen sind in Releasebuilds im Allgemeinen aktiviert. Es wird außerdem eine andere Speicherzuweisung verwendet.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a> Zeigerunterstützung

Durch den Mangel an Debugginginformationen wird die Auffüllung Ihrer Anwendung entfernt. In einem Releasebuild ist die Wahrscheinlichkeit bei hängenden Zeigern höher, dass diese auf nicht initialisierten Speicher anstatt auf Debuginformationen zeigen.

## <a name="optimizations"></a><a name="_core_optimizations"></a> Optimierungen

Je nach der Beschaffenheit bestimmter Codesegmente kann der Optimierungscompiler unerwarteten Code generieren. Diese Ursache ist diejenige mit der geringsten Wahrscheinlichkeit, kommt jedoch gelegentlich vor. Weitere Informationen zur Lösung finden Sie unter [Optimieren Ihres Codes](optimizing-your-code.md).

## <a name="see-also"></a>Siehe auch

[Releasebuilds](release-builds.md)<br/>
[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
