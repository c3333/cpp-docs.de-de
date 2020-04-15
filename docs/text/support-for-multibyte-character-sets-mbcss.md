---
title: Unterstützung von Mehrbyte-Zeichensätzen (MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 0b43168ec4331e99dea7e939b097674cc880804e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375768"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Unterstützung von Mehrbyte-Zeichensätzen (MBCS)

Mehrbyte-Zeichensätze (MBCS) sind ein älterer Ansatz, mit dem die erforderliche Unterstützung von Zeichensätzen sichergestellt wird, die nicht mit einem Byte pro Zeichen dargestellt werden können, z. B. Japanisch und Chinesisch. Wenn Sie Neuentwicklungen ausführen, sollten Sie Unicode für alle Textzeichenfolgen außer Systemzeichenfolgen verwenden, die nicht für die Endbenutzer sichtbar sind. MBCS ist eine ältere Technologie und wird nicht für Neuentwicklungen empfohlen.

Bei den gängigsten MBCS-Implementierungen handelt es sich um Doppelbyte-Zeichensätze (DBCS). Visual C++ im Allgemeinen und MFC im Besonderen sind vollständig DBCS-aktiviert.

Beispiele finden Sie in den MFC-Quellcodedateien.

Für Plattformen, die in Ländern mit umfangreichen Zeichensätzen verwendet werden, stellt MBCS die beste Alternative zu Unicode dar. MFC unterstützt MBCS durch Verwendung internationalisierbarer Datentypen und C-Laufzeitfunktionen. Es empfiehlt sich, im Code ebenso vorzugehen.

Unter MBCS werden Zeichen in ein oder zwei Bytes codiert. In zwei Bytes breiten Zeichen zeigt das erste oder führende Byte an, dass es selbst und das nächste Byte als ein einziges Zeichen zu interpretieren sind. Das erste Byte stammt aus einem Bereich mit Codes, die zur Verwendung als führende Bytes reserviert sind. Welche Bytebereiche als führende Bytes verwendet werden können, hängt von der jeweils verwendeten Codepage ab. Von der japanischen Codepage 932 wird z. B. der Bereich von 0 x 81 bis 0 x 9 F für führende Bytes verwendet, während von der koreanischen Codepage 949 hierfür ein anderer Bereich verwendet wird.

Beachten Sie bei der MBCS-Programmierung alle der nachfolgenden Punkte.

MBCS-Zeichen in der Umgebung MBCS-Zeichen können in Zeichenfolgen wie Datei- und Verzeichnisnamen angezeigt werden.

### <a name="editing-operations"></a>Bearbeitungsvorgänge

Bearbeitungsvorgänge in MBCS-Anwendungen sollten auf Zeichen und nicht auf Bytes basieren. Die Einsiedebank sollte kein Zeichen teilen, die **Rechte Pfeiltaste** sollte ein Zeichen rechts bewegen usw. **Löschen** sollte ein Zeichen löschen; **Rückgängig** sollte es wieder einfügen.

### <a name="string-handling"></a>Zeichenfolgenbehandlung

In Anwendungen, die MBCS verwenden, wirft die Behandlung von Zeichenfolgen besondere Probleme auf. Da dieselbe Zeichenfolge breite und normale Zeichen enthalten kann, sind unbedingt Überprüfungen auf führende Bytes vorzusehen.

### <a name="run-time-library-support"></a>Unterstützung der Laufzeitbibliothek

Die C-Laufzeitbibliothek und MFC unterstützen die Einzelbyte-, MBCS- und Unicode-Programmierung. Single-Byte-Zeichenfolgen werden `str` mit der Reihe von Laufzeitfunktionen verarbeitet, `_mbs` MBCS-Zeichenfolgen werden mit `wcs` entsprechenden Funktionen und Unicode-Zeichenfolgen mit entsprechenden Funktionen verarbeitet. In Implementierungen von Memberfunktionen der MFC-Klasse werden portable Laufzeitfunktionen verwendet, die unter den richtigen Voraussetzungen der normalen `str`-Funktionsreihe, den MBCS-Funktionen oder den Unicode-Funktionen zugeordnet werden, wie unter "MBCS/Unicode-Portabilität" beschrieben.

### <a name="mbcsunicode-portability"></a>MBCS/Unicode-Portabilität

Mithilfe der Headerdatei tchar.h können Sie Single-Byte-, MBCS- und Unicode-Anwendungen aus denselben Quellen erstellen. Tchar.h definiert Makros mit *_tcs* , `str`die `_mbs`ggf. , oder `wcs` Funktionen zuordnen. Definieren Sie zur Erstellung von MBCS das `_MBCS`-Symbol. Um Unicode zu erstellen, definieren Sie das Symbol `_UNICODE`. Standardmäßig wird `_UNICODE` für MFC-Anwendungen definiert. Weitere Informationen finden Sie unter [Generic-Text Mappings in tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
> Das Verhalten ist nicht `_UNICODE` definiert, wenn Sie beide und `_MBCS`definieren.

Von den Headerdateien Mbctype.h und Mbstring.h werden MBCS-spezifische Funktionen und Makros definiert, die in bestimmten Fällen benötigt werden. Mit `_ismbblead` können Sie z. B. ermitteln, ob ein bestimmtes Byte einer Zeichenfolge ein führendes Byte ist.

Für die internationale Portabilität codieren Sie Ihr Programm mit [Unicode-](../text/support-for-unicode.md) oder Multibyte-Zeichensätzen (MBCSs).

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [MBCS im Programm aktivieren](../text/international-enabling.md)

- [Sowohl Unicode als auch MBCS im Programm aktivieren](../text/internationalization-strategies.md)

- [MBCS verwenden, um ein internationales Programm zu erstellen](../text/mbcs-programming-tips.md)

- [Eine Zusammenfassung zur MBCS-Programmierung ansehen](../text/mbcs-programming-tips.md)

- [Etwas über die Zuordnungen generischer Texte bei Byte-breiter Portabilität erfahren](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Siehe auch

[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[MBCS-Unterstützung in Visual C++](../text/mbcs-support-in-visual-cpp.md)
