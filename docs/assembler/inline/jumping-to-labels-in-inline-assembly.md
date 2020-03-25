---
title: Springen zu Bezeichnungen in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 199156a08af13f4a70793609b37c70b0c95bf9ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169330"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Springen zu Bezeichnungen in der Inlineassembly

**Microsoft-spezifisch**

Wie bei einer normalen C C++ -oder-Bezeichnung hat eine Bezeichnung in einem `__asm`-Block einen Bereich in der Funktion, in der Sie definiert ist (nicht nur im-Block). Sowohl Assemblyanweisungen als auch `goto` Anweisungen können zu Bezeichnungen innerhalb oder außerhalb des `__asm` Blocks springen.

In `__asm` Blöcken definierte Bezeichnungen unterliegen nicht der Groß-/Kleinschreibung. sowohl `goto`-als auch Assemblyanweisungen können diese Bezeichnungen ohne Berücksichtigung der Groß-/Kleinschreibung bezeichnen. Bei C C++ -und-Bezeichnungen wird nur dann `goto` nach Groß-/Kleinschreibung unterschieden, wenn Assemblyanweisungen können ohne Berücksichtigung der C++ Groß-/Kleinschreibung zu einer C-oder-Bezeichnung

Der folgende Code zeigt alle Permutationen:

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

Verwenden Sie keine C-Bibliotheks Funktionsnamen als Bezeichnungen in `__asm` Blöcken. Beispielsweise ist es möglicherweise verlockend, `exit` wie folgt als Bezeichnung zu verwenden:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Da **Exit** der Name einer C-Bibliotheksfunktion ist, kann dieser Code einen Sprung zur **Exit** -Funktion statt an die gewünschte Position auslösen.

Wie bei MASM-Programmen fungiert das Dollarsymbol (`$`) als aktueller Speicherort. Es handelt sich um eine Bezeichnung für die zurzeit assemblierte Anweisung. In `__asm` Blöcken besteht der Haupt Verwendungs Umfang darin, lange bedingte Sprünge zu erstellen:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
