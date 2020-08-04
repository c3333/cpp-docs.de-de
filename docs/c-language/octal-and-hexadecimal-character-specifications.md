---
title: Spezifikationen von Oktal- und Hexadezimalzeichen
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: bcd6eb84503b80b1e38be5d134e7506a0f490891
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229583"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Spezifikationen von Oktal- und Hexadezimalzeichen

Die Sequenz **\\** <em>ooo</em> bedeutet, dass jedes Zeichen im ASCII-Zeichensatz als dreistelliger oktaler Zeichencode angeben werden kann. Der numerische Wert der oktalen ganzen Zahl gibt den Wert des gewünschten Zeichens oder Breitzeichens an.

Ebenso können Sie mit der Sequenz **\x**<em>hhh</em> jedes beliebige ASCII-Zeichen als Hexadezimalzeichencode angeben. Beispielsweise können Sie das Zeichen für die ASCII-Rücktaste als die normale C-Escapesequenz ( **\b**) zuweisen, oder Sie können es als **\010** (oktal) oder **\x008** (hexadezimal) codieren.

Sie können in einer oktalen Escapesequenz nur die Ziffern 0 bis 7 verwenden. Oktale Escapesequenzen können nie mehr als drei Ziffern aufweisen und werden vom ersten Zeichen, das keine oktale Ziffer ist, beendet. Sie müssen zwar nicht alle drei Ziffern verwenden, jedoch mindestens eine. Beispielsweise ist die oktale Darstellung **\10** für das ASCII-Rücktastenzeichen und **\101** für den Buchstaben A, wie in einem ASCII-Diagramm angegeben.

Ebenso müssen Sie mindestens eine Ziffer für eine hexadezimale Escapesequenz verwenden, Sie können jedoch die zweite und dritte Ziffer weglassen. Daher können Sie die hexadezimale Escapesequenz für das Rücktastenzeichen entweder als **\x8**, **\x08** oder **\x008** angeben.

Der Wert der oktalen oder hexadezimalen Escapesequenz muss bei Zeichenkonstanten im Bereich der darstellbaren Werte für den Typ **`unsigned char`** und bei Breitzeichenkonstanten im Bereich darstellbarer Werte für den Typ **`wchar_t`** liegen. Weitere Informationen über Breitzeichenkonstanten erhalten Sie unter [Mehrbyte- und Breitzeichen](../c-language/multibyte-and-wide-characters.md).

Im Gegensatz zu oktalen Escapekonstanten ist die Anzahl von hexadezimalen Stellen in einer Escapesequenz unendlich. Eine hexadezimale Escapesequenz endet am ersten Zeichen, das keine Hexadezimalziffer ist. Da Hexadezimalstellen die Buchstaben **a** bis **f** enthalten, muss sorgfältig vorgegangen werden, um sicherzustellen, dass die Escapesequenz an der gewünschten Stelle beendet wird. Um Verwirrungen zu vermeiden, können Sie oktale oder hexadezimale Zeichendefinitionen in eine Makrodefinition einfügen:

```
#define Bell '\x07'
```

Bei Hexadezimalwerten können Sie die Zeichenfolge unterbrechen, um den richtigen Wert eindeutig anzuzeigen:

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>Siehe auch

[C-Zeichenkonstanten](../c-language/c-character-constants.md)
