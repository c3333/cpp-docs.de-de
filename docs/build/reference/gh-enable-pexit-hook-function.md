---
title: /GH (_pexit-Hookfunktion aktivieren)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749226"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (_pexit-Hookfunktion aktivieren)

Ruft `_pexit` die Funktion am Ende jeder Methode oder Funktion auf.

## <a name="syntax"></a>Syntax

```
/GH
```

## <a name="remarks"></a>Bemerkungen

Die `_pexit` Funktion ist nicht Teil einer Bibliothek und es liegt `_pexit`an Ihnen, eine Definition für bereitzustellen.

Wenn Sie nicht `_pexit`explizit aufrufen möchten, müssen Sie keinen Prototyp bereitstellen. Die Funktion muss so aussehen, als hätte sie den folgenden Prototyp, und sie muss den Inhalt aller Register beim Eintrag übertragen und den unveränderten Inhalt beim Beenden auffüllen:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`ist ähnlich `_penter`wie ; siehe [/Gh (Enable _penter Hook Function)](gh-enable-penter-hook-function.md) für `_pexit` ein Beispiel zum Schreiben einer Funktion.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
