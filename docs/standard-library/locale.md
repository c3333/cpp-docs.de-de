---
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: ae008ef45e8a6bb57505432f2c931a768d4c8ea4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224798"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

Definiert Klassen Vorlagen und Funktionen, mit denen C++-Programme verschiedene kulturelle Konventionen in Bezug auf Darstellung und Formatierung von numerischen, monetären und Kalenderdaten Kapseln und bearbeiten können, einschließlich der Internationalisierungsunterstützung für Zeichen Klassifizierung und Zeichen folgen Sortierung.

## <a name="syntax"></a>Syntax

```cpp
#include <locale>
```

### <a name="functions"></a>Functions

|Funktion|Beschreibung|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Testet, ob ein bestimmtes Facet in einem angegebenen Gebietsschema gespeichert wird.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Testet, ob ein Element in einem Gebietsschema ein alphabetisches oder ein numerisches Zeichen ist.|
|[isalpha](../standard-library/locale-functions.md#isalpha)|Testet, ob ein Element in einem Gebietsschema ein alphabetisches Zeichen ist.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Testet, ob ein Element in einem Gebietsschema ein Steuerzeichen ist.|
|[isdigit](../standard-library/locale-functions.md#isdigit)|Testet, ob ein Element in einem Gebietsschema ein numerisches Zeichen ist.|
|[isgraph](../standard-library/locale-functions.md#isgraph)|Testet, ob ein Element in einem Gebietsschema ein alphanumerisches Zeichen oder ein Interpunktionszeichen ist.|
|[islower](../standard-library/locale-functions.md#islower)|Testet, ob ein Element in einem Gebietsschema kleingeschrieben ist.|
|[isprint](../standard-library/locale-functions.md#isprint)|Testet, ob ein Element in einem Gebietsschema ein druckbares Zeichen ist.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Testet, ob ein Element in einem Gebietsschema ein Interpunktionszeichen ist.|
|[isspace](../standard-library/locale-functions.md#isspace)|Testet, ob ein Element in einem Gebietsschema ein Leerzeichen ist.|
|[isupper](../standard-library/locale-functions.md#isupper)|Testet, ob ein Element in einem Gebietsschema großgeschrieben ist.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Testet, ob ein Element in einem Gebietsschema ein Zeichen ist, mit dem eine Hexadezimalzahl dargestellt wird.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Konvertiert ein Zeichen in einen Kleinbuchstaben.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Konvertiert ein Zeichen in einen Großbuchstaben.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Gibt einen Verweis auf ein Facet eines angegebenen Typs zurück, der in einem Gebietsschema gespeichert wird.|

### <a name="classes"></a>Klassen

|Klasse|Beschreibung|
|-|-|
|[Codecvt](../standard-library/codecvt-class.md)|Eine Klassen Vorlage, die einen Facette bereitstellt, der für die Konvertierung zwischen internen und externen Zeichen Codierungen verwendet wird.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Eine Basisklasse für die Codecvt-Klasse, die verwendet wird, um einen Enumerationstyp zu definieren, der als bezeichnet wird `result` , der als Rückgabetyp für die facetmember-Funktionen verwendet wird, um das Ergebnis einer Konvertierung anzugeben.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als COLLATE-Facette eines bestimmten Gebiets Schemas fungieren kann. Dies ermöglicht das Abrufen von Informationen, die für einen kulturellen Bereich in Bezug auf Konvertierungen spezifisch sind|
|[COLLATE](../standard-library/collate-class.md)|Eine COLLATE-Klassen Vorlage, die eine Facette bereitstellt, die Zeichen folgen-Sortier Konventionen behandelt.|
|[collate_byname](../standard-library/collate-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als COLLATE-Facette eines bestimmten Gebiets Schemas fungieren kann. Dies ermöglicht das Abrufen von Informationen, die für einen Kulturbereich in Bezug auf Zeichen folgen Sortier Konventionen gelten.|
|[ctype](../standard-library/ctype-class.md)|Eine Klassen Vorlage, die eine Facette bereitstellt, die zum Klassifizieren von Zeichen, Konvertieren von Groß-und Kleinbuchstaben und zwischen dem systemeigenen Zeichensatz und dem vom Gebiets Schema verwendeten Zeichensatz verwendet wird.|
|[CType\<char>](../standard-library/ctype-char-class.md)|Eine Klasse, bei der es sich um eine explizite Spezialisierung der Klassen Vorlage `ctype<CharType>` zum Eingeben von handelt **`char`** , die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um verschiedene Eigenschaften eines Zeichens vom Typ zu bezeichnen **`char`** .|
|[ctype_base](../standard-library/ctype-base-class.md)|Eine Basisklasse für die ctype-Klasse, die verwendet wird, um die Enumerationstypen zu definieren, mit denen Zeichen entweder einzeln oder innerhalb eines gesamten Bereichs klassifiziert oder getestet werden.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als CType-Facette eines bestimmten Gebiets Schemas fungieren kann und die Klassifizierung von Zeichen und die Konvertierung von Zeichen zwischen Groß-/Kleinschreibung und systemeigenen und Gebiets Schema spezifischen Zeichensätzen ermöglicht.|
|[locale](../standard-library/locale-class.md)|Eine Klasse, die ein Gebietsschemaobjekt beschreibt, das kulturspezifische Informationen als einen Satz von Facets kapselt, die zusammen eine bestimmte lokalisierte Umgebung definieren.|
|[messages](../standard-library/messages-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um lokalisierte Nachrichten aus einem Katalog mit internationalisierten Nachrichten für ein bestimmtes Gebiets Schema abzurufen.|
|[messages_base](../standard-library/messages-base-class.md)|Eine Basisklasse, die einen- **`int`** Typ für den Katalog von Meldungen beschreibt.|
|[messages_byname](../standard-library/messages-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als Nachrichten Facette eines bestimmten Gebiets Schemas fungieren kann und den Abruf lokalisierter Nachrichten ermöglicht.|
|[money_base](../standard-library/money-base-class.md)|Eine Basisklasse für die ctype-Klasse, die verwendet wird, um die Enumerationstypen zu definieren, mit denen Zeichen entweder einzeln oder innerhalb eines gesamten Bereichs klassifiziert oder getestet werden.|
|[money_get](../standard-library/money-get-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Sequenzen vom Typ **CharType** in monetäre Werte zu steuern.|
|[money_put](../standard-library/money-put-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Währungswerten in Sequenzen vom Typ **CharType**zu steuern.|
|[moneypunct](../standard-library/moneypunct-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um die Sequenzen vom Typ **CharType** zu beschreiben, die zur Darstellung eines monetären Eingabe Felds oder eines monetären Ausgabe Felds verwendet werden.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als Moneypunct-Facette eines bestimmten Gebiets Schemas fungieren kann und die Formatierung von monetären Eingabe-oder Ausgabe Feldern ermöglicht.|
|[num_get](../standard-library/num-get-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Sequenzen vom Typ **CharType** in numerische Werte zu steuern.|
|[num_put](../standard-library/num-put-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema Aspekt dienen kann, um Konvertierungen numerischer Werte in Sequenzen vom Typ **CharType**zu steuern.|
|[numpunct](../standard-library/numpunct-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als lokaler Aspekt dienen kann, um die Sequenzen vom Typ **CharType** zu beschreiben, mit denen Informationen zur Formatierung und Interpunktions Zeichen von numerischen und booleschen Ausdrücken dargestellt werden.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als Moneypunct-Facette eines bestimmten Gebiets Schemas dienen kann und die Formatierung und Interpunktions Zeichen von numerischen und booleschen Ausdrücken ermöglicht.|
|[time_base](../standard-library/time-base-class.md)|Eine Klasse, die als Basisklasse für Facetten von Klassen Vorlagen Time_get dient und nur den enumerierten Typ dateorder und mehrere Konstanten dieses Typs definiert.|
|[time_get](../standard-library/time-get-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Sequenzen vom Typ **CharType** in Time-Werte zu steuern.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette vom Typ Time_get fungieren kann \<**CharType**, **InputIterator**> .|
|[time_put](../standard-library/time-put-class.md)|Eine Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette dienen kann, um Konvertierungen von Zeitwerten in Sequenzen vom Typ **CharType**zu steuern.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Eine abgeleitete Klassen Vorlage, die ein Objekt beschreibt, das als Gebiets Schema-Facette vom Typ fungieren kann `time_put` \<**CharType**, **OutputIterator**> .|
|[Wbuffer_convert-Klasse](../standard-library/wbuffer-convert-class.md)|Beschreibt einen Streampuffer, der die Übertragung von Elementen in einen bzw. aus einem Streampuffer steuert.|
|[Wstring_convert-Klasse](../standard-library/wstring-convert-class.md)|Eine Klassen Vorlage, die Konvertierungen zwischen einer breiten Zeichenfolge und einer Byte Zeichenfolge ausführt.|

## <a name="see-also"></a>Siehe auch

[Codepages](../c-runtime-library/code-pages.md)\
[Gebiets Schema Namen, Sprachen und Länder-/regionszeichenfolgen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
