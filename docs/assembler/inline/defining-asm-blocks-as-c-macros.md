---
title: Definieren von __asm-Blöcken als C-Makros
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: 4195624078c53f6c1f20cd2a03ed53dac937d9cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192105"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>Definieren von __asm-Blöcken als C-Makros

**Microsoft-spezifisch**

C-Makros bieten eine bequeme Möglichkeit zum Einfügen von Assemblycode in Ihren Quellcode, Sie erfordern jedoch besondere Sorgfalt, da ein Makro in eine einzelne logische Linie erweitert wird. Gehen Sie folgendermaßen vor, um fehlerfreie Makros zu erstellen:

- Schließen Sie den **`__asm`** Block in geschweifte Klammern ein.

- Fügen Sie das- **`__asm`** Schlüsselwort vor jeder Assemblyanweisung vor.

- Verwenden Sie c-Kommentare im alten Stil ( `/* comment */` ) anstelle von Kommentaren im `; comment` AssemblyFormat () oder einzeiligen c-Kommentaren ( `// comment` ).

Im folgenden Beispiel wird ein einfaches Makro definiert, um dies zu veranschaulichen:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

Auf den ersten Blick scheinen die letzten drei **`__asm`** Schlüsselwörter überflüssig zu sein. Sie werden jedoch benötigt, da das Makro in eine einzelne Zeile erweitert wird:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Das dritte und vierte **`__asm`** Schlüsselwort werden als Trennzeichen für die-Anweisung benötigt. Die einzigen Anweisungs Trennzeichen, die in- **`__asm`** Blöcken erkannt werden, sind das Zeilen-und- **`__asm`** Schlüsselwort. Da ein Block, der als Makro definiert ist, eine logische Linie ist, müssen Sie jede Anweisung mit trennen **`__asm`** .

Die geschweiften Klammern sind ebenfalls unverzichtbar. Wenn Sie sie weglassen, kann der Compiler von C-oder C++-Anweisungen in derselben Zeile auf der rechten Seite des Makro aufzurufenden verwechselt werden. Ohne die schließende geschweifte Klammer kann der Compiler nicht feststellen, an welcher Stelle der Assemblycode angehalten wird, und es werden C-oder C++-Anweisungen nach dem **`__asm`** Block als

Kommentare im assemblystil, die mit einem Semikolon (**;**) beginnen, werden bis zum Ende der Zeile fortgesetzt. Dies verursacht Probleme in Makros, da der Compiler alles nach dem Kommentar ignoriert, bis zum Ende der logischen Zeile. Das gleiche gilt für einzeilige C-oder C++-Kommentare ( `// comment` ). Um Fehler zu vermeiden, verwenden Sie C-Kommentare im alten Stil ( `/* comment */` ) in Blöcken, die **`__asm`** als Makros definiert sind.

Ein **`__asm`** als C-Makro geschriebener Block kann Argumente annehmen. Anders als bei einem normalen C-Makro kann ein Makro jedoch keinen **`__asm`** Wert zurückgeben. Daher können solche Makros in C-oder C++-Ausdrücken nicht verwendet werden.

Achten Sie darauf, dass keine Makros dieses Typs willkürlich aufgerufen werden. Beispielsweise kann das Aufrufen eines assemblysprachenmakros in einer Funktion, die mit der Konvention deklariert wurde, zu **`__fastcall`** unerwarteten Ergebnissen führen. (Siehe [verwenden und beibehalten von Registern in der Inlineassembly](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
