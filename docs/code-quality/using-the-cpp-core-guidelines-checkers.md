---
title: Verwenden der Überprüfungen für C++ Core Guidelines
description: Einrichten und Verwenden der Microsoft C++-Code Analyse Regeln für C++ Core Guidelines.
ms.date: 07/27/2020
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 4fb06b0f78c93e6b76e0b8d64d7dfbdc541cf299
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334142"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Verwenden der Überprüfungen für C++ Core Guidelines

Die C++ Core Guidelines sind ein portabler Satz an Richtlinien, Regeln und bewährten Methoden zum Programmieren in C++, die von C++-Experten und-Designern erstellt werden. Visual Studio unterstützt derzeit eine Teilmenge dieser Regeln als Teil der Code Analysetools für C++. Die wichtigsten Leitfäden werden standardmäßig in Visual Studio 2017 und Visual Studio 2019 installiert. Sie sind [als nuget-Paket für Visual Studio 2015 verfügbar](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Das C++ Core Guidelines Projekt

Die C++ Core Guidelines von Bjarne Stroustrup und anderen erstellt, sind ein Leitfaden zur sicheren und effektiven Verwendung moderner C++. Die Richtlinien betonen die statische Typsicherheit und die Ressourcensicherheit. Sie identifizieren Möglichkeiten, um die Fehler anfälligsten Teile der Sprache zu eliminieren oder zu minimieren. Außerdem wird empfohlen, den Code einfacher und zuverlässiger zu gestalten und eine bessere Leistung zu erzielen. Diese Richtlinien werden von der Standard mäßigen C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)und Zugriff auf die C++ Core Guidelines Dokumentationsprojekt Dateien auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren der C++ Core Check Richtlinien in der Code Analyse

::: moniker range="<=msvc-150"

Eine Teilmenge der C++ Core Check Regeln ist im systemeigenen empfohlenen Microsoft-Regelsatz enthalten. Dies ist der Regelsatz, der standardmäßig ausgeführt wird, wenn die Code Analyse aktiviert ist.

### <a name="to-enable-code-analysis-on-your-project"></a>So aktivieren Sie die Code Analyse für Ihr Projekt

1. Öffnen Sie das Dialogfeld  **Eigenschaften Seiten** für das Projekt.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **Code Analyse** aus.

1. Aktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** .

![Eigenschaften Seite für allgemeine Code Analyse Einstellungen](media/cppcorecheck_codeanalysis_general.png)

Öffnen Sie die Dropdown Liste, und wählen Sie die Regelsätze aus, die Sie einschließen möchten, um zusätzliche kernregel Regeln zu aktivieren:

![Dropdown für zusätzliche C++ Core Check Regelsätze](media/cppcorecheck_codeanalysis_extensions.png)

::: moniker-end
::: moniker range=">=msvc-160"

Eine Teilmenge der C++ Core Check Regeln ist im systemeigenen empfohlenen Microsoft-Regelsatz enthalten. Dies ist der Regelsatz, der standardmäßig ausgeführt wird, wenn die Microsoft-Code Analyse aktiviert ist.

### <a name="to-enable-code-analysis-on-your-project"></a>So aktivieren Sie die Code Analyse für Ihr Projekt:

1. Öffnen Sie das Dialogfeld  **Eigenschaften Seiten** für das Projekt.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **Code Analyse** aus.

1. Legen Sie die Eigenschaften **Code Analyse für Build aktivieren** und **Microsoft-Code Analyse aktivieren** fest.

Sie haben auch die Möglichkeit, alle unterstützten C++ Core Check Regeln auszuführen, oder Sie können eine eigene Teilmenge auswählen, um Folgendes auszuführen:

### <a name="to-enable-additional-core-check-rules"></a>So aktivieren Sie zusätzliche kernregel Regeln

1. Öffnen Sie das Dialogfeld  **Eigenschaften Seiten** für das Projekt.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **Code Analyse** > **Microsoft** aus.

1. Öffnen Sie die Dropdown Liste **aktive Regeln** , und wählen Sie **mehrere Regelsätze** auswählen aus.

1. Wählen Sie im Dialogfeld **Regelsätze hinzufügen oder entfernen** die Regelsätze aus, die Sie einschließen möchten.

::: moniker-end

## <a name="examples"></a>Beispiele

Im folgenden finden Sie ein Beispiel für einige der Probleme, die die C++ Core Check Regeln finden können:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

In diesem Beispiel werden einige der Warnungen veranschaulicht, die die C++ Core Check Regeln finden können:

- C26494 ist vom Regeltyp. 5: Initialisieren Sie immer ein Objekt.

- C26485 ist Regel Begrenzungen. 3: kein Array-zu-Zeiger-Zerfall.

- C26481 ist Regel Begrenzungen. 1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.

Installieren und aktivieren Sie die C++ Core Check Code Analyse-Regelsätze, und kompilieren Sie dann diesen Code. Die Code Analyse gibt die ersten beiden Warnungen aus und unterdrückt die dritte. Hier ist die Buildausgabe des Beispielcodes in Visual Studio 2015:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Die C++ Core Guidelines sind vorhanden, damit Sie besseren und sichereren Code schreiben können. Möglicherweise finden Sie jedoch eine Instanz, in der eine Regel oder ein Profil nicht angewendet werden sollte. Es ist einfach, ihn direkt im Code zu unterdrücken. Sie können das- `[[gsl::suppress]]` Attribut verwenden, um zu verhindern, dass C++ Core Check jegliche Verstöße gegen eine Regel im folgenden Codeblock erkennen und melden. Sie können einzelne Anweisungen markieren, um bestimmte Regeln zu unterdrücken. Sie können sogar das gesamte Begrenzungen-Profil unterdrücken, indem Sie schreiben, `[[gsl::suppress(bounds)]]` ohne eine bestimmte Regel Nummer einzubeziehen.

## <a name="supported-rule-sets"></a>Unterstützte Regelsätze

Wenn der C++ Core Guidelines Prüfung neue Regeln hinzugefügt werden, kann sich die Anzahl der Warnungen, die für bereits vorhandenen Code erzeugt werden, erhöhen. Sie können vordefinierte Regelsätze verwenden, um zu filtern, welche Arten von Regeln aktiviert werden sollen. Referenz Artikel zu den meisten Regeln finden Sie unter [Visual Studio C++ Core Check Referenz](code-analysis-for-cpp-corecheck.md).

- **Arithmetische Regeln** : Regeln zum Erkennen von arithmetischen [Überlauf](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow) [-, signierten, nicht signierten Vorgängen](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned)und [Bitmanipulation](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative). <sup>15,6</sup>

- Begrenzungs **Regeln** : erzwingen Sie das [Rahmenprofil der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile). <sup>15,3</sup>

- **Klassenregeln** : einige Regeln, die sich auf die ordnungsgemäße Verwendung von speziellen Member-Funktionen und virtuellen Spezifikationen konzentrieren. Dabei handelt es sich um eine Teilmenge der Überprüfungen, die für [Klassen und Klassenhierarchien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)empfohlen werden. <sup>15,5</sup>

- Parallelitäts **Regeln** : eine einzelne Regel, die fehlerhafte Wächter Objekt Deklarationen abfängt. Weitere Informationen finden Sie unter [Richtlinien im Zusammenhang mit](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)der Parallelität. <sup>15,5</sup>

- **Regeln für konstantenregeln** : erzwingen Sie [die Überprüfung auf Konstanten aus der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). <sup>15,3</sup>

- **Deklarations Regeln** : einige Regeln aus den [Schnittstellen Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) , die sich darauf konzentrieren, wie globale Variablen deklariert werden. <sup>15,5</sup>

- **Enum-Regeln** : diese Regeln erzwingen [Aufzählungs bezogene Überprüfungen aus dem C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). <sup>16,3</sup>

- **Experimentelle Regeln** Dies sind experimentelle C++ Core Check Regeln, die nützlich sind, aber nicht für die alltägliche Verwendung bereit sind. Probieren Sie es aus, und geben Sie uns [Feedback](https://aka.ms/feedback/suggest?space=62). <sup>16,0</sup>

- **Funktions Regeln** : zwei Überprüfungen, die bei der Annahme des **`noexcept`** Spezifizierers helfen. Sie sind Teil der Richtlinien für den [klaren Funktions Entwurf und die Implementierung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions). <sup>15,5</sup>

- **Gsl-Regeln** : diese Regeln erzwingen Überprüfungen im Zusammenhang mit der [Unterstützungs Bibliothek für Richtlinien aus der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). <sup>15,7</sup>

- **Lebensdauer Regeln** : diese Regeln erzwingen das [Lebensdauer Profil der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). <sup>15,7</sup>

- **Besitzer Zeiger Regeln** : erzwingen [Sie Ressourcen Verwaltungs Prüfungen im Zusammenhang mit \<T> dem Besitzer aus der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup> 15,3</sup>

- **Rohzeiger Regeln** : erzwingen [Sie Ressourcen Verwaltungs Prüfungen im Zusammenhang mit unformatierten Zeigern aus der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup>15,3</sup>

- Frei **gegebene Zeiger Regeln** : Sie sind Teil der Erzwingung von Richtlinien zur [Ressourcenverwaltung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) . <sup>15,5</sup> wir haben einige Regeln hinzugefügt, die für die Übergabe von freigegebenen Zeigern an Funktionen und die Verwendung von lokal verwendet werden.

- **STL-Regeln** : diese Regeln erzwingen Überprüfungen im Zusammenhang mit der [C++-Standard Bibliothek (STL) aus dem C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib). <sup>15,7</sup>

- **Stilregeln** : eine einfache, aber wichtige Überprüfung, die die Verwendung von [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)verbietet. <sup>15,5</sup> es ist der erste Schritt, den Codierungsstil und die Verwendung von Ausdrücken und Anweisungen in C++ zu verbessern.

- **Typregeln** : erzwingen Sie das [Typprofil der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). <sup>15,3</sup>

- **Eindeutige Zeiger Regeln** : erzwingen [Sie Ressourcen Verwaltungs Prüfungen in Bezug auf Typen mit eindeutiger Zeiger Semantik aus der C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). <sup>15,3</sup>

- **C++ Core Check Regeln** : Dieser Regelsatz enthält alle derzeit implementierten Überprüfungen des [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines), mit Ausnahme der experimentellen Regeln.

<sup>15,3</sup> diese Regeln wurden zuerst in Visual Studio 2017, Version 15,3 \, angezeigt.
<sup>15,5</sup> diese Regeln wurden zuerst in Visual Studio 2017, Version 15,5 \, angezeigt.
<sup>15,6</sup> diese Regeln wurden zuerst in Visual Studio 2017, Version 15,6 \, angezeigt.
<sup>15,7</sup> diese Regeln wurden zuerst in Visual Studio 2017, Version 15,7 \, angezeigt.
<sup>16,0</sup> diese Regeln wurden zuerst in Visual Studio 2019, Version 16,0 \, angezeigt.
<sup>16,3</sup> diese Regeln wurden zuerst in Visual Studio 2019, Version 16,3, angezeigt.

Sie können Warnungen auf nur eine oder mehrere Gruppen beschränken. Die systemeigenen empfohlenen **Minimal** -und systemeigenen **empfohlenen** Regelsätze umfassen C++ Core Check Regeln und andere vorab Überprüfungen.

::: moniker range="<=msvc-150"

Öffnen Sie das Dialogfeld " **Projekteigenschaften** ", um die verfügbaren Regelsätze anzuzeigen. Wählen Sie im Dialogfeld Eigenschaften **Seiten** die **Eigenschaften**  >  Seite allgemeine **Code Analyse** für die Konfiguration aus  >  **General** . Öffnen Sie dann im Kombinations Feld **Regelsätze** die Dropdown Liste, um die verfügbaren Regelsätze anzuzeigen. Wählen Sie **mehrere Regelsätze** auswählen aus, um eine benutzerdefinierte Kombination von Regelsätzen zu erstellen. Im Dialogfeld **Regelsätze hinzufügen oder entfernen** werden die Regeln aufgelistet, aus denen Sie auswählen können. Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [Verwenden von Regelsätzen zum Angeben der zu testenden C++ Regeln](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

::: moniker-end
::: moniker range=">=msvc-160"

Öffnen Sie das Dialogfeld " **Projekteigenschaften** ", um die verfügbaren Regelsätze anzuzeigen. Wählen Sie im Dialogfeld Eigenschaften **Seiten** die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **Code Analyse**  >  **Microsoft** aus. Öffnen Sie dann die Dropdown Liste im Kombinations Feld **aktive Regeln** , um die verfügbaren Regelsätze anzuzeigen. Wählen Sie **mehrere Regelsätze** auswählen aus, um eine benutzerdefinierte Kombination von Regelsätzen zu erstellen. Im Dialogfeld **Regelsätze hinzufügen oder entfernen** werden die Regeln aufgelistet, aus denen Sie auswählen können. Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [Verwenden von Regelsätzen zum Angeben der zu testenden C++ Regeln](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

::: moniker-end

## <a name="macros"></a>Makros

Die C++ Core Guidelines Prüfung enthält eine Header Datei, die Makros definiert, die das unterdrücken ganzer Kategorien von Warnungen im Code vereinfachen:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Diese Makros entsprechen den Regelsätzen und werden in eine durch Leerzeichen getrennte Liste mit Warnungs Nummern erweitert. Mithilfe der entsprechenden Pragma-Konstrukte können Sie den effektiven Satz von Regeln konfigurieren, der für ein Projekt oder einen Code Abschnitt interessant ist. Im folgenden Beispiel werden bei der Code Analyse nur fehlende konstantenmodifiziererer gewarnt:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attribute

Der Microsoft C++-Compiler hat eingeschränkte Unterstützung für das- `[[gsl::suppress]]` Attribut. Sie kann verwendet werden, um Warnungen für Ausdrucks-und Block Anweisungen innerhalb von Funktionen zu unterdrücken.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Analyse mithilfe von Befehlszeilenoptionen unterdrücken

Anstelle #Pragmas können Sie die Befehlszeilenoptionen auf der Eigenschaften Seite der Datei verwenden, um Warnungen für ein Projekt oder eine einzelne Datei zu unterdrücken. So deaktivieren Sie z. b. die Warnung C26400 für eine Datei:

1. Klicken Sie mit der rechten Maustaste auf **Projektmappen-Explorer** , und wählen Sie **Eigenschaften** aus.

1. Wählen Sie im Dialogfeld Eigenschaften **Seiten** die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie im Bearbeitungsfeld **zusätzliche Optionen** hinzu *`/wd26400`* .

Sie können die Befehlszeilenoption verwenden, um die gesamte Code Analyse für eine Datei temporär zu deaktivieren, indem Sie angeben **`/analyze-`** . Sie sehen eine Warnung *D9025 Überschreiben von "/Analyze" mit "/Analyze-"* , die Sie daran erinnert, die Code Analyse später erneut zu aktivieren.

## <a name="enable-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a> Aktivieren der C++ Core Guidelines Prüfung für bestimmte Projektdateien

Manchmal ist es hilfreich, eine fokussierte Code Analyse durchzuführen und die Visual Studio-IDE weiterhin zu verwenden. Verwenden Sie das folgende Beispielszenario für große Projekte. Sie kann die Buildzeit sparen und das Filtern von Ergebnissen vereinfachen:

1. Legen Sie in der Befehlsshell `esp.extension` die `esp.annotationbuildlevel` Umgebungsvariablen und fest.

1. Um diese Variablen zu erben, öffnen Sie Visual Studio über die Befehlsshell.

1. Laden Sie das Projekt, und öffnen Sie seine Eigenschaften.

1. Aktivieren Sie die Code Analyse, wählen Sie die entsprechenden Regelsätze aus, aktivieren Sie jedoch keine Code Analyse Erweiterungen.

1. Wechseln Sie zu der Datei, die Sie mit der C++ Core Guidelines Prüfung analysieren möchten, und öffnen Sie die zugehörigen Eigenschaften.

1. Wählen Sie **Konfigurations Eigenschaften**  >  **C/C++**  >  **Befehlszeile**  >  **zusätzliche Optionen** aus, und fügen Sie hinzu. *`/analyze:plugin EspXEngine.dll`*

1. Deaktivieren Sie die Verwendung des vorkompilierten Headers ( **Konfigurations Eigenschaften**  >  : vorkompilierte **C/C++-**  >  **Header** ). Dies ist erforderlich, da das Erweiterungsmodul möglicherweise versucht, seine internen Informationen aus dem vorkompilierten Header (PCH) zu lesen. Wenn das PCH mit Standard Projektoptionen kompiliert wurde, ist es nicht kompatibel.

1. Erstellen Sie das Projekt neu. Die allgemeinen PREfast-Überprüfungen sollten für alle Dateien ausgeführt werden. Da die C++ Core Guidelines Prüfung nicht standardmäßig aktiviert ist, sollte Sie nur in der Datei ausgeführt werden, die für deren Verwendung konfiguriert ist.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Verwenden der C++ Core Guidelines Checker außerhalb von Visual Studio

Sie können die C++ Core Guidelines Überprüfungen in automatisierten Builds verwenden.

### <a name="msbuild"></a>MSBuild

Der Native Code Analysis Checker (PREfast) ist in die MSBuild-Umgebung durch benutzerdefinierte Zieldateien integriert. Sie können die Projekteigenschaften verwenden, um es zu aktivieren, und die C++ Core Guidelines Prüfung (auf der Grundlage von PREfast) hinzufügen:

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Stellen Sie sicher, dass Sie diese Eigenschaften vor dem Importieren der Datei hinzufügen *`Microsoft.Cpp.targets`* . Sie können bestimmte Regelsätze auswählen oder einen benutzerdefinierten Regelsatz erstellen. Oder verwenden Sie den Standard Regelsatz, der andere vorab Überprüfungen enthält.

Sie können C++ Core Checker nur für angegebene Dateien ausführen. Verwenden Sie den gleichen Ansatz wie [zuvor beschrieben](#corecheck_per_file), aber verwenden Sie MSBuild-Dateien. Die Umgebungsvariablen können mithilfe des-Elements festgelegt werden `BuildMacro` :

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Wenn Sie die Projektdatei nicht ändern möchten, können Sie Eigenschaften in der Befehlszeile übergeben:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Nicht-MSBuild-Projekte

Wenn Sie ein Buildsystem verwenden, das nicht auf MSBuild beruht, können Sie die Prüfung trotzdem ausführen. Um es zu verwenden, müssen Sie sich mit einigen Internalen der Code Analyse-Engine-Konfiguration vertraut machen. Wir garantieren keine Unterstützung für diese internale in zukünftigen Versionen von Visual Studio.

Die Code Analyse erfordert einige Umgebungsvariablen und Compilerbefehlszeilenoptionen. Wir empfehlen Ihnen die Verwendung der **native Tools-Eingabe** Aufforderungs Umgebung, sodass Sie nicht nach bestimmten Pfaden für den Compiler suchen müssen, Verzeichnisse einschließen usw.

- **Umgebungsvariablen**
  - `set esp.extensions=cppcorecheck.dll` Dies weist die Engine an, das C++ Core Guidelines-Modul zu laden.
  - `set esp.annotationbuildlevel=ignore` Dadurch wird die Logik zum Verarbeiten von Sal-Anmerkungen deaktiviert. Anmerkungen wirken sich nicht auf die Code Analyse im C++ Core Guidelines Checker aus, ihre Verarbeitung dauert jedoch Zeit (manchmal sehr lange). Diese Einstellung ist optional, wird jedoch dringend empfohlen.
  - `set caexcludepath=%include%` Es wird dringend empfohlen, Warnungen zu deaktivieren, die für Standard Header ausgelöst werden. Hier können Sie weitere Pfade hinzufügen, z. b. den Pfad zu den allgemeinen Headern in Ihrem Projekt.

- **Befehlszeilenoptionen**
  - **`/analyze`**  Aktiviert die Code Analyse (Beachten Sie auch **`/analyze:only`** und **`/analyze:quiet`** ).
  - **`/analyze:plugin EspXEngine.dll`** Mit dieser Option wird die Engine für die Code Analyse Erweiterungen in den PREfast-Wert geladen. Diese Engine lädt wiederum den C++ Core Guidelines Checker.

## <a name="use-the-guideline-support-library"></a>Verwenden der Unterstützungs Bibliothek für Richtlinien

Die Richtlinien-Unterstützungs Bibliothek (GSL) soll Ihnen helfen, die grundlegenden Richtlinien zu befolgen. Die GSL enthält Definitionen, mit denen Sie fehleranfällige Konstrukte durch sicherere Alternativen ersetzen können. Beispielsweise können Sie ein `T*, length` Parameter paar durch den `span<T>` Typ ersetzen. Die GSL ist unter verfügbar [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Die Bibliothek ist Open Source, sodass Sie die Quellen anzeigen, Kommentare erstellen oder mitwirken können. Das Projekt finden Sie unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

::: moniker range="msvc-140"

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a> Verwenden der C++ Core Check-Richtlinien in Visual Studio 2015-Projekten

Wenn Sie Visual Studio 2015 verwenden, werden die C++ Core Check Code Analyse-Regelsätze standardmäßig nicht installiert. Bevor Sie die C++ Core Check Code Analysetools in Visual Studio 2015 aktivieren können, sind zusätzliche Schritte erforderlich. Microsoft bietet Unterstützung für Visual Studio 2015-Projekte mithilfe eines nuget-Pakets. Das Paket heißt "Microsoft. cppcorecheck" und ist unter verfügbar [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Für dieses Paket ist mindestens Visual Studio 2015 mit installiertem Update 1 erforderlich.

Das Paket installiert auch ein anderes Paket als Abhängigkeit, die nur-Header-Richtlinien-Unterstützungs Bibliothek (GSL). Die GSL ist auch auf GitHub unter verfügbar [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

Aufgrund der Art und Weise, wie die Code Analyse Regeln innerhalb von Visual Studio 2015 geladen werden, müssen Sie das `Microsoft.CppCoreCheck` nuget-Paket in jedem C++-Projekt installieren, das Sie überprüfen möchten.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>So fügen Sie dem Projekt das Microsoft. cppcorecheck-Paket in Visual Studio 2015 hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf, um das Kontextmenü Ihres Projekts in der Projekt Mappe zu öffnen, der Sie das Paket hinzufügen möchten. Wählen Sie **nuget-Pakete verwalten** , um den **nuget-Paket-Manager** zu öffnen.

1. Suchen Sie im Fenster **nuget-Paket-Manager** nach Microsoft. cppcorecheck.

    ![Das Fenster des nuget-Paket-Managers zeigt das cppcorecheck-Paket](../code-quality/media/cppcorecheck_nuget_window.png)

1. Wählen Sie das Paket Microsoft. cppcorecheck aus, und klicken Sie dann auf die Schaltfläche **Installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.

   Das nuget-Paket fügt Ihrem Projekt eine zusätzliche MSBuild- *`.targets`* Datei hinzu, die aufgerufen wird, wenn Sie die Code Analyse für Ihr Projekt aktivieren. Die *`.targets`* Datei fügt die C++ Core Check Regeln als zusätzliche Erweiterung zum Visual Studio-Code Analysetool hinzu. Wenn das Paket installiert ist, können Sie das Dialogfeld Eigenschaften Seiten verwenden, um die veröffentlichten und experimentellen Regeln zu aktivieren oder zu deaktivieren.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-C++ Core Check Referenz](code-analysis-for-cpp-corecheck.md)
