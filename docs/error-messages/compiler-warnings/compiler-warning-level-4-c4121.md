---
title: Compilerwarnung (Stufe 4) C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 0e5bdab6ff0d0508abaf5f726d1356102cfca04a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219975"
---
# <a name="compiler-warning-level-4-c4121"></a>Compilerwarnung (Stufe 4) C4121

'symbol': Ausrichtung eines Elements hängt vom Pragma 'pack' ab

Der Compiler hat eine Auffüllung hinzugefügt, um einen Strukturmember an der Ausrichtungsgrenze auszurichten, aber der Paketwert ist geringer als die Größe des Members. Beispielsweise wird durch folgenden Codeausschnitt C4121 erstellt:

```cpp
// C4121.cpp
// compile with: /W4 /c
#pragma pack(2)
struct s
{
   char a;
   int b; // C4121
   long long c;
};
```

Nehmen Sie zur Behebung dieses Problems eine der folgenden Änderungen vor:

- Ändern Sie die Paketgröße mindestens auf die Größe des Members, der die Warnung verursacht hat. Ändern Sie beispielsweise in diesem Ausschnitt `pack(2)` in `pack(4)` oder `pack(8)`.

- Ordnen Sie die Memberdeklarationen aufsteigend nach Größe neu an. Umkehren Sie im Code Ausschnitt die Reihenfolge der Strukturmember so, dass der **`long long`** Member vor dem **`int`** steht, und der vor **`int`** dem **`char`** .

Diese Warnung tritt nur auf, wenn der Compiler den Datenmembern eine Auffüllung voranstellt. Sie tritt nicht auf, wenn beim Packen Daten an einer Speicheradresse platziert werden, die für den Datentyp nicht ausgerichtet ist, aber dem Datenmember keine Auffüllung vorangestellt wurde. Daten, die nicht an Grenzen ausgerichtet sind, bei denen es sich um ein Vielfaches der Datengröße handelt, können die Leistung mindern. Lese- und Schreibvorgänge von nicht ausgerichteten Daten führen in manchen Architekturen zu Prozessorfehlern; die Behebung dieser Fehler nimmt zwei- bis dreimal mehr Zeit in Anspruch. Zugriffe auf nicht ausgerichtete Daten können zu einigen RISC-Architekturen nicht portiert werden.

Sie können [#pragma pack](../../preprocessor/pack.md) oder [/ZP](../../build/reference/zp-struct-member-alignment.md) verwenden, um die Struktur Ausrichtung anzugeben. (Der Compiler generiert diese Warnung nicht, wenn **/Zp1** angegeben wird.)
