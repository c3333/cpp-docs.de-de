---
title: /Zl (Kein Standardbibliotheksname)
ms.date: 11/04/2016
f1_keywords:
- /zl
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: c72377314abf755469075c7a4b431f4b8a64ee7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438634"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Kein Standardbibliotheksname)

Lässt den Standard-C-Lauf Zeit Bibliotheksnamen aus der obj-Datei aus. Standardmäßig legt der Compiler den Namen der Bibliothek in der OBJ-Datei ab, um den Linker zur richtigen Bibliothek zu leiten.

## <a name="syntax"></a>Syntax

```
/Zl
```

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Standardbibliothek finden Sie unter [Verwenden der Lauf Zeit Bibliothek](md-mt-ld-use-run-time-library.md).

Sie können **/Zl** verwenden, um OBJ-Dateien zu kompilieren, die Sie in einer Bibliothek speichern möchten. Obwohl der Bibliotheksname weggelassen wird, wird nur ein wenig Speicherplatz für eine einzelne OBJ-Datei gespart, da der gesamte Speicherplatz in einer Bibliothek, die viele Objekt Module enthält, bedeutend ist.

Bei dieser Option handelt es sich um eine erweiterte Option. Wenn Sie diese Option festlegen, wird eine bestimmte Unterstützung der C-Lauf Zeit Bibliothek entfernt, die möglicherweise von der Anwendung benötigt wird Wenn Sie diese Option verwenden, müssen Sie die erforderlichen Komponenten auf andere Weise bereitstellen.

Verwenden Sie [/NODEFAULTLIB (Bibliotheken ignorieren)](nodefaultlib-ignore-libraries.md). , um den Linker anzuweisen, Bibliotheks Verweise in allen OBJ-Dateien zu ignorieren.

Weitere Informationen finden Sie unter [CRT Library Features (CRT-Bibliotheksfunktionen)](../../c-runtime-library/crt-library-features.md).

Beim Kompilieren mit **/Zl**wird `_VC_NODEFAULTLIB` definiert.  Beispiel:

```cpp
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaften Seite **erweitert** .

1. Ändern Sie die Eigenschaft **Standard Bibliotheksnamen weglassen** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
