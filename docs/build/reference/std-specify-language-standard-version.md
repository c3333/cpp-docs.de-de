---
title: /std (Standardversion für die Sprache festlegen)
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: eef44858064b89d4a836c80a48552599bceec242
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223823"
---
# <a name="std-specify-language-standard-version"></a>`/std`(Standard Version der Sprache angeben)

Aktivieren Sie unterstützte Features der Programmiersprache C++ aus der angegebenen Version des C++-Sprachstandards.

## <a name="syntax"></a>Syntax

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**]

## <a name="remarks"></a>Bemerkungen

Die **`/std`** Option ist in Visual Studio 2017 und höher verfügbar. Sie wird verwendet, um die Versions spezifischen Standard Features der ISO C++-Programmiersprache zu steuern, die während der Kompilierung Ihres Codes aktiviert wurden. Mit dieser Option können Sie die Unterstützung für bestimmte neue sprach-und Bibliotheks Features deaktivieren: solche, die den vorhandenen Code unterbrechen können, der einer bestimmten Version des Sprachstandards entspricht. Standardmäßig **`/std:c++14`** ist angegeben. Dadurch werden die Sprach-und Standard Bibliotheksfunktionen deaktiviert, die in späteren Versionen des C++-Sprachstandards gefunden werden. Verwenden **`/std:c++17`** Sie, um c++ 17-Standard spezifische Features und Verhalten zu aktivieren. Verwenden Sie, um die derzeit implementierten Compiler-und Standard Bibliotheksfunktionen, die für den nächsten Entwurfs Standard vorgeschlagen werden, explizit zu aktivieren **`/std:c++latest`** . Alle c++ 20 Features erfordern **`/std:c++latest`** ; Wenn die Implementierung vollständig ist, wird eine neue **`/std:c++20`** Option aktiviert.

Die Standard **`/std:c++14`** Option aktiviert den Satz von c++ 14-Funktionen, die vom MSVC-Compiler implementiert werden. Mit dieser Option wird die Unterstützung von Compiler-und Standardbibliotheken für Funktionen deaktiviert, die in neueren Versionen des Sprachstandards geändert oder neu sind. Einige c++ 17-Features, die bereits in vorherigen Versionen des MSVC-Compilers implementiert wurden, werden nicht deaktiviert. Um wichtige Änderungen für Benutzer zu vermeiden, die bereits Abhängigkeiten von den in oder vor Visual Studio 2015 Update 2 verfügbaren Features übernommen haben, bleiben diese Features aktiviert, wenn die **`/std:c++14`** Option angegeben wird:

- [Regeln für `auto` mit geschweizten Klammern-init-Lists](https://wg21.link/n3922)

- [`typename`in Vorlagen Vorlagen-Parametern](https://wg21.link/n4051)

- [Entfernen von Trigraphen](https://wg21.link/n4086)

- [Attribute für Namespaces und Enumeratoren](https://wg21.link/n4266)

- [u8-Zeichenliterale](https://wg21.link/n4267)

Eine Liste der Funktionen c++ 14 und c++ 17 ist aktiviert, wenn Sie angeben, dass **`/std:c++14`** verfügbar ist. Weitere Informationen finden Sie in den Hinweisen in der [Tabelle Microsoft C++ Language Konformitäts](../../overview/visual-cpp-language-conformance.md).

Die **`/std:c++17`** Option aktiviert den vollständigen Satz von c++ 17-Funktionen, die vom MSVC-Compiler implementiert werden. Diese Option deaktiviert die Unterstützung von Compiler-und Standardbibliotheken für Funktionen, die nach c++ 17 neu sind oder geändert wurden. Dies umfasst die Änderungen nach dem C + + 17 in den Versionen des funktionierenden Entwurfs und die Mängel des C++-Standards.

**`/std:c++latest`** Mit der-Option werden die Sprach-und Bibliotheks Features von Post-C + + 17 aktiviert, die derzeit im Compiler und in Bibliotheken implementiert sind. Diese Features können Änderungen aus dem c++ 20 Working Draft, Mängel Updates, die nicht in c++ 17 enthalten sind, und experimentelle Vorschläge für den Entwurfs Standard enthalten. Eine Liste der unterstützten Sprach- und Bibliotheksfeatures finden Sie unter [Neuerungen bei Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). **`/std:c++latest`** Durch die Option werden keine Funktionen aktiviert, die durch den **`/experimental`** Switch geschützt sind, aber möglicherweise erforderlich sind, um Sie zu aktivieren

> [!IMPORTANT]
> Die von aktivierten Compilerfunktionen und Bibliotheksfunktionen **`/std:c++latest`** stellen Funktionen dar, die in einem zukünftigen C++-Standard und in C++ 20 genehmigten Features angezeigt werden können. Features, die nicht genehmigt wurden, unterliegen Breaking Changes oder der Entfernung ohne Benachrichtigung und werden „wie besehen“ zur Verfügung gestellt.

Die **`/std`** Option, die während einer C++-Kompilierung wirksam ist, kann mit dem [ \_ MSVC \_ lang](../../preprocessor/predefined-macros.md) -Präprozessormakro erkannt werden. Weitere Informationen finden Sie unter [Präprozessormakros](../../preprocessor/predefined-macros.md).

Die **`/std:c++14`** **`/std:c++latest`** Optionen und sind ab Visual Studio 2015 Update 3 verfügbar. Die **`/std:c++17`** Option ist ab Visual Studio 2017 Version 15,3 verfügbar. Wie bereits erwähnt, wird das Standardverhalten von c++ 17 durch die **`/std:c++14`** Option aktiviert, aber alle anderen Funktionen von c++ 17 werden durch aktiviert **`/std:c++17`** . C++ 20-Funktionen werden durch aktiviert, **`/std:c++latest`** bis die Implementierung beendet ist.

> [!NOTE]
> Abhängig von der Version oder Update Ebene des MSVC-Compilers werden c++ 17-Funktionen möglicherweise nicht vollständig implementiert oder vollständig kompatibel sein, wenn Sie die **`/std:c++17`** Optionen angeben. Eine Übersicht über die C++-sprach Konformität in Visual C++ nach Releaseversion finden Sie unter [Microsoft C++ Language Konformitäts Table](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurationseigenschaften**, **C/C++**, **Sprache**aus.

1. Wählen Sie unter **C++-Sprachstandard** in der Dropdownliste den zu unterstützenden Sprachstandard und dann **OK** oder **Übernehmen** aus, um Ihre Änderungen zu speichern.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
