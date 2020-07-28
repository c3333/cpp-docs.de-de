---
title: scanf-Breitenangabe
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 781e292140babd61fbcde77cefcb917736b17cc3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188738"
---
# <a name="scanf-width-specification"></a>`scanf`breiten Angabe

Diese Informationen gelten für die Interpretation von Formatzeichenfolgen in der `scanf`-Funktionsreihe, einschließlich der sicheren Versionen wie `scanf_s`. Diese Funktionen nehmen in der Regel an, dass der Eingabestream in eine Folge von Token unterteilt ist. Token werden durch Leerzeichen (Leerzeichen, Tabstopp oder Zeilen Vorstrich) oder für numerische Typen durch das natürliche Ende eines numerischen Datentyps getrennt, wie durch das erste Zeichen angegeben, das nicht in numerischen Text konvertiert werden kann. Mit den Breitenangaben können Sie jedoch festlegen, dass die Analyse der Eingabe vor dem natürlichen Ende eines Tokens beendet wird.

Die *Width* -Angabe besteht aus Zeichen zwischen dem `%` und dem typfeldspezifizierer, der eine positive ganze Zahl, die als *Width* -Feld bezeichnet wird, und mindestens einem Zeichen, das die Größe des Felds angibt, enthalten kann, das auch als Modifizierer des Feldtyps betrachtet werden kann, z. b. ein Hinweis darauf, ob der ganzzahlige Typ **`short`** oder ist **`long`** . Solche Zeichen werden als das Größenpräfix bezeichnet.

## <a name="the-width-field"></a>Das Feld "Breite"

Das *Width* -Feld ist eine positive ganze Dezimalzahl, die die maximale Anzahl von Zeichen steuert, die für dieses Feld gelesen werden sollen. Es werden nicht mehr als die *breiten* Zeichen konvertiert und im entsprechenden gespeichert `argument` . Weniger als *breiten* Zeichen werden möglicherweise gelesen, wenn ein Leerzeichen oder ein Zeichen, das nicht gemäß dem angegebenen Format konvertiert werden kann, vor dem Erreichen der *Breite* auftritt.

Die Width-Spezifikation ist unabhängig und unterscheidet sich vom Puffergrößen Argument, das von den sicheren Versionen dieser Funktionen benötigt wird (z.b., `scanf_s` `wscanf_s` usw.). Im folgenden Beispiel beträgt die Breitenangabe 20 und gibt somit an, dass bis zu 20 Zeichen aus dem Eingabestream gelesen werden. Die Pufferlänge beträgt 21 und schließt somit die möglichen 20 Zeichen mit dem Null-Abschlusszeichen ein:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Wenn das Feld *Width* nicht verwendet wird, `scanf_s` versucht, das gesamte Token in der Zeichenfolge zu lesen. Wenn die angegebene Größe nicht groß genug für das gesamte Token ist, wird nichts in die Ziel Zeichenfolge geschrieben. Wenn das *Width* -Feld angegeben wird, werden die ersten *breiten* Zeichen im Token zusammen mit dem NULL-Terminator in die Ziel Zeichenfolge geschrieben.

## <a name="the-size-prefix"></a>Das Größen Präfix

Die optionalen Präfixe **h**, **HH**, **l**, **ll**, **I64**und **l** geben die Größe des an `argument` (lang oder kurz, Einzel Byte Zeichen oder breit Zeichen, je nach Typzeichen, das Sie ändern). Diese Formatangabezeichen werden in `scanf`- oder `wscanf`-Funktionen mit Typzeichen für die Interpretation von Argumenten verwendet, wie in der folgenden Tabelle dargestellt. Das Typpräfix **I64** ist eine Microsoft-Erweiterung und ist nicht mit dem Standard-C kompatibel. Die Typzeichen und ihre Bedeutungen werden in der Tabelle "Typzeichen für scanf-Funktionen" in [ `scanf` tyfeldzeichen](../c-runtime-library/scanf-type-field-characters.md)beschrieben.

> [!NOTE]
> Die **h**-, **l**-und **l** -Präfixe sind Microsoft-Erweiterungen, wenn Sie mit Daten vom Typ verwendet werden **`char`** .

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Größen Präfixe für `scanf` und `wscanf` formattypspezifizierer

|Angabe von|Präfix|Mit Typspezifizierer|
|----------------|----------------|-------------------------|
|**`double`**|**l**|**e**, **E**, **f**, **g** oder **G**|
|**`long double`**(identisch mit **`double`** )|**Int**|**e**, **E**, **f**, **g** oder **G**|
|**`long int`**|**l**|**d**, **i**, **o**, **x** oder **X**|
|**`long unsigned int`**|**l**|**n**|
|**`long long`**|**Pfeifen**|**d**, **i**, **o**, **x** oder **X**|
|**`short int`**|**h**|**d**, **i**, **o**, **x** oder **X**|
|**`short unsigned int`**|**h**|**n**|
|**`char`**|**hh**|**d**, **i**, **o**, **x** oder **X**|
|**`unsigned char`**|**hh**|**n**|
|**`int64`**|**I64**|**d**, **i**, **o**, **u**, **x** oder **X**|
|Einzelbytezeichen mit `scanf`|**h**|**c** oder **c**|
|Einzelbytezeichen mit `wscanf`|**h**|**c** oder **c**|
|Breitzeichen mit `scanf`|**l**|**c** oder **c**|
|Breitzeichen mit `wscanf`|**l**|**c**oder **c**|
|Einzel Byte-Zeichenfolge mit`scanf`|**h**|**s** oder **S**|
|Einzel Byte-Zeichenfolge mit`wscanf`|**h**|**s** oder **S**|
|Zeichenfolge mit breit Zeichen mit`scanf`|**l**|**s** oder **S**|
|Zeichenfolge mit breit Zeichen mit`wscanf`|**l**|**s** oder **S**|

Die folgenden Beispiele verwenden die Präfixe **h** und **l** mit `scanf_s`- und `wscanf_s`-Funktionen:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Lassen Sie beim Verwenden einer nicht sicheren Funktion in der `scanf`-Reihe den Größenparameter aus, der die Pufferlänge des vorherigen Arguments angibt.

## <a name="reading-undelimited-strings"></a>Lesen von Zeichen folgen ohne Trennzeichen

Zum Lesen von Zeichen folgen, die nicht durch Leerzeichen getrennt sind, kann ein Zeichensatz in eckigen Klammern ( **`[ ]`** ) durch das **s** Zeichen (Zeichen folgen) ersetzt werden. Der Zeichensatz in Klammern wird als *Steuer Zeichenfolge*bezeichnet. Das entsprechende Eingabefeld wird bis zum ersten Zeichen gelesen, das nicht in der Steuer Zeichenfolge angezeigt wird. Wenn das erste Zeichen im Satz ein Caretzeichen ( **`^`** ) ist, wird der Effekt umgekehrt: das Eingabefeld wird bis zum ersten Zeichen gelesen, das im restlichen Zeichensatz angezeigt wird.

Beide **% [a-z]** und **% [z-a]** werden als äquivalent zu **% [abcde... z]**. Es handelt `scanf` sich um eine gängige Funktionserweiterung, ist jedoch nicht für Standard-C erforderlich.

## <a name="reading-unterminated-strings"></a>Nicht abgeschlossener Zeichen folgen werden gelesen.

Um eine Zeichenfolge zu speichern, ohne ein abschließendes NULL-Zeichen (' \ 0 ') zu speichern, verwenden Sie die-Spezifikation `%Nc` , wobei *N* eine ganze Dezimalzahl ist. In diesem Fall gibt das **c**-Typzeichen an, dass das Argument ein Zeiger auf ein Zeichenarray ist. Die nächsten *N* -Zeichen werden aus dem Eingabestream in den angegebenen Speicherort gelesen, und es wird kein NULL-Zeichen (' \ 0 ') angefügt. Wenn *N* nicht angegeben wird, ist der Standardwert 1.

## <a name="when-scanf-stops-reading-a-field"></a>Wenn das `scanf` Lesen eines Felds beendet

Die `scanf`-Funktion überprüft Zeichen für Zeichen jedes Eingabefeld. Möglicherweise wird das Lesen eines bestimmten Eingabe Felds beendet, bevor es aus einem der folgenden Gründe ein Leerzeichen erreicht:

- Die angegebene Breite wurde erreicht.

- Das nächste Zeichen kann nicht wie angegeben konvertiert werden.

- Das nächste Zeichen steht in Konflikt mit einem Zeichen in der Steuer Zeichenfolge, mit dem es abgeglichen werden soll.

- Das nächste Zeichen kann nicht in einem angegebenen Zeichensatz angezeigt werden.

Wenn die `scanf`-Funktion, unabhängig von dem Grund, das Lesen eines Eingabefelds beendet, beginnt das nächste Eingabefeld beim ersten ungelesenen Zeichen. Das widersprüchliche Zeichen, falls vorhanden, gilt als ungelesen. Es ist das erste Zeichen des nächsten Eingabe Felds oder das erste Zeichen in nachfolgenden Lesevorgängen des Eingabestreams.

## <a name="see-also"></a>Weitere Informationen

[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Formatspezifikations Felder: `scanf` -und- `wscanf` Funktionen](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[`scanf`Typfeldzeichen](../c-runtime-library/scanf-type-field-characters.md)<br/>
