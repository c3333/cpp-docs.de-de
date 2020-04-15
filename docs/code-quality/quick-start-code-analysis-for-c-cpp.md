---
title: 'Schnellstart: Codeanalyse für C/C++'
description: Führen Sie statische Analysen für C++-Code in Visual Studio aus, um häufige Codierungsprobleme und -fehler zu erkennen.
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370570"
---
# <a name="quickstart-code-analysis-for-cc"></a>Schnellstart: Codeanalyse für C/C++

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C++-Code regelmäßig ausgeführt werden. Die Codeanalyse kann Ihnen dabei helfen, häufige Probleme und Verstöße gegen die gute Programmierpraxis zu finden. Und es findet Mängel, die durch Tests schwer zu entdecken sind. Seine Warnungen unterscheiden sich von Compilerfehlern und Warnungen: Es sucht nach bestimmten Codemustern, von denen bekannt ist, dass sie Probleme verursachen. Das heißt, Code, der gültig ist, aber dennoch Probleme verursachen kann, entweder für Sie oder für andere Personen, die Ihren Code verwenden.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurieren von Regelsätzen für ein Projekt

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den Projektnamen, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie optional in den **Konfigurations-** und **Plattformlisten** die Buildkonfiguration und die Zielplattform aus.

1. Um die Codeanalyse jedes Mal auszuführen, wenn das Projekt mithilfe der ausgewählten Konfiguration erstellt wird, aktivieren Sie das Kontrollkästchen **Codeanalyse unter Build aktivieren.** Sie können die Codeanalyse auch manuell ausführen, indem Sie das Menü **Analysieren** öffnen und dann **Codeanalyse für** *ProjectName* ausführen oder **Codeanalyse für Datei ausführen**auswählen.

1. Wählen Sie den [Regelsatz](using-rule-sets-to-specify-the-cpp-rules-to-run.md) aus, den Sie verwenden möchten, oder erstellen Sie einen [benutzerdefinierten Regelsatz](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Wenn Sie LLVM/clang-cl verwenden, finden Sie weitere Informationen unter [Verwenden von Clang-Tidy in Visual Studio](../code-quality/clang-tidy.md) zum Konfigurieren von Clang-Tidy-Analyseoptionen.

### <a name="standard-cc-rule-sets"></a>Standard C/C++-Regelsätze

Visual Studio enthält die folgenden Standardsätze von Regeln für systemeigenen Code:

| Regelsatz | BESCHREIBUNG |
|--|--|
| **C++Core Check Arithmetische Regeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit [arithmetischen Vorgängen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **C++-Kernprüfregeln** | Mit diesen Regeln wird das [Bounds-Profil der C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)erzwungen. |
| **C++-Kernprüfungsklassenregeln** | Diese Regeln erzwingen Prüfungen, die sich auf [Klassen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies)beziehen. |
| **C++-Kernprüfungsparallelitätsregeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit [Parallelität aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency). |
| **C++Core Check Const-Regeln** | Diese Regeln erzwingen [const-bezogene Prüfungen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). |
| **C++-Kernprüfungsdeklarationsregeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit [Deklarationen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces). |
| **C++-Core-Überprüfungs-Enum-Regeln** | Diese Regeln erzwingen [Enum-bezogene Prüfungen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). |
| **C++Core Check Experimentelle Regeln** | Diese Regeln sammeln einige experimentelle Kontrollen. Letztendlich erwarten wir, dass diese Prüfungen auf andere Regelsätze verschoben oder vollständig entfernt werden. |
| **C++-Kernprüfungsfunktionsregeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit [Funktionen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions). |
| **C++-Core-Check-GSL-Regeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit der [Richtliniensupportbibliothek aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). |
| **C++-Kernüberprüfungs-Lebensdauerregeln** | Diese Regeln erzwingen das [Lifetime-Profil der C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). |
| **C++Core Check Owner Pointer Rules** | Diese Regeln erzwingen Ressourcenverwaltungsprüfungen im Zusammenhang mit [Besitzer&lt;T&gt; aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **C++-Kernprüfung Rohzeigerregeln** | Diese Regeln erzwingen Ressourcenverwaltungsprüfungen im Zusammenhang mit [Unformatzeigern aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **C++-Kernprüfregeln** | Diese Regeln erzwingen eine Teilmenge der Prüfungen aus den [C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines). Verwenden Sie diesen Regelsatz, um alle C++-Kernprüfungsregeln mit Ausnahme der Enum- und Experimental-Regelsätze einzuschließen. |
| **C++-Kernprüfung freigegebener Zeigerregeln** | Diese Regeln erzwingen Ressourcenverwaltungsprüfungen im Zusammenhang mit [Typen mit freigegebener Zeigersemantik aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **C++-Core-Check-STL-Regeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit der [C++-Standardvorlagenbibliothek (STL) aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib). |
| **C++-Kernprüfungsstilregeln** | Diese Regeln erzwingen Prüfungen im Zusammenhang mit der Verwendung von [Ausdrücken und Anweisungen aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **C++-Kernprüfungstypregeln** | Diese Regeln erzwingen das [Typprofil der C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). |
| **C++-Kernprüfung Eindeutige Zeigerregeln** | Diese Regeln erzwingen Ressourcenverwaltungsprüfungen für Typen mit [eindeutiger Zeigersemantik aus den C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Parallelitätsprüfungsregeln** | Diese Regeln erzwingen einen Satz von Win32-Parallelitätsmusterprüfungen in C++. |
| **Parallelitätsregeln** | Fügt Parallelitätsregeln aus C++-Kernrichtlinien zu **Parallelitätsprüfungsregeln**hinzu. |
| **Microsoft Native-Mindestregeln** | Diese Regeln konzentrieren sich auf die wichtigsten Probleme in Ihrem systemeigenen Code, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürze. Es wird empfohlen, diesen Regelsatz in jeden benutzerdefinierten Regelsatz aufzunehmen, den Sie für Ihre systemeigenen Projekte erstellen. |
| **Von Microsoft empfohlene Regeln für eigene Projekte** | Diese Regeln konzentrieren sich auf die kritischsten und häufigsten Probleme in Ihrem systemeigenen Code. Zu diesen Problemen gehören potenzielle Sicherheitslücken und Anwendungsabstürze. Es wird empfohlen, diesen Regelsatz in jeden benutzerdefinierten Regelsatz aufzunehmen, den Sie für Ihre systemeigenen Projekte erstellen. Dieser Regelsatz ist für die Verwendung mit Visual Studio Professional Edition und höher vorgesehen. Sie enthält alle Regeln in **Microsoft Native Minimum Rules**. |

Visual Studio enthält die folgenden Standardsätze von Regeln für verwalteten Code:

| Regelsatz | BESCHREIBUNG |
|--|--|
| **Microsoft Basic Correctness-Regeln** | Diese Regeln zielen auf logische Fehler und häufige Irrtümer bei der Verwendung von Framework-APIs ab. Binden Sie diesen Regelsatz zur Erweiterung der Liste von Warnungen mit ein, die von den empfohlenen Mindestregeln gemeldet werden. |
| **Microsoft Basic Design-Richtlinienregeln** | Diese Regeln zielen auf die Erzwingung von Best Practices ab, sodass Ihr Code leicht verständlich und einfach zu verwenden ist. Binden Sie diesen Regelsatz mit ein, wenn Ihr Projekt Bibliothekscode umfasst oder wenn Sie Best Practices erzwingen möchten, um einen leicht verwaltbaren Code zu gewährleisten. |
| **Microsoft Extended Correctness-Regeln** | Diese Regeln erweitern die grundlegenden Korrektheitsregeln, um die gemeldeten Logik- und Frameworkverwendungsfehler zu maximieren. Besonderes Augenmerk wird auf spezifische Szenarien gelegt, z. B. COM-Interop und mobile Anwendungen. Binden Sie diesen Regelsatz mit ein, wenn eines dieser Szenarien auf Ihr Projekt zutrifft, oder um weitere Probleme in Ihrem Projekt zu ermitteln. |
| **Microsoft Extended Design-Richtlinienregeln** | Diese Regeln erweitern die grundlegenden Entwurfsrichtlinienregeln, um die gemeldeten Usability- und Wartbarkeitsprobleme zu maximieren. Besonderes Augenmerk wird auf Benennungsrichtlinien gelegt. Binden Sie diesen Regelsatz mit ein, wenn Ihr Projekt Bibliothekscode umfasst, oder wenn Sie höchste Standards für das Schreiben von verwaltbarem Code erzwingen möchten. |
| **Microsoft-Globalisierungsregeln** | Diese Regeln zielen auf Probleme ab, durch die verhindert wird, dass Daten in Ihrer Anwendung bei Verwendung in unterschiedlichen Sprachen, Gebietsschemas und Kulturen ordnungsgemäß angezeigt werden. Fügen Sie diesen Regelsatz ein, wenn Ihre Anwendung lokalisiert und/oder globalisiert ist. |
| **Microsoft Managed Minimum Rules** | Diese Regeln zielen auf die kritischsten Probleme in Ihrem Code ab, für die die Codeanalyse die genaueste Lösung darstellt.  Es gibt nur wenige dieser Regeln und sie sind nur für die Verwendung in begrenzten Visual Studio-Editionen vorgesehen.  Verwenden Sie MinimumRecommendedRules.ruleset in Verbindung mit anderen Visual Studio-Editionen. |
| **Microsoft Managed Recommended Rules** | Diese Regeln konzentrieren sich auf die wichtigsten Probleme im Code. Zu diesen Problemen gehören potenzielle Sicherheitslücken, Anwendungsabstürze und andere wichtige Logik- und Konstruktionsfehler. Es wird empfohlen, diesen Regelsatz in jeden benutzerdefinierten Regelsatz aufzunehmen, den Sie für Ihre Projekte erstellen. |
| **Microsoft Mixed (C++ /CLR) Mindestregeln** | Diese Regeln konzentrieren sich auf die kritischsten Probleme in Ihren C++-Projekten, die die Common Language Runtime unterstützen. Zu diesen Problemen gehören potenzielle Sicherheitslücken, Anwendungsabstürze und andere wichtige Logik- und Konstruktionsfehler. Es wird empfohlen, diesen Regelsatz in jeden benutzerdefinierten Regelsatz aufzunehmen, den Sie für Ihre C++-Projekte erstellen, die die Common Language Runtime unterstützen. |
| **Microsoft Mixed (C++ /CLR) Empfohlene Regeln** | Diese Regeln konzentrieren sich auf die häufigsten und kritischsten Probleme in Ihren C++-Projekten, die die Common Language Runtime unterstützen. Zu diesen Problemen gehören potenzielle Sicherheitslücken, Anwendungsabstürze und andere wichtige Logik- und Konstruktionsfehler. Dieses Regelwerk ist für die Verwendung in der Visual Studio Professional-Edition und höher konzipiert. |
| **Microsoft-Sicherheitsregeln** | Dieser Regelsatz enthält alle Microsoft-Sicherheitsregeln. Binden Sie diesen Regelsatz mit ein, um die Anzahl gemeldeter potenzieller Sicherheitsprobleme zu maximieren. |

So schließen Sie jede Regel ein:

| Regelsatz | BESCHREIBUNG |
|--|--|
| **Microsoft Alle Regeln** | Dieser Regelsatz enthält alle Regeln. Das Ausführen dieses Regelsatzes führt möglicherweise zu einer hohen Anzahl gemeldeter Warnungen. Verwenden Sie diesen Regelsatz, um einen Überblick über alle Probleme in Ihrem Code zu erhalten. Es kann Ihnen helfen, zu entscheiden, welche der fokussierteren Regelsätze für Ihre Projekte am besten geeignet sind. |

## <a name="run-code-analysis"></a>Codeanalyse ausführen

Auf der Seite **Codeanalyse** des Dialogfelds Projekteigenschaften können Sie die Codeanalyse so konfigurieren, dass sie jedes Mal ausgeführt wird, wenn Sie Ihr Projekt erstellen. Sie können die Codeanalyse auch manuell ausführen.

Zum Ausführen der Codeanalyse in einer Projektmappe:

- Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen**aus.

Zum Ausführen der Codeanalyse in einem Projekt:

1. Wählen Sie im Projektmappen-Explorer den Namen des Projekts aus.

1. Wählen Sie im Menü **Build** die Option **Codeanalyse für** *Projektnamen ausführen*aus.

So führen Sie die Codeanalyse für eine Datei aus:

1. Wählen Sie im Projektmappen-Explorer den Namen der Datei aus.

1. Wählen Sie im Menü **Build** die Option **Codeanalyse in Datei ausführen** aus oder drücken Sie **Strg+Umschalt+Alt+F7**.

   Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt. Die Ergebnisse werden im Fenster Fehlerliste angezeigt.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analysieren und Auflösen von Codeanalysewarnungen

Im Fenster Fehlerliste werden die gefundenen Codeanalysewarnungen aufgelistet. Die Ergebnisse werden in einer Tabelle angezeigt. Wenn weitere Informationen zu einer bestimmten Warnung verfügbar sind, enthält die erste Spalte ein Erweiterungssteuerelement. Wählen Sie es aus, um die Anzeige zu erweitern, um weitere Informationen zum Problem zu erhalten. Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat.

Um detaillierte Informationen über die Warnung, einschließlich möglicher Lösungen für das Problem, zu erhalten, wählen Sie die Warn-ID in der Spalte Code aus, um den entsprechenden Online-Hilfeartikel anzuzeigen.

Doppelklicken Sie auf eine Warnung, um den Cursor in die Codezeile zu bewegen, die die Warnung im Visual Studio-Codeeditor verursacht hat. Oder drücken Sie die Eingabetaste auf die ausgewählte Warnung.

Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben. Führen Sie dann die Codeanalyse erneut aus, um sicherzustellen, dass die Warnung nicht mehr in der Fehlerliste angezeigt wird.

## <a name="create-work-items-for-code-analysis-warnings"></a>Erstellen von Arbeitsaufgaben für Codeanalysewarnungen

Funktionen für die Arbeitselementeverfolgung können Sie in Visual Studio protokollieren. Um diese Funktion verwenden zu können, müssen Sie eine Verbindung mit einer Instanz von Azure DevOps Server (früher Team Foundation Server) herstellen.

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Erstellen eine Arbeitsaufgabe für eine oder mehrere Warnungen für C/C++-Code

1. Erweitern und wählen Sie in der Fehlerliste die Warnungen aus

1. Wählen Sie im Kontextmenü für die Warnungen die Option **Arbeitsaufgabe erstellen**aus, und wählen Sie dann den Arbeitsaufgabentyp aus.

1. Visual Studio erstellt ein einzelnes Arbeitselement für die ausgewählten Warnungen und zeigt das Arbeitselement in einem Dokumentfenster der IDE.

1. Fügen Sie zusätzliche Informationen hinzu, und wählen Sie dann **Arbeitsaufgabe speichern**aus.

## <a name="search-and-filter-code-analysis-results"></a>Such- und Filtercodeanalyseergebnisse

Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.

- **So filtern Sie Warnungen nach Titel oder Warnungs-ID:** Geben Sie das Schlüsselwort in das Feld Suchfehlerliste ein.

- **So filtern Sie Warnungen nach Schweregrad:** Standardmäßig wird Codeanalysemeldungen der Schweregrad **Warnung**zugewiesen. Sie können den Schweregrad einer oder mehrerer Nachrichten als **Fehler** in einem benutzerdefinierten Regelsatz zuweisen. Wählen Sie in der Spalte **Schweregrad** der **Fehlerliste**den Dropdown-Pfeil und dann das Filtersymbol aus. Wählen Sie **Warnung** oder **Fehler** aus, um nur die Meldungen anzuzeigen, denen der jeweilige Schweregrad zugewiesen ist. Wählen **Sie Alle auswählen,** um alle Meldungen anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Codeanalyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
