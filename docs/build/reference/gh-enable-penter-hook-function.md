---
title: /Gh (_penter-Hookfunktion aktivieren)
description: Beschreibt die/GH-Compileroption, um die angegebene _penter Funktion aufzurufen.
ms.date: 07/06/2020
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 96597d964e6a341aa25f4d52d34974949eb7b096
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058580"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (_penter-Hookfunktion aktivieren)

Bewirkt, dass die- `_penter` Funktion am Anfang jeder Methode oder Funktion aufgerufen wird.

## <a name="syntax"></a>Syntax

> **`/Gh`**

## <a name="remarks"></a>Hinweise

Die `_penter` Funktion ist nicht Teil einer Bibliothek. Es liegt an Ihnen, eine Definition für bereitzustellen `_penter` .

`_penter`Sie müssen keinen Prototyp bereitstellen, es sei denn, Sie beabsichtigen, explizit aufzurufen. Die Funktion muss den Inhalt aller Register bei einem Eintrag per Push übersetzen und den unveränderten Inhalt beim Beenden per Pop übersetzen. Es muss wie folgt aussehen:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Diese Deklaration ist für 64-Bit-Projekte nicht verfügbar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Beispiel

Der folgende Code zeigt bei der Kompilierung mit **/GH**, wie `_penter` zweimal aufgerufen wird, einmal bei der Eingabe der Funktion `main` und einmal bei der Eingabe der Funktion `x` . Das Beispiel besteht aus zwei Quelldateien, die separat kompiliert werden.

```cpp
// local_penter.cpp
// compile with: cl /EHsc /c local_penter.cpp
// processor: x86
#include <stdio.h>

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

```cpp
// Gh_compiler_option.cpp
// compile with: cl /EHsc /Gh Gh_compiler_option.cpp local_penter.obj
// processor: x86
#include <stdio.h>

void x() {}

int main() {
   x();
}
```

Wenn Sie ausführen, wird die lokale `_penter` Funktion beim Eintrag für `main` und aufgerufen `x` :

```Output

In a function!
In a function!
```

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[`/GH`(_Pexit Hook-Funktion aktivieren)](gh-enable-pexit-hook-function.md)
