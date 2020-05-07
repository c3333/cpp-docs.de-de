---
title: Trigraphen
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 001eb90b5cb4dda933571fd053598995d3ef613e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345315"
---
# <a name="trigraphs"></a>Trigraphen

Der Quellzeichensatz von C-Quellprogrammen ist im 7-Bit-ASCII-Zeichensatz enthalten, ist aber eine Obermenge des Invariantencodesatzes nach ISO 646-1983. Trigraphsequenzen ermöglichen es, C-Programme ausschließlich mit dem Invariantencodesatz nach ISO(International Standards Organization) zu schreiben. Trigraphen sind Sequenzen von drei Zeichen, die mit zwei aufeinander folgenden Fragezeichen beginnen, und werden vom Compiler durch die entsprechenden Interpunktionszeichen ersetzt. Sie können Trigraphen in C-Quelldateien verwenden, die einen Zeichensatz besitzen, der für einige Interpunktionszeichen keine passenden grafischen Darstellungen enthält.

C++17 entfernt Trigraphen aus der Sprache. Implementierungen unterstützen Trigraphen möglicherweise weiterhin als Teil der durch die Implementierung definierten Zuordnung von der physischen Quelldatei bis zum *grundlegenden Quellzeichensatz*, obwohl Implementierungen dies nach dem Standard nicht sollen. C++14 unterstützt Trigraphen wie in C.

Visual C++ unterstützt weiterhin die Trigraphersetzung, diese ist jedoch standardmäßig deaktiviert. Informationen zum Aktivieren der Trigraphenersetzung finden Sie unter [/Zc: trigraphs (Trigraphs Substitution (Trigraphenersetzung))](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Die folgende Tabelle zeigt die neun Trigraphsequenzen. Alle in einer Quelldatei vorkommenden Interpunktionszeichen in der ersten Spalte werden durch das entsprechende Zeichen in der zweiten Spalte ersetzt.

### <a name="trigraph-sequences"></a>Trigraphsequenzen

| Trigraph | Interpunktionszeichen |
|----------|-----------------------|
| ??= | # |
| ??( | \[ |
| ??/ | \\ |
| ??) | ] |
| ??' | ^ |
| ??\< | { |
| ??! | &#124; |
| ??> | } |
| ??- | ~ |

Ein Trigraph wird immer als einzelnes Quellzeichen behandelt. Die Übersetzung von Trigraphen findet vor der Erkennung von Escapezeichen in Zeichenfolgenliteralen und Zeichenkonstanten in der ersten [Übersetzungsphase](../preprocessor/phases-of-translation.md) statt. Nur die neun Trigraphen, die in der obigen Tabelle angegeben sind, werden erkannt. Alle anderen Zeichensequenzen werden unübersetzt gelassen.

Die Zeichen-Escapesequenz **\\?** verhindert die Fehlinterpretation von Zeichenfolgen, die einem Trigraphen ähneln. (Informationen zu Escapesequenzen finden Sie unter [Escape Sequences (Escapesequenzen)](../c-language/escape-sequences.md).) Nehmen wir einmal an, Sie versuchen, die Zeichenfolge `What??!` mit dieser `printf`-Anweisung zu drucken:

```C
printf( "What??!\n" );
```

Die gedruckte Zeichenfolge lautet `What|`, da `??!` eine Trigraphsequenz ist, die durch das Zeichen `|` ersetzt wurde. Schreiben Sie die Anweisung wie folgt, um die Zeichenfolge ordnungsgemäß auszugeben:

```C
printf( "What?\?!\n" );
```

In dieser `printf`-Anweisung verhindert der umgekehrte Schrägstrich als Escapezeichen vor dem zweiten Fragezeichen die Fehlinterpretation von `??!` als Trigraph.

## <a name="see-also"></a>Siehe auch

[/Zc:trigraphs (Trigraphenersetzung)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[C-Bezeichner](../c-language/c-identifiers.md)
