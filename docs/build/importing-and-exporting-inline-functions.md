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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328514"
---
# <a name="importing-and-exporting-inline-functions"></a>Importieren und Exportieren von Inlinefunktionen

Importierte Funktionen können als Inlinefunktionen definiert werden. Der Effekt ist ungefähr identisch mit der Definition einer standardmäßigen Inlinefunktion. Aufrufe der Funktion werden ähnlich wie bei einem Makro in Inlinecode erweitert. Dies ist in erster Linie nützlich, um C++-Klassen in einer DLL zu unterstützen, die möglicherweise einige ihrer Memberfunktionen aus Effizienzgründen inline erstellen möchten.

Ein Feature einer importierten Inlinefunktion besteht darin, dass Sie deren Adresse in C++ übernehmen können. Der Compiler gibt die Adresse der Kopie der Inlinefunktion zurück, die in der DLL verbleibt. Ein weiteres Feature importierter Inlinefunktionen ist, dass Sie statische lokale Daten der importierten Funktion im Gegensatz zu global importierten Daten initialisieren können.

> [!CAUTION]
> Beim Bereitstellen importierter Inlinefunktionen müssen Sie vorsichtig vorgehen, da sie die Möglichkeit von Versionskonflikten schaffen können. Eine Inlinefunktion wird in den Anwendungscode erweitert. Wenn Sie deshalb die Funktion später neu schreiben, wird sie erst dann aktualisiert, wenn die Anwendung selbst neu kompiliert wird. (In der Regel können DLL-Funktionen ohne Neuerstellung der Anwendungen aktualisiert werden, die diese verwenden.)

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL](exporting-from-a-dll.md)

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von „AFX_EXT_CLASS“](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Siehe auch

[Importieren und Exportieren](importing-and-exporting.md)
