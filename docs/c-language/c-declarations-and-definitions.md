---
title: C-Deklarationen und -Definitionen
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: 3be9cd72e9f4dbad4d279cc1bb65dfb92a61cd42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326052"
---
# <a name="c-declarations-and-definitions"></a>C-Deklarationen und -Definitionen

Eine "Deklaration" erstellt eine Zuordnung zwischen einer bestimmten Variable, einer Funktion oder einem Typ und den zugehörigen Attributen. [Übersicht über Deklarationen](../c-language/overview-of-declarations.md) gibt die ANSI-Syntax für das `declaration`-Nichtterminal an. Eine Deklaration gibt auch an, wo und wann auf einen Bezeichner zugegriffen werden kann (die "Verknüpfung" eines Bezeichners). Weitere Informationen zu Verknüpfungen finden Sie unter [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md).

Eine Definition einer Variablen erstellt die gleichen Zuordnungen wie eine Deklaration, bewirkt jedoch auch, dass Speicher für die Variable zugeordnet wird.

Beispielsweise werden `main`-, `find`- und `count`-Funktionen sowie `var`- und `val`-Variablen in einer Quelldatei in dieser Reihenfolge definiert:

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

Die Variablen `var` und `val` können in den Funktionen `find` und `count` verwendet werden; weitere Deklarationen sind nicht erforderlich. Diese Namen sind jedoch in `main` nicht sichtbar (auf sie kann nicht zugegriffen werden).

## <a name="see-also"></a>Siehe auch

[Quelldateien und Quellprogramme](../c-language/source-files-and-source-programs.md)
