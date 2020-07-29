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
ms.openlocfilehash: d95fed3d9af81d89ac03a52a1e6433786118430e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223836"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Standardmäßig "unsigned char")

Ändert den **`char`** Standardtyp von **`signed char`** in **`unsigned char`** , und der **`char`** -Typ ist mit 0 (null) erweitert, wenn er auf einen-Typ erweitert wird **`int`** .

## <a name="syntax"></a>Syntax

```
/J
```

## <a name="remarks"></a>Bemerkungen

Wenn ein **`char`** Wert explizit als deklariert wird **`signed`** , wirkt sich die **/J** -Option nicht auf die Option aus, und der Wert ist "Sign-Extended", wenn er auf einen Typ erweitert wird **`int`** .

Die **/J** -Option definiert `_CHAR_UNSIGNED` , das mit `#ifndef` in der Limits. h-Datei verwendet wird, um den Bereich des Standard Typs zu definieren **`char`** .

ANSI C und C++ erfordern keine bestimmte Implementierung des **`char`** Typs. Diese Option ist nützlich, wenn Sie mit Zeichendaten arbeiten, die schließlich in eine andere Sprache als Englisch übersetzt werden.

> [!NOTE]
> Wenn Sie diese Compileroption mit ATL/MFC verwenden, kann ein Fehler generiert werden. Obwohl Sie diesen Fehler durch Definieren von deaktivieren können `_ATL_ALLOW_CHAR_UNSIGNED` , wird diese Problem Umgehung nicht unterstützt und funktioniert möglicherweise nicht immer.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.

1. Erweitern Sie im Dialogfeld Projekteigenschaften **Seiten** im linken Bereich unter **Konfigurations Eigenschaften**die Option **C/C++** , und wählen Sie dann **Befehlszeile**aus.

1. Geben Sie im Bereich **zusätzliche Optionen** die **/J** -Compileroption an.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>
[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md)
