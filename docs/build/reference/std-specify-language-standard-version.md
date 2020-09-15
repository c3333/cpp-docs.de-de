---
title: /std (Standardversion für die Sprache festlegen)
description: Die MSVC-Compileroption/Std gibt den C-oder C++-Sprachstandard an, der vom Compiler unterstützt wird.
ms.date: 09/11/2020
f1_keywords:
- /std
- -std
- /std:c++14
- /std:c++17
- /std:c11
- /std:c17
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 82f37377dc223bfe3f5e578e1c7f390da91752a1
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075828"
---
# <a name="std-specify-language-standard-version"></a>`/std` (Standard Version der Sprache angeben)

Aktivieren Sie die unterstützten c-und C++-sprach Features der angegebenen Version des c-oder C++-Sprachstandards.

## <a name="syntax"></a>Syntax

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**\
> **`/std:c11`**\
> **`/std:c17`**

## <a name="remarks"></a>Bemerkungen

Die **`/std`** Option ist in Visual Studio 2017 und höher verfügbar. Sie wird verwendet, um die Versions spezifischen Standard Features der ISO C-oder C++-Programmiersprache zu steuern, die während der Kompilierung Ihres Codes aktiviert wurden. Mit dieser Option können Sie die Unterstützung für bestimmte neue sprach-und Bibliotheks Features deaktivieren: solche, die den vorhandenen Code unterbrechen können, der einer bestimmten Version des Sprachstandards entspricht.

### <a name="c-standards-support"></a>C++-Standardunterstützung

Standardmäßig **`/std:c++14`** ist angegeben. Dadurch werden die Sprach-und Standard Bibliotheksfunktionen deaktiviert, die in späteren Versionen des C++-Sprachstandards gefunden werden. Verwenden  **`/std:c++17`** Sie, um c++ 17-Standard spezifische Features und Verhalten zu aktivieren. Verwenden Sie, um die derzeit implementierten Compiler-und Standard Bibliotheksfunktionen, die für den nächsten Entwurfs Standard vorgeschlagen werden, explizit zu aktivieren **`/std:c++latest`** . Alle c++ 20 Features erfordern **`/std:c++latest`** ; Wenn die Implementierung vollständig ist, wird eine neue **`/std:c++20`** Option aktiviert.

Die Standard **`/std:c++14`** Option aktiviert den Satz von c++ 14-Funktionen, die vom MSVC-Compiler implementiert werden. Mit dieser Option wird die Unterstützung von Compiler-und Standardbibliotheken für Funktionen deaktiviert, die in neueren Versionen des Sprachstandards geändert oder neu sind. Einige c++ 17-Features, die bereits in vorherigen Versionen des MSVC-Compilers implementiert wurden, werden nicht deaktiviert. Um wichtige Änderungen für Benutzer zu vermeiden, die bereits Abhängigkeiten von den in oder vor Visual Studio 2015 Update 2 verfügbaren Features übernommen haben, bleiben diese Features aktiviert, wenn die **`/std:c++14`** Option angegeben wird:

- [Regeln für `auto` mit geschweizten Klammern-init-Lists](https://wg21.link/n3922)

- [`typename` in Vorlagen Vorlagen-Parametern](https://wg21.link/n4051)

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

### <a name="c-standards-support"></a>C-Standardunterstützung

Wenn Code als c kompiliert wird, entspricht der MSVC-Compiler standardmäßig keinem bestimmten C-Standard. Es implementiert ANSI C89 mit mehreren Microsoft-Erweiterungen, von denen einige Teil von ISO C99 sind. Einige Microsoft-Erweiterungen können mit der- [`/Za`](za-ze-disable-language-extensions.md) Compileroption deaktiviert werden, aber andere bleiben in Kraft. Es ist nicht möglich, strikte C89-Konformität anzugeben.

Ab Visual Studio 2019 Version 16,8 können Sie **`/std:c11`** oder **`/std:c17`** für als C kompilierte Code angeben. Diese Optionen geben Konformitäts Modi an, die ISO C11 und ISO C17 entsprechen. Da der neue Präprozessor benötigt wird, um diese Standards zu unterstützen, **`/std:c11`** **`/std:c17`** legen die Compileroptionen und die [`/Zc:preprocessor`](zc-preprocessor.md) Option automatisch fest. Wenn Sie den herkömmlichen (Legacy-) Präprozessor für C11 oder C17 verwenden möchten, müssen Sie die- **`/Zc:preprocessor-`** Compileroption explizit festlegen. Das Festlegen der **`/Zc:preprocessor-`** Option kann zu unerwartetem Verhalten führen und wird nicht empfohlen.

> [!NOTE]
> Zum Zeitpunkt der Veröffentlichung unterstützen die neuesten Windows SDK-und ucrt-Bibliotheken noch nicht C11-und C17-Code. Eine Vorabversion der Windows SDK und ucrt ist erforderlich. Weitere Informationen und Installationsanweisungen finden Sie [unter Installieren von C11 und C17-Unterstützung in Visual Studio](../../overview/install-c17-support.md).

Wenn Sie **`/std:c11`** oder angeben **`/std:c17`** , unterstützt MSVC alle erforderlichen Features von C11 und C17. Die Compileroptionen aktivieren die Unterstützung für diese Funktionen:

- **`_Pragma`**

- **`restrict`**

- **`_Noreturn`** immer \<stdnoreturn.h>

- **`_Alignas`**, **`_Alignof`** und \<stdalign.h>

- **`_Generic`** immer \<tgmath.h>

- **`_Static_assert`**

Die IDE verwendet C-Einstellungen für IntelliSense und Code Hervorhebung, wenn die Quelldateien eine *`.c`* Dateierweiterung aufweisen oder wenn Sie die- [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) Compileroption angeben. Derzeit ist die IntelliSense-Hervorhebung nur für Schlüsselwörter verfügbar, nicht für die Makros, die von den Standard Headern eingeführt werden.

Da C17 größtenteils eine Programmfehler Behebung von ISO C11 ist, enthält die MSVC-Unterstützung für C11 bereits alle relevanten Mängel Berichte. Derzeit gibt es keine Unterschiede zwischen der C11-und der C17-Version, mit Ausnahme des- `__STDC_VERSION__` Makros. Sie wird auf `201112L` für C11 und `201710L` für C17 erweitert.

Der Compiler unterstützt keine optionalen Features von ISO C11. Einige dieser optionalen Features von C11 waren erforderliche Features von C99, die MSVC aus architektonischen Gründen nicht implementiert hat. Sie können die featuretestmakros wie z `__STDC_NO_VLA__` . b. verwenden, um compilerunterstützungs Stufen für einzelne Funktionen zu erkennen. Weitere Informationen zu C-spezifischen vordefinierten Makros finden Sie unter [vordefinierte Makros](../../preprocessor/predefined-macros.md).

- In der Version von Visual Studio 2019 Version 16,8 gibt es keine konforme Unterstützung für Multithreading, atomarische oder komplexe Zahlen.

- `aligned_alloc` der Support fehlt aufgrund der Windows-Heap Implementierung. Die Alternative ist die Verwendung von [`_aligned_malloc`](../../c-runtime-library/reference/aligned-malloc.md) .

- Die Dr 400-Unterstützung ist für nicht implementiert `realloc` , da diese Änderung die ABI unterbrechen würde.

- Vla-Unterstützung (Variable Length Array) ist nicht geplant. Arrays variabler Länge sind häufig weniger effizient als vergleichbare Arrays mit fester Größe. Sie sind im Vergleich zu gleichwertigen Heap Speicher Belegungen ebenfalls ineffizient, wenn Sie sicher und sicher implementiert werden. Vlas bietet Angriffsvektoren `gets()` , die mit vergleichbar sind, die veraltet sind und entfernt werden müssen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurationseigenschaften**, **C/C++**, **Sprache**aus.

1. Wählen Sie im **C++-Sprachstandard** (oder für c, **c-Sprachstandard**) im Dropdown-Steuerelement den zu unterstützten Sprachstandard aus, und **Klicken** Sie dann auf OK **oder übernehmen, um** die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
