---
title: Spezielle Memberfunktionen
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178690"
---
# <a name="special-member-functions"></a>Spezielle Memberfunktionen

Die *speziellen Member-Funktionen* sind Klassen-oder Strukturmember-Funktionen, die in bestimmten Fällen automatisch für Sie generiert werden. Diese Funktionen sind der [Standardkonstruktor](constructors-cpp.md#default_constructors), [der debugtor](destructors-cpp.md), der [Kopierkonstruktor und der Kopier Zuweisungs Operator](copy-constructors-and-copy-assignment-operators-cpp.md)sowie der [bewegungskonstruktor und Bewegungs Zuweisungs Operator](move-constructors-and-move-assignment-operators-cpp.md). Wenn die Klasse eine oder mehrere der sondermember-Funktionen nicht definiert, kann der Compiler die verwendeten Funktionen implizit deklarieren und definieren. Die vom Compiler generierten Implementierungen werden als *Standard* mäßige spezielle Member-Funktionen bezeichnet. Der Compiler generiert keine Funktionen, wenn Sie nicht benötigt werden.

Sie können eine standardmäßige spezielle Element Funktion explizit mit dem Schlüsselwort **= default** deklarieren. Dies bewirkt, dass der Compiler die Funktion nur bei Bedarf definiert, und zwar auf dieselbe Weise, als wenn die Funktion überhaupt nicht deklariert wurde.

In einigen Fällen generiert der Compiler möglicherweise *Gelöschte* besondere Member-Funktionen, die nicht definiert und daher nicht aufgerufen werden können. Dies kann vorkommen, wenn ein Aufrufe einer bestimmten speziellen Member-Funktion für eine Klasse bei anderen Eigenschaften der Klasse keinen Sinn macht. Um die automatische Generierung einer speziellen Member-Funktion explizit zu verhindern, können Sie Sie mit dem Schlüsselwort " **= Delete** " als gelöscht deklarieren.

Der Compiler generiert einen *Standardkonstruktor*, einen Konstruktor, der keine Argumente annimmt, nur, wenn Sie keinen anderen Konstruktor deklariert haben. Wenn Sie nur einen Konstruktor deklariert haben, der Parameter annimmt, bewirkt dies, dass Code, der versucht, einen Standardkonstruktor aufzurufen, bewirkt, dass der Compiler eine Fehlermeldung erzeugt. Der vom Compiler generierte Standardkonstruktor führt eine einfache, Element Weise [Standard Initialisierung](initializers.md#default_initialization) des Objekts aus. Bei der Standard Initialisierung bleiben alle Element Variablen in einem unbestimmten Zustand.

Der standardedekonstruktor führt die Element Weise Zerstörung des Objekts aus. Es ist nur virtuell, wenn ein basisklassendekonstruktor virtuell ist.

Die standardmäßigen Kopier-und Verschiebungs Vorgänge für die Erstellung und Zuweisung führen Element Weise Bitmuster Kopien oder Verschiebungen nicht statischer Datenmember aus. Verschiebe Vorgänge werden nur generiert, wenn weder Dekonstruktor-noch verschiebe-oder Kopiervorgänge deklariert werden. Ein Standardkopierkonstruktor wird nur generiert, wenn kein Kopierkonstruktor deklariert wurde. Er wird implizit gelöscht, wenn ein Verschiebungs Vorgang deklariert wird. Ein standardmäßiger Kopier Zuweisungs Operator wird nur generiert, wenn kein Kopier Zuweisungs Operator explizit deklariert wurde. Er wird implizit gelöscht, wenn ein Verschiebungs Vorgang deklariert wird.

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](cpp-language-reference.md)
