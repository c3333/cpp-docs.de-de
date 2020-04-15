---
title: Importieren und Exportieren von Inlinefunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328514"
---
# <a name="importing-and-exporting-inline-functions"></a>Importieren und Exportieren von Inlinefunktionen

Importierte Funktionen können als Inline definiert werden. Der Effekt entspricht in etwa der Definition einer Standardfunktion inline; Aufrufe der Funktion werden in Inlinecode erweitert, ähnlich wie ein Makro. Dies ist hauptsächlich nützlich, um C++-Klassen in einer DLL zu unterstützen, die einige ihrer Memberfunktionen aus Effizienzgründen inlineisieren können.

Ein Merkmal einer importierten Inlinefunktion besteht darin, dass Sie ihre Adresse in C++ verwenden können. Der Compiler gibt die Adresse der Kopie der Inlinefunktion zurück, die sich in der DLL befindet. Ein weiteres Merkmal importierter Inlinefunktionen besteht darin, dass Sie statische lokale Daten der importierten Funktion im Gegensatz zu globalen importierten Daten initialisieren können.

> [!CAUTION]
> Sie sollten beim Bereitstellen importierter Inlinefunktionen Vorsicht walten lassen, da sie die Möglichkeit von Versionskonflikten verursachen können. Eine Inline-Funktion wird in den Anwendungscode erweitert. Wenn Sie die Funktion später neu schreiben, wird sie daher nur aktualisiert, wenn die Anwendung selbst neu kompiliert wird. (Normalerweise können DLL-Funktionen aktualisiert werden, ohne die Anwendungen, die sie verwenden, neu zu erstellen.)

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Exportieren aus einer DLL](exporting-from-a-dll.md)

- [Exportieren aus einer DLL mit . DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Bestimmen, welche Exportmethode verwendet werden soll](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Siehe auch

[Importieren und Exportieren](importing-and-exporting.md)
