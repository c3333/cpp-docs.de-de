---
title: /Wp64 (Nach 64-Bit-Portabilitätsproblemen suchen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: e5c30ac9096094948a83195f5b3990794c421685
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335885"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Nach 64-Bit-Portabilitätsproblemen suchen)

Diese Compileroption ist veraltet. In Versionen von Visual Studio vor Visual Studio 2013 werden dadurch 64-Bit-Portabilitätsprobleme für Typen ermittelt, die mit dem Schlüsselwort [__w64](../../cpp/w64.md) markiert sind.

## <a name="syntax"></a>Syntax

```
/Wp64
```

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist in Versionen von Visual Studio vor Visual Studio 2013 die Compileroption **/Wp64** im MSVC-Compiler deaktiviert, der 32-Bit-x86-Code erstellt, und im MSVC-Compiler, der 64-Bit-x64-Code erstellt.

> [!IMPORTANT]
> Die [/Wp64](wp64-detect-64-bit-portability-issues.md) Compileroption und das [__w64](../../cpp/w64.md) -Schlüsselwort sind in Visual Studio 2010 und Visual Studio 2012 veraltet und werden ab Visual Studio 2013 nicht mehr unterstützt. Wenn Sie ein Projekt konvertieren, das diesen Schalter verwendet, wird der Schalter während der Konvertierung nicht migriert. Um diese Option in Visual Studio 2010 oder Visual Studio 2012 zu verwenden, müssen Sie den Compilerschalter unter **Zusätzliche Optionen** im **** Befehlszeilenabschnitt der Projekteigenschaften eingeben. Wenn Sie die **/Wp64** -Compileroption in der Befehlszeile verwenden, gibt der Compiler eine Befehlszeilenwarnung D9002 aus. Anstatt diese Option und dieses Schlüsselwort zum Erkennen von 64-Bit-Portabilitätsproblemen zu verwenden, verwenden Sie einen MSVC-Compiler, der auf eine 64-Bit-Plattform abzielt, und geben Sie die Option [/W4](compiler-option-warning-level.md) an. Weitere Informationen finden Sie unter Konfigurieren von [C++-Projekten für 64-Bit-, x64-Ziele](../configuring-programs-for-64-bit-visual-cpp.md).

Variablen der folgenden Typen werden auf einem 32-Bit-Betriebssystem getestet, als ob sie auf einem 64-Bit-Betriebssystem verwendet würden:

- INT

- long

- Zeiger

Wenn Sie Ihre Anwendung regelmäßig mithilfe eines Compilers kompilieren, der 64-Bit-X64-Code erstellt, können Sie **/Wp64** einfach in Ihren 32-Bit-Kompilierungen deaktivieren, da der 64-Bit-Compiler alle Probleme erkennt. Weitere Informationen zum Targeting eines Windows 64-Bit-Betriebssystems finden Sie unter Konfigurieren von [C++-Projekten für 64-Bit-, x64-Ziele](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts.

   Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Ändern Sie das Feld **Zusätzliche Optionen** so, dass **/Wp64**eingeschlossen ist.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Konfigurieren von C++-Projekten für 64-Bit-x64-Ziele](../configuring-programs-for-64-bit-visual-cpp.md)
