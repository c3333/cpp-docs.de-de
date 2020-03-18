---
title: 'Formatangabefelder: scanf- und wscanf-Funktionen'
ms.date: 11/04/2016
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 025d4c164d3afe1ca6b05c1c8e76441109cbc4ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438365"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Formatangabefelder: scanf- und wscanf-Funktionen

Die hier aufgeführten Informationen gelten für die gesamte `scanf`-Funktionsfamilie, einschließlich der sicheren Versionen. Sie beschreiben die Symbole, mithilfe derer `scanf`-Funktionen angewiesen werden, wie sie Eingabedatenströme in Werten analysieren, die in Programmvariablen eingefügt werden sollen; so z.B der Eingabestrom `stdin` für `scanf`.

Eine Formatspezifikation hat folgendes Format:

`%`[`*`] [[width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)

Das Argument `format` gibt die Interpretation einer Eingabe an und kann mindestens eines der folgenden Zeichen enthalten:

- Leerzeichen: Leerschritt (' '), Tabstopp ('\t') oder Zeilenvorschub ('\n'). Durch ein Leerzeichen liest `scanf` alle aufeinander folgenden Leerzeichen in der Eingabe bis zum nächsten Nichtleerzeichen, allerdings ohne zu speichern. Ein Leerzeichen im Format entspricht einer beliebigen Zahl (einschließlich 0) und einer Kombination von Leerzeichen in der Eingabe.

- Nichtleerzeichen, außer das Prozentzeichen (`%`). Durch ein Nichtleerzeichen liest `scanf` ein entsprechendes Nichtleerzeichen, ohne es zu speichern. Wenn das nächste Zeichen im Eingabestream nicht übereinstimmt, wird `scanf` beendet.

- Durch das Prozentzeichen (`%`) eingeführte Formatspezifikationen. Durch eine Formatspezifikation liest `scanf` Zeichen in der Eingabe und konvertiert sie in die Werte eines angegebenen Typs. Der Wert wird einem Argument in der Argumentliste zugewiesen.

Das Format wird von links nach rechts gelesen. Zeichen außerhalb von Formatspezifikationen müssen der Zeichensequenz im Eingabestream entsprechen. Die übereinstimmenden Zeichen im Eingabestream werden geprüft, aber nicht gespeichert. Wenn ein Zeichen im Eingabestream mit der Spezifikation in Konflikt steht, wird `scanf` beendet und das Zeichen verbleibt im Eingabestream, als ob es nicht gelesen worden wäre.

Wenn die erste Formatspezifikation gefunden wird, wird der Wert des ersten Eingabefelds gemäß dieser Spezifikation konvertiert und an dem Speicherort gespeichert, der vom ersten `argument` angegebenen wurde. Durch die zweite Formatspezifikation wird das zweite Eingabefeld konvertiert und im zweiten `argument` gespeichert. So geht es weiter bis zum Ende der Zeichenfolge.

Ein Eingabefeld ist definiert als alle Zeichen bis zu dem ersten Leerzeichen (Leerzeichen, Tabstopp oder Zeilenvorschub), als alle Zeichen bis zum ersten Zeichen, das entsprechend der Formatspezifikation nicht konvertiert werden kann, oder als alle Zeichen bis zur maximalen Feldbreite (falls angegeben). Wenn zu viele Argumente für die angegebenen Spezifikationen vorhanden sind, werden die zusätzlichen Argumente zwar ausgewertet, aber ignoriert. Die Ergebnisse sind unvorhersehbar, wenn nicht genügend Argumente für die Formatspezifikation vorhanden sind.

Jedes Feld der Formatspezifikation ist entweder ein einzelnes Zeichen oder eine Zahl, das bzw. die eine bestimmte Formatoption darstellt. Das `type`-Zeichen, das nach dem letzten optionalen Formatfeld angezeigt wird, bestimmt, ob das Eingabefeld als Zeichen, Zeichenfolge oder als Zahl interpretiert wird.

Die einfachste Formatspezifikation enthält nur das Prozentzeichen und ein `type`-Zeichen (z.B. `%s`). Wenn ein Prozentzeichen (`%`) von einem als Formatsteuerungszeichen bedeutungslosen Zeichen gefolgt wird, werden dieses Zeichen und die folgenden (bis zum nächsten Prozentzeichen) wie eine normale Zeichensequenz, d.h. als Zeichensequenz, die der Eingabe entsprechen muss, behandelt. Verwenden Sie z.B. `%%`, um anzugeben, dass ein Prozentzeichen Eingabe darstellen soll.

Ein Sternchen (`*`), gefolgt von einem Prozentzeichen, unterdrückt die Zuweisung des nächsten Eingabefelds, das als Feld des angegebenen Typs interpretiert wird. Das Feld wird überprüft, aber nicht gespeichert.

Die sicheren Versionen der `_s`-Funktionsfamilie (mit dem Suffix `scanf`) erfordern, dass ein Puffergrößenparameter unmittelbar nach jedem Parameter des Typs `c`, `C`, `s`, `S` oder `[` übergeben wird. Weitere Informationen zu den sicheren Versionen der `scanf`-Funktionsfamilie finden Sie unter [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Weitere Informationen

[scanf-Breitenangabe](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf-Typenfeldzeichen](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
