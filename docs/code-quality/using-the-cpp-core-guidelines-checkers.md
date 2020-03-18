---
title: Verwenden der Überprüfungen für C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 955a445fbc29fca479a64684b4b60909234a0b38
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467090"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Verwenden der Überprüfungen für C++ Core Guidelines

Die C++ wichtigsten Richtlinien sind ein portabler Satz an Richtlinien, Regeln und bewährten Methoden zum C++ Programmieren C++ in, die von Experten und Designern erstellt werden. Visual Studio unterstützt derzeit eine Teilmenge dieser Regeln als Teil der Code Analysetools für C++. Die wichtigsten Leitfäden werden standardmäßig in Visual Studio 2017 und Visual Studio 2019 installiert und sind [als nuget-Paket für Visual Studio 2015 verfügbar](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Das C++ Kern Leitlinien-Projekt

Die C++ grundlegenden Richtlinien werden von Bjarne Stroustrup und anderen erstellt und sind ein Leitfaden C++ zur sicheren und effektiven Verwendung von modern. Die Richtlinien betonen die statische Typsicherheit und die Ressourcensicherheit. Sie identifizieren Möglichkeiten, um die Fehler anfälligsten Teile der Sprache zu eliminieren oder zu minimieren, und legen fest, wie Sie Ihren Code auf zuverlässige Weise einfacher und leistungsfähiger machen können. Diese Richtlinien werden von der Standard C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [ C++ den grundlegenden Richtlinien](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)und C++ dem Zugriff auf die Dokumentationsprojekt Dateien der wichtigsten Richtlinien auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren der C++ grundlegenden Check-Richtlinien in der Code Analyse

Sie können die Code Analyse für Ihr Projekt aktivieren, indem Sie im Dialogfeld " **Code Analyse** " des Dialog Felds " **Eigenschaften Seiten** " für Ihr Projekt das Kontrollkästchen " **Code Analyse in Build aktivieren" aktivieren** .

![Eigenschaften Seite für allgemeine Code Analyse Einstellungen](media/cppcorecheck_codeanalysis_general.png)

Eine Teilmenge von C++ kernregel Regeln ist im von Microsoft empfohlenen Regel Satz enthalten, der standardmäßig ausgeführt wird, wenn die Code Analyse aktiviert ist. Wenn Sie zusätzliche kernregel Regeln aktivieren möchten, klicken Sie auf die Dropdown Liste, und wählen Sie die Regelsätze aus, die Sie einschließen möchten:

![Dropdown Liste für C++ zusätzliche kernregel Sätze zur Regelüberprüfung](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Beispiele

Im folgenden finden Sie ein Beispiel für einige der Probleme, C++ die die grundlegenden Prüfregeln finden können:

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

In diesem Beispiel werden einige der Warnungen veranschaulicht, die C++ die grundlegenden Prüfregeln finden können:

- C26494 ist vom Regeltyp. 5: Initialisieren Sie immer ein Objekt.

- C26485 ist Regel Begrenzungen. 3: kein Array-zu-Zeiger-Zerfall.

- C26481 ist Regel Begrenzungen. 1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.

Wenn die C++ Code Analyse-Regelsätze der Kern Überprüfung installiert und aktiviert sind, wenn Sie diesen Code kompilieren, werden die ersten beiden Warnungen ausgegeben, das dritte wird jedoch unterdrückt. Dies ist die Buildausgabe des Beispielcodes:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Die C++ wichtigsten Richtlinien sind vorhanden, die Ihnen helfen, besseren und sichereren Code zu schreiben. Wenn Sie jedoch über eine Instanz verfügen, bei der eine Regel oder ein Profil nicht angewendet werden sollte, ist es einfach, Sie direkt im Code zu unterdrücken. Sie können das `gsl::suppress`-Attribut verwenden, C++ um zu verhindern, dass die Kern Überprüfung eine Verletzung einer Regel im folgenden Codeblock erkennt und meldet. Sie können einzelne Anweisungen markieren, um bestimmte Regeln zu unterdrücken. Sie können sogar das gesamte Begrenzungen-Profil unterdrücken, indem Sie `[[gsl::suppress(bounds)]]` ohne Angabe einer bestimmten Regel Nummer schreiben.

## <a name="supported-rule-sets"></a>Unterstützte Regelsätze

Wenn der C++ kernrichtlinienprüfung neue Regeln hinzugefügt werden, kann sich die Anzahl der Warnungen, die für bereits vorhandenen Code erzeugt werden, erhöhen. Sie können vordefinierte Regelsätze verwenden, um zu filtern, welche Arten von Regeln aktiviert werden sollen.
Referenz Themen zu den meisten Regeln finden [Sie unter C++ Referenz zu Visual Studio Core-Überprüfung](code-analysis-for-cpp-corecheck.md).

Ab Visual Studio 2017 Version 15,3 sind folgende Regelsätze unterstützt:

- **Besitzer Zeiger Regeln** erzwingen [Ressourcen Verwaltungs Prüfungen im Zusammenhang mit Besitzer-\<t- C++ > aus den grundlegenden Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- Mit **Konstanten Regeln** werden über [Prüfungen C++ der Kern Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)durchgeführt.

- **Rohzeiger Regeln** erzwingen [Ressourcen Verwaltungs Prüfungen im Zusammenhang mit unformatierten C++ Zeigern aus den grundlegenden Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Eindeutige Zeiger Regeln** erzwingen [Ressourcen Verwaltungs Prüfungen in Bezug auf Typen mit eindeutiger Zeiger Semantik aus C++ den grundlegenden Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Grenzen Regeln** erzwingen das [Rahmenprofil der C++ grundlegenden Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Typregeln** erzwingen das [Typprofil der C++ grundlegenden Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 Version 15.5**:

- **Klassenregeln** Einige Regeln, die sich auf die ordnungsgemäße Verwendung von speziellen Member-Funktionen und virtuellen Spezifikationen konzentrieren. Dies ist eine Teilmenge der Überprüfungen, die für [Klassen und Klassenhierarchien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)empfohlen werden.
- Parallelitäts **Regeln** Eine einzelne Regel, die falsch deklarierte Wächter Objekte abfängt. Weitere Informationen finden Sie unter [Richtlinien im Zusammenhang mit](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)der Parallelität.
- **Deklarations Regeln** Eine Reihe von Regeln aus den [Schnittstellen Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) , die sich darauf konzentrieren, wie globale Variablen deklariert werden.
- **Funktions Regeln** Zwei Überprüfungen, die bei der Übernahme des `noexcept` Spezifizierers helfen. Dies ist ein Bestandteil der Richtlinien für den [klaren Funktions Entwurf und die Implementierung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- Frei **gegebene Zeiger Regeln** Im Rahmen der Erzwingung von Richtlinien für die [Ressourcenverwaltung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) haben wir einige Regeln hinzugefügt, die für die Übergabe von freigegebenen Zeigern in Funktionen und die lokale Verwendung von
- **Stilregeln** Eine einfache, aber wichtige Überprüfung, die die Verwendung von [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)verbietet. Dies ist der erste Schritt bei der Verbesserung des Codierungs Stils und der Verwendung von Ausdrücken C++und Anweisungen in.

**Visual Studio 2017-Version 15.6:**

- **Arithmetische Regeln** Regeln zum Erkennen von arithmetischen [Überlauf](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow)-, signierten und [Bitmanipulation](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative) [-Vorgängen](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) .

Sie können Warnungen auf nur eine oder mehrere Gruppen beschränken. Die systemeigenen empfohlenen **Minimal** -und systemeigenen C++ **empfohlenen** Regelsätze enthalten neben anderen vorab Überprüfungen auch Kern Prüfregeln. Um die verfügbaren Regelsätze anzuzeigen, öffnen Sie das Dialogfeld Projekteigenschaften, wählen Sie **Code analysis\allgemein**aus, öffnen Sie die Dropdown Liste im Kombinations Feld **Regelsätze** , und wählen **Sie mehrere Regelsätze auswählen**aus. Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [Verwenden von Regelsätzen zum C++ angeben der zu testenden Regeln](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

## <a name="macros"></a>Makros

Die C++ Kern Richtlinien Prüfung enthält eine Header Datei, die Makros definiert, die das unterdrücken ganzer Warn Kategorien im Code vereinfachen:

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

## <a name="attributes"></a>Attributes

Der Microsoft C++ -Compiler bietet eingeschränkte Unterstützung für das gsl-Unterbrechungs Attribut. Sie kann verwendet werden, um Warnungen für Ausdrucks-und Block Anweisungen innerhalb einer Funktion zu unterdrücken.

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

1. Klicken Sie mit der rechten Maustaste auf die Datei in **Projektmappen-Explorer**

1. **Eigenschaften auswählen | C/C++| Befehlszeile**

1. Fügen Sie im Fenster **zusätzliche Optionen** `/wd26400`hinzu.

Sie können die Befehlszeilenoption verwenden, um die gesamte Code Analyse für eine Datei temporär zu deaktivieren, indem Sie `/analyze-`angeben. Dies erzeugt eine Warnung *D9025 Überschreiben von "/Analyze" mit "/Analyze-"* , wodurch Sie daran erinnert werden, die Code Analyse später erneut zu aktivieren.

## <a name="corecheck_per_file"></a>Aktivieren der C++ grundlegenden Richtlinien Prüfung für bestimmte Projektdateien

Manchmal kann es nützlich sein, eine fokussierte Code Analyse durchzuführen und die Visual Studio-IDE weiterhin zu verwenden. Das folgende Beispielszenario kann für große Projekte verwendet werden, um Buildzeit zu sparen und das Filtern von Ergebnissen zu vereinfachen:

1. Legen Sie in der Befehlsshell die Umgebungsvariablen `esp.extension` und `esp.annotationbuildlevel` fest.
1. Um diese Variablen zu erben, öffnen Sie Visual Studio über die Befehlsshell.
1. Laden Sie das Projekt, und öffnen Sie seine Eigenschaften.
1. Aktivieren Sie die Code Analyse, wählen Sie die entsprechenden Regelsätze aus, aktivieren Sie jedoch keine Code Analyse Erweiterungen.
1. Wechseln Sie zu der Datei, die Sie mit der C++ Kern Leitlinien Prüfung analysieren möchten, und öffnen Sie deren Eigenschaften.
1. Wählen Sie **CC++/\befehlszeilenoptionen** und `/analyze:plugin EspXEngine.dll` hinzufügen
1. Deaktivieren Sie die Verwendung des vorkompilierten Headers (**C/C++\vorkompilierte Header**). Dies ist erforderlich, da das Erweiterungsmodul möglicherweise versucht, seine internen Informationen aus dem vorkompilierten Header (PCH) zu lesen. Wenn das mit Standard Projektoptionen kompilierte PCH nicht kompatibel ist, ist es nicht kompatibel.
1. Erstellen Sie das Projekt neu. Die allgemeinen PREfast-Überprüfungen sollten für alle Dateien ausgeführt werden. Da die C++ Basis Richtlinien Prüfung nicht standardmäßig aktiviert ist, sollte Sie nur in der Datei ausgeführt werden, die für deren Verwendung konfiguriert ist.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Verwenden der C++ Kern Leitlinien Überprüfung außerhalb von Visual Studio

Sie können die C++ wichtigsten Richtlinien Überprüfungen in automatisierten Builds verwenden.

### <a name="msbuild"></a>MSBuild

Der Native Code Analysis Checker (PREfast) ist in die MSBuild-Umgebung durch benutzerdefinierte Zieldateien integriert. Sie können die Projekteigenschaften verwenden, um es zu aktivieren, C++ und die grundlegenden Richtlinien-Prüfung (auf der Grundlage von PREfast) hinzufügen:

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Stellen Sie sicher, dass Sie diese Eigenschaften vor dem Importieren der Datei "Microsoft. cpp. targets" hinzufügen. Sie können bestimmte Regelsätze auswählen oder einen benutzerdefinierten Regelsatz erstellen oder den Standard Regelsatz verwenden, der andere vorab Überprüfungen enthält.

Sie können die C++ Core-Prüfung nur für angegebene Dateien ausführen, indem Sie den gleichen Ansatz wie [zuvor beschrieben](#corecheck_per_file)verwenden, aber MSBuild-Dateien verwenden. Die Umgebungsvariablen können mithilfe des `BuildMacro` Elements festgelegt werden:

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

Wenn Sie ein Buildsystem verwenden, das nicht auf MSBuild beruht, können Sie die Prüfung trotzdem ausführen, aber Sie müssen sich mit einigen Internalen der Code Analyse-Engine-Konfiguration vertraut machen. Diese internale werden in Zukunft nicht garantiert unterstützt.

Sie müssen einige Umgebungsvariablen festlegen und geeignete Befehlszeilenoptionen für den Compiler verwenden. Es ist besser, in der Umgebung "Native Tools-Eingabeaufforderung" zu arbeiten, sodass Sie nicht nach bestimmten Pfaden für den Compiler suchen müssen, Verzeichnisse einschließen usw.

- **Umgebungsvariablen**
  - `set esp.extensions=cppcorecheck.dll` Dies weist die Engine an, das C++ Kern Richtlinien Modul zu laden.
  - `set esp.annotationbuildlevel=ignore` Hierdurch wird die Logik für die Verarbeitung von Sal-Anmerkungen deaktiviert. Anmerkungen wirken sich nicht auf die Code Analyse C++ in der Kern Leitlinien Prüfung aus, ihre Verarbeitung dauert jedoch Zeit (manchmal sehr lange). Diese Einstellung ist optional, wird jedoch dringend empfohlen.
  - `set caexcludepath=%include%` wir dringend die Deaktivierung von Warnungen empfohlen, die für Standard Header ausgelöst werden. Hier können Sie weitere Pfade hinzufügen, z. b. den Pfad zu den allgemeinen Headern in Ihrem Projekt.

- **Befehlszeilenoptionen**
  - `/analyze` aktiviert die Code Analyse (Beachten Sie auch/ANALYZE: Only und/ANALYZE: Quiet).
  - `/analyze:plugin EspXEngine.dll` mit dieser Option wird die Code Analyse-Erweiterungs-Engine in den PREfast-Wert geladen. Diese Engine lädt wiederum die C++ grundlegenden Leitlinien Prüfung.

## <a name="use-the-guideline-support-library"></a>Verwenden der Unterstützungs Bibliothek für Richtlinien

Die Unterstützungs Bibliothek für die Richtlinie soll Ihnen helfen, die grundlegenden Richtlinien zu befolgen. Die GSL enthält Definitionen, mit denen Sie fehleranfällige Konstrukte durch sicherere Alternativen ersetzen können. Beispielsweise können Sie ein `T*, length` Parameter paar durch den `span<T>`-Typ ersetzen. Die GSL ist unter [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)verfügbar. Die Bibliothek ist Open Source, sodass Sie die Quellen anzeigen, Kommentare erstellen oder mitwirken können. Das Projekt finden Sie unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Verwenden der C++ grundlegenden Check-Richtlinien in Visual Studio 2015-Projekten

Wenn Sie Visual Studio 2015 verwenden, werden C++ die Kern Regelsätze für die Code Analyse nicht standardmäßig installiert. Sie müssen einige zusätzliche Schritte ausführen, bevor Sie die Analyse C++ Tools für die Kern Überprüfung in Visual Studio 2015 aktivieren können. Microsoft bietet Unterstützung für Visual Studio 2015-Projekte mithilfe eines nuget-Pakets. Das Paket heißt "Microsoft. cppcorecheck" und ist unter [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)verfügbar. Für dieses Paket ist mindestens Visual Studio 2015 mit installiertem Update 1 erforderlich.

Das Paket installiert auch ein anderes Paket als Abhängigkeit, eine nur-Header-Richtlinien-Unterstützungs Bibliothek (GSL). Die GSL ist auch auf GitHub unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)verfügbar.

Aufgrund der Art und Weise, wie die Code Analyse Regeln geladen werden, müssen Sie das nuget-Paket "Microsoft. cppcorecheck" in jedem C++ Projekt installieren, das Sie in Visual Studio 2015 überprüfen möchten.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>So fügen Sie dem Projekt das Microsoft. cppcorecheck-Paket in Visual Studio 2015 hinzu

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf, um das Kontextmenü Ihres Projekts in der Projekt Mappe zu öffnen, der Sie das Paket hinzufügen möchten. Wählen Sie **nuget-Pakete verwalten** , um den **nuget-Paket-Manager**zu öffnen.

1. Suchen Sie im Fenster **nuget-Paket-Manager** nach Microsoft. cppcorecheck.

    ![Das Fenster des nuget-Paket-Managers zeigt das cppcorecheck-Paket](../code-quality/media/cppcorecheck_nuget_window.png)

1. Wählen Sie das Paket Microsoft. cppcorecheck aus, und klicken Sie dann auf die Schaltfläche **Installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.

   Das nuget-Paket fügt dem Projekt eine zusätzliche MSBuild *. targets* -Datei hinzu, die aufgerufen wird, wenn Sie die Code Analyse für Ihr Projekt aktivieren. Diese *Targets* -Datei fügt die C++ grundlegenden Prüfregeln als zusätzliche Erweiterung zum Visual Studio-Code Analysetool hinzu. Wenn das Paket installiert ist, können Sie das Dialogfeld Eigenschaften Seiten verwenden, um die veröffentlichten und experimentellen Regeln zu aktivieren oder zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

- [Referenz zur C++ Visual Studio-Kern Überprüfung](code-analysis-for-cpp-corecheck.md)
