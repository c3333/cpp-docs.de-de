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
ms.openlocfilehash: 0c411289745466bd6478cc82ab30e6a05be9cc25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192001"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Springen zu Bezeichnungen in der Inlineassembly

**Microsoft-spezifisch**

Wie bei einer normalen C-oder C++-Bezeichnung hat eine Bezeichnung in einem- **`__asm`** Block einen Bereich in der Funktion, in der Sie definiert ist (nicht nur im-Block). Sowohl Assemblyanweisungen als auch **`goto`** Anweisungen können zu Bezeichnungen innerhalb oder außerhalb des **`__asm`** Blocks springen.

Bei Bezeichnungen, **`__asm`** die in-Blöcken definiert sind, wird die Groß-/Kleinschreibung nicht **`goto`** beachtet. sowohl Anweisungen als auch Assemblyanweisungen können auf diese Bezeichnungen verweisen C-und C++-Bezeichnungen werden nur bei Verwendung durch- **`goto`** Anweisungen beachtet. Assemblyanweisungen können ohne Berücksichtigung der Groß-/Kleinschreibung zu einer C-oder C++-Bezeichnung springen

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

Verwenden Sie keine C-Bibliotheks Funktionsnamen als Bezeichnungen in- **`__asm`** Blöcken. Beispielsweise kann es ratsam sein `exit` , als Bezeichnung wie folgt zu verwenden:

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

Wie bei MASM-Programmen fungiert das Dollarsymbol ( `$` ) als aktueller Speicherort. Es handelt sich um eine Bezeichnung für die zurzeit assemblierte Anweisung. In- **`__asm`** Blöcken besteht seine Hauptverwendung darin, lange bedingte Sprünge zu erstellen:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
