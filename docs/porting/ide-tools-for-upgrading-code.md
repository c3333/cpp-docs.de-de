---
title: Visual Studio-IDE-Tools zum Aktualisieren von C++-Code
description: Der C++-Code-Editor und die Code Analysetools in Visual Studio helfen Ihnen beim modernisieren Ihrer C++-Codebasis.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: 0d43da784e1e2f7789ac17ec01163ce29944e93d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205729"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>Visual Studio-IDE-Tools zum Aktualisieren von C++-Code

Visual Studio unterstützt Sie bei der Aktualisierung von Legacy-C++-Code mit Compileroptionen, Code Analyse Warnungen und Editor-Funktionen wie schnell Korrekturen, QuickInfo und der verbesserten Bild Lauf Leiste. Der Begriff "Legacy Code" bezieht sich auf eine dieser Kategorien:

- Code, der zuvor vom Microsoft C++ Compiler (MSVC) zugelassen wurde, aber nie mit dem C++-standardkonform ist.

   Um älteren nicht kompatiblen MSVC-Code zu aktualisieren, aktivieren Sie die [/permissive-](../build/reference/permissive-standards-conformance.md) -Compileroption. Alle Instanzen von nicht konformen Verwendungen werden im Code-Editor mit roten Wellenlinien unterstrichen. Die Fehlermeldungen im **Fehlerliste** Fenster enthalten eine Empfehlung zum Beheben des Fehlers. Klicken Sie auf den Fehlercode, um zur zugehörigen Hilfeseite in der Dokumentation zu wechseln. Wenn alle Fehler gleichzeitig behoben werden können, können Sie nicht kompatiblen Code in Phasen aktualisieren, indem Sie die Option " **permissive-** Option" aktivieren, einige Fehler beheben und die Option dann wieder deaktivieren. Der Code wird mit den neuen Verbesserungen kompiliert, und Sie können die restlichen Probleme zu einem späteren Zeitpunkt wieder beheben. Beispiele für nicht konformen MSVC-Code finden Sie auf der Seite [/permissive-](../build/reference/permissive-standards-conformance.md) .

- Code, der in einer früheren Version des C++-Standards zulässig war, jedoch in einer späteren Version veraltet ist oder entfernt wurde.

   Wenn Sie ein Upgrade auf einen neueren Sprachstandard durchführen möchten, legen Sie die [Standardoption C++ Language](../build/reference/std-specify-language-standard-version.md) auf den gewünschten Standard fest, und beheben Sie alle Fehler, die ausgelöst werden. Im Allgemeinen wird empfohlen, den Sprachstandard auf [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)festzulegen. Die Fehler, die beim Upgrade auf einen neueren Standard ausgelöst werden, stehen nicht im Zusammenhang mit den Fehlern, die bei Verwendung der **permissive-** Option ausgelöst werden.

- Code, der allen Versionen des Standards entspricht, aber in modernem C++ nicht mehr als bewährte Vorgehensweise gilt.

   Führen Sie die [Code Analyse](/cpp/code-quality/code-analysis-for-c-cpp-overview)aus, um Code zu identifizieren, in dem Änderungen empfohlen werden.

## <a name="open-and-convert-a-legacy-project"></a>Öffnen und Konvertieren eines Legacy Projekts

Wenn Ihr Legacy Projekt auf einer älteren Version von Visual Studio basiert, können Sie es in Visual Studio 2017 oder Visual Studio 2019 öffnen. Visual Studio konvertiert sie automatisch in das aktuelle Projekt Schema mit Unterstützung für alle neuesten Compiler-und IDE-Features.

![Aktualisieren eines Projekts](media/upgrade-dialog-v142.png "Aktualisieren eines Projekts")

Weitere Informationen finden Sie unter [Aktualisieren von C++-Projekten aus früheren Versionen von Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

## <a name="search-the-code-base"></a>Durchsuchen der Codebasis

Das Upgrade einer Codebasis umfasst häufig das Durchsuchen mehrerer Dateien. Um in der Codebasis nach etwas zu suchen, drücken Sie **STRG + T** , um das Feld **Gehe zu allen** suchen zu öffnen.

![Gehe zu allen](media/go-to-all.png "Gehe zu allen")

Um den Suchbereich einzugrenzen, geben Sie einen der Filter mit den 1 Buchstaben ein, gefolgt von einem Leerzeichen und dem gesuchten, das Sie suchen.

## <a name="error-list"></a>Fehlerliste

Nachdem Sie den gewünschten C++-sprach Standard und alle anderen Compileroptionen (**Projekt**  >  **Eigenschaften**  >  **Allgemein**) festgelegt haben, drücken Sie **STRG + UMSCHALT + B** , um das Projekt zu kompilieren. Es ist zu erwarten, dass einige Fehler und Warnungen in Form von roten Wellenlinien an verschiedenen Stellen im Code angezeigt werden. Die Fehler werden auch im **Fehlerliste**angezeigt. Um weitere Informationen zu einem bestimmten Fehler zu erhalten, klicken Sie auf den Fehlercode, um zur Hilfeseite in der Dokumentation zu gelangen. Fehlercodes, die mit "C" beginnen, sind Compilerfehler. Codes, die mit "MSB" beginnen, sind MSBuild-Fehler, die auf ein Problem mit der Projekt Konfiguration hinweisen.

![Compilerfehler und MSBuild-Fehler in Fehlerliste](media/compiler-error-list.png "Compilerfehler und MSBuild-Fehler in Fehlerliste")

## <a name="document-health-indicator"></a>Dokumentintegritätsindikator

Der Dokument Integritäts Indikator unten im Editor zeigt die Anzahl der Fehler und Warnungen im aktuellen Dokument an und ermöglicht es Ihnen, direkt von einer Warnung/einem Fehler zum nächsten zu navigieren.

![Dokument Integritäts Indikator](media/document-health-indicator.png "Dokument Integritäts Indikator")

In vielen Fällen finden Sie weitere Informationen zu einem bestimmten Fehler in der Dokumentation zu Visual Studio-Änderungs Verlauf und den Verbesserungen bei der Konformität.

- [Verbesserungen an C++ bei der Übereinstimmung mit Standards](../overview/cpp-conformance-improvements.md)
- [Visual C++ Änderungs Verlauf 2003-2015](visual-cpp-change-history-2003-2015.md)
- [Überblick über potenzielle Upgradeprobleme (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>Verwenden der Code Analyse zur Modernisierung ihres Codes

Beim Upgrade wird empfohlen, dass Sie die Code Analyse für Ihr Projekt ausführen, damit der Code mindestens den von Microsoft systemeigenen empfohlenen Regeln entspricht. Diese Regeln sind eine Kombination der von Microsoft definierten Regeln und einer Teilmenge der [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines). Wenn Sie diese einhalten, werden häufige Fehlerquellen erheblich reduziert oder beseitigt, und gleichzeitig wird der Code besser lesbar und somit einfacher zu verwalten. Standardmäßig ist die Code Analyse mit den empfohlenen Microsoft-Regeln aktiviert. Sie können zusätzliche Regeln in der **Project**  >  **Properties**  >  **Code Analyse**für Projekteigenschaften aktivieren. Code, der gegen eine der Regeln verstößt, wird als Warnung gekennzeichnet und im Code-Editor mit einer grünen Wellenlinie unterstrichen. Zeigen Sie auf die Wellenlinie, um eine **QuickInfo-QuickInfo** anzuzeigen, in der das Problem beschrieben wird.

![Code Analyse-QuickInfo](media/code-analysis-tooltip.png "Code Analyse Warnung")

Klicken Sie in der Spalte **Code** auf das Filter Symbol, um auszuwählen, welche Warnungen angezeigt werden.

![Code Analyse Filter in Fehlerliste](media/code-analysis-filter.png "Code Analyse Filter in Fehlerliste")

Code Analysefehler und-Warnungen werden auch im **Fehlerliste** wie Compilerfehler angezeigt.

![Code Analyse Warnungen in Fehlerliste](media/code-analysis-error-list.png "Code Analyse Warnungen in Fehlerliste")

Sie können ändern, welche Regeln aktiv sind, und benutzerdefinierte RuleSets erstellen. Weitere Informationen zur Verwendung der Code Analyse finden Sie unter Übersicht über die [Code Analyse für C/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="use-quick-actions-to-modernize-code"></a>Verwenden von schnellen Aktionen zur Modernisierung von Code

Der Code-Editor bietet schnelle Aktionen für einige gängige Empfehlungen. Wenn das Glühbirnen Symbol angezeigt wird, können Sie darauf klicken, um die verfügbaren schnellen Aktionen anzuzeigen.

### <a name="convert-macros-to-constexpr-functions"></a>Konvertieren von Makros in constexpr-Funktionen

Die folgende Abbildung zeigt die Verwendung des Makros mit `AVERAGE` dem Namen, der über die standardmäßige semantische Farbgebung verfügt. Das Bild zeigt außerdem die QuickInfo-QuickInfo an, die angezeigt wird, wenn mit dem Mauszeiger darauf gezeigt wird:

![QuickInfo-Makro Erweiterung](media/macro-expansion-quick-info.png "QuickInfo-QuickInfo-Makro Erweiterung")

Da die Verwendung von Makros in modernem C++ nicht empfehlenswert ist, erleichtert Visual Studio das Konvertieren von Makros in **`constexpr`** Funktionen:

1. Klicken Sie mit der rechten Maustaste auf `AVERAGE` , und wählen Sie **Gehe zu Definition**.
2. Klicken Sie auf das Schrauben Schraubensymbol, und wählen Sie **Makro in constexpr konvertieren** aus.

   ![Schnell Action-Makro in constexpr](media/quick-action-macro-to-constexpr.png "Schnell Action-Makro in constexpr")

Das-Makro wird wie unten dargestellt konvertiert:

![constexpr-Funktion](media/constexpr-function.png "constexpr-Funktion")

Und der-Befehl `AVERAGE` wird jetzt als Funktions aufzurufen markiert, und die QuickInfo zeigt den deduzierten Typ der Funktion an:

![constexpr-Funktionsaufrufe](media/constexpr-function-call.png "constexpr-Funktionsaufrufe")

### <a name="initialize-variables"></a>Initialisieren der Variablen

Nicht initialisierte Variablen können zufällige Werte enthalten, die zu schwerwiegenden Fehlern führen. Die Code Analyse Flags diese Instanzen, und der Editor stellt eine schnelle Aktion bereit:

![Initialisieren einer Variablen](media/init-variable.png "Schnelles Eingreifen der Variablen initialisieren")

### <a name="convert-to-raw-string-literal"></a>Konvertieren in ein Rohzeichenfolgenliteral

Unformatierte Zeichen folgen Literale sind weniger fehleranfällig und bequemer zum eingeben als Zeichen folgen mit eingebetteten Escapezeichen. Klicken Sie mit der rechten Maustaste auf eine Zeichenfolge, und wählen Sie **schnelle Aktionen** aus, um Sie in eine unformatierte Zeichenfolge

![RAW String-wahrsten](media/raw-string-literal.png "RAW String-wahrsten")

Die Zeichenfolge wird in: konvertiert `R"(C:\Users\bjarnes\demo\output.txt)"` .
