---
title: Profilgesteuerte Optimierungen
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: efa4c35810f6272b89ff11cd1c890a7f535cfc1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232728"
---
# <a name="profile-guided-optimizations"></a>Profilgesteuerte Optimierungen

Mit der profilgesteuerten Optimierung (PGO) können Sie eine ganze ausführbare Datei optimieren, wobei der Optimierer Daten aus Testläufen der EXE- oder DLL-Datei verwendet. Die Daten repräsentieren die wahrscheinliche Leistung des Programms in einer Produktionsumgebung.

Profilgesteuerte Optimierungen sind nur für native x86- oder x64-Ziele verfügbar. Profilgesteuerte Optimierungen sind nicht für ausführbare Dateien verfügbar, die in der Common Language Runtime ausgeführt werden. Auch wenn Sie eine Assembly mit einer Mischung aus nativem und verwaltetem Code (mithilfe der Compileroption **/clr**) erstellen, können Sie die profilgesteuerte Optimierung nicht für den nativen Code verwenden. Der Versuch, ein Projekt zu erstellen, bei dem diese Optionen in der IDE festgelegt sind, verursacht einen Buildfehler.

> [!NOTE]
> Informationen, die bei Testläufen für die Profilerstellung erfasst wurden, setzen Optimierungen außer Kraft, die ansonsten wirksam wären, wenn Sie **/Ob**, **/Os** oder **/Ot** angeben. Weitere Informationen finden Sie unter [/Ob (Inlinefunktionserweiterung)](reference/ob-inline-function-expansion.md) und [/Os, /Ot (Kompakten Code bevorzugen, Schnellen Code bevorzugen)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Schritte zum Optimieren Ihrer App

Um die profilgesteuerte Optimierung zu verwenden, führen Sie die folgenden Schritte aus, um Ihre App zu optimieren:

- Kompilieren von einer oder mehreren Quellcodedateien mit [/GL](reference/gl-whole-program-optimization.md)

   Jedes mit **/GL** erstellte Modul kann während der profilgesteuerten Optimierungstestläufe untersucht werden, um das Laufzeitverhalten aufzuzeichnen. Nicht jedes Modul in einem profilgesteuerten Optimierungsbuild muss mit **/GL** kompiliert werden. Jedoch werden nur die mit **/GL** kompilierten Module instrumentiert und sind später für profilgesteuerte Optimierungen verfügbar.

- Link zu [/LTCG](reference/ltcg-link-time-code-generation.md) und [/GENPROFILE oder /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)

   Durch die Verwendung von **/LTCG** und **/GENPROFILE** oder **/FASTGENPROFILE** wird eine `.pgd`-Datei erstellt, wenn die instrumentierte App ausgeführt wird. Nachdem die Testlaufdaten zur `.pgd`-Datei hinzugefügt wurden, kann diese als Eingabe für den nächsten Linkschritt (Erstellen des optimierten Images) verwendet werden. Wenn Sie **/GENPROFILE** angeben, können Sie optional ein Argument **PGD =** _Dateiname_ hinzufügen, um einen nicht standardmäßigen Namen oder Speicherort für die `.pgd`-Datei anzugeben. Die Kombination der Linkeroptionen **/LTCG** und **/GENPROFILE** oder **/FASTGENPROFILE** ersetzt die veraltete Linkeroption **/LTCG: PGINSTRUMENT**.

- Profilieren der Anwendung

   Jedes Mal, wenn eine profilierte EXE-Sitzung endet oder eine profilierte DLL entladen wird, wird eine `appname!N.pgc`-Datei erstellt. Eine `.pgc`-Datei enthält Informationen über einen bestimmten Anwendungstestlauf. *appname* ist der Name Ihrer App, und *N* ist eine Zahl, die mit 1 beginnt und entsprechend der Anzahl der anderen `appname!N.pgc`-Dateien im Verzeichnis erhöht wird. Sie können eine `.pgc`-Datei löschen, wenn der Testlauf kein zu optimierendes Szenario darstellt.

   Während eines Testlaufs können Sie das Schließen der aktuell geöffneten `.pgc`-Datei und das Erstellen einer neuen `.pgc`-Datei mit dem [pgosweep](pgosweep.md)-Hilfsprogramm erzwingen (wenn beispielsweise das Ende eines Testszenarios nicht mit dem Beenden der Anwendung einhergeht).

   Die Anwendung kann auch direkt eine PGO-Funktion aufrufen, [PgoAutoSweep](pgoautosweep.md), um die Profildaten zum Zeitpunkt des Aufrufs als `.pgc`-Datei zu erfassen. So können Sie den Code, der von den erfassten Daten in Ihren `.pgc`-Dateien abgedeckt wird, genauer kontrollieren. Ein Beispiel für die Verwendung dieser Funktion finden Sie in der [PgoAutoSweep](pgoautosweep.md)-Dokumentation.

   Wenn Sie den instrumentierten Build erstellen, erfolgt die Datenerfassung standardmäßig im nicht threadsicheren Modus, der schneller, aber möglicherweise ungenau ist. Mit dem Argument **EXACT** für **/GENPROFILE** oder **/FASTGENPROFILE** können Sie die Datenerfassung im threadsicheren Modus festlegen, der präziser, aber langsamer ist. Diese Option ist auch verfügbar, wenn Sie beim Erstellen des instrumentierten Builds die veraltete [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode)-Umgebungsvariable oder die veraltete **/POGOSAFEMODE**-Linkeroption festlegen.

- Link zu  **/LTCG** und **/USERPROFILE**

   Verwenden Sie sowohl die Linkeroptionen **/LTCG** als auch [/USEPROFILE](reference/useprofile.md), um das optimierte Image zu erstellen. Bei diesem Schritt wird die `.pgd`-Datei als Eingabe verwendet. Wenn Sie **/USEPROFILE** angeben, können Sie optional ein Argument **PGD =** _Dateiname_ hinzufügen, um einen nicht standardmäßigen Namen oder Speicherort für die `.pgd`-Datei anzugeben. Sie können diesen Namen auch mit der veralteten **/PGD**-Linkeroption angeben. Die Kombination aus **/LTCG** und **/USERPROFILE** ersetzt die veralteten Linkeroptionen **/LTCG:PGOPTIMIZE** und **/LTCG:PGUPDATE**.

Es ist sogar möglich, die optimierte ausführbare Datei zu erstellen und später zu ermitteln, ob eine zusätzliche Profilierung zum Erstellen eines weiter optimierten Images sinnvoll wäre. Wenn das instrumentierte Image und seine `.pgd`-Datei verfügbar sind, können Sie zusätzliche Testläufe ausführen und das optimierte Image mit der neueren `.pgd`-Datei neu erstellen, indem Sie die gleichen Linkeroptionen **/LTCG** und **/USEPROFILE** verwenden.

> [!NOTE]
> Bei den zwei Dateien `.pgc` und `.pgd` handelt es sich um Binärdateien. Wenn diese in einem Quellcodeverwaltungssystem gespeichert werden, werden jegliche automatischen Transformationen vermieden, die möglicherweise an Textdateien vorgenommen werden.

## <a name="optimizations-performed-by-pgo"></a>Von PGO ausgeführte Optimierungen

Die profilgesteuerten Optimierungen umfassen diese Überprüfungen und Verbesserungen:

- **Inlinefunktion**: Wenn beispielsweise eine Funktion A eine Funktion B häufig aufruft, und Funktion B relativ klein ist, wird bei der profilgesteuerten Optimierung Funktion B in eine Inlinefunktion von Funktion A umgewandelt.

- **Spekulatives Laden virtueller Aufrufe**: Wenn ein virtueller oder anderer Aufruf über einen Funktionszeiger häufig eine bestimmte Funktion zum Ziel hat, kann bei einer profilgesteuerten Optimierung ein bedingt ausgeführter direkter Aufruf der häufig als Ziel dienenden Funktion eingefügt und der direkte Aufruf als Inlinefunktion umgesetzt werden.

- **Registerzuteilung**: Die Optimierung auf der Grundlage von Profildaten führt zu einer besseren Registerzuteilung.

- **Basisblockoptimierung**: Die Basisblockoptimierung ermöglicht, dass häufig ausgeführte Basisblöcke, die temporär innerhalb eines bestimmten Rahmens ausgeführt werden, in derselben Seitengruppe platziert werden (Lokalität). Das minimiert die Anzahl der verwendeten Seiten und damit den Arbeitsspeicherverbrauch.

- **Optimierung von Größe/Geschwindigkeit**: Funktionen, für die das Programm die meiste Zeit benötigt, können auf Geschwindigkeit optimiert werden.

- **Funktionslayout**: Auf Grundlage des Aufrufdiagramms und des profilierten Verhaltens von aufrufender/aufgerufener Funktion werden Funktionen, die tendenziell denselben Ausführungspfad verwenden, im selben Abschnitt platziert.

- **Optimierung der bedingten Verzweigung**: Mit den Wertetests lässt sich durch profilgesteuerte Optimierungen herausfinden, ob ein bestimmter Wert in einer switch-Anweisung öfter als andere Werte verwendet wird.  Dieser Wert kann dann aus der switch-Anweisung herausgezogen werden.  Dasselbe Verfahren kann bei **`if`** ... **`else`** -Anweisungen verwendet werden, bei denen der Optimierer die **`if`** ... **`else`** -Anweisungen so anordnen kann, dass abhängig davon, welcher Block häufiger den Wert „TRUE“ aufweist, entweder der **`if`** - oder der **`else`** -Block zuerst platziert wird.

- **Abtrennung von totem Code**: Während der Profilierung wird nicht aufgerufener Code in einen speziellen Bereich verschoben, der an das Ende der Gruppe von Abschnitten angehängt wird. Damit wird dieser Abschnitt effektiv von den oft verwendeten Seiten getrennt.

- **EH-Code-Trennung**: Da EH-Code nur in Ausnahmefällen ausgeführt wird, kann er oft in einen separaten Abschnitt verschoben werden. Es wird verschoben, wenn durch profilgesteuerte Optimierungen festgestellt werden kann, dass die Ausnahmen nur unter Ausnahmebedingungen auftreten.

- **Systeminterne Arbeitsspeicher**: Ob eine systeminterne Funktion erweitert werden soll oder nicht, hängt davon ab, ob sie häufig aufgerufen wird. Eine systeminterne Funktion kann auch auf Grundlage der Blockgröße von Verschiebungen oder Kopien optimiert werden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über diese Umgebungsvariablen, Funktionen und Tools, die Sie bei profilgesteuerten Optimierungen verwenden können:

[Umgebungsvariablen für profilgesteuerte Optimierungen](environment-variables-for-profile-guided-optimizations.md)<br/>
Diese Variablen wurden verwendet, um das Laufzeitverhalten von Testszenarios anzugeben. Sie sind nun veraltet und wurden durch neue Linkeroptionen ersetzt. In diesem Dokument wird gezeigt, wie Sie von den Umgebungsvariablen zu den Linkeroptionen wechseln.

[PgoAutoSweep](pgoautosweep.md)<br/>
Eine Funktion, die Sie Ihrer App hinzufügen können, um eine differenzierte Steuerung der Datenerfassung für Datei `.pgc` bereitzustellen.

[pgosweep](pgosweep.md)<br/>
Ein Befehlszeilen-Hilfsprogramm, das alle Profildaten in die `.pgc`-Datei schreibt, die `.pgc`-Datei schließt und eine neue `.pgc`-Datei öffnet.

[pgomgr](pgomgr.md)<br/>
Ein Befehlszeilen-Hilfsprogramm, mit dem der `.pgd`-Datei Profildaten aus einer oder mehreren `.pgc`-Dateien hinzugefügt werden.

[How to: Zusammenführen mehrerer PGO-Profile in einem einzigen Profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Beispiele für **pgomgr**-Verwendung.

## <a name="see-also"></a>Siehe auch

[Zusätzliche MSVC-Buildtools](reference/c-cpp-build-tools.md)
