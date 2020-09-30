---
title: '&lt;charcharv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: c9dfb8e18a8f7fd367ec4f6b52b1a0af74b3f939
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507705"
---
# <a name="ltcharconvgt"></a>&lt;charcharv&gt;

Konvertieren Sie eine Zeichenfolge schnell in einen ganzzahligen oder Gleit Komma Wert, und umgekehrt.
Eine Möglichkeit, diese Bibliothek zu verwenden, ist das Schreiben und Roundtrip von Gleit Komma Werten in JSON-und Textdateien.

Die Konvertierungs Funktionen werden auf die Leistung optimiert und unterstützen auch das kürzeste Roundtrip-Verhalten. Das kürzeste Roundtrip-Verhalten bedeutet, dass bei der Konvertierung einer Zahl in Zeichen nur ausreichend Genauigkeit ausgegeben wird, um das Wiederherstellen der ursprünglichen Anzahl bei der Wiederherstellung dieser Zeichen in einen Gleit Komma Wert zu ermöglichen. Diese Funktion wird von keiner anderen CRT-oder STL-Funktion bereitstellt.

Die Verwendung der Bibliothek bietet folgende Vorteile `<charconv>` :

- Die Sequenz von Zeichen, die einen numerischen Wert darstellen, muss nicht auf Null enden. Ebenso, wenn eine Zahl in Zeichen konvertiert wird, wird das Ergebnis nicht mit Null beendet.
- Konvertierungs Funktionen weisen keinen Arbeitsspeicher zu. Sie besitzen den Puffer in allen Fällen.
- Konvertierungs Funktionen lösen nicht aus. Sie geben eine-Struktur zurück, die Fehlerinformationen enthält.
- Konvertierungen sind nicht im Lauf Zeit-Rundungs Modus sensibel
- Konvertierungen sind nicht Gebiets Schema fähig. Sie drucken und analysieren immer Dezimalstellen als '. ' niemals als ', ' für Gebiets Schemas, die Kommas verwenden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<charconv>

**Namespace:** std

/Std: c++ 17 (oder höher) ist erforderlich.

## <a name="members"></a>Members

### <a name="types"></a>Typen

| Type | Beschreibung |
|-|:-|
| [chars_format](chars-format-class.md) | Gibt den Formatierungstyp an, z. b. Scientific, Hex usw. |
| [from_chars_result](from-chars-result-structure.md) | Enthält das Ergebnis einer `from_chars` Konvertierung. |
| [to_chars_result](to-chars-result-structure.md) | Enthält das Ergebnis einer `to_chars` Konvertierung. |

### <a name="functions"></a>Functions

| Funktion | Beschreibung |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | Konvertieren Sie Zeichen in eine Ganzzahl, float oder Double. |
| [to_chars](charconv-functions.md#to_chars)| Konvertiert eine Ganzzahl, float oder Double in Zeichen. |

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](cpp-standard-library-header-files.md)
