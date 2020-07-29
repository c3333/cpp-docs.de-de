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
ms.openlocfilehash: ff0fb4102a0453b900b5b406739492a9420a5b07
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228088"
---
# <a name="international-enabling"></a>Aktivierung der Internationalen Programmierung

Der herkömmliche C-und C++-Code trifft Annahmen über Zeichen-und Zeichen folgen Bearbeitung, die für internationale Anwendungen nicht geeignet sind. MFC und die Lauf Zeit Bibliothek unterstützen zwar Unicode oder MBCS, aber es gibt noch weitere Möglichkeiten. In diesem Abschnitt wird die Bedeutung der "internationalen Aktivierung" in Visual C++ erläutert:

- Sowohl Unicode als auch MBCS werden mithilfe von portablen Datentypen in MFC-Funktionsparameter Listen und Rückgabe Typen aktiviert. Diese Typen werden bedingt entsprechend definiert, abhängig davon, ob Ihr Build das Symbol `_UNICODE` oder das Symbol definiert `_MBCS` (d.h. DBCS). Unterschiedliche Varianten der MFC-Bibliotheken werden automatisch mit Ihrer Anwendung verknüpft, je nachdem, welche dieser beiden Symbole der Build definiert.

- Der Klassen Bibliotheks Code verwendet Portable Lauf Zeitfunktionen und andere Methoden, um das korrekte Verhalten von Unicode oder MBCS sicherzustellen.

- Sie müssen nach wie vor bestimmte Arten von Internationalisierungs Aufgaben in Ihrem Code behandeln:

  - Verwenden Sie dieselben portablen Lauf Zeitfunktionen, die MFC in beiden Umgebungen portabel machen.

  - Verwenden Sie das-Makro, um Literalzeichenfolgen und-Zeichen in beiden Umgebungen portabel `_T` Weitere Informationen finden Sie unter Zuordnungen für [generischen Text in Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

  - Treffen Sie Vorsichtsmaßnahmen bei der Verarbeitung von Zeichen folgen unter MBCS. Diese Vorsichtsmaßnahmen sind unter Unicode nicht erforderlich. Weitere Informationen finden Sie unter [Tipps für die MBCS-Programmierung](../text/mbcs-programming-tips.md).

  - Achten Sie darauf, dass Sie ANSI-(8-Bit) und Unicode-Zeichen (16-Bit) in der Anwendung mischen. Es ist möglich, ANSI-Zeichen in einigen Teilen des Programms und Unicode-Zeichen in anderen zu verwenden, aber Sie können Sie nicht in derselben Zeichenfolge mischen.

  - Zeichen folgen in Ihrer Anwendung dürfen nicht hart codiert werden. Machen Sie Sie stattdessen STRINGTABLE-Ressourcen, indem Sie Sie der RC-Datei der Anwendung hinzufügen. Die Anwendung kann dann lokalisiert werden, ohne dass Quell Codeänderungen oder eine erneute Kompilierung erforderlich sind. Weitere Informationen zu STRINGTABLE-Ressourcen finden Sie unter Zeichen folgen- [Editor](../windows/string-editor.md).

> [!NOTE]
> Europäische und MBCS-Zeichensätze enthalten einige Zeichen, z. b. Zeichen, die größer sind als 0x80. Da in den meisten Codes signierte Zeichen verwendet werden, werden diese Zeichen größer als 0x80 bei der Konvertierung in bei konvertiert **`int`** . Dies ist ein Problem bei der Array Indizierung, da die als negativ signiertes Vorzeichen außerhalb des Arrays indiziert werden. Sprachen, die MBCS verwenden, wie z. b. Japanisch, sind ebenfalls eindeutig. Da ein Zeichen möglicherweise aus 1 oder 2 Bytes besteht, sollten Sie immer beide Bytes gleichzeitig bearbeiten.

## <a name="see-also"></a>Siehe auch

[Unicode und MBCS](../text/unicode-and-mbcs.md)<br/>
[Internationalisierungsstrategien](../text/internationalization-strategies.md)
