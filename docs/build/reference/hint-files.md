---
title: Hinweisdateien
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: 8037cb8025cc85a8479528490e1512531cbcc035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322310"
---
# <a name="hint-files"></a>Hinweisdateien

Makros führen normalerweise dazu, dass bestimmte Codebereiche vom Parser für die Datenbank zum Durchsuchen von C++-Code übersprungen werden. Dies wird vermieden, indem Makros einer *Hinweisdatei* hinzugefügt werden. Wenn Sie ein Visual Studio C++-Projekt öffnen, analysiert der Parser den Code in jeder Quelldatei des Projekts und erstellt eine Datenbank mit Informationen zu jedem Bezeichner. Die IDE verwendet diese Informationen, um Features zum Durchsuchen von Code wie die **Klassenansicht** und die **Navigationsleiste** zu unterstützen.

Der Parser für die Datenbank zum Durchsuchen von C++-Code ist ein Fuzzyparser, der große Mengen an Code in kurzer Zeit analysieren kann. Ein Grund dafür ist, dass die Inhalte von Blöcken übersprungen werden. Beispielsweise wird nur erfasst, wo sich eine Funktion befindet und welche Parameter für diese vorhanden sind. Der Inhalt der Funktion wird hingegen ignoriert. Bestimmte Makros können zu Problemen mit den Heuristiken führen, die zur Ermittlung des Anfangs und Endes eines Blocks eingesetzt werden. Dadurch werden bestimmte Codebereiche nicht richtig erfasst.

Die übersprungenen Bereiche können unterschiedliche Auswirkungen haben:

- Typen und Funktionen fehlen in der **Klassenansicht**, im Fenster **Gehe zu** und in der **Navigationsleiste**.

- In der **Navigationsleiste** werden falsche Bereiche angezeigt.

- Für bereits definierte Funktionen werden **Deklaration/Definition erstellen**-Vorschläge angezeigt.

Eine Hinweisdatei enthält vom Benutzer anpassbare Hinweise, die die gleiche Syntax wie die C/C++-Makrodefinitionen aufweisen. Visual C++ verfügt über eine integrierte Hinweisdatei, die für die meisten Projekte ausreicht. Sie können allerdings eigene Hinweisdateien erstellen, um die Leistung des Parsers speziell für Ihr Projekt zu verbessern.

> [!IMPORTANT]
> Wenn Sie eine Hinweisdatei ändern oder hinzufügen, sind zusätzliche Schritte erforderlich, damit die Änderungen wirksam werden:
>
> - In Versionen vor Visual Studio 2017 Version 15.6: Löschen Sie die .sdf-Datei und/oder VC.db-Datei in der Projektmappe für alle Änderungen.
> - In Visual Studio 2017 Version 15.6 und höher: Schließen und öffnen Sie die Lösung nach dem Hinzufügen neuer Hinweisdateien erneut.

## <a name="scenario"></a>Szenario

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Ohne eine Hinweisdatei wird `Function` nicht in der **Klassenansicht**, im Fenster **Gehe zu** oder in der **Navigationsleiste** angezeigt. Nachdem Sie eine Hinweisdatei mit dieser Makrodefinition hinzugefügt haben, ersetzt der Parser das `NOEXCEPT`-Makro und analysiert die Funktion fehlerfrei:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Störende Makros

Es gibt zwei Kategorien von Makros, die die Funktionsweise des Parsers stören:

- Makros, die Schlüsselwörter einer Funktion kapseln

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Für diese Makros muss nur der Name des Makros in der Hinweisdatei angegeben werden:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makros, die eine ungleiche Anzahl öffnender und geschlossener Klammern enthalten

   ```cpp
   #define BEGIN {
   ```

   Für diese Makros müssen sowohl der Name des Makros als auch der zugehörige Inhalt in der Hinweisdatei angegeben werden:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Editor-Unterstützung

Ab Version 15.8 von Visual Studio 2017 gibt es verschiedene Features, mit denen sich störende Makros identifizieren lassen:

- Makros, die sich innerhalb von Bereichen befinden und vom Parser übersprungen werden, werden hervorgehoben.

- Mit einer Schnellaktion kann eine Hinweisdatei erstellt werden, die das hervorgehobene Makro einschließt. Wenn bereits eine Hinweisdatei vorhanden ist, kann ihr mit einer anderen Schnellaktion das Makro hinzugefügt werden.

![Hervorgehobenes Makro.](media/hint-squiggle-and-actions.png "Hinweis-Squiggle und schnelle Aktionen")

Nach dem Ausführen einer der beiden Schnellaktionen analysiert der Parser die Dateien neu, die von der Hinweisdatei betroffen sind.

Standardmäßig wird das störende Makro als Vorschlag hervorgehoben. Die Hervorhebung kann beispielsweise durch eine grüne oder rote Wellenlinie so angepasst werden, dass sie deutlicher zu sehen ist. Verwenden Sie dazu unter **Extras** > **Optionen** > **Text-Editor** > **C/C++** > **Ansicht** im Abschnitt **Wellenlinien im Code** die Option **Makros in übersprungenen Suchbereichen**.

![Makros in der Option Übersprungene Browsing-Regionen.](media/skipped-regions-squiggle-option.png "Übersprungene Bereiche squiggle Option.")

## <a name="display-browsing-database-errors"></a>Anzeigen von Fehlern beim Durchsuchen der Datenbank

Der Menübefehl **Projektanzeige** > **Browsing Database Errors** zeigt alle Bereiche an, die in der **Fehlerliste**nicht analysiert werden konnten. Der Befehl dient dazu, die Erstellung der Hinweisdatei zu optimieren. Vom Parser kann jedoch nicht ermittelt werden, ob die Ursache des Fehlers ein störendes Makro ist. Sie müssen daher jeden Fehler einzeln analysieren. Führen Sie den Befehl **Fehler beim Durchsuchen der Datenbank anzeigen** aus, und navigieren Sie zu jedem Fehler, um die betroffene Datei im Editor zu laden. Wenn sich Makros im Bereich befinden, werden sie hervorgehoben. Sie können diese mit Schnellaktionen einer Hinweisdatei hinzufügen. Nach einem Update der Hinweisdatei wird die Fehlerliste automatisch aktualisiert. Wenn Sie die Hinweisdatei manuell ändern, können Sie mit dem Befehl **Projektmappe neu prüfen** ein Update auslösen.

## <a name="architecture"></a>Aufbau

Hinweisdateien beziehen sich auf physische Verzeichnisse, nicht auf die lokalen Verzeichnisse, die im **Projektmappen-Explorer** angezeigt werden. Sie müssen eine Hinweisdatei nicht Ihrem Projekt hinzufügen, damit diese wirksam ist. Das Analysesystem verwendet Hinweisdateien nur, wenn es Quelldateien analysiert.

Jede Hinweisdatei heißt **cpp.hint**. Viele Verzeichnisse können eine Hinweisdatei enthalten, es kann jedoch nur eine Hinweisdatei pro Verzeichnis vorhanden sein.

Null oder mehr Hinweisdateien können Auswirkungen auf Ihr Projekt haben. Wenn keine Hinweisdateien vorhanden sind, verwendet das Analysesystem Wiederherstellungstechniken für Fehler, um den unlesbaren Quellcode zu ignorieren. Andernfalls verwendet das Analysesystem folgende Strategie, um Hinweise zu suchen und zu sammeln.

### <a name="search-order"></a>Suchreihenfolge

Das Analysesystem durchsucht Verzeichnisse in folgender Reihenfolge nach Hinweisdateien.

- Das Verzeichnis, das das Installationspaket für Visual C++ enthält (**vcpackages**). Dieses Verzeichnis enthält eine integrierte Hinweisdatei, die Symbole in häufig verwendeten Systemdateien (z.B. **windows.h**) beschreibt. Deshalb erbt Ihr Projekt automatisch die meisten erforderlichen Hinweise.

- Der Pfad vom Stammverzeichnis einer Quelldatei zu dem Verzeichnis, das die Quelldatei enthält. In einem typischen Visual Studio C++-Projekt enthält das Stammverzeichnis die Projektmappen- oder die Projektdatei.

   Eine Ausnahme besteht darin, wenn sich eine *STOP-Datei* im Pfad zur Quelldatei befindet. Eine Stoppdatei ist eine Datei mit dem Namen **cpp.stop**. Sie stellt eine zusätzliche Möglichkeit zum Einstellen der Suchreihenfolge dar. Statt im Stammverzeichnis zu beginnen, sucht das Analysesystem von dem Verzeichnis aus, das die STOP-Datei enthält, und beendet die Suche in dem Verzeichnis, das die Quelldatei enthält. In einem typischen Projekt benötigen Sie keine Stoppdatei.

### <a name="hint-gathering"></a>Sammeln von Hinweisen

Eine Hinweisdatei enthält null oder mehr *Hinweise*. Ein Hinweis wird genau wie ein C/C++-Makro definiert oder gelöscht. Das bedeutet, dass die Präprozessordirektive `#define` einen Hinweis erstellt oder neu definiert und die Direktive `#undef` einen Hinweis löscht.

Das Analysesystem öffnet jede Hinweisdatei in der zuvor beschriebenen Suchreihenfolge. Es fasst die Hinweise aller Dateien in einer Menge *effektiver Hinweise* zusammen. Diese werden dann zur Auswertung der Bezeichner im Code verwendet.

Das Analysesystem verwendet folgende Regeln, um Hinweise zu sammeln:

- Wenn der neue Hinweis einen Namen festlegt, der noch nicht definiert ist, fügt der neue Hinweis diesen den effektiven Hinweisen hinzu.

- Wenn der neue Hinweis einen Namen festlegt, der bereits definiert ist, definiert der neue Hinweis den vorhandenen Hinweisen neu.

- Wenn der neue Hinweis eine `#undef`-Direktive ist, die einen vorhandenen effektiven Hinweis angibt, löscht der neue Hinweis den vorhandenen Hinweis.

Die erste Regel bedeutet, dass effektive Hinweise von zuvor geöffneten Hinweisdateien geerbt werden. Durch die letzten beiden Regeln wird festgelegt, dass Hinweise, die in der Suchreihenfolge eher am Ende stehen, vorherige Hinweise überschreiben können. Sie können beispielsweise alle vorherigen Hinweise überschreiben, wenn Sie eine Hinweisdatei in dem Verzeichnis erstellen, das eine Quelldatei enthält.

Im Abschnitt [Beispiel](#example) finden Sie eine Abbildung, auf der die Erfassung von Hinweisen illustriert wird.

### <a name="syntax"></a>Syntax

Sie können Hinweise mit der gleichen Syntax erstellen und löschen, die in Präprozessoranweisungen zum Erstellen und Löschen von Makros verwendet wird. Tatsächlich verwendet das Analysesystem den C/C++-Präprozessor, um die Hinweise auszuwerten. Weitere Informationen zu den Präprozessordirektiven finden Sie unter [#define Directive (C/C++) (#define-Direktive (C/C++))](../../preprocessor/hash-define-directive-c-cpp.md) und [#undef Directive (C/C++) (#undef-Direktive (C/C++))](../../preprocessor/hash-undef-directive-c-cpp.md).

Die einzigen ungewöhnlichen Syntaxelemente sind die Ersatzzeichenfolgen `@<`, `@=` und `@>`. Diese Ersatzzeichenfolgen werden nur bei Hinweisdateien und ausschließlich für *Zuordnungsmakros* verwendet. Eine Zuordnung besteht aus mehreren Makros, die Daten, Funktionen oder Ereignisse mit anderen Daten, Funktionen oder Ereignishandlern in Verbindung bringen. `MFC` verwendet beispielsweise Zuordnungen, um [Meldungszuordnungen](../../mfc/reference/message-maps-mfc.md) zu erstellen, und `ATL` verwendet Zuordnungen, um [Objektzuordnungen](../../atl/reference/object-map-macros.md) zu erstellen. Die für die Hinweisdateien spezifischen Ersatzzeichenfolgen geben die Start-, Zwischen- und Endelemente einer Zuordnung an. Nur der Name eines Zuordnungsmakros ist relevant. Deshalb blendet jede Ersatzzeichenfolge die Implementierung des Makros absichtlich aus.

Für Hinweise wird die folgende Syntax verwendet:

|Syntax|Bedeutung|
|------------|-------------|
|`#define` *Hinweisname* *Ersatzzeichenfolge*<br /><br /> `#define` *Hinweisname* `(` *Parameter*, ...`)`*Ersatzzeichenfolge*|Eine Präprozessordirektive, die einen neuen Hinweis definiert oder einen vorhandenen Hinweis neu definiert. Nach der Direktive ersetzt der Präprozessor jedes Vorkommen von *Hinweisname* im Quellcode mit *Ersatzzeichenfolge*.<br /><br /> Durch das zweite Syntaxformat wird ein funktionsähnlicher Hinweis definiert. Wenn ein funktionsähnlicher Hinweis im Quellcode vorkommt, ersetzt der Präprozessor zunächst jedes Vorkommen von *Parameter* in *Ersatzzeichenfolge* mit dem entsprechenden Argument im Quellcode. Anschließend wird *Hinweisname* durch *Ersatzzeichenfolge* ersetzt.|
|`@<`|Eine für Hinweisdateien spezifische *Ersatzzeichenfolge*, die den Anfang von einer Reihe von Zuordnungselementen definiert.|
|`@=`|Eine für Hinweisdateien spezifische *Ersatzzeichenfolge*, die ein Zwischenzuordnungselement definiert. Eine Zuordnung kann mehrere Zuordnungselemente enthalten.|
|`@>`|Eine für Hinweisdateien spezifische *Ersatzzeichenfolge*, die das Ende von einer Reihe von Zuordnungselementen definiert.|
|`#undef` *Hinweisname*|Die Präprozessordirektive, die einen vorhandenen Hinweis löscht. Der Name des Hinweises wird durch den Bezeichner *Hinweisname* bereitgestellt.|
|`//` *Kommentar*|Ein einzeiliger Kommentar.|
|`/*` *Kommentar* `*/`|Ein mehrzeiliger Kommentar.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Hinweise aus Hinweisdateien gesammelt werden. Stoppdateien werden in diesem Beispiel nicht verwendet.

Die Abbildung stellt einige der physischen Verzeichnisse in einem Visual Studio C++-Projekt dar. Die Hinweisdateien befinden sich in den Verzeichnissen `vcpackages`, `Debug`, `A1` und `A2`.

### <a name="hint-file-directories"></a>Hinweisdateiverzeichnisse

![Allgemeines und Projekt&#45;spezifische Hinweisdateiverzeichnisse.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Verzeichnisse und Hinweisdateiinhalte

Die folgende Liste enthält Projektverzeichnisse mit Hinweisdateien und deren zugehörige Inhalten. Es werden nur einige der vielen Hinweise in der Hinweisdatei des Verzeichnisses `vcpackages` aufgeführt:

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Debuggen

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Effektive Hinweise

In der folgenden Tabelle werden die effektiven Hinweise für die Quelldateien in diesem Projekt aufgeführt:

- Quelldatei: A1_A2_B.cpp

- Effektive Hinweise:

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

Die folgenden Hinweise gelten für die vorangehende Liste:

- Die effektiven Hinweise stammen aus den Verzeichnissen `vcpackages`, `Debug`, `A1`, und `A2`.

- Die **#undef**-Direktive in der Hinweisdatei `Debug` hat den Hinweis `#define _In_` aus der Verzeichnishinweisdatei `vcpackages` gelöscht.

- Die Hinweisdatei im Verzeichnis `A1` definiert `START_NAMESPACE` neu.

- Der Hinweis `#undef` im Verzeichnis `A2` hat die Hinweise für `OBRACE` und `CBRACE` aus der Verzeichnishinweisdatei `Debug` gelöscht.

## <a name="see-also"></a>Siehe auch

[Für Visual Studio C++-Projekte erstellte Dateitypen](file-types-created-for-visual-cpp-projects.md)<br>
[#define-Direktive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef Richtlinie (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[SAL Anmerkungen](../../c-runtime-library/sal-annotations.md)<br>
