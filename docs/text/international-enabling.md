---
title: Aktivierung der Internationalen Programmierung
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375804"
---
# <a name="international-enabling"></a>Aktivierung der Internationalen Programmierung

Der traditionelle C- und C++-Code macht Annahmen über Zeichen- und Zeichenfolgenmanipulationen, die für internationale Anwendungen nicht gut funktionieren. Obwohl sowohl MFC als auch die Laufzeitbibliothek Unicode oder MBCS unterstützen, müssen Sie noch arbeiten. In diesem Abschnitt wird die Bedeutung von "international enabling" in Visual C++ erläutert:

- Sowohl Unicode als auch MBCS werden über portable Datentypen in MFC-Funktionsparameterlisten und Rückgabetypen aktiviert. Diese Typen sind bedingt definiert, je nachdem, ob Der `_UNICODE` Build das `_MBCS` Symbol oder das Symbol definiert (d. h. DBCS). Je nachdem, welche dieser beiden Symbole Ihr Build definiert, werden verschiedene Varianten der MFC-Bibliotheken automatisch mit Ihrer Anwendung verknüpft.

- Klassenbibliothekscode verwendet portable Laufzeitfunktionen und andere Mittel, um das korrekte Unicode- oder MBCS-Verhalten sicherzustellen.

- Sie müssen immer noch bestimmte Arten von Internationalisierungsaufgaben in Ihrem Code behandeln:

  - Verwenden Sie dieselben tragbaren Laufzeitfunktionen, mit denen MFC unter beiden Umgebungen portierbar ist.

  - Machen Sie Literalzeichenfolgen und Zeichen `_T` unter beiden Umgebungen unter Verwendung des Makros portierbar. Weitere Informationen finden Sie unter [Generic-Text Mappings in tchar.h](../text/generic-text-mappings-in-tchar-h.md).

  - Beachten Sie Vorsichtsmaßnahmen beim Analysieren von Zeichenfolgen unter MBCS. Diese Vorsichtsmaßnahmen sind unter Unicode nicht erforderlich. Weitere Informationen finden Sie unter [MBCS-Programmiertipps](../text/mbcs-programming-tips.md).

  - Achten Sie darauf, wenn Sie ANSI-Zeichen (8-Bit) und Unicode (16-Bit) in Ihrer Anwendung mischen. Es ist möglich, ANSI-Zeichen in einigen Teilen Ihres Programms und Unicode-Zeichen in anderen zu verwenden, aber Sie können sie nicht in derselben Zeichenfolge mischen.

  - Verwenden Sie Zeichenfolgen in Ihrer Anwendung nicht mit Hardcode. Machen Sie sie stattdessen STRINGTABLE-Ressourcen, indem Sie sie der .rc-Datei der Anwendung hinzufügen. Ihre Anwendung kann dann lokalisiert werden, ohne dass Quellcodeänderungen oder Neukompilierung erforderlich sind. Weitere Informationen zu STRINGTABLE-Ressourcen finden Sie unter [String Editor](../windows/string-editor.md).

> [!NOTE]
> Europäische und MBCS-Zeichensätze haben einige Zeichen, z. B. akzentuierte Buchstaben, deren Zeichencodes größer als 0x80 sind. Da der größte Teil des Codes signierte Zeichen verwendet, werden diese Zeichen größer als 0x80 beim Konvertieren in **in int**signiert. Dies ist ein Problem für die Arrayindizierung, da die zeichenverlängerten Zeichen, die negativ sind, außerhalb des Arrays indizieren. Sprachen, die MBCS verwenden, z. B. Japanisch, sind ebenfalls einzigartig. Da ein Zeichen aus 1 oder 2 Bytes bestehen kann, sollten Sie immer beide Bytes gleichzeitig bearbeiten.

## <a name="see-also"></a>Siehe auch

[Unicode und MBCS](../text/unicode-and-mbcs.md)<br/>
[Strategien für die Internationalisierung](../text/internationalization-strategies.md)
