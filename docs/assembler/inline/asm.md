---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 14a40bef5b2edba76fc130604414c45eee589bcd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193002"
---
# `__asm`

**Microsoft-spezifisch**

Das **`__asm`** Schlüsselwort Ruft den Inline Assembler auf und kann überall dort vorkommen, wo eine C-oder C++-Anweisung zulässig ist. Es kann nicht allein stehen. Ihm muss eine Assemblyanweisung, eine Gruppe von Anweisungen, die in geschweifte Klammern eingeschlossen sind, oder zumindest ein leeres Paar geschweifter Klammern folgen. Der Begriff " **`__asm`** Block" bezieht sich hier auf eine beliebige Anweisung oder Gruppe von Anweisungen, egal ob in geschweiften Klammern.

> [!NOTE]
> Visual C++ Unterstützung für das C++-Standard **`asm`** Schlüsselwort ist auf die Tatsache beschränkt, dass der Compiler keinen Fehler für das Schlüsselwort generiert. Ein- **`asm`** Block generiert jedoch keinen sinnvollen Code. Verwenden Sie **`__asm`** anstelle von **`asm`** .

## <a name="grammar"></a>Grammatik

*ASM-Block*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***Assembly-Anweisung* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***Assembly-Instruction-List* **`}`** **`;`** <sub>opt</sub>

*Assembly-Instruction-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Assembly-Anweisung* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Assembly-Anweisung* **`;`** *Assembly-Instruction-List* **`;`** <sub>opt</sub>

## <a name="remarks"></a>Bemerkungen

Wenn Sie ohne geschweifte Klammern verwendet wird, bedeutet das- **`__asm`** Schlüsselwort, dass der Rest der Zeile eine Assembly-Language-Anweisung ist. Wenn es mit geschweiften Klammern verwendet wird, bedeutet es, dass jede Zeile zwischen den geschweiften Klammern eine Assemblysprachanweisung ist. Aus Gründen der Kompatibilität mit früheren Versionen **`_asm`** ist ein Synonym für **`__asm`** .

Da das- **`__asm`** Schlüsselwort ein Trennzeichen für Anweisungen ist, können Sie Assemblyanweisungen in die gleiche Zeile einfügen.

Vor Visual Studio 2005 ist die Anweisung

```cpp
__asm int 3
```

hat bei der Kompilierung mit **/CLR**nicht bewirkt, dass nativer Code generiert wird. der Compiler hat die Anweisung in eine CLR-Break-Anweisung übersetzt.

`__asm int 3` führt jetzt zur Generierung von systemeigenem Code für die Funktion. Wenn eine Funktion einen Haltepunkt im Code verursachen soll und diese Funktion in MSIL kompiliert werden soll, verwenden Sie [__debugbreak](../../intrinsics/debugbreak.md).

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_asm`** ein Synonym für, **`__asm`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Das folgende Code Fragment ist ein einfacher Block, der in geschweiften **`__asm`** Klammern eingeschlossen ist:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Alternativ können Sie **`__asm`** jede Assemblyanweisung in den Vordergrund stellen:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Da das- **`__asm`** Schlüsselwort ein Trennzeichen für Anweisungen ist, können Sie auch Assemblyanweisungen in die gleiche Zeile einfügen:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Alle drei Beispiele generieren denselben Code, aber der erste Stil (der Block in geschweifte Klammern umschließt **`__asm`** ) hat einige Vorteile. Die geschweiften Klammern trennen den Assemblycode deutlich von C-oder C++-Code und vermeiden eine unnötige Wiederholung des **`__asm`** Schlüssel Worts. Geschweifte Klammern können auch Mehrdeutigkeiten verhindern. Wenn Sie eine C-oder C++-Anweisung in derselben Zeile wie einen-Block platzieren möchten **`__asm`** , müssen Sie den Block in geschweifte Klammern einschließen. Ohne die Klammern kann der Compiler nicht feststellen, wo Assemblycode endet und C- oder C++-Anweisungen beginnen. Und Sie können Text einfach aus bestehenden MASM-Quelldateien kopieren und einfügen, da der Text in geschweiften Klammer das gleiche Format aufweist wie gewöhnlicher MASM-Text.

Anders als geschweifte Klammern in C und C++ beeinflussen die geschweiften Klammern, die einen-Block einschließen, den **`__asm`** Variablen Bereich nicht Sie können auch Blöcke schachteln; die Schachtelung wirkt sich nicht auf den **`__asm`** Variablen Bereich aus.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../../cpp/keywords-cpp.md)<br/>
[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
