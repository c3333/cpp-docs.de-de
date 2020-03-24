---
title: Schwerwiegender Fehler C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: e1255578883c8d2bc278184a02575a0a51ed9b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204957"
---
# <a name="fatal-error-c1001"></a>Schwerwiegender Fehler C1001

> Interner Compilerfehler (compilerdateidatei, Zeilen *Nummer*) *file*

Der Compiler kann keinen korrekten Code für ein Konstrukt generieren, häufig aufgrund der Kombination eines bestimmten Ausdrucks und einer Optimierungs Option oder eines Problems bei der Verarbeitung. Wenn die aufgelistete Compilerdatei ein UTC-oder C2-Pfad Segment enthält, ist dies wahrscheinlich ein Optimierungs Fehler. Wenn die Datei ein cxxfe-oder c1xx Path-Segment aufweist oder msc1. cpp ist, ist dies wahrscheinlich ein Parserfehler. Wenn die Datei "CL. exe" lautet, sind keine weiteren Informationen verfügbar.

Sie können ein Optimierungsproblem häufig beheben, indem Sie eine oder mehrere Optimierungs Optionen entfernen. Um zu ermitteln, welche Option fehlerhaft ist, entfernen Sie die Optionen nacheinander, und kompilieren Sie Sie neu, bis die Fehlermeldung entfernt wird. Die am häufigsten Verantwortlichen Optionen sind [/og (globale Optimierungen)](../../build/reference/og-global-optimizations.md) und [/Oi (intrinsische Funktionen generieren)](../../build/reference/oi-generate-intrinsic-functions.md). Nachdem Sie festgestellt haben, welche Optimierungs Option verantwortlich ist, können Sie Sie um die Funktion deaktivieren, in der der Fehler auftritt, indem Sie das Pragma [optimieren](../../preprocessor/optimize.md) verwenden und die Option für den Rest des Moduls weiterhin verwenden. Weitere Informationen zu Optimierungs Optionen finden Sie unter [bewährte Methoden](../../build/optimization-best-practices.md)für die Optimierung.

Wenn Optimierungen für den Fehler nicht verantwortlich sind, versuchen Sie, die Zeile, in der der Fehler gemeldet wird, oder mehrere Codezeilen, die diese Zeile betreffen, neu zu schreiben. Um den Code so anzuzeigen, wie der Compiler ihn nach der Vorverarbeitung sieht, können Sie die Option [/P (Vorverarbeitung in eine Datei)](../../build/reference/p-preprocess-to-a-file.md) verwenden.

Weitere Informationen dazu, wie Sie die Fehlerquelle isolieren und einen internen Compilerfehler an Microsoft melden, finden Sie unter [melden eines Problems mit dem visuellen C++ Toolset](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).
