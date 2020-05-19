---
title: Escapesequenzen
ms.date: 11/04/2016
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "form feed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\n escape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 5de0b5f1a73fcfb6ea0325bea3247ebe4c85d411
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375821"
---
# <a name="escape-sequences"></a>Escapesequenzen

Zeichenkombinationen, die aus einem umgekehrten Schrägstrich ( **\\** ), gefolgt von einem Buchstaben oder einer Zahlenkombination, bestehen, werden „Escapesequenzen“ genannt. Um ein Zeilenumbruchzeichen, ein einfaches Anführungszeichen oder bestimmte andere Zeichen in einer Zeichenkonstante darzustellen, müssen Sie Escapesequenzen verwenden. Eine Escapesequenz wird als ein einzelnes Zeichen betrachtet und ist daher als Zeichenkonstante gültig.

Escapesequenzen werden in der Regel verwendet, um Aktionen, wie etwa Wagenrückläufe und Tabstopps, auf Terminals und Druckern anzugeben. Sie werden auch verwendet, um Literaldarstellungen von nicht druckbaren Zeichen und Zeichen, die normalerweise eine besondere Bedeutung haben, bereitzustellen, z.B. von doppelten Anführungszeichen ( **"** ). Die folgende Tabelle zeigt die ANSI-Escapesequenzen und was sie darstellen.

Beachten Sie, dass das Fragezeichen, dem ein umgekehrter Schrägstrich ( **\\?** ) vorangestellt ist, ein literales Fragezeichen angibt, wenn die Zeichenfolge als Trigraph fehlinterpretiert werden würde. Weitere Informationen finden Sie unter [Trigraphen](../c-language/trigraphs.md).

### <a name="escape-sequences"></a>Escapesequenzen

|Escapesequenz|Repräsentiert|
|---------------------|----------------|
|**\a**|Glocke (Warnung)|
|**\b**|Rückschritt|
|**\f**|Seitenvorschub|
|**\n**|Zeilenwechsel|
|**\r**|Wagenrücklauf|
|**\t**|Horizontaler Tabulator|
|**\v**|Vertikaler Tabulator|
|**\\'**|Einfaches Anführungszeichen|
|**\\"**|Doppeltes Anführungszeichen|
|**\\\\**|Umgekehrter Schrägstrich|
|**\\?**|Literales Fragezeichen|
|**\\** *ooo*|ASCII-Zeichen in der Oktalnotation|
|**\x** *hh*|ASCII-Zeichen in der Hexadezimalnotation|
|**\x** *hhhh*|Unicode-Zeichen in der Hexadezimalnotation, wenn diese Escapesequenz in einer Konstante mit Breitzeichen oder in einem Unicode-Zeichenfolgenliteral verwendet wird.<br /><br /> Beispielsweise `WCHAR f = L'\x4e00'` oder `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Microsoft-spezifisch**

Wenn einem Zeichen ein umgekehrter Schrägstrich vorangestellt ist, der nicht in der Tabelle enthalten ist, behandelt der Compiler das nicht definierte Zeichen als das Zeichen selbst. Beispielsweise wird `\c` als `c` behandelt.

**Ende Microsoft-spezifisch**

Mithilfe von Escapesequenzen können Sie nicht grafische Steuerzeichen an ein Anzeigegerät senden. Beispielsweise wird das ESC-Zeichen ( **\033**) häufig als erstes Zeichen eines Steuerungsbefehls für ein Terminal oder einen Drucker verwendet. Einige Escapesequenzen sind gerätespezifisch. Die Escapesequenzen für vertikale Tabstopps und Seitenvorschübe ( **\v** und **\f**) beeinflussen beispielsweise die Bildschirmausgabe nicht, sondern sie führen die entsprechenden Druckervorgänge aus.

Sie können den umgekehrten Schrägstrich ( **\\** ) auch als Fortsetzungszeichen verwenden. Wenn ein Zeilenumbruchzeichen (entsprechend dem Drücken der EINGABETASTE) direkt auf den umgekehrten Schrägstrich folgt, ignoriert der Compiler den umgekehrten Schrägstrich und das Zeilenumbruchzeichen und behandelt die nächste Zeile als Teil der vorherigen Zeile. Dies wird in erster Linie für Präprozessordefinitionen verwendet, die länger als eine einzige Zeile sind. Zum Beispiel:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Siehe auch

[C-Zeichenkonstanten](../c-language/c-character-constants.md)
