---
title: Text und Zeichenfolgen in Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 80b7139996fddc82b206828d4a036922fa1446d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167601"
---
# <a name="text-and-strings-in-visual-c"></a>Text und Zeichenfolgen in Visual C++

Ein wichtiger Aspekt bei der Entwicklung von Anwendungen für internationale Märkte ist die korrekte Darstellung lokaler Zeichensätze. Mit dem ASCII-Zeichensatz werden Zeichen im Bereich zwischen 0 x 00 und 0 x 7 F definiert. Von anderen Zeichensätzen (hauptsächlich europäischer Herkunft) werden wie beim ASCII-Zeichensatz die Zeichen innerhalb des Bereichs von 0 x 00 bis 0 x 7 F definiert; zusätzlich wird ein erweiterter Zeichensatz im Bereich von 0 x 80 bis 0 x FF definiert. Daher ist ein Einzelbyte-Zeichensatz (Single-Byte Character Set, SBCS) mit 8 Bits ausreichend, um den ASCII-Zeichensatz sowie viele andere Zeichensätze für europäische Sprachen darzustellen. Einige außereuropäische Zeichensätze, z. B. das japanische Kanji, enthalten jedoch so viele Zeichen, dass sie nicht mehr in Einzelbytecodierung dargestellt werden können. Sie müssen daher mit einem Mehrbyte-Zeichensatz (Multibyte Character Set, MBCS) codiert werden.

## <a name="in-this-section"></a>In diesem Abschnitt

[Unicode und MBCS](../text/unicode-and-mbcs.md)<br/>
Beschreibt die Visual C++-Unterstützung für Unicode und MBCS-Programmierung.

[Unterstützung für Unicode](../text/support-for-unicode.md)<br/>
Beschreibt Unicode, eine Spezifikation zur Unterstützung sämtlicher Zeichensätze, einschließlich Zeichensätzen, zu deren Darstellung mehr als ein Byte erforderlich ist.

[Unterstützung für Multibyte-Zeichensätze (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Beschreibt MBCS, eine Alternative zu Unicode für die Unterstützung von Zeichensätzen, die nicht mit einem Byte pro Zeichen dargestellt werden können, z. B. Japanisch und Chinesisch.

[Zuordnungen für generischen Text in tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Enthält Microsoft-spezifische Zuordnungen für generischen Text für viele Datentypen, Routinen und andere Objekte.

[Vorgehensweise: Konvertieren zwischen verschiedenen Zeichenfolgentypen](../text/how-to-convert-between-various-string-types.md)<br/>
Veranschaulicht, wie verschiedene Visual C++-Zeichenfolgentypen in andere Zeichenfolgen konvertiert werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
Beschreibt die internationale Unterstützung in der C-Laufzeitbibliothek.

[Internationale Beispiele](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
Enthält Verknüpfungen mit Beispielen, die die Internationalisierung in Visual C++ demonstrieren.

[Zeichenfolgen in Sprach- und Länder-/Regionseinstellungen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Stellt die Zeichenfolgen in Sprach- und Länder-/Regionseinstellungen in der C-Laufzeitbibliothek bereit.
