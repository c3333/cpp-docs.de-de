---
title: Unicode und MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375756"
---
# <a name="unicode-and-mbcs"></a>Unicode und MBCS

Die MFC-Bibliothek (Microsoft Foundation Classes), die C-Laufzeitbibliothek für Visual C++ und die Visual C++-Entwicklungsumgebung unterstützen Sie bei der internationalen Programmierung. Sie bieten:

- Unterstützung für den Unicode-Standard unter Windows. Unicode ist der aktuelle Standard und sollte möglichst verwendet werden.

   Unicode ist ein 16-Bit-Verfahren für die Zeichencodierung, in dem die Zeichensätze aller Sprachen codiert werden können. Alle ASCII-Zeichen sind in Unicode als erweiterte Zeichen enthalten.

- Unterstützung für den Doppelbyte-Zeichensatz (Double-Byte Character Set, DBCS), einer Variante des Mehrbyte-Zeichensatzes (MBCS) auf allen Plattformen

   DBCS-Zeichen bestehen aus einem oder zwei Bytes. Bestimmte Bytebereiche sind zur Verwendung als führende Bytes reserviert. Ein führendes Byte zeigt an, dass es selbst und das nächste Byte (das nachfolgende Byte) ein einziges, aus zwei Bytes bestehendes Zeichen darstellen. Es ist wichtig, stets zu wissen, bei welchen Bytes es sich um führende Bytes handelt. In einem bestimmten Mehrbyte-Zeichensatz liegen die führenden Bytes ebenso wie die nachfolgenden Bytes innerhalb eines bestimmten Bereichs. Wenn sich diese Bereiche überschneiden, muss unter Umständen anhand des Kontexts ermittelt werden, ob ein bestimmtes Byte als führendes oder als nachfolgendes Byte verwendet wird.

- Unterstützung für Tools, die die MBCS-Programmierung von Anwendungen für internationale Märkte vereinfachen

   Bei der Ausführung unter einer MBCS-aktivierten Version des Betriebssystems Windows 2000 ist das Visual C++-Entwicklungssystem, einschließlich des integrierten Quellcode-Editors, Debuggers und der Befehlszeilentools, vollständig MBCS-aktiviert. Weitere Informationen finden Sie unter [MBCS-Support in Visual C++](../text/mbcs-support-in-visual-cpp.md).

> [!NOTE]
> In der vorliegenden Dokumentation umschreibt der Begriff MBCS jede Nicht-Unicode-Unterstützung für Mehrbytezeichen. In Visual C++ ist MBCS gleichbedeutend mit DBCS. Zeichensätze, die "breiter" als zwei Byte sind, werden nicht unterstützt.

Der ASCII-Zeichensatz ist definitionsgemäß eine Teilmenge jedes Mehrbyte-Zeichensatzes. In vielen Multibyte-Zeichensätzen sind die Zeichen im Bereich von 0x00 bis 0x7F mit den gleichwertigen Zeichen des ASCII-Zeichensatzes identisch. Das ein Byte lange NULL-Zeichen ('\0') in ASCII- und MBCS-Zeichenfolgen hat z. B. den Wert 0x00 und steht für das abschließende NULL-Zeichen.

## <a name="see-also"></a>Siehe auch

[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[Aktivierung der Internationalen Programmierung](../text/international-enabling.md)
