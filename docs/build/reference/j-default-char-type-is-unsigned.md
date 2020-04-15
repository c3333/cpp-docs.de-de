---
title: /J (Standardmäßig "unsigned char")
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322194"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Standardmäßig "unsigned char")

Ändert den `char` Standardtyp `signed char` von , `unsigned char`und der `char` Typ wird null `int` erweitert, wenn er auf einen Typ erweitert wird.

## <a name="syntax"></a>Syntax

```
/J
```

## <a name="remarks"></a>Bemerkungen

Wenn `char` ein Wert explizit `signed`als deklariert wird, wirkt sich die **/J-Option** nicht darauf aus, und der Wert wird sign-extended, wenn er auf einen `int` Typ erweitert wird.

Die Option **/J** definiert , `#ifndef` die in der Datei LIMITS.h verwendet `char` wird, um den Bereich des Standardtyps `_CHAR_UNSIGNED`zu definieren.

ANSI C und C++ erfordern keine `char` spezifische Implementierung des Typs. Diese Option ist nützlich, wenn Sie mit Zeichendaten arbeiten, die schließlich in eine andere Sprache als Englisch übersetzt werden.

> [!NOTE]
> Wenn Sie diese Compileroption mit ATL/MFC verwenden, kann ein Fehler generiert werden. Obwohl Sie diesen Fehler `_ATL_ALLOW_CHAR_UNSIGNED`deaktivieren können, indem Sie definieren, wird diese Problemumgehung nicht unterstützt und funktioniert möglicherweise nicht immer.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.

1. Erweitern Sie im Dialogfeld **Eigenschaftenseiten** des Projekts im linken Bereich unter **Konfigurationseigenschaften** **C/C++** und wählen Sie dann **Befehlszeile**aus.

1. Geben Sie im Bereich **Zusätzliche Optionen** die Compileroption **/J** an.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md)
