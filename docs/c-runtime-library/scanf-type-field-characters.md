---
title: scanf-Typenfeldzeichen
ms.date: 11/04/2016
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: dbc6142a87bee00b130589fef5ab92a44f189864
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444753"
---
# <a name="scanf-type-field-characters"></a>scanf-Typenfeldzeichen

Die folgenden Informationen gelten für die `scanf` -Funktionsreihe, einschließlich der sicheren Versionen wie `scanf_s`.

Das `type` -Zeichen ist das einzige Formatpflichtfeld und erscheint nach allen optionalen Feldern. Das `type` -Zeichen bestimmt, ob das zugeordnete Argument als Zeichen, Zeichenfolge oder Zahl interpretiert wird.

### <a name="type-characters-for-scanf-functions"></a>Typzeichen für scanf-Funktionen

|Zeichen|Erwarteter Typ der Eingabe|Typ des Arguments|Größenargument in der sicheren Version?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Zeichen Gibt bei Verwendung mit `scanf` -Funktionen ein Einzelbytezeichen und bei Verwendung mit `wscanf` -Funktionen ein Breitzeichen an. In der Regel übersprungene Leerzeichen werden gelesen, wenn `c` angegeben ist. Verwenden Sie `%1s` zum Lesen des nächsten Einzelbytezeichens, das kein Leerzeichen ist, und `%1ws` zum Lesen des nächsten Breitzeichens, das kein Leerzeichen ist.|Zeiger auf `char` bei Verwendung mit `scanf` -Funktionen, Zeiger auf `wchar_t` bei Verwendung mit `wscanf` -Funktionen.|Erforderlich. Größe enthält keinen Platz für ein Null-Abschlusszeichen.|
|`C`|Umgekehrtes Größenzeichen Gibt bei Verwendung mit `scanf` -Funktionen Breitzeichen und bei Verwendung mit `wscanf` -Funktionen Einzelbytezeichen an. In der Regel übersprungene Leerzeichen werden gelesen, wenn `C` angegeben ist. Verwenden Sie `%1s` zum Lesen des nächsten Einzelbytezeichens, das kein Leerzeichen ist, und `%1ws` zum Lesen des nächsten Breitzeichens, das kein Leerzeichen ist.|Zeiger auf `wchar_t` bei Verwendung mit `scanf` -Funktionen, Zeiger auf `char` bei Verwendung mit `wscanf` -Funktionen.|Erforderlich. Größenargument enthält keinen Platz für ein Null-Abschlusszeichen.|
|`d`|Ganze Dezimalzahl|Zeiger auf `int`|Nein.|
|`i`|Eine ganze Zahl Hexadezimal, wenn die Eingabezeichenfolge mit "0x" oder "0X" beginnt, oktal, wenn die Zeichenfolge mit "0" beginnt, andernfalls dezimal.|Zeiger auf `int`|Nein.|
|`o`|Oktale ganze Zahl|Zeiger auf `int`|Nein.|
|`p`|Eine Zeigeradresse in hexadezimalen Ziffern. Die maximale Anzahl von gelesenen Ziffern hängt von der Größe eines Zeigers (32 oder 64 Bit) ab, die wiederum von der Computerarchitektur abhängt. „0x“ oder „0X“ wird als Präfix akzeptiert.|Zeiger auf `void*`|Nein.|
|`u`|Ganze Dezimalzahl ohne Vorzeichen|Zeiger auf `unsigned int`|Nein.|
|`x`|Ganze Hexadezimalzahl|Zeiger auf `int`|Nein.|
|`e`, `E`, `f`, `F`, `g`, `G`|Gleitkommawert, der aus optionalem Vorzeichen (+ oder -), Dezimalstellen mit Dezimaltrennzeichen und einem optionalen Exponenten („e“ oder „E“) besteht, gefolgt von einer ganzen Zahl (optional mit Vorzeichen).|Zeiger auf `float`|Nein.|
|`a`, `A`|Ein Gleitkommawert, der aus einer Reihe von einer oder mehreren hexadezimalen Ziffern besteht, die ein optionales Dezimaltrennzeichen und einen Exponenten („p“ oder „P“) enthalten, gefolgt von einem Dezimalwert.|Zeiger auf `float`|Nein.|
|`n`|Kein Eingabe aus dem Stream oder Puffer gelesen.|Zeiger auf `int`, in dem die Anzahl der aus dem Stream oder Puffer erfolgreich gelesenen Zeichen bis zu diesem Zeitpunkt im aktuellen Aufruf von `scanf` -Funktionen oder `wscanf` -Funktionen gespeichert ist.|Nein.|
|`s`|Zeichenfolge bis zum ersten Leerzeichen (Leerzeichen, Tabstopps oder Zeilenumbruch) Um Zeichenfolgen zu lesen, die nicht durch Leerzeichen getrennt sind, verwenden Sie eckige Klammern (`[ ]`), wie dies in [scanf Width Specification](../c-runtime-library/scanf-width-specification.md).|Steht bei Verwendung mit `scanf` -Funktionen für ein Einzelbyte-Zeichenarray und bei Verwendung mit `wscanf` -Funktionen für ein Breitzeichenarray. In jedem Fall muss das Zeichenarray groß genug für das Eingabefeld und einen automatisch angefügten abschließenden NULL-Wert sein.|Erforderlich. Größe einschließlich Platz für einen Nullterminator.|
|`S`|Umgekehrte Größenzeichenfolge bis zum ersten Leerzeichen (Leerzeichen, Tabstopps oder Zeilenumbruch) Um Zeichenfolgen zu lesen, die nicht durch Leerzeichen getrennt sind, verwenden Sie eckige Klammern (`[ ]`), wie dies in [scanf Width Specification](../c-runtime-library/scanf-width-specification.md).|Steht bei Verwendung mit `scanf`-Funktionen für ein Einzelbyte-Zeichenarray und bei Verwendung mit `wscanf`-Funktionen für ein Breitzeichenarray. In jedem Fall muss das Zeichenarray groß genug für das Eingabefeld und einen automatisch angefügten abschließenden NULL-Wert sein.|Erforderlich. Größe einschließlich Platz für einen Nullterminator.|

Die Größenargumente müssen ggf. in der Parameterliste unmittelbar nach dem Argument übergeben werden, für das sie gelten. Beispielsweise folgender Code:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

Liest eine Zeichenfolge mit einer maximalen Länge von 10 in `string1`und eine Zeichenfolge mit einer maximalen Länge von 8 in `string2`. Die Puffergrößen müssen mindestens um eins größer sein als der Wert für die Breitenangaben, da noch Platz für das Nullabschlusszeichen reserviert werden muss.

Die Formatzeichenfolge kann Einzelbyte- oder Breitzeicheneingaben unabhängig davon bewältigen, ob die Einzelbyte- oder Breitzeichenversion der Funktion verwendet wird. Verwenden Sie deshalb zum Lesen von Einzelbyte- oder Breitzeichen mit `scanf` - und `wscanf` -Funktionen Formatbezeichner wie im Folgenden beschrieben:

|Zum Lesen von Zeichen als|Verwenden Sie diese Funktion|Mit diesen Formatbezeichnern|
|--------------------------|-----------------------|----------------------------------|
|Einzelbyte|`scanf` -Funktionen|`c`, `hc` oder `hC`|
|Einzelbyte|`wscanf` -Funktionen|`C`, `hc` oder `hC`|
|Breit|`wscanf` -Funktionen|`c`, `lc` oder `lC`|
|Breit|`scanf` -Funktionen|`C`, `lc` oder `lC`|

Verwenden Sie zum Überprüfen von Zeichenfolgen mit `scanf` -Funktionen und `wscanf` -Funktionen die oben dargestellte Tabelle mit den Typformatbezeichnern `s` und `S` anstelle von `c` und `C`.

## <a name="see-also"></a>Weitere Informationen

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
