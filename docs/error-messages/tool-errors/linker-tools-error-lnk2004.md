---
title: Linkertoolfehler LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 0d26ab12c5b82d52b7dcbb176d9bfa033d7ddfee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194836"
---
# <a name="linker-tools-error-lnk2004"></a>Linkertoolfehler LNK2004

GP relativer Fixup-Überlauf zu ' target '; der kurze Abschnitt "section" ist zu groß oder liegt außerhalb des zulässigen Bereichs.

Der Abschnitt war zu groß.

Um diesen Fehler zu beheben, verringern Sie die Größe des kurzen Abschnitts, indem Sie entweder explizit Daten in den langen Abschnitten über #pragma Abschnitt (". sectionname", Read, Write, Long) und `__declspec(allocate(".sectionname"))` für Daten Definitionen und Deklarationen verwenden.  Beispiel:

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

Sie können logisch gruppierte Daten auch in eine eigene Struktur verschieben, bei der es sich um eine Sammlung von Daten handelt, die größer als 8 Bytes sind, die der Compiler in einem long-Daten Abschnitt zuweist.  Beispiel:

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

Auf diesen Fehler folgt ein schwerwiegender Fehler `LNK1165`.
