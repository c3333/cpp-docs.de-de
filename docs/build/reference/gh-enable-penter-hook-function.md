---
title: /Gh (_penter-Hookfunktion aktivieren)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749291"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (_penter-Hookfunktion aktivieren)

Verursacht einen Aufruf `_penter` der Funktion am Anfang jeder Methode oder Funktion.

## <a name="syntax"></a>Syntax

```
/Gh
```

## <a name="remarks"></a>Bemerkungen

Die `_penter` Funktion ist nicht Teil einer Bibliothek und es liegt `_penter`an Ihnen, eine Definition für bereitzustellen.

Wenn Sie nicht `_penter`explizit aufrufen möchten, müssen Sie keinen Prototyp bereitstellen. Die Funktion muss so aussehen, als hätte sie den folgenden Prototyp, und sie muss den Inhalt aller Register beim Eintrag übertragen und den unveränderten Inhalt beim Beenden auffüllen:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Diese Deklaration ist für 64-Bit-Projekte nicht verfügbar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wenn er `_penter` mit **/Gh**kompiliert wird, wie zweimal aufgerufen wird. einmal bei `main` der Eingabe der `x`Funktion und einmal bei der Eingabe der Funktion .

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
