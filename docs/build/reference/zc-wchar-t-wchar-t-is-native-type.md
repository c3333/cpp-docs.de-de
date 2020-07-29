---
title: /Zc:wchar_t (wchar_t ist der systemeigene Typ)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 114ed4a279b66571c0dc81fc1139dcdc59c17eae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234314"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t ist der systemeigene Typ)

Analysieren **`wchar_t`** Sie als integrierter Typ gemäß dem C++-Standard.

## <a name="syntax"></a>Syntax

> **/Zc: wchar_t**[ **-** ]

## <a name="remarks"></a>Bemerkungen

Wenn **/Zc: wchar_t** auf on gesetzt ist, **`wchar_t`** ist ein Schlüsselwort für einen integrierten ganzzahligen Typ in Code, der als C++ kompiliert wird. Wenn **/Zc: wchar_t-** (mit einem Minuszeichen) oder in Code, der als C kompiliert wird, **`wchar_t`** kein integrierter Typ ist. Stattdessen **`wchar_t`** wird als **`typedef`** für **`unsigned short`** in der kanonischen Kopfzeile STDDEF. h definiert. (Die Microsoft-Implementierung definiert Sie in einem anderen Header, der in "STDDEF. h" enthalten ist, und in anderen Standard Headern.)

" **/Zc: wchar_t** " wird nicht empfohlen, da der C++-Standard erfordert, dass **`wchar_t`** ein integrierter Typ ist. Die Verwendung der- **`typedef`** Version kann Portabilitäts Probleme verursachen. Wenn Sie ein Upgrade von früheren Versionen von Visual Studio ausführen und Compilerfehler auftreten [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) da der Code versucht, eine implizit **`wchar_t`** in zu konvertieren **`unsigned short`** , empfiehlt es sich, den Code zu ändern, um den Fehler zu beheben, anstatt **/Zc: wchar_t-** festzulegen.

Die Option **/Zc: wchar_t** ist in C++-Kompilierungen standardmäßig aktiviert und wird in C-Kompilierungen ignoriert. Die [/permissive-](permissive-standards-conformance.md) -Option hat keine Auswirkung auf **/Zc: wchar_t**.

Microsoft implementiert **`wchar_t`** als einen 2-Byte-Wert ohne Vorzeichen. Es wird dem Microsoft-spezifischen systemeigenen Typ zugeordnet **`__wchar_t`** . Weitere Informationen zu **`wchar_t`** finden Sie unter [Datentyp Bereiche](../../cpp/data-type-ranges.md) und [grundlegende Typen](../../cpp/fundamental-types-cpp.md).

Wenn Sie neuen Code schreiben, der mit dem älteren Code interagiert, der weiterhin die **`typedef`** -Version von verwendet **`wchar_t`** , können Sie über Ladungen für die **`unsigned short`** -und- **`__wchar_t`** Variationen von bereitstellen **`wchar_t`** , sodass der Code mit Code verknüpft werden kann, der mit/Zc kompiliert wird **: wchar_t** oder Code, der ohne ihn kompiliert wurde. Andernfalls müssten Sie zwei unterschiedliche Builds der Bibliothek bereitstellen, eine mit und eine ohne **/Zc: wchar_t** aktiviert. Allerdings wird in beiden Fällen empfohlen, den älteren und den neuen Code mit demselben Compiler zu erstellen. Kombinieren Sie niemals die Binärdateien, die mit unterschiedlichen Compilern erstellt wurden.

Wenn **/Zc: wchar_t** angegeben wird, werden ** \_ WCHAR \_ t \_ ** -definierte und systemeigene ** \_ \_ WCHAR \_ t- \_ definierte** Symbole definiert. Weitere Informationen finden Sie unter [Predefined Macros](../../preprocessor/predefined-macros.md).

Wenn Ihr Code die globalen com-Funktionen des Compilers verwendet, da **/Zc: wchar_t** jetzt standardmäßig aktiviert ist, empfiehlt es sich, explizite Verweise auf comsupp. lib (entweder vom [kommentarpragma](../../preprocessor/comment-c-cpp.md) oder in der Befehlszeile) entweder in "comsuppw. lib" oder "comsuppwd. lib" zu ändern. (Verwenden Sie comsupp. lib, wenn Sie die Kompilierung mit **/Zc: wchar_t-** ausführen müssen.) Wenn Sie die Header Datei "comdef. h" einschließen, wird die richtige Bibliothek für Sie angegeben. Weitere Informationen zur Unterstützung von Compiler-com finden Sie unter [Compiler COM-Unterstützung](../../cpp/compiler-com-support.md).

Der **`wchar_t`** integrierte Typ wird nicht unterstützt, wenn Sie C-Code kompilieren. Weitere Informationen zu Konformitäts Problemen bei Visual C++ finden Sie unter [nicht dem Standard entsprechende Verhalten](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Seite **Konfigurations Eigenschaften**  >  **C/C++-**  >  **Sprache** aus.

1. Ändern Sie die Eigenschaft **wchar_t als integrierten Typ behandeln** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Siehe auch

[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
