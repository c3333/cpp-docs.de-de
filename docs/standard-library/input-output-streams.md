---
title: Eingabe-/Ausgabestreams
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 54b53f96d487e466106fe92a01affa7bd3e55c16
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228257"
---
# <a name="inputoutput-streams"></a>Eingabe-/Ausgabestreams

`basic_iostream`, das in der Header Datei definiert ist \<istream> , ist die Klassen Vorlage für Objekte, die sowohl Eingabe-als auch Ausgabe zeichenbasierte e/a-Streams verarbeiten.

Es gibt zwei Typdefinitionen, die Zeichen spezifische spezizierungen von definieren `basic_iostream` und den Code leichter lesbar machen können: `iostream` (nicht mit der Header Datei verwechselt \<iostream> ) ist ein e/a-Stream, der auf basiert `basic_iostream<char>` ; `wiostream` ist ein e/a-Stream, der auf basiert `basic_iostream<wchar_t>` .

Weitere Informationen finden Sie unter [basic_iostream-Klasse](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md), und [wiostream](../standard-library/basic-iostream-class.md).

Abgeleitet von `basic_iostream` ist die Klassenvorlage `basic_fstream`, die zum Übertragen von Zeichendaten in und aus Dateien verwendet wird.

Es gibt auch Typdefinitionen, die zeichenspezifische Spezialisierungen von `basic_fstream` bereitstellen. Dabei handelt es sich `fstream` um einen Datei-e/a-Datenstrom, der auf und basiert. Hierbei handelt es sich **`char`** um einen Datei-e/a-Stream, `wfstream` der auf basiert **`wchar_t`** . Weitere Informationen finden Sie unter [basic_fstream-Klasse](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md) und [wfstream](../standard-library/basic-fstream-class.md). Die Verwendung dieser Typedefs erfordert die Einbindung der Header Datei \<fstream> .

> [!NOTE]
> Wenn ein `basic_fstream`-Objekt die Datei-E/A verwendet, obwohl die zugrundeliegenden Puffer separat festgelegte Positionen für Lesen und Schreiben enthalten, sind die aktuellen Eingabe- und Ausgabepositionen miteinander verbunden. Das Lesen einiger Daten verschiebt die Ausgabeposition.

Die Klassenvorlage `basic_stringstream` und seine allgemeine Spezialisierung `stringstream`, werden häufig zum Arbeiten mit E/A-Streamobjekten zum Einfügen und Extrahieren von Zeichendaten verwendet. Weitere Informationen finden Sie unter [basic_stringstream-Klasse](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Siehe auch

[stringstream](../standard-library/basic-stringstream-class.md)\
[Basic_stringstream-Klasse](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[C++-Standard Bibliothek](../standard-library/cpp-standard-library-reference.md)
