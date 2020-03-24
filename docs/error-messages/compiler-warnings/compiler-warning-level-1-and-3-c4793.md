---
title: Compilerwarnung (Stufe 1 und 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164806"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Compilerwarnung (Stufe 1 und 3) C4793

> "*Function*": die Funktion wird als nativer Code kompiliert: "*reason*"

## <a name="remarks"></a>Bemerkungen

Der Compiler kann die *Funktion* nicht in verwalteten Code kompilieren, auch wenn die [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Compileroption angegeben ist. Stattdessen gibt der Compiler Warning C4793 und eine Erläuterung der Fortsetzungs Meldung aus und kompiliert dann die *Funktion* in nativen Code. Die Fortsetzungs Meldung enthält den *Grund* Text, in dem erläutert wird, warum die *Funktion* nicht in `MSIL`kompiliert werden kann.

Dies ist eine Warnung der Stufe 1, wenn Sie die Compileroption **/clr: pure** angeben.  Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

In der folgenden Tabelle sind alle möglichen Fortsetzungs Nachrichten aufgeführt.

|Grund Nachricht|Bemerkungen|
|--------------------|-------------|
|Ausgerichtete Datentypen werden in verwaltetem Code nicht unterstützt.|Die CLR muss bei Bedarf Daten zuordnen können. Dies ist möglicherweise nicht möglich, wenn die Daten mit Deklarationen wie [__m128](../../cpp/m128.md) oder [align](../../cpp/align-cpp.md)ausgerichtet sind.|
|Funktionen, die "__ImageBase" verwenden, werden in verwaltetem Code nicht unterstützt.|`__ImageBase` ist ein spezielles Linker-Symbol, das in der Regel nur von System eigenem Code auf niedriger Ebene verwendet wird, um eine DLL zu laden.|
|VarArgs werden von der Compileroption '/CLR ' nicht unterstützt.|Native Funktionen können keine verwalteten Funktionen mit [Variablen Argumentlisten](../../cpp/functions-with-variable-argument-lists-cpp.md) (VarArgs) abrufen, da die Funktionen unterschiedliche Anforderungen für das Stapel Layout aufweisen. Wenn Sie jedoch die **/clr: pure** -Compileroption angeben, werden Variablen Argumentlisten unterstützt, da die Assembly nur verwaltete Funktionen enthalten kann. Weitere Informationen finden Sie unter [reiner und überprüfbarerC++Code (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|Die 64-Bit-CLR unterstützt keine Daten, die mit dem __ptr32-Modifizierer deklariert werden.|Ein Zeiger muss dieselbe Größe aufweisen wie ein nativer Zeiger auf der aktuellen Plattform. Weitere Informationen finden Sie unter [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|Die 32-Bit-CLR unterstützt keine Daten, die mit dem __ptr64-Modifizierer deklariert werden.|Ein Zeiger muss dieselbe Größe aufweisen wie ein nativer Zeiger auf der aktuellen Plattform. Weitere Informationen finden Sie unter [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|Mindestens eine intrinsie wird in verwaltetem Code nicht unterstützt.|Der Name der systeminternen ist nicht verfügbar, wenn die Meldung ausgegeben wird. Eine intrinsische, die diese Nachricht verursacht, stellt jedoch in der Regel eine Computer Anweisung auf niedriger Ebene dar.|
|Die systemeigene Inline Assembly ("__asm") wird in verwaltetem Code nicht unterstützt.|[Inline](../../assembler/inline/asm.md) -Assemblycode kann beliebigen nativen Code enthalten, der nicht verwaltet werden kann.|
|Ein nicht __clrcall virtuelle Funktions Thunk muss als Native kompiliert werden.|Eine nicht[__clrcall](../../cpp/clrcall.md) virtuelle Funktions Thunk muss eine nicht verwaltete Adresse verwenden.|
|Eine Funktion, die "_setjmp" verwendet, muss als Native kompiliert werden.|Die CLR muss in der Lage sein, die Programmausführung zu steuern. Die Funktion " [setjmp](../../cpp/using-setjmp-longjmp.md) " umgeht jedoch die reguläre Programmausführung durch Speichern und Wiederherstellen von Informationen auf niedriger Ebene, wie z. b. Registern und Ausführungs Status.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4793 generiert.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

Im folgenden Beispiel wird C4793 generiert.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```
