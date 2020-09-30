---
title: Linkertoolfehler LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: ea1509d846c0bc5a85f0f0252b611dfd38496bcb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506003"
---
# <a name="linker-tools-error-lnk2038"></a>Linkertoolfehler LNK2038

> Konflikt bei "*Name*" erkannt: der Wert "*value_1*" stimmt nicht mit dem Wert "*value_2*" in " *Dateiname. obj* " überein.

Ein Symbolkonflikt wurde vom Linker erkannt. Dieser Fehler zeigt an, dass unterschiedliche Teile einer APP, einschließlich Bibliotheken oder anderer Objektcode, mit denen die APP verknüpft ist, widersprüchliche Definitionen des Symbols verwenden. Das [Detect Konflikt](../../preprocessor/detect-mismatch.md) -Pragma wird verwendet, um solche Symbole zu definieren und ihre in Konflikt stehenden Werte zu erkennen.

## <a name="possible-causes-and-solutions"></a>Mögliche Ursachen und Lösungen

Dieser Fehler kann auftreten, wenn eine Objektdatei im Projekt veraltet ist. Bevor Sie andere Lösungen zur Fehlerbehebung ausprobieren, versuchen Sie, einen bereinigten Build auszuführen, um sicherzustellen, dass die Objektdateien aktuell sind.

Visual Studio definiert die folgenden Symbole, um das Verknüpfen von nicht kompatiblem Code zu verhindern, der Laufzeitfehler oder anderes unerwartetes Verhalten verursachen kann.

- `_MSC_VER` Gibt die Haupt-und neben Versionsnummern des Microsoft C++-Compilers (MSVC) an, der zum Erstellen einer APP oder Bibliothek verwendet wird. Code, der mit einer Version von MSVC kompiliert wird, ist nicht mit Code kompatibel, der mithilfe einer Version kompiliert wurde, die andere Haupt-und neben Versionsnummern aufweist. Weitere Informationen finden Sie unter `_MSC_VER` in [vordefinierten Makros](../../preprocessor/predefined-macros.md).

   Wenn Sie eine Verknüpfung mit einer Bibliothek herstellen, die nicht mit der von Ihnen verwendeten MSVC-Version kompatibel ist, und Sie keine kompatible Version der Bibliothek abrufen oder erstellen können, können Sie das Projekt mit einer früheren Version des Compilers erstellen: Ändern Sie die Eigenschaft **Platt Form Toolset** des Projekts in das frühere Toolset. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Ziel Frameworks und des Platt Form Tool Sets](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` Gibt die Ebene der Sicherheits-und Debuggingfunktionen an, die in der C++-Standard Bibliothek aktiviert sind. Diese Funktionen können die Darstellung bestimmter C++-Standardbibliotheksobjekte ändern. Dadurch werden diese möglicherweise mit solchen Objekten inkompatibel, die andere Sicherheits- und Debugfunktionen verwenden. Weitere Informationen finden Sie unter [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` Gibt die Version der C++-Standard Bibliothek und der C-Laufzeit an, die von einer APP oder Bibliothek verwendet wird. Code, der eine Version der C++-Standardbibliothek oder C-Laufzeit verwendet, ist nicht mit Code kompatibel, der eine andere Version verwendet. Weitere Informationen finden Sie unter [/MD,/MT,/LD (Lauf Zeit Bibliothek verwenden)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` Gibt an, dass Code, der die [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) verwendet, mit Objekten verknüpft ist, die mit einer anderen Einstellung für die [/ZW](../../build/reference/zw-windows-runtime-compilation.md) -Compileroption kompiliert wurden. (**/ZW** unterstützt C++/CX.) Code, der die ppl verwendet oder davon abhängt, muss mit der gleichen **/ZW** -Einstellung kompiliert werden, die im Rest der APP verwendet wird.

Stellen Sie sicher, dass die Werte dieser Symbole für alle Projekte in der Visual Studio-Projektmappe konsistent sind, ebenso wie mit Code und Bibliotheken, mit denen die App verknüpft ist.

## <a name="third-party-library-issues-and-vcpkg"></a>Drittanbieter-Bibliotheks Probleme und vcpkg

Wenn dieser Fehler angezeigt wird, wenn Sie versuchen, eine Drittanbieter Bibliothek als Teil Ihres Builds zu konfigurieren, sollten Sie die Verwendung von [vcpkg](../../build/vcpkg.md), einem C++ Package Manager, zum Installieren und Erstellen der Bibliothek in Erwägung gezogen. vcpkg unterstützt eine große und wachsende [Liste von Bibliotheken von Drittanbietern](https://github.com/Microsoft/vcpkg/tree/master/ports)und legt alle Konfigurations Eigenschaften und Abhängigkeiten, die für erfolgreiche Builds erforderlich sind, als Teil des Projekts fest.

## <a name="see-also"></a>Weitere Informationen

[Fehler und Warnungen der Linkertools](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
