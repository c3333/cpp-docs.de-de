---
title: Neuerungen bei C++ in Visual Studio
description: Die neuen Features und Korrekturen in Microsoft C/C++-Compiler und -Tools in Visual Studio.
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: c5e1f368060b650781c413a03e1bc2f9e368941a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924847"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Neuerungen bei C++ in Visual Studio

::: moniker range=">=msvc-160"

Visual Studio 2019 enthält viele Updates und Fixes für die C++-Umgebung von Microsoft. Es wurden zahlreiche Fehler und Probleme mit dem Compiler sowie mit Tools behoben. Viele Probleme wurden von Kunden über die Optionen [Problem melden](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019&preserve-view=true) und [Vorschlag senden](https://developercommunity.visualstudio.com/spaces/62/index.html) unter **Feedback senden** übermittelt. Vielen Dank für das Melden von Fehlern! Weitere Informationen zu Neuerungen in Visual Studio finden Sie unter [Neuerungen in Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Weitere Informationen zu Neuerungen für C++ in Visual Studio 2017 finden Sie unter [Neuerungen für C++ in Visual Studio 2017](?preserve-view=true&view=msvc-150). Weitere Informationen zu Neuerungen für C++ in Visual Studio 2015 und frühere Versionen finden Sie unter [Visual C++: Neuerungen von 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

## <a name="c-compiler"></a>C++-Compiler

- Verbesserte Unterstützung für C++17-Features und Korrekturen der Genauigkeit sowie experimentelle Unterstützung für C++20-Features wie Module und Coroutinen. Ausführliche Informationen finden Sie unter [C++ Conformance Improvements in Visual Studio 2019 (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio 2019)](cpp-conformance-improvements.md).

- Die Option `/std:c++latest` schließt nun C++20-Features ein, deren Entwicklung möglicherweise noch nicht abgeschlossen ist. Hierzu gehört beispielsweise die Unterstützung des C++20-Operators \<=>> („Spaceship“) für Dreifachvergleiche.

- Die C++-Compileroption `/Gm` ist nun veraltet. Es empfiehlt sich, die `/Gm`-Option in Buildskripts zu deaktivieren, wenn sie explizit festgelegt wurde. Sie können die Warnung für die veraltete Option allerdings auch für `/Gm` ignorieren, da sie bei Verwendung der Einstellung „Warnungen als Fehler behandeln“ (`/WX`) nicht als Fehler behandelt wird.

- Da für MSVC mit der Implementierung der Features aus dem C++20-Standardentwurf unter dem Flag `/std:c++latest` begonnen wurde, ist `/std:c++latest` jetzt mit `/clr` (alle Arten), `/ZW` und `/Gm` inkompatibel. Verwenden Sie in Visual Studio 2019 den Modus `/std:c++17` oder `/std:c++14` beim Kompilieren mit `/clr`, `/ZW` oder `/Gm` (siehe vorheriger Aufzählungspunkt).

- Vorkompilierte Header werden nicht mehr standardmäßig für C++-Konsolen- und -Desktop-Apps generiert.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegenerierung, Sicherheit, Diagnosen und Versionsverwaltung

Verbesserte Analysen mit `/Qspectre` unterstützen die Entschärfung der Spectre-Variante 1 (CVE-2017-5753). Weitere Informationen finden Sie unter [Spectre Mitigations in MSVC (Spectre-Entschärfungen in MSVC)](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Verbesserungen der C++-Standardbibliothek

- Implementierung von zusätzlichen C++17- und C++20-Bibliotheksfeatures und Korrekturen der Genauigkeit. Ausführliche Informationen finden Sie unter [C++ Conformance Improvements in Visual Studio 2019 (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio 2019)](cpp-conformance-improvements.md).

- Das Clang-Format wurde zur besseren Lesbarkeit auf die Header der C++-Standardbibliothek angewendet.

- Da Visual Studio jetzt „Nur eigenen Code“ für C++ unterstützt, muss die Standardbibliothek keine benutzerdefinierten Komponenten für `std::function` und `std::visit` mehr bereitstellen, um den gleichen Effekt zu erzielen. Die Entfernung dieser Komponenten hat im Allgemeinen keine für Benutzer sichtbare Auswirkung. Eine Ausnahme ist jedoch, dass der Compiler keine Diagnose zum Angeben von Problemen in Zeile 15732480 oder 16707566 von \<type_traits> oder \<variant> mehr durchführt.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Verbesserungen in Bezug auf Leistung/Durchsatz im Compiler und in der Standardbibliothek

- Der Durchsatz für Builds wurde verbessert. Zu den Optimierungen gehören unter anderem der Umgang des Linkers mit E/A-Vorgängen für Dateien und die Linkzeit beim Zusammenführen und Erstellen von PDB-Typen.

- Die OpenMP-SIMD-Vektorisierung wird nun grundlegend unterstützt. Sie können sie mit der neuen Compileroption **`/openmp:experimental`** aktivieren. Wenn diese Option festgelegt ist, werden Schleifen mit der Anmerkung `#pragma omp simd` möglicherweise vektorisiert. Die Vektorisierung wird allerdings nicht garantiert. Für Schleifen, die mit einer Anmerkung versehen sind, aber nicht vektorisiert werden, wird eine Warnung ausgegeben. SIMD-Klauseln werden nicht unterstützt. Sie werden ignoriert, und es wird eine Warnung angezeigt.

- Die neue Inlining-Befehlszeilenoption **`/Ob3`** wurde hinzugefügt. Diese führt im Vergleich zur **`/Ob2`** -Version mehr Inliningvorgänge aus. **`/O2`** (Binärdateioptimierung für höhere Geschwindigkeit) impliziert weiterhin standardmäßig **`/Ob2`** . Wenn Sie feststellen, dass der Compiler nicht genug Inliningvorgänge ausführt, sollten Sie **`/O2 -Ob3`** verwenden.

- Intrinsische Funktionen der Short Vector Math Library (SVML) werden nun unterstützt. Diese Funktionen berechnen die Entsprechungen von 128-, 256- oder 512-Bit-Vektoren. Dadurch werden die manuelle Vektorisierung von Schleifen mit Aufrufen für mathematische Bibliotheksfunktionen und bestimmte andere Operationen wie Ganzzahldivisionen ermöglicht. Definitionen der unterstützten Funktionen finden Sie im [Intel Intrinsics Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Neue und verbesserte Optimierungen:

  - Auswertung von Ausdrücken, die zur Kompilierzeit in Konstanten umgewandelt werden können (Constant Folding), und arithmetische Vereinfachungen für Ausdrücke mit intrinsischen SIMD-Vektorfunktionen für Float- und Integerformen

  - Leistungsfähigere Analyse zum Extrahieren von Informationen aus der Ablaufsteuerung (if/else/switch-Anweisungen), um Zweige zu entfernen, für die feststeht, dass sie immer TRUE oder FALSE sind

  - Verbesserte memset-Auflösung zur Verwendung von SSE2-Vektoranweisungen

  - Verbessertes Entfernen von nutzlosen struct/class-Kopien, insbesondere für C++-Programme, in denen Übergaben nach Wert erfolgen

  - Verbesserte Optimierung von Code mithilfe von `memmove`, z. B. im Fall von `std::copy` oder bei der Erstellung von `std::vector`- und `std::string`-Objekten

- Optimierung des physischen Designs der Standardbibliothek, um zu vermeiden, dass Teile der Standardbibliothek, die nicht direkt enthalten sind, kompiliert werden. Diese Änderung verkürzte die Erstellungszeit einer leeren Datei, die nur \<vector> enthält, um die Hälfte. Daher müssen Sie ggf. `#include`-Anweisungen für Header hinzufügen, die zuvor indirekt eingebunden waren. Beispielsweise muss bei Code, der `std::out_of_range` verwendet, jetzt ggf. `#include <stdexcept>` hinzugefügt werden. Bei Code, für den ein Operator zum Einfügen eines Datenstroms verwendet wird, muss jetzt ggf. `#include <ostream>` hinzugefügt werden. Der Vorteil besteht darin, dass nur für Übersetzungseinheiten, in denen tatsächlich \<stdexcept>- oder \<ostream>-Komponenten verwendet werden, der Durchsatzaufwand für die Kompilierung anfällt.

- `if constexpr` wurde in der Standardbibliothek an mehr Stellen angewendet, um für Kopiervorgänge einen besseren Durchsatz und eine geringere Codegröße zu erzielen, sowie in Permutationen wie Umkehrung und Drehung und in der Bibliothek mit den parallelen Algorithmen.

- In der Standardbibliothek wird intern jetzt `if constexpr` verwendet, um die Kompilierzeiten zu reduzieren (auch im C ++14-Modus).

- Bei der Erkennung von dynamischen Verknüpfungen zur Laufzeit für die Bibliothek mit den parallelen Algorithmen wird nicht mehr eine gesamte Seite genutzt, um das Funktionszeigerarray zu speichern. Die Kennzeichnung dieses Speichers als schreibgeschützt wurde als nicht mehr relevant für die Sicherheit angesehen.

- Der Konstruktor `std::thread` wartet nicht mehr darauf, dass der Thread startet, und fügt zwischen der zugrunde liegenden C-Bibliothek `_beginthreadex` und dem angegebenen aufrufbaren Objekt nicht mehr so viele Funktionsaufrufe ein. Bisher wurden von `std::thread` sechs Funktionen zwischen `_beginthreadex` und dem angegebenen aufrufbaren Objekt eingefügt. Diese Zahl wurde auf drei reduziert (zwei davon sind lediglich `std::invoke`). Darüber hinaus wird mit dieser Änderung ein rätselhafter Zeitsteuerungsfehler behoben, bei dem ein Konstruktor von `std::thread` hängt, wenn die Systemuhr genau während der Erstellung eines `std::thread`-Elements geändert wird.

- Es wurde ein Leistungsverlust in `std::hash` behoben, der sich aus der Implementierung von `std::hash<std::filesystem::path>` ergeben hat.

- An mehreren Stellen der Standardbibliothek werden anstelle von catch-Blöcken jetzt Destruktoren verwendet, um Korrektheit zu erzielen. Dies führt zu einer besseren Interaktion mit dem Debugger: Ausnahmen, die über die Standardbibliothek an den betroffenen Orten auftreten, werden jetzt so angezeigt, dass sie am ursprünglichen Auslösungsort ausgelöst wurden (anstatt durch unseren Rethrow-Vorgang). Nicht alle catch-Blöcke der Standardbibliothek wurden beseitigt. Wir gehen davon aus, dass die Anzahl von catch-Blöcken in späteren Releases von MSVC weiter reduziert wird.

- Suboptimale Codegenerierung in `std::bitset` durch eine bedingte Auslösung in einer noexcept-Funktion wurde behoben, indem der Auslösepfad ausgeklammert wurde.

- Für die `std::list`- und `std::unordered_*`-Familie werden Iteratoren ohne Debugging intern an mehr Stellen verwendet.

- Mehrere `std::list`-Member wurden geändert, um, soweit möglich, Listenknoten wiederzuverwenden, anstatt hierfür die Zuordnung aufzuheben und diese dann erneut durchzuführen. Bei einem `list<int>`, der bereits eine Größe von 3 hat, überschreibt ein Aufruf von `assign(4, 1729)` jetzt beispielsweise die Int-Elemente in den ersten drei Listenknoten und weist einen neuen Listenknoten mit dem Wert 1729 zu.

- Alle `erase(begin(), end())`-Aufrufe der Standardbibliothek wurden in `clear()` geändert.

- Mit `std::vector` werden Elemente in bestimmten Fällen jetzt effizienter initialisiert und gelöscht.

- `std::variant` wurde verbessert und kann daher leichter optimiert werden. Dies führt zu besserem generierten Code. Codeinlining mit `std::visit` ist nun deutlich effizienter.

## <a name="c-ide"></a>C++-IDE

### <a name="live-share-c-support"></a>C++-Unterstützung für Live Share

[Live Share](/visualstudio/liveshare/) unterstützt nun C++ und ermöglicht es Entwicklern, die Visual Studio oder Visual Studio Code verwenden, in Echtzeit zusammenzuarbeiten. Weitere Informationen finden Sie unter [Announcing Live Share for C++: Real-Time Sharing and Collaboration (Ankündigung: Live Share für C++ ermöglicht Austausch von Codeinformationen und Zusammenarbeit)](https://devblogs.microsoft.com/cppblog/cppliveshare/).

### <a name="intellicode-for-c"></a>IntelliCode für C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

IntelliCode nutzt umfassendes eigenes Training und Ihren Codekontext, um Codeelemente, die Sie wahrscheinlich verwenden, am Anfang der Vervollständigungsliste anzuzeigen. Dadurch müssen Sie oft nicht in der Liste nach unten scrollen. IntelliCode eignet sich für C++ insbesondere dann, wenn häufig eingesetzte Bibliotheken wie die Standardbibliothek verwendet werden. IntelliCode ist eine optionale Erweiterung, die als Workloadkomponente im Installer verfügbar ist. Weitere Informationen finden Sie unter [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode (IntelliCode stellt für C++ KI-gestützte Codevervollständigungsvorschläge bereit)](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>IntelliSense für Vorlagen

Für die **Vorlagenleiste** wird nun die **Vorschaufenster** -Benutzeroberfläche anstelle eines modalen Fensters verwendet. Außerdem unterstützt die Vorlagenleiste verschachtelte Vorlagen und füllt alle Standardargumente im **Vorschaufenster** vorab aus. Weitere Informationen finden Sie unter [Template IntelliSense Improvements for Visual Studio 2019 Preview 2 (IntelliSense-Verbesserungen für Vorlagen in Vorschauversion 2 von Visual Studio 2019)](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Mit der Dropdownliste **Zuletzt verwendet** in der **Vorlagenleiste** können Sie schnell zwischen vorherigen Beispielargumenten wechseln.

### <a name="new-start-window-experience"></a>Neues Startfenster

Beim Starten der IDE wird ein neues Startfenster angezeigt. Dieses Fenster enthält Optionen, mit denen Sie die zuletzt verwendeten Projekte öffnen oder Code aus der Quellcodeverwaltung klonen können. Außerdem haben Sie die Möglichkeit, lokalen Code als Projektmappe oder Ordner zu öffnen oder ein neues Projekt zu erstellen. Auch das Dialogfeld „Neues Projekt“ wurde angepasst. In diesem können Sie nun Suchvorgänge ausführen und Ergebnisse filtern.

### <a name="new-names-for-some-project-templates"></a>Umbenennung mehrerer Projektvorlagen

Mehrere Projektvorlagennamen und -beschreibungen wurden so geändert, dass sie zum aktualisierten Dialogfeld „Neues Projekt“ passen.

### <a name="various-productivity-improvements"></a>Features zur Produktivitätssteigerung

Die folgenden Features in Visual Studio 2019 unterstützen Sie dabei, leichter und intuitiver zu programmieren:

- Schnellkorrekturen für folgende Aufgaben:
  - Hinzufügen fehlender #include-Anweisungen
  - Umwandeln von NULL in nullptr
  - Add missing semicolon
  - Auflösen fehlender Namespaces oder Bereiche
  - Ersetzen ungültiger Dereferenzierungsoperanden (\* in & und & in \*)
- Anzeigen einer QuickInfo für einen Block, sobald mit dem Mauszeiger auf eine schließende geschweifte Klammer gezeigt wird
- Anzeigen der Vorschau für eine Header-/Codedatei
- Öffnen einer Datei durch Verwenden von „Zur Definition wechseln“ für #include-Anweisungen

Weitere Informationen finden Sie unter [C++ Productivity Improvements in Visual Studio 2019 Preview 2 (C++-Produktivitätsfeatures in Vorschauversion 2 von Visual Studio 2019)](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>QuickInfo-Verbesserungen

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

Für die QuickInfo wird jetzt die semantische Farbgebung Ihres Editors berücksichtigt. Außerdem verfügt sie über den neuen Link **Online suchen** , mit dem nach Onlinedokumenten gesucht wird, um mehr Informationen zum jeweiligen Codekonstrukt zu erhalten. Über den Link in der QuickInfo, der für rot unterschlängelten Code angezeigt wird, kann online nach dem Fehler gesucht werden. Auf diese Weise müssen Sie die Nachricht nicht erneut in Ihren Browser eingeben. Weitere Informationen finden Sie unter [Quick Info Improvements in Visual Studio 2019: Colorization and Search Online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/) (QuickInfo-Verbesserungen in Visual Studio 2019: Farbgebung und Onlinesuche).

### <a name="intellicode-available-in-c-workload"></a>In C++-Workload verfügbarer IntelliCode

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

IntelliCode ist jetzt als optionale Komponente in der Workload **Desktopentwicklung mit C++** enthalten. Weitere Informationen finden Sie unter [Improved C++ IntelliCode now Ships with Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/) (Verbesserter C++ IntelliCode ist jetzt in Visual Studio 2019 enthalten).

## <a name="cmake-support"></a>CMake-Unterstützung

- Unterstützung für CMake 3.14

- Visual Studio kann nun vorhandene CMake-Caches öffnen, die von externen Tools wie CMakeGUI, benutzerdefinierten Metabuildsystemen oder Buildskripts generiert werden, die „cmake.exe“ selbst aufrufen.

- Verbesserte IntelliSense-Leistung.

- Der neue Editor für Einstellungen stellt eine Alternative zum manuellen Bearbeiten der Datei „CMakeSettings.json“ dar. Die Funktionen ähneln denen von CMakeGUI.

- Visual Studio unterstützt Sie, Ihre C++-Entwicklung mit CMake unter Linux zu beginnen, indem es erkennt, ob Sie eine kompatible Version von CMake auf Ihrem Linux-Rechner haben. Ist dies nicht der Fall, bietet Visual Studio Ihnen an, CMake für Sie zu installieren.

- Inkompatible Einstellungen in CMakeSettings, etwa nicht passende Architekturen oder inkompatible CMake-Generatoreinstellungen, bewirken, dass Wellenlinien im JSON-Editor und Fehler in der Fehlerliste angezeigt werden.

- Die vcpkg-Toolkette wird für CMake-Projekte, die in der IDE geöffnet werden, sobald `vcpkg integrate install` ausgeführt wurde, automatisch erkannt und aktiviert. Dieses Verhalten kann deaktiviert werden, indem eine leere Toolkettendatei in CMakeSettings angegeben wird.

- Für CMake-Projekte wird „Nur eigenen Code“-Debuggen jetzt standardmäßig aktiviert.

- Warnungen bei statischer Analyse werden nun im Hintergrund verarbeitet und im Editor für CMake-Projekte angezeigt.

- Es wurden eindeutigere build- und konfigurationsbezogene „begin“- und „end“-Nachrichten für CMake-Projekte hinzugefügt. Außerdem wird die Buildstatusanzeige von Visual Studio nun unterstützt. Zusätzlich gibt es nun unter **Extras > Optionen** eine CMake-Ausführlichkeitseinstellung, um den Detaillierungsgrad der CMake-Build- und -Konfigurationsmeldungen für das Ausgabefenster anzupassen.

- Die Einstellung `cmakeToolchain` wird jetzt in der Datei „CMakeSettings.json“ unterstützt, damit Sie Toolketten angeben können, ohne die CMake-Befehlszeile manuell zu ändern.

- Mit **STRG+UMSCHALTTASTE+B** ist nun eine neue Menüverknüpfung für **Alle erstellen** verfügbar.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

- Integrierte Unterstützung für die Bearbeitung, die Erstellung und das Debugging von CMake-Projekten mit Clang/LLVM. Weitere Informationen finden Sie unter [Clang/LLVM Support in Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/) (Clang/LLVM-Unterstützung in Visual Studio).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux und das Windows-Subsystem für Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

- Unterstützung für [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) in plattformübergreifenden Linux- und CMake-Projekten. Weitere Informationen finden Sie unter [AddressSanitizer (ASan) for the Linux Workload in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/) (AddressSanitizer (ASan) für die Linux-Workload in Visual Studio 2019).

- Integrierte Visual Studio-Unterstützung für die Verwendung von C++ mit dem Windows-Subsystem für Linux (WSL). Weitere Informationen finden Sie unter [C++ with Visual Studio 2019 and Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/) (C++ mit Visual Studio 2019 und Windows-Subsystem für Linux (WSL)).

## <a name="incredibuild-integration"></a>IncrediBuild-Integration

IncrediBuild ist jetzt als optionale Komponente in der Workload **Desktopentwicklung mit C++** enthalten. Der IncrediBuild Build Monitor ist vollständig in die Visual Studio-IDE integriert. Weitere Informationen finden Sie unter [Visualisieren Ihres Builds mit IncrediBuild Build Monitor und Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Debuggen

- Für C++-Anwendungen unter Windows werden PDB-Dateien jetzt in einem separaten 64-Bit-Prozess geladen. Diese Änderung behebt eine Reihe von Abstürzen, die dadurch verursacht wurden, dass dem Debugger nicht genügend Arbeitsspeicher zur Verfügung stand. Beispielsweise beim Debuggen von Anwendungen, die eine große Anzahl von Modulen und PDB-Dateien enthielten.

- Die Suche wird in den Fenstern **Überwachen** , **Auto** und **Lokal** aktiviert.

## <a name="windows-desktop-development-with-c"></a>Windows Desktop-Entwicklung mit C++

- Die folgenden C++-ATL/MFC-Assistenten sind nicht mehr verfügbar:

  - ATL COM+ 1.0 Komponenten-Assistent
  - ATL-Assistent für Active Server Pages-Komponenten
  - ATL-OLE DB-Anbieter-Assistent
  - ATL-Eigenschaftenseiten-Assistent
  - ATL-OLE DB-Consumer-Assistent
  - MFC-ODBC-Consumer
  - MFC-Klasse aus ActiveX-Steuerelement
  - MFC-Klasse aus Typbibliothek

  Beispielcode für diese Technologien ist in der Microsoft-Dokumentation und im VCSamples-GitHub-Repository archiviert.

- Das Windows 8.1 Software Development Kit (SDK) ist nicht mehr im Visual Studio-Installer verfügbar. Empfohlen wird ein Upgrade von C++-Projekten auf das neueste Windows 10 SDK. Wenn eine erforderliche Abhängigkeit zu 8.1 besteht, können Sie das SDK aus dem Windows SDK-Archiv herunterladen.

- Windows XP als Ziel ist für den neuesten C++-Toolset nicht mehr verfügbar. XP wird als Ziel mit MSVC-Compiler und -Bibliotheken in der Version für Visual Studio 2017 weiterhin unterstützt und kann über „Einzelne Komponenten“ installiert werden.

- In der Dokumentation wird aktiv von einer Verwendung von Mergemodulen für die Bereitstellung von Visual C++ Runtime abgeraten. In diesem Release werden zusätzlich MSM-Dateien als veraltet gekennzeichnet. Sie sollten erwägen, Ihre zentrale VCRuntime-Bereitstellung von MSMs zum Redistributable Package zu migrieren.

## <a name="mobile-development-with-c-android-and-ios"></a>Mobile Entwicklung mit C++ (Android und iOS)

Die C++-Android-Erfahrung verwendet jetzt standardmäßig das Android SDK 25 und Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Clang/C2-Plattformtoolset

Die experimentelle Komponente „Clang/C2“ wurde entfernt. Verwenden Sie das MSVC-Toolset für vollständige Konformität mit den C++-Standards, und nutzen Sie dabei `/permissive-` und `/std:c++17` oder die Clang/LLVM-Toolkette für Windows.

## <a name="code-analysis"></a>Codeanalyse

- Die Codeanalyse wird jetzt automatisch im Hintergrund ausgeführt. Warnungen werden während der Eingabe als grüne Wellenlinien im Editor angezeigt. Weitere Informationen finden Sie unter [In-editor code analysis in Visual Studio 2019 Preview 2 (Codeanalyse im Editor in Vorschauversion 2 von Visual Studio 2019)](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Neue, experimentelle ConcurrencyCheck-Regeln für bekannte Standardbibliothekstypen des \<mutex>-Headers sind nun verfügbar. Weitere Informationen finden Sie unter [Concurrency Code Analysis in Visual Studio 2019 (Codeanalyse für parallele Programmierung in Visual Studio 2019)](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Eine aktualisierte Teilimplementierung der [Lebensdauerprofil-Prüfung](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/) ist nun verfügbar, um verbleibende Zeiger und Referenzen zu erkennen. Weitere Informationen finden Sie unter [Lifetime Profile Update in Visual Studio 2019 Preview 2 (Lebensdauerprofil-Aktualisierung in Vorschauversion 2 von Visual Studio 2019)](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Weitere Überprüfungen für Coroutinen wie C26138, C26810, C26811 und die experimentelle Regel C26800 sind nun verfügbar. Weitere Informationen finden Sie unter [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine (Neue Codeanalysen in Visual Studio 2019: Überprüfungen für Coroutinen und für die Verwendung von Objekten nach Nutzung der Move-Semantik)](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 Version 16.1

- Neue Schnellkorrekturen für nicht initialisierte Variablenüberprüfungen. Weitere Informationen finden Sie unter [New code analysis quick fixes for uninitialized memory (C6001) and use before init (C26494) warnings](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/) (Neue Codeanalyse-Schnellkorrekturen für nicht initialisierten Speicher (C6001) und Verwendung vor der Initialisierung (C26494) von Warnungen).

## <a name="unit-testing"></a>Komponententest

Die Vorlage für verwaltete C++-Testprojekte (Managed C++ Test Project) ist nicht mehr verfügbar. Sie können aber weiterhin das Framework für verwaltete C++-Tests für Ihre vorhandenen Projekte einsetzen. Für neue Komponententests sollten Sie eines der nativen Testframeworks (MSTest, Google Test) verwenden, für das Visual Studio Vorlagen bereitstellt. Alternativ können Sie auch die Vorlage für verwaltete C#-Testprojekte nutzen.

::: moniker-end

::: moniker range="=msvc-150"

Visual Studio 2017 RC enthält viele Updates und Problembehebungen der C++-Umgebung. Es wurden mehr als 250 Fehler und Probleme mit dem Compiler sowie mit Tools behoben. Viele dieser Probleme wurden von Kunden über die Optionen [Problem melden](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017&preserve-view=true) und „Vorschlag senden“ unter **Feedback senden** übermittelt. Vielen Dank für das Melden von Fehlern! Weitere Informationen zu Neuerungen in Visual Studio finden Sie unter [Neuerungen in Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017&preserve-view=true). Weitere Informationen zu Neuerungen für C++ in Visual Studio 2019 finden Sie unter [Neuerungen für C++ in Visual Studio](?preserve-view=true&view=msvc-160). Weitere Informationen zu Neuerungen für C++ in Visual Studio 2015 und frühere Versionen finden Sie unter [Visual C++: Neuerungen von 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

## <a name="visual-studio-2017-c-compiler"></a>Visual Studio 2017 C++-Compiler

### <a name="c-conformance-improvements"></a>Verbesserungen an C++ bei der Übereinstimmung mit Standards

Der C++-Compiler und die Standardbibliothek wurden in diesem Release mit verbesserter Unterstützung für C++11- und C++14-Funktionen aktualisiert. Diese Verbesserungen schließen auch vorläufige Unterstützung für bestimmte Features ein, deren Implementierung im C++17-Standard erwartet wird. Ausführliche Informationen finden Sie unter [Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual C++ 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Der Compiler unterstützt ungefähr 75 % der Features, die neu in C++17 sind (z. B. strukturierte Bindungen, **`constexpr`** -Lambdaausdrücke, `if constexpr`, Inlinevariablen, fold-Ausdrücke und das Hinzufügen von **`noexcept`** zum Typsystem). Diese Features sind unter der Option **`/std:c++17`** verfügbar. Weitere Informationen finden Sie unter [Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

Das MSVC-Compilertoolset in Visual Studio-Version 15.7 erfüllt nun den C++-Standard. Weitere Informationen finden Sie unter [Announcing: MSVC Conforms to the C++ Standard (Ankündigung: MSVC erfüllt den C++-Standard)](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) und [Microsoft C++-Sprachkonformität](./visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 Version 15.8

Mit der Compileroption [`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md) wird der neue experimentelle MSVC-Präprozessor aktiviert, der letztendlich mit allen gültigen C- und C++-Standards konform sein wird. Weitere Informationen finden Sie unter [Übersicht zum neuen MSVC-Präprozessor](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Neue Compileroptionen

- [`/permissive-`](../build/reference/permissive-standards-conformance.md): Aktiviert alle strikten Compileroptionen für die Übereinstimmung mit Standards und deaktiviert die meisten Microsoft-spezifischen Compilererweiterungen (aber z.B. nicht `__declspec(dllimport)`). Diese Option ist in Visual Studio 2017-Version 15.5 standardmäßig aktiviert.  Der Konformitätsmodus **`/permissive-`** schließt Unterstützung für die Zweiphasen-Namenssuche ein. Weitere Informationen finden Sie unter [C++ Conformance Improvements in Visual Studio (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio)](cpp-conformance-improvements.md).

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md): Aktiviert die Anzeige des Orts, an dem der Diagnosefehler oder die Warnung aufgetreten ist. Dabei sind drei Möglichkeiten verfügbar: nur die Zeilennummer, die Zeilennummer und die Spalte oder die Zeilennummer und die Spalte mit einem Caretzeichen unter der Codezeile, in der der Fehler oder die Warnung gefunden wurde.

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md): Ermöglicht um bis zu 30 % schnellere inkrementelle Verknüpfungszeiten (im Vergleich mit Visual Studio 2015), indem nicht alle Debuginformationen in die PDB-Datei kopiert werden. Die PDB-Datei zeigt stattdessen auf die Debuginformationen für das Objekt und die Bibliotheksdateien, die zum Erstellen der ausführbaren Datei verwendet wurden. Weitere Informationen finden Sie in den Blogbeiträgen [Faster C++ build cycle in VS "15" with `/Debug:fastlink`](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (Schnellerer C++-Buildzyklus in VS „15“ mit /Debug:fastlink) und [Recommendations to speed C++ builds in Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/) (Empfehlungen zum Beschleunigen von C++-Builds in Visual Studio).

- Visual Studio 2017 ermöglicht die Verwendung von [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) mit [`/await`](../build/reference/await-enable-coroutine-support.md). Die [`/RTC`](../build/reference/rtc-run-time-error-checks.md)-Einschränkung mit Coroutinen wurde beseitigt.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- [`/std:c++14` und `/std:c++latest`](../build/reference/std-specify-language-standard-version.md): Diese Compileroptionen ermöglichen Ihnen das Verwenden bestimmter Versionen der Programmiersprache ISO C++ in einem Projekt. Die meisten Standardfeatures des neuen Entwurfs werden von der Option **`/std:c++latest`** geschützt.

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) aktiviert die C++17-Features, die vom Compiler implementiert werden. Diese Option deaktiviert die Unterstützung von Compiler- und Standardbibliotheken für Features, die nach C++17 veröffentlicht wurden: Versionen des Arbeitsentwurfs und Fehlerbehebungsaktualisierungen des C++-Standards, die in späteren Versionen geändert wurden oder neu sind. Verwenden Sie zum Aktivieren dieser Funktionen **`/std:c++latest`** .

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegenerierung, Sicherheit, Diagnosen und Versionsverwaltung

Dieses Release bietet mehrere Verbesserungen hinsichtlich Optimierung, Codegenerierung, Versionsverwaltung für das Toolset sowie Diagnose. Zu diesen Verbesserungen gehören folgende:

- Verbesserte Generierung von Code für Schleifen: Unterstützung der automatischen Vektorisierung der Division von konstanten Integerwerten und verbesserte Erkennung von memset-Mustern.
- Verbesserte Codesicherheit: Verbesserte Ausgabe der Compilerdiagnose eines Pufferüberlaufs. [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) schützt jetzt switch-Anweisungen, die Sprungtabellen generieren.
- Versionsverwaltung: Der Wert des integrierten Präprozessormakros **\_MSC\_VER** wird nun bei jedem Update des Visual C++-Toolsets monoton aktualisiert. Weitere Informationen finden Sie unter [Visual C++-Compilerversion](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Neues Layout des Toolsets: Der Compiler und verwandte Buildtools haben auf dem Entwicklungscomputer einen neuen Speicherort und eine neue Verzeichnisstruktur. Das neue Layout ermöglicht die parallele Installation mehrerer Versionen des Compilers. Weitere Informationen finden Sie unter [Layout der Compilertools in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Verbesserte Diagnose: Das Ausgabefenster zeigt jetzt die Spalte an, in der ein Fehler auftritt. Weitere Informationen finden Sie im Blogbeitrag [C++ compiler diagnostics improvements in VS „15“ Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Bei Verwendung von Coroutinen wurde das experimentelle Schlüsselwort **yield** (verfügbar unter der Option **`/await`** ) entfernt. Der Code sollte so aktualisiert werden, dass stattdessen `co_yield` verwendet wird. Weitere Informationen finden Sie im Schlüsselwort [`yield`, das in VS 2017 `co_yield` wird](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

Weitere Verbesserungen der Diagnose im Compiler. Weitere Informationen finden Sie unter [Diagnostic Improvements in Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/) (Verbesserungen bei der Diagnose in Visual Studio 2017 15.3.0).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Die Visual C++-Laufzeitleistung wird weiterhin durch eine besser generierte Codequalität verbessert. Jetzt können Sie Ihren Code einfach neu kompilieren, und Ihre App wird schneller ausgeführt. Einige der Compileroptimierungen sind brandneu, z.B. die Vektorisierung von bedingten skalaren Speichern, die Kombination der Aufrufe `sin(x)` und `cos(x)` in einem neuen Aufruf `sincos(x)` und die Beseitigung von redundanten Anweisungen aus dem SSA-Optimierer. Weitere Compileroptimierungen sind Verbesserungen an bestehenden Funktionen wie Vektorisierungsheuristiken für bedingte Ausdrücke, bessere Schleifenoptimierungen und float min/max codegen. Der Linker verfügt über eine neue und schnellere **`/OPT:ICF`** -Implementierung, die die Linkzeit um bis zu 9 % beschleunigen kann, und es sind weitere Leistungsoptimierungen für „inkrementelles Verknüpfen“ vorhanden. Weitere Informationen finden Sie unter [/OPT (Optimierungen)](../build/reference/opt-optimizations.md) und [/INCREMENTAL (inkrementelles Verknüpfen)](../build/reference/incremental-link-incrementally.md).

Der Microsoft C++-Compiler bietet Unterstützung für AVX-512 von Intel. Er verfügt über Anweisungen zur Vektorlänge, die neue Funktionen in AVX-512 für 128 und 256 Bit breite Register bereitstellen.

Die Option [/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) kann verwendet werden, um zur C++14-Version von **`noexcept`** zurückzukehren, während allgemein der C++17-Modus verwendet wird. Diese Option ermöglicht es Ihnen, Ihren Quellcode zu aktualisieren, um ihn an C++17 anzupassen, ohne dass Sie Ihren gesamten `throw()`-Code zur gleichen Zeit neu schreiben müssen. Weitere Informationen dazu finden Sie unter [Entfernen der dynamischen Ausnahmespezifikation und noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

- Neuer Compilerschalter [/Qspectre ](../build/reference/qspectre.md), um Speculative-Execution-Seitenkanalangriffe zu verringern. Weitere Informationen finden Sie unter [Spectre Mitigations in MSVC (Spectre-Entschärfungen in MSVC)](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Neue Diagnosewarnung für Spectre-Entschärfung. Weitere Informationen finden Sie unter [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4 (Spectre-Diagnose in Visual Studio 2017-Version 15.7, Vorschauversion 4)](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Neuer Wert für/Zc, **`/Zc:__cplusplus`** : ermöglicht korrekte Berichterstattung für die Unterstützung des C++-Standards. Wenn die Option beispielsweise festgelegt ist und der Compiler sich im Modus **`/std:c++17`** befindet, wird der Wert auf **`201703L`** erweitert. Weitere Informationen finden Sie unter [MSVC now correctly reports __cplusplus (MSVC meldet jetzt ordnungsgemäß __cplusplus)](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>C++-Standardbibliothek

### <a name="correctness-improvements"></a>Verbesserungen der Richtigkeit

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (Version 15.0)

- Kleinere Verbesserungen bei der Diagnose von `basic_string``_ITERATOR_DEBUG_LEVEL != 0`. Beim Auslösen einer IDL-Überprüfung in einem Zeichenfolgenmechanismus wird nun das Verhalten gemeldet, das die Überprüfung ausgelöst hat. Anstelle von „string iterator not dereferencable“ (Zeichenfolgeniterator nicht dereferenzierbar), erhalten Sie „cannot dereference string iterator because it is out of range (e.g. an end iterator)“ (Zeichenfolgeniterator ist nicht dereferenzierbar, da er sich außerhalb des Bereichs befindet (z.B. ein End-Iterator)).
- Der Bewegungszuweisungsoperator `std::promise`, der zuvor zum dauerhaften Blockieren von Code führen konnte, wurde korrigiert.
- Compilerfehler bei der impliziten Konvertierung von `atomic<T*>` in `T*` wurden behoben.
- `pointer_traits<Ptr>` erkennt jetzt ordnungsgemäß `Ptr::rebind<U>`.
- Ein fehlender **`const`** -Qualifizierer im `move_iterator`-Subtraktionsoperator wurde ergänzt.
- Die lautlose, ungültige Codegenerierung für zustandsbehaftete benutzerdefinierte Allokatoren, die `propagate_on_container_copy_assignment` und `propagate_on_container_move_assignment` anfordern, wurde korrigiert.
- `atomic<T>` toleriert nun den überladenen `operator&()`.
- Compilerdiagnosen für falsche `bind()`-Aufrufe wurden leicht verbessert.

Es sind weitere Verbesserungen an der Standardbibliothek in Visual Studio 2017 RTM verfügbar. Eine vollständige Liste finden Sie im C++-Teamblogeintrag [Standard Library Fixes In VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/) (Behobene Probleme in der Standardbibliothek in VS 2017 RTM).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Standardbibliothekscontainer binden nun ihre `max_size()` an `numeric_limits<difference_type>::max()`, anstatt `max()` an `size_type`. Dadurch wird sichergestellt, dass das Ergebnis von `distance()` in Iteratoren von diesem Container im Rückgabetyp von `distance()` darstellbar ist.
- Fehlende Spezialisierung wurde behoben: `auto_ptr<void>`.
- Bei den Algorithmen `for_each_n()`, `generate_n()` und `search_n()` war in der Vergangenheit keine Kompilierung möglich, wenn es sich beim Längenargument nicht um einen integralen Typ handelte. Es wird nun versucht, nicht integrale Längen in einen `difference_type` des Iterators umzuwandeln.
- `normal_distribution<float>` gibt in der Standardbibliothek beim Einschränken von double auf float keine Warnungen mehr aus.
- Einige `basic_string`-Vorgänge wurden korrigiert, bei denen bei Überprüfung der maximalen Überlaufgröße `npos` anstatt `max_size()` verwendet wurde.
- `condition_variable::wait_for(lock, relative_time, predicate)` wartete bisher bei einer fälschlicherweise erfolgten Aktivierung die gesamte relative Zeit. Es wird nun nur für ein einzelnes Intervall der relativen Zeit gewartet.
- `future::get()` macht jetzt das `future`-Objekt ungültig, so wie es der Standard erfordert.
- `iterator_traits<void *>` war zuvor ein harter Fehler, weil versucht wurde, `void&` zu formen. Es wird jetzt zu einer leeren Struktur, um die Verwendung von `iterator_traits` in "is iterator" SFINAE-Bedingungen zuzulassen.
- Einige von Clang **-Wsystem-headers** -Objekten gemeldete Warnungen wurden korrigiert.
- Die von „Clang **-Wmicrosoft-exception-spec** “ gemeldete Warnung „exception specification in declaration does not match previous declaration“ (die Ausnahmespezifikation in der Deklaration entspricht nicht der vorherigen Deklaration) wurde ebenfalls korrigiert.
- Von Clang und C1XX gemeldete mem-initializer-list-Reihenfolgewarnungen wurden ebenfalls korrigiert.
- Die unsortierten Container tauschten ihre Hashfunktionen oder Prädikate nicht, wenn die Container selbst getauscht wurden. Dies erfolgt jetzt.
- Viele Tauschvorgänge für Container sind jetzt als **`noexcept`** markiert (da die Standardbibliothek nie eine Ausnahme auslösen soll, wenn sie die nicht definierte Verhaltensbedingung „non-`propagate_on_container_swap` non-equal-allocator“ erkennt).
- Viele `vector<bool>`-Vorgänge sind jetzt mit **`noexcept`** gekennzeichnet.
- Die Standardbibliothek erzwingt jetzt den Abgleich von `value_type` (im C++17-Modus) mit einem Escapehatch für die Abwahl.
- Einige Bedingungen wurden korrigiert, bei denen „self-range-insert“ in `basic_string` den Inhalt der Zeichenfolge durcheinandergebracht hat. (Hinweis: „self-range-insert“ in Vektoren ist im Standard immer noch nicht zulässig.)
- `basic_string::shrink_to_fit()` wird nicht länger vom `propagate_on_container_swap` der Zuweisung beeinträchtigt.
- `std::decay` verarbeitet jetzt abominable-Funktionstypen (also Funktionstypen mit cv- und/oder ref-Qualifizierer).
- include-Direktiven wurden geändert und verwenden jetzt die richtige Groß- und Kleinschreibung und Schrägstriche, was die Portierbarkeit verbessert.
- Warnung C4061 „enumerator ' *enumerator* ' in switch of enum ' *enumeration* ' is not explicitly handled by a case label“ (Enumerator 'enumerator' in der switch-Anweisung der Enumeration 'enumeration' wird von keiner case-Bezeichnung explizit behandelt) wurde korrigiert. Diese Warnung ist standardmäßig deaktiviert und wurde als Ausnahme der allgemeinen Richtlinie der Standardbibliothek für Warnungen korrigiert. (Die Standardbibliothek ist „ **`/W4`** clean“, versucht jedoch nicht, „ **`/Wall`** clean“ zu sein. Viele standardmäßig deaktivierte Warnungen verbrauchen übermäßig viele Ressourcen und sind nicht für die regelmäßige Verwendung gedacht.)
- Verbesserte `std::list`-Debugüberprüfungen. Listeniteratoren überprüfen jetzt `operator->()`, und `list::unique()` markiert Iteratoren jetzt als ungültig.
- Die Metaprogrammierung von „uses-allocator“ wurde im `tuple` korrigiert.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- `std::partition` ruft nun in Übereinstimmung mit dem Standard das Prädikat `N` Mal anstatt `N + 1` Mal auf.
- Versuche, Magic Statics in Version 15.3 zu vermeiden, wurden in Version 15.5 korrigiert.
- `std::atomic<T>` erfordert nicht mehr, dass `T` standardmäßig konstruierbar ist.
- Heapalgorithmen, die die logarithmische Zeit nutzen, weisen ein anderes Verhalten auf, wenn das Iteratordebugging aktiviert ist. Es erfolgt keine Assertion der linearen Zeit zur Bestimmung, dass es sich bei der Eingabe tatsächlich um einen Heap handelt.
- `__declspec(allocator)` wird jetzt nur noch für C1XX geschützt, um Warnungen des Compiler-Front-Ends Clang zu verhindern, das diesen Modifizierer von declspec nicht versteht.
- `basic_string::npos` ist nun als Kompilierzeitkonstante verfügbar.
- `std::allocator` verarbeitet nun im C++17-Modus ordnungsgemäß die Speicherbelegung von überausgerichteten Typen, also von Typen, deren Ausrichtung größer als `max_align_t` ist (sofern keine Deaktivierung durch **`/Zc:alignedNew-`** erfolgt).  Vektoren von Objekten mit 16- oder 32-Byte-Ausrichtung werden z.B. nun ordnungsgemäß für SSE- und AVX-Anweisungen ausgerichtet.

### <a name="conformance-improvements"></a>Verbesserungen bei der Übereinstimmung mit Standards

- Wir haben \<any\>, \<string_view\>, `apply()` und `make_from_tuple()` hinzugefügt.
- \<optional\>, \<variant\>, `shared_ptr::weak_type` und \<cstdalign\> wurden hinzugefügt.
- **`constexpr`** wurde in C++14 für `min(initializer_list)`, `max(initializer_list)` und `minmax(initializer_list)` sowie `min_element()`, `max_element()` und `minmax_element()` aktiviert.

Weitere Informationen finden Sie unter [Microsoft C++-Sprachkonformität: Tabelle](./visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Es wurden verschiedene weitere C++17-Features implementiert. Weitere Informationen finden Sie unter [Microsoft C++-Sprachkonformität: Tabelle](cpp-conformance-improvements.md#improvements_153).
- P0602R0 wurde implementiert: „variant and optional should propagate copy/move triviality“.
- Die Standardbibliothek toleriert jetzt offiziell das Deaktivieren dynamischer RTTI über die Option [/GR-](../build/reference/gr-enable-run-time-type-information.md). `dynamic_pointer_cast()` und `rethrow_if_nested()` erfordern grundsätzlich **`dynamic_cast`** . Daher kennzeichnet die Standardbibliothek sie jetzt unter **`/GR-`** als `=delete`.
- Auch wenn dynamische RTTI über **`/GR-`** deaktiviert wurde, ist „statische RTTI“ (in Form von `typeid(SomeType)`) weiterhin verfügbar und unterstützt verschiedene Komponenten der Standardbibliothek. Die Standardbibliothek unterstützt über **`/D_HAS_STATIC_RTTI=0`** jetzt auch die Deaktivierung der statischen RTTI. Durch diese Flag werden `std::any`, die Memberfunktionen `target()` und `target_type()` von `std::function` sowie die Friend-Memberfunktionen `get_deleter()` von `std::shared_ptr` und `std::weak_ptr` deaktiviert.
- Die Standardbibliothek verwendet jetzt die C++14-Version von **`constexpr`** ohne Bedingung anstelle von bedingt definierten Makros.
- Die Standardbibliothek verwendet jetzt intern Aliasvorlagen.
- Die Standardbibliothek verwendet jetzt intern **`nullptr`** anstelle von `nullptr_t{}`. (Die interne Nutzung von NULL wurde gelöscht. Die interne Nutzung von „0-as-null“ wird nach und nach bereinigt.)
- Die Standardbibliothek verwendet jetzt intern `std::move()` anstelle der stilistisch fehlerhaften Verwendung von `std::forward()`.
- `static_assert(false, "message")` wurde in `#error message` geändert. Dies verbessert die Compilerdiagnose, da `#error` die Kompilierung sofort beendet.
- Die Standardbibliothek markiert Funktionen nicht mehr als `__declspec(dllimport)`. Für moderne Linkertechnologien ist dies nicht mehr erforderlich.
- SFINAE wurde in Standardvorlagenargumente extrahiert, wodurch der Code im Vergleich zu Rückgabetypen und Funktionsargumenttypen übersichtlicher wurde.
- Debugüberprüfungen in \<random\> verwenden jetzt die üblichen Mechanismen der Standardbibliothek anstelle der internen Funktion `_Rng_abort()`, die `fputs()` für **stderr** aufgerufen hat. Die Implementierung dieser Funktion wurde für Binärkompatibilität beibehalten. Sie wird in der nächsten binärinkompatiblen Version der Standardbibliothek entfernt.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- Mehrere Features der Standardbibliothek wurden in Übereinstimmung mit dem C++17-Standard hinzugefügt, als veraltet markiert oder entfernt. Weitere Informationen finden Sie unter [C++ Conformance Improvements in Visual Studio (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio)](cpp-conformance-improvements.md#improvements_155).
- Experimentelle Unterstützung für die folgenden parallelen Algorithmen:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Die Signaturen für die folgenden parallelen Algorithmen werden hinzugefügt, aktuell jedoch nicht parallelisiert. Bei der Profilerstellung wurden durch die Parallelisierung von Algorithmen, mit denen Elemente lediglich verschoben oder permutiert werden, keine Vorteile ermittelt:
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 Version 15.6

- \<memory_resource>
- Bibliotheksgrundlagen V1
- Löschen der `polymorphic_allocator`-Zuweisung
- Verbesserung der Klassenvorlagenargumentableitung

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

- Unterstützung für parallele Algorithmen ist nicht mehr experimentell
- Eine neue Implementierung von \<filesystem>
- Elementare Zeichenfolgenkonvertierungen (partiell)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Vermeiden unnötigen Verfalls
- Mathematische spezielle Funktionen
- `constexpr char_traits`
- Herleitungsregelwerk für die Standardbibliothek

Weitere Informationen finden Sie unter [Microsoft C++-Sprachkonformität: Tabelle](./visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Korrekturen für Leistung und Durchsatz

- Vorgenommene `basic_string::find(char)`-Überladungen rufen `traits::find` nur einmalig auf. Dies wurde zuvor als eine allgemeine Zeichenfolgensuche nach einer Zeichenfolge der Länge 1 implementiert.
- `basic_string::operator==` überprüft nun die Größe der Zeichenfolge, bevor der Inhalt der Zeichenfolge verglichen wird.
- Die Kontrollkopplung in `basic_string`, die für den Compileroptimierer schwer zu analysieren war, wurde entfernt. Bei kurzen Zeichenfolgen verursacht der Aufruf von `reserve` auch dann Kosten, wenn keine Arbeit erledigt wird.
- `std::vector` wurde aus Leistungsgründen und zur Sicherstellung der korrekten Funktionsweise überholt. Das Aliasing während des Einfügens bzw. während des Neuerstellens und Einfügens (Emplacement) wird nun korrekt entsprechend des Standards durchgeführt. Die starke Ausnahmegarantie wird nun bereitgestellt, wenn dies laut Standard über `move_if_noexcept()` oder über eine andere Logik erforderlich ist. Beim Einfügen bzw. Neuerstellen und Einfügen werden weniger Elementoperationen durchgeführt.
- Die C++-Standardbibliothek vermeidet nun die Dereferenzierung von Fancy Pointern des Typs NULL.
- Verbesserte `weak_ptr::lock()`-Leistung.
- Header der C++-Standardbibliothek vermeiden nun das Einschließen von Deklarationen für unnötige intrinsische Compilerfunktionen, um den Compilerdurchsatz zu erhöhen.
- Die Leistung des Bewegungskonstruktors von `std::string` und `std::wstring` wurde um mehr als das Dreifache verbessert.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Für Interaktionen mit **`noexcept`** , die ein Inlining der `std::atomic`-Implementierung in Funktionen verhindert haben, die die strukturierte Ausnahmebehandlung verwenden, wurde eine Problemumgehung eingeführt.
- Die interne `_Deallocate()`-Funktion der Standardbibliothek wurde in kleinere Codeabschnitte optimiert, sodass sie jetzt inline an mehr Stellen eingebettet werden kann.
- `std::try_lock()` wurde geändert und verwendet jetzt Paketerweiterung anstelle von Rekursion.
- Der Algorithmus von `std::lock()` zum Verhindern von Deadlocks wurde verbessert und verwendet jetzt `lock()`-Vorgänge, anstatt alle `try_lock()` auf allen Sperren zu durchlaufen.
- Die Optimierung von benannten Rückgabewerten in `system_category::message()` wurde aktiviert.
- `conjunction` und `disjunction` instanziieren jetzt `N + 1`-Typen anstatt `2N + 2`-Typen.
- `std::function` instanziiert den Mechanismus für die Zuweisungsunterstützung nicht mehr für jedes aufrufbare Objekt mit Typlöschung. Dies erhöht den Durchsatz und reduziert die OBJ-Größe in Programmen, die viele verschiedene Lambdas an `std::function` übergeben.
- `allocator_traits<std::allocator>` enthält manuelle `std::allocator`-Inlinevorgänge und verringert die Codegröße in Code, der mit `std::allocator` nur über `allocator_traits` interagiert (dies gilt für den Großteil von Codes).
- Die minimale Zuweisungsschnittstelle von C++11 wird jetzt von der Standardbibliothek verarbeitet, die `allocator_traits` direkt aufruft, anstatt die Zuweisung in einer internen Klasse `_Wrap_alloc` zu umschließen. Dies reduziert den Umfang des Codes, der für die Unterstützung der Zuweisung generiert wird, verbessert in einigen Fällen die Möglichkeit des Optimierers, sich mit den Standardbibliothekscontainern auseinanderzusetzen, und verbessert das Debuggen (Sie sehen im Debugger jetzt Ihren Zuweisungstyp anstelle von `_Wrap_alloc<your_allocator_type>`).
- Die Metaprogrammierung für benutzerdefinierte `allocator::reference`-Elemente, die von Zuweisungen nicht angepasst werden dürfen, wurde entfernt. (Durch Zuweisungen können Container originelle Zeiger verwenden, aber keine originellen Verweise.)
- Das Compiler-Front-End entpackt jetzt Debugiteratoren in reihenfolgebasierten for-Schleifen und verbessert so die Leistung von Debugbuilds.
- Der interne Reduzierungspfad von `basic_string` für `shrink_to_fit()` und `reserve()` befindet sich nicht mehr im Pfad für Neuzuweisungsvorgänge, wodurch der Codeumfang für alle mutierenden Member reduziert wird.
- Der interne Erweiterungspfad von `basic_string` befindet sich nicht mehr im Pfad von `shrink_to_fit()`.
- Mutierende Vorgänge von `basic_string` werden jetzt in nicht zuweisende schnelle Pfadfunktionen und zuweisende langsame Pfadfunktionen einbezogen, sodass allgemeine, nicht erneut zuweisende Funktionen wahrscheinlicher inline in aufrufende Funktionen eingebettet werden.
- Mutierende Vorgänge von `basic_string` konstruieren jetzt erneut zugewiesene Puffer im bevorzugten Zustand, anstatt lokal die Größe zu ändern. Durch eine Einfügung am Anfang einer Zeichenfolge wird der Inhalt nach der Einfügung jetzt z. B. exakt einmal verschoben. Er wird entweder nach unten oder in den neu zugeordneten Puffer verschoben. Folglich wird er bei der Neuzuordnung nicht mehr zweimal verschoben (zunächst in den neu zugeordneten Puffer und dann nach unten).
- Vorgänge, die die C-Standardbibliothek in \<string\> aufrufen, speichern jetzt die Adresse von `errno`, um wiederholte Interaktionen mit TLS zu entfernen.
- Die Implementierung von `is_pointer` wurde vereinfacht.
- Die Umstellung von SFINAE für Ausdrücke von einer Funktionsbasis auf eine **`struct`** - und `void_t`-Basis wurde abgeschlossen.
- Algorithmen der Standardbibliothek vermeiden jetzt postinkrementelle Iteratoren.
- Warnungen zu Abschneidungen beim Verwenden von 32-Bit-Zuweisungen in 64-Bit-Systemen wurden korrigiert.
- Die Zuweisung von `std::vector`-Verschiebungen erfolgt jetzt für Vorgänge, die weder der Zuweisung noch POCMA entsprechen, effizienter, indem nach Möglichkeit der Puffer wiederverwendet wird.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- `basic_string<char16_t>` interagiert nun mit den gleichen Optimierungen von `memcmp` und `memcpy` sowie ähnlichen Optimierungen, die von `basic_string<wchar_t>` verwendet werden.
- Eine Einschränkung des Optimierers, die verhindert hat, dass Funktionszeiger durch unsere Arbeitsweise „Vermeiden von Kopierfunktionen“ in Visual Studio 2015 Update 3 inline dargestellt wurden, wurde umgangen, wodurch die Leistung von `lower_bound(iter, iter, function pointer)` wiederhergestellt wurde.
- Der Mehraufwand für die Überprüfung der Reihenfolge von Eingaben (`includes`, `set_difference`, `set_symmetric_difference` und `set_union`) des Iteratordebuggens wurde durch das Entpacken von Iteratoren vor der Überprüfung der Reihenfolge verringert.
- `std::inplace_merge` überspringt nun Elemente, die sich bereits in der richtigen Position befinden.
- Das Erstellen von `std::random_device` erstellt nicht länger ein `std::string`-Element bzw. zerstört es auch nicht mehr.
- Für `std::equal` und `std::partition` wurde ein Jump Threading-Optimierungsdurchlauf ausgeführt, durch den ein Iteratorvergleich weniger erforderlich ist.
- Wenn `std::reverse` Zeiger auf trivial kopierbares `T` übergeben werden, erfolgt die Ausgabe nun an eine handgeschriebene vektorisierte Implementierung.
- `std::fill`, `std::equal` und `std::lexicographical_compare` wurden beigebracht, wie die Weiterleitung an `memset` und `memcmp` für `std::byte` und `gsl::byte` (sowie für andere char-ähnliche Enumerationen und Enumerationsklassen) funktioniert. Die Weiterleitung für `std::copy` erfolgt mithilfe von `is_trivially_copyable`. Daher sind keine Änderungen notwendig.
- Die Standardbibliothek enthält keine Destruktoren mehr mit leeren Klammern, deren einziges Verhalten darin bestand, Typen als nicht tribial zerstörbar zu definieren.

## <a name="other-libraries"></a>Weitere Bibliotheken

### <a name="open-source-library-support"></a>Unterstützung für Open-Source-Bibliotheken

**Vcpkg** ist ein Open-Source-Befehlszeilentool, das den Prozess des Beziehens und Erstellens von statischen C++-Open-Source Bibliotheken und DLLs in Visual Studio sehr stark vereinfacht. Weitere Informationen finden Sie unter [vcpkg: Ein C++-Paket-Manager für Windows, Linux und macOS](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>C++ REST SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Das C++ REST SDK, eine plattformübergreifende Web-API für C++, wurde auf Version 2.9.0 aktualisiert. Weitere Informationen finden Sie im Blogbeitrag [CppRestSDK 2.9.0 is available on GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- Weitere Korrekturen an der Übereinstimmung bei der Suche nach Namen
- Vorhandene Bewegungskonstruktoren und Bewegungszuweisungsoperatoren werden jetzt ordnungsgemäß als nicht auslösend markiert.
- Die gültige Warnung C4640 zur threadsicheren Initialisierung von lokalen statischen Variablen in „atlstr.h“ wird nicht mehr unterdrückt.
- Die threadsichere Initialisierung lokaler statischer Variablen wurde bei Verwendung von ATL zum Erstellen einer DLL im XP-Toolset automatisch deaktiviert. Dies ist nicht mehr der Fall. Wenn Sie keine threadsichere Initialisierung wünschen, können Sie **`/Zc:threadSafeInit-`** in Ihren Projekteinstellungen hinzufügen.

### <a name="visual-c-runtime"></a>Visual C++ Runtime

- Neuer Header „cfguard.h“ für Ablaufsteuerungsschutz-Symbole.

## <a name="visual-studio-2017-c-ide"></a>Visual Studio 2017 C++-IDE

- Die Leistung bei Konfigurationsänderungen ist jetzt für native C++-Projekte besser und für C++-/CLI-Projekte viel besser. Wenn eine Projektmappenkonfiguration zum ersten Mal aktiviert wird, ist sie jetzt schneller, und alle späteren Aktivierungen dieser Projektmappenkonfiguration erfolgen fast unmittelbar.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Verschiedene Projekt- und Code-Assistenten wurden im Signaturdialogstil umgeschrieben.
- **Klasse hinzufügen** startet den Assistenten zum Hinzufügen von Klassen nun direkt. Alle anderen Elemente, die hier zuvor verfügbar waren, finden Sie nun unter **Hinzufügen > Neues Element**.
- Win32-Projekte sind nun im Dialogfeld **Neues Projekt** in der **Windows Desktop-Kategorie** zu finden.
- Die **Windows-Konsolen** - und **Desktopanwendungsvorlagen** erstellen die Projekte nun, ohne einen Assistenten anzuzeigen. Es gibt einen neuen **Windows Desktop-Assistenten** in der gleichen Kategorie, der die gleichen Optionen wie der alte Assistent für die **Win32-Konsolenanwendung** anzeigt.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Mehrere Vorgänge in C++, die die IntelliSense-Engine für Refactoring und Codenavigation verwenden, werden viel schneller ausgeführt. Die folgenden Angaben basieren auf der Visual Studio Chromium-Lösung mit 3.500 Projekten:

| Feature | Leistungssteigerung |
|--|--|
| Umbenennen | 5,3-fach |
| Signatur ändern | 4,5-fach |
| Alle Verweise suchen | 4,7-fach |

C++ unterstützt jetzt STRG+Klick- **GoTo-Definition** , was die Navigation mit der Maus zu Definitionen vereinfacht. Die Strukturvisualisierung aus dem Productivity Power Tools-Paket ist nun standardmäßig auch im Produkt enthalten.

## <a name="intellisense"></a>IntelliSense

- Die neue, auf SQLite basierende Datenbank-Engine wird jetzt standardmäßig verwendet. Mit der neuen Engine werden Datenbankvorgänge wie **Zur Definition wechseln** und **Alle Verweise suchen** beschleunigt. Die Dauer der anfänglichen Projektmappenanalyse wird erheblich reduziert. Diese Einstellung befindet sich jetzt unter **Tools > Optionen > Text-Editor > C/C++ > Erweitert**. (Bisher befand sie sich unter „...C/C++ > Experimentell“.)

- Wir haben die IntelliSense-Leistung für Projekte und Dateien verbessert, die keine vorkompilierten Header verwenden. Ein automatisch vorkompilierter Header wird für Header in der aktuellen Datei erstellt.

- Wir haben die Fehlerfilterung und Hilfe für IntelliSense-Fehler in der Fehlerliste hinzugefügt. Das Klicken auf die Fehlerspalte ermöglicht jetzt die Filterung. Durch Klicken auf die einzelnen Fehler oder durch Drücken von F1 wird eine Onlinesuche nach der Fehlermeldung gestartet.

  ![Fehlerliste](media/ErrorList1.png "Fehlerliste")

  ![Gefilterte Fehlerliste](media/ErrorList2.png "Gefilterte Fehlerliste")

- Die Möglichkeit zum Filtern von Elementen der Memberliste nach Typ wurde hinzugefügt.

  ![Filtern der Memberliste](media/mlfiltering.png "Filtern der Memberliste")

- Eine neue experimentelle, vorhersehbare IntelliSense-Funktion, die das kontextbewusste Filtern in der Memberliste bereitstellt, wurde hinzugefügt. Weitere Informationen finden Sie im Blogbeitrag [C++ IntelliSense Improvements – Predictive IntelliSense & Filtering (Verbesserungen in C++-IntelliSense: Predictive IntelliSense und Filtern)](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Alle Verweise suchen** (UMSCHALT+F12) ermöglicht nun eine einfachere Navigation, auch in komplexen Codebasen. Das Feature bietet eine erweiterte Gruppierung, Filterung, Sortierung, Suche in Ergebnissen und (für einige Sprachen) eine Einfärbung, damit Sie Ihre Verweise umfassend verstehen können. Für C++ enthält die neue Benutzeroberfläche Informationen dazu, ob Informationen aus einer Variablen gelesen oder in eine Variable geschrieben werden.
- Die Punkt-zu-Pfeil-Funktion von IntelliSense wurde aus „experimentell“ in „erweitert“ verschoben und ist nun standardmäßig aktiviert. Die Editor-Funktionen **Erweiterungsbereiche** und **Erweiterungsrangfolge** wurden auch von „experimentell“ zu „erweitert“ verschoben.
- Die experimentellen Refactoringfeatures **Signatur ändern** und **Funktion extrahieren** sind nun standardmäßig verfügbar.
- Das neue experimentelle Feature „Schnelleres Laden von Projekten“ für C++-Projekte wurde hinzugefügt. Wenn Sie das nächste Mal ein C++-Projekt öffnen, wird es schneller geladen. Anschließende Ladevorgänge erfolgen sogar *noch* schneller!
- Einige dieser Features sind auch in anderen Sprachen gängig, während einige C++-spezifisch sind. Weitere Informationen zu diesen neuen Features finden Sie im Blogbeitrag [Announcing Visual Studio "15" Preview 5 (Ankündigung von Visual Studio 2017 Vorschauversion 5)](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

- Unterstützung für ClangFormat wurde hinzugefügt. Weitere Informationen finden Sie im Blogbeitrag [ClangFormat Support in Visual Studio 2017 (Unterstützung für ClangFormat in Visual Studio 2017)](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Nicht-MSBuild-Projekte mit „Ordner öffnen“

In Visual Studio 2017 wurde das Feature **Ordner öffnen** eingeführt. Dieses Feature ermöglicht Ihnen das Programmieren, Erstellen von Builds und Debuggen in einem Ordner mit Quellcode, ohne dass Projektmappen oder Projekte erstellt werden müssen. Dadurch wird der Einstieg in Visual Studio wesentlich einfacher, selbst wenn Ihr Projekt kein auf MSBuild basierendes Projekt ist. Über **Ordner öffnen** erhalten Sie Zugriff auf leistungsstarke Funktionen zum Bearbeiten, Erstellen und Debuggen von Code. Diese Funktionen entsprechen den Funktionen, die in Visual Studio bereits für MSBuild-Projekte verfügbar sind. Weitere Informationen finden Sie unter [Open Folder projects for C++ (Verwenden von „Ordner öffnen“ mit Projekten in Visual C++)](../build/open-folder-projects-cpp.md).

- Verbesserungen in der Benutzeroberfläche „Ordner öffnen“. Sie können die Oberfläche über diese JSON-Dateien anpassen:
  - CppProperties.json zum Anpassen des IntelliSense- und Browsererlebnisses.
  - Tasks.json zum Anpassen der Buildschritte.
  - Launch.json zum Anpassen des Debugvorgangs.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Die Unterstützung für alternative Compiler und Buildumgebungen wie MinGW und Cygwin wurde verbessert. Weitere Informationen finden Sie unter [Using MinGW and Cygwin with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/) (Verwenden von MinGW und Cygwin mit Visual C++ und „Ordner öffnen“).
- Unterstützung für das Definieren von globalen und konfigurationsspezifischen Umgebungsvariablen in „CppProperties.json“ und „CMakeSettings.json“ wurde hinzugefügt. Diese Umgebungsvariablen können von in „launch.vs.json“ definierten Debugkonfigurationen und von Aufgaben in „tasks.vs.json“ verwendet werden. Weitere Informationen finden Sie unter [Anpassen Ihrer Umgebung mit Visual C++ und „Ordner öffnen“](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Unterstützung für den Ninja-Generator von CMake wurde verbessert, einschließlich der Möglichkeit, ganz einfach 64-Bit-Plattformen als Ziel zu verwenden.

## <a name="cmake-support-via-open-folder"></a>Unterstützung von CMake über „Ordner öffnen“

Visual Studio 2017 führt die Unterstützung für die Verwendung von CMake-Projekten ohne Konvertierung in MSBuild-Projektdateien (.vcxproj) ein. Weitere Informationen finden Sie unter [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md). Durch Öffnen von CMake-Projekten mit **Ordner öffnen** wird die Umgebung für die Bearbeitung, Erstellung und das Debuggen von C++ automatisch konfiguriert.

- C++-IntelliSense funktioniert, ohne dass Sie eine „CppProperties.json“-Datei im Stammordner erstellen müssen. Wir haben darüber hinaus ein neues Dropdownmenü hinzugefügt, sodass Benutzer einfach zwischen von CMake- und CppProperties.json-Dateien bereitgestellten Konfigurationen wechseln können.

- Weitere Konfigurationen werden über eine Datei „CMakeSettings.json“ unterstützt, die sich im gleichen Ordner wie die Datei „CMakeLists.txt“ befindet.

  ![CMake – Ordner öffnen](media/cmake-cpp.png "CMake – Ordner öffnen")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Unterstützung für den Ninja-Generator von CMake wurde hinzugefügt.

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017 Version 15.4

- Unterstützung für das Importieren von vorhandenen CMake-Caches wurde hinzugefügt.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- Unterstützung für CMake 3.11, die Codeanalyse in CMake-Projekten, die Ansicht „Ziele“ im Projektmappen-Explorer, die Optionen zur Cachegenerierung und die Kompilierung von Einzeldateien wurde hinzugefügt. Weitere Informationen finden Sie im Blogbeitrag [CMake Support in Visual Studio – Targets View, Single File Compilation, and Cache Generation Settings (CMake-Unterstützung in Visual Studio: Ansicht „Ziele“, Kompilierung von Einzeldateien und Einstellungen für Cachegenerierung)](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) und [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development"></a>Windows-Desktopentwicklung

Die Installationsoberfläche ermöglicht bei der Installation der ursprünglichen C++-Arbeitsauslastung jetzt eine feinere Abstimmung. Wir haben auswählbare Komponenten hinzugefügt, sodass Sie nur die Tools installieren können, die Sie benötigen. Die angegebenen Installationsgrößen für die im Installationsprogramm aufgeführten Komponenten sind falsch, sodass die Gesamtgröße unterschätzt wird.

Wenn Sie Win32-Projekte erfolgreich in der C++-Desktoparbeitsauslastung erstellen möchten, müssen Sie ein Toolset und ein Windows SDK installieren. Zum Installieren der empfohlenen (ausgewählten) Komponenten benötigen Sie **VC++ 2017 c141 Toolset (x86, x64)** und **Windows 10 SDK (10.0.nnnnn)** . Sollten die erforderlichen Tools nicht installiert sein, werden Projekte nicht erfolgreich erstellt. Außerdem reagiert der Assistent nicht mehr.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Die Visual C++ Build-Tools (zuvor als eigenständiges Produkt verfügbar) sind jetzt als Workload im Visual Studio-Installer enthalten. Diese Workload installiert nur die Tools, die zum Erstellen von C++-Projekten ohne Installation der Visual Studio-IDE erforderlich sind. Die Toolsets v140 und v141 sind beide enthalten. Das v141-Toolset enthält die neuesten Verbesserungen in Version 15.5 von Visual Studio 2017. Weitere Informationen finden Sie unter [Visual Studio Build Tools enthalten nun die MSVC-Toolsets VS2017 und VS2015](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

Die beliebte Erweiterung [Visual C++ für Linux-Entwicklung](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.VisualCforLinuxDevelopment) ist nun Bestandteil von Visual Studio. Diese Installation bietet alles, was Sie zum Entwickeln und Debuggen von C++-Anwendungen in einer Linux-Umgebung benötigen.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 Version 15.2

Verbesserungen für plattformübergreifende gemeinsame Codenutzung und Typvisualisierung. Weitere Informationen finden Sie unter [Linux C++ improvements for cross-platform code sharing and type visualization](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/) (Linux C++ – Verbesserungen für plattformübergreifende gemeinsame Codenutzung und Typvisualisierung).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- Die Linux-Workload hat Unterstützung für **rsync** als Alternative zu **sftp** hinzugefügt, um Dateien auf Linux-Remotecomputern zu synchronisieren.
- Unterstützung für Kreuzkompilierung für ARM-Mikrocontroller wurde hinzugefügt. Um dies in der Installation zu aktivieren, wählen Sie **Linux-Entwicklung mit der C++-Workload** und dann die Option für **Eingebettete und IoT-Entwicklung** aus. Durch diese Option werden die ARM GCC-Kreuzkompilierungstools und Make Ihrer Installation hinzugefügt. Weitere Informationen finden Sie unter [ARM GCC-Kreuzkompilierung in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Unterstützung für CMake wurde hinzugefügt. Sie können nun an Ihrer bestehenden CMake-Codebasis arbeiten, ohne sie in ein Visual Studio-Projekt konvertieren zu müssen. Weitere Informationen finden Sie unter [Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md).
- Unterstützung für das Ausführen von Remotetasks wurde hinzugefügt. Mit dieser Funktion können Sie jeden Befehl auf einem Remotesystem ausführen, das im Verbindungs-Manager von Visual Studio definiert ist. Remotetasks bieten auch die Möglichkeit zum Kopieren von Dateien auf das Remotesystem.
Weitere Informationen finden Sie unter [Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

- Verschiedene Verbesserungen für Linux-Workload-Szenarios. Weitere Informationen finden Sie unter [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process (Verbesserungen der Linux-C++-Workload für das Projektsystem, die Linux-Konsole, Windows, rsync und „An den Prozess anhängen“)](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense für Header in Linux-Remoteverbindungen. Weitere Informationen finden Sie unter [IntelliSense for Remote Linux Headers (IntelliSense für Linux-Remoteheaders)](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) und [Konfigurieren eines Linux-CMake-Projekts](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Spieleentwicklung mit C++

Verwenden Sie die volle Leistung von C++, um professionelle Spiele zu erstellen, die von DirectX oder Cocos2d unterstützt werden.

## <a name="mobile-development-with-c-for-android-and-ios"></a>Mobile Entwicklung mit C++ für Android und iOS

Sie können nun mithilfe von Visual Studio mobile Apps erstellen und debuggen, die auf Android und iOS ausgerichtet sind.

## <a name="universal-windows-apps"></a>Universelle Windows-Apps

C++ wird als optionale Komponente für die Arbeitsauslastung der Universellen Windows-App bereitgestellt. Aktuell müssen C++-Projekte manuell aktualisieren werden. Sie können ein Projekt für die Universelle Windows-Plattform mit dem Ziel v140 in Visual Studio 2017 öffnen. Wenn Visual Studio 2015 nicht installiert ist, müssen Sie das v141-Plattformtoolset jedoch auf den Projekteigenschaftenseiten auswählen.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Neue Optionen für C++ auf der universellen Windows-Plattform (UWP)

Ihnen stehen nun neue Optionen zum Schreiben und Packen von C++-Anwendungen für die Universelle Windows-Plattform und den Microsoft Store zur Verfügung: Mit der Desktop Bridge-Infrastruktur können Sie Ihre vorhandene Desktopanwendung oder das COM-Objekt für die Bereitstellung über den Microsoft Store packen. Oder für die Bereitstellung über Ihre vorhandenen Kanäle mittels Querladen. Mit den neuen Funktionen in Windows 10 können Sie Ihre Desktopanwendung auf unterschiedliche Weise um die Funktionalität der universellen Windows-Plattform (UWP) erweitern. Weitere Informationen finden Sie unter [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Eine Projektvorlage **Paketerstellungsprojekt für Windows-Anwendungen** wurde hinzugefügt, die die Paketerstellung von Desktopanwendungen mithilfe von Desktop Bridge unterstützt. Sie ist unter **Datei > Neu > Projekt > Installiert > Visual C++ > Universelle Windows-Plattform** verfügbar. Weitere Informationen finden Sie unter [Packen einer App mit Visual Studio (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Beim Schreiben von neuem Code können Sie nun C++/WinRT verwenden. Dies ist eine C++-Standardsprachprojektion für Windows-Runtime (WinRT), die nur in Headerdateien implementiert wird. Mit ihr können Sie Windows-Runtime-APIs mit jedem standardkonformen C++-Compiler nutzen und erstellen. C++/WinRT wurde dafür konzipiert, C++-Entwicklern erstklassigen Zugriff auf die moderne Windows-API zur Verfügung zu stellen. Weitere Informationen finden Sie unter [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/).

Ab Build 17025 der Windows SDK Insider Preview ist C++/WinRT im Windows SDK enthalten. Weitere Informationen finden Sie unter [C++/WinRT ist jetzt im Windows SDK enthalten](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="the-clangc2-platform-toolset"></a>Das Clang/C2-Plattformtoolset

Das Clang/C2-Toolset, das im Lieferumfang von Visual Studio 2017 enthalten ist, unterstützt jetzt die Option **`/bigobj`** , die für das Erstellen großer Projekte entscheidend ist. Es umfasst außerdem eine Reihe wichtiger Fehlerbehebungen, sowohl im Front-End als auch im Back-End des Compilers.

## <a name="c-code-analysis"></a>C++-Codeanalyse

Visual Studio liefert nun die C++-Kernprüfungen zum Erzwingen der [C++-Kernrichtlinien](https://github.com/isocpp/CppCoreGuidelines). Aktivieren Sie die Prüfungen auf den Projekteigenschaftenseiten in den **Erweiterungen für die Codeanalyse**. Die Erweiterungen werden dann beim Ausführen der Codeanalyse eingeschlossen. Weitere Informationen finden Sie unter [Verwenden der C++-Core-Richtlinienprüfungen](../code-quality/using-the-cpp-core-guidelines-checkers.md).

![Screenshot des Dialogfelds „Eigenschaftenseiten“, in dem „Konfigurationseigenschaften“ > „Codeanalyse“ > „Allgemein“ ausgewählt ist und im Abschnitt „Diesen Regelsatz ausführen“ eine Reihe von Core-Prüfungen aufgeführt werden](media/CppCoreCheck.png "CppCoreCheck-Eigenschaftenseite")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 Version 15.3

- Es wurde Unterstützung für Regeln in Bezug auf die Ressourcenverwaltung hinzugefügt.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

- Neue C++ Core Guidelines-Überprüfungen umfassen die Richtigkeit von intelligenten Zeigern, die richtige Verwendung von globalen Initialisierern und die Kennzeichnung der Verwendung von Konstrukten wie **`goto`** und fehlerhaften Umwandlungen.

- Einige Warnnummern, die in Version 15.3 vorhanden waren, sind in Version 15.5 nicht mehr verfügbar. Diese Warnungen wurden durch genauere Überprüfungen ersetzt.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 Version 15.6

- Unterstützung für die Analyse von Einzeldateien hinzugefügt und Verbesserungen der Laufzeitleistung der Analyse vorgenommen. Weitere Informationen finden Sie unter [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2 (Verbesserungen an der statischen C++-Analyse für Visual Studio 2017-Version 15.6, Vorschauversion 2)](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

- Unterstützung für [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) hinzugefügt. So können Sie angeben, welche Codeanalyseregeln ausgeführt werden sollen.
- Unterstützung für zusätzliche C++ Core Guidelines-Regeln hinzugefügt.  Weitere Informationen finden Sie unter [Verwenden der C++-Core-Richtlinienprüfungen](../code-quality/using-the-cpp-core-guidelines-checkers.md).

## <a name="unit-testing-in-visual-studio-2017"></a>Komponententests in Visual Studio 2017

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 Version 15.5

Google Test Adapter und Boost.Test-Adapter sind jetzt als Komponenten der Workload **Desktopentwicklung mit C++** verfügbar. Sie sind in den **Test-Explorer** integriert. CTest-Unterstützung wurde für CMake-Projekte hinzugefügt (unter Verwendung von „Ordner öffnen“), obwohl die vollständige Integration in den **Test-Explorer** noch nicht verfügbar ist. Weitere Informationen finden unter [Erstellen von Komponententests für C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 Version 15.6

- Unterstützung für dynamische `Boost.Test`-Bibliotheksunterstützung hinzugefügt.
- In der IDE steht jetzt eine `Boost.Test`-Elementvorlage zur Verfügung.

Weitere Informationen finden Sie unter [`Boost.Test` Unit Testing: Dynamic Library support and New Item Template (Komponententests mit Boost.Test: Unterstützung für dynamische Bibliotheken und neue Elementvorlagen)](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017-Version 15.7

Unterstützung für [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) für C++-Komponententestprojekte hinzugefügt. Weitere Informationen finden Sie unter [Announcing CodeLens for C++ Unit Testing (Ankündigung: CodeLens für C++-Unittests)](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio-Grafikdiagnose

Visual Studio-Grafikdiagnosetools: Mit diesen Tools können Sie Rendering- und Leistungsprobleme bei Direct3D-Apps erfassen und analysieren. Verwenden Sie sie für Apps, die lokal auf Ihrem Windows-PC, in einem Windows-Geräteemulator oder auf einem Remotecomputer oder -gerät ausgeführt werden.

- **Ein- und Ausgabe von Vertex- und Geometrieshadern:** Die Möglichkeit der Anzeige der Ein- und Ausgabe von Vertex- und Geometrieshadern war eines der am häufigsten gewünschten Features. Dieses Feature wird nun in den Tools unterstützt. Wählen Sie die VS- oder GS-Phase in der Ansicht „Pipelinestufen“, um mit dem Untersuchen der Ein- und Ausgabe in der nachstehenden Tabelle zu beginnen.

  ![Ein-/Ausgabe für Shader](media/io-shaders.png)

- **Suchen und Filtern in der Objekttabelle:** Diese Option stellt eine schnelle und einfache Möglichkeit dar, die gesuchten Ressourcen zu finden.

  ![Screenshot des Abschnitts „Objekttabelle“, in dem das Dropdown „Typ“ und das Suchfeld gekennzeichnet sind.](media/search.png)

- **Ressourcenverlauf:** In dieser neue Ansicht wurde der gesamte Änderungsverlaufs einer Ressource und deren Verwendung während des Renderns eines aufgezeichneten Frames optimiert. Um den Verlauf für jede Ressource aufzurufen, klicken Sie auf das Uhrsymbol neben jeden Ressourcenlink.

  ![Ressourcenverlauf](media/resource-history.png)

  Dadurch wird das Toolfenster **Ressourcenverlauf** angezeigt, in dem sich der Änderungsverlauf der Ressource befindet.

  ![Ressourcenverlaufsänderung](media/resource-history-change.png)

  Sie können Frames bei aktivierter Erfassung der vollständigen Aufrufliste erfassen. Dadurch können Sie im Handumdrehen den Kontext der einzelnen Änderungsereignisse ableiten und innerhalb Ihres Visual Studio-Projekts untersuchen. Die Option zur Erfassung der vollständigen Liste wird in Visual Studio im Dialogfeld **Tools > Optionen** unter **Grafikdiagnose** festgelegt.

- **API-Statistiken:** Eine allgemeine Zusammenfassung der API-Verwendung in Ihrem Frame. Dies kann beim Ermitteln von Aufrufen nützlich sein, von denen Sie nicht wissen, dass sie erfolgen, oder von Aufrufen, die zu häufig erfolgen. Dieses Fenster steht über **Ansicht > API Statistiken** in der Visual Studio-Grafikanalyse zur Verfügung.

  ![API-Statistiken](media/api-stats.png)

- **Speicherstatistiken:** Diese Option stellt dar, wie viel Arbeitsspeicher der Treiber für die Ressourcen reserviert, die Sie im Frame erstellen. Dieses Fenster steht über **Ansicht > Speicherstatistiken** in der **Visual Studio-Grafikanalyse** zur Verfügung. Um Daten zur Anzeige in einer Tabellenkalkulation in eine CSV-Datei zu kopieren, klicken Sie mit der rechten Maustaste, und wählen Sie **Alles kopieren**.

  ![Speicherstatistiken](media/memory-stats.png)

- **Frame-Überprüfung:** Mit dieser neuen Liste mit Fehlern und Warnungen können Sie je nach Problem, das auf Direct3D-Debugebene erkannt wurde, einfach zu Ihrer Ereignisliste navigieren. Klicken Sie zum Öffnen des Fensters in der Visual Studio-Grafikanalyse auf **Ansicht > Frame-Überprüfung**. Klicken Sie dann auf **Überprüfung ausführen** , um die Analyse zu starten. Je nach Komplexität des Frames kann dieser Vorgang mehrere Minuten dauern.

  ![Frame-Überprüfung](media/frame-validation.png)

- **Frame-Analyse für D3D12:** Verwenden Sie die Frame-Analyse zum Analysieren der Leistung von Zeichenvorgängen mit „Was-wäre-wenn“-Experimenten. Wechseln Sie zur Registerkarte „Frame-Analyse“, und führen Sie Analysen aus, um den Bericht anzuzeigen. Weitere Informationen finden Sie im Video [GoingNative 25: Visual Studio Graphics Frame Analysis (GoingNative 25: Grafikframe-Analyse in Visual Studio)](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool).

  ![Frame-Analyse](media/frame-analysis.png)

- **Verbesserungen der GPU-Nutzung:** Öffnen Sie Ablaufverfolgungen, die über den Visual Studio-Profiler für GPU-Nutzung mit dem Tool „GPU-Ansicht“ oder Windows Performance Analyzer (WPA) erstellt wurden, um eine ausführlichere Analyse zu erhalten. Wenn das Windows Performance Toolkit installiert ist, sind rechts unten in der Sitzungsübersicht zwei Links vorhanden: einer für WPA und einer für die GPU-Ansicht.

  ![GPU-Nutzung](media/gpu-usage.png)

  Ablaufverfolgungen, die über diesen Link in der GPU-Ansicht geöffnet werden, unterstützen das synchronisierte Zoomen und Schwenken auf der Zeitachse in Visual Studio und der GPU-Ansicht. Über ein Kontrollkästchen in Visual Studio wird festgelegt, ob die Synchronisierung aktiviert ist oder nicht.

  ![GPU-Ansicht](media/gpu-view.png)

::: moniker-end

::: moniker range="=msvc-140"

Eine vollständige Liste der Neuerungen bis zum Visual Studio 2015 Update 3 finden Sie unter [Visual C++: Neuerungen von 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

Weitere Informationen zu Neuerungen in Visual Studio 2015 finden Sie in den Versionshinweisen. Sie sind im [Verlauf der Versionshinweise zu Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history) verlinkt.

Weitere Informationen zu Neuerungen für C++ in Visual Studio 2019 finden Sie unter [Neuerungen bei C++ in Visual Studio](?preserve-view=true&view=msvc-160).

Weitere Informationen zu Neuerungen für C++ in Visual Studio 2017 finden Sie unter [Neuerungen für C++ in Visual Studio 2017](?preserve-view=true&view=msvc-150).

::: moniker-end
