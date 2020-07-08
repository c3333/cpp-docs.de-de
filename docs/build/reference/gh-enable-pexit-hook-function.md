---
title: /GH (_pexit-Hookfunktion aktivieren)
description: Beschreibt die/GH-Compileroption, um eine lokale _pexit Hook-Funktion festzulegen.
ms.date: 07/06/2020
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: b8fc355503055af8b928874ced39cb8224901d3e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058606"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (_pexit-Hookfunktion aktivieren)

Ruft die `_pexit` Funktion am Ende jeder Methode oder Funktion auf.

## <a name="syntax"></a>Syntax

> **`/GH`**

## <a name="remarks"></a>Hinweise

Die `_pexit` Funktion ist nicht Teil einer Bibliothek. Es liegt an Ihnen, eine Definition für bereitzustellen `_pexit` .

`_pexit`Sie müssen keinen Prototyp bereitstellen, es sei denn, Sie beabsichtigen, explizit aufzurufen. Die Funktion muss den Inhalt aller Register bei einem Eintrag per Push übersetzen und den unveränderten Inhalt beim Beenden per Pop übersetzen. Es muss wie folgt aussehen:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

Diese Deklaration ist für 64-Bit-Projekte nicht verfügbar.

`_pexit`ähnelt `_penter` . ein Beispiel für das Schreiben einer Funktion finden Sie unter [ `/Gh` (aktivieren _penter Hook-Funktion)](gh-enable-penter-hook-function.md) `_penter` .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[`/Gh`(_Penter Hook-Funktion aktivieren)](gh-enable-penter-hook-function.md)
