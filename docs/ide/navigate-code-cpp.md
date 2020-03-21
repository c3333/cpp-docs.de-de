---
title: Navigieren in C++-Code in Visual Studio
description: Verwenden Sie verschiedene Tools in Visual Studio, um in Ihrer C++-Codebasis zu navigieren.
ms.date: 05/28/2019
ms.openlocfilehash: 932694db70019924557259d4defe802b53ef0f89
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079076"
---
# <a name="navigate-c-code-in-visual-studio"></a>Navigieren in C++-Code in Visual Studio

Visual Studio stellt eine Reihe von Tools zur Verfügung, mit denen Sie schnell und effizient in Ihrer Codebasis navigieren können.

## <a name="open-an-included-file"></a>Öffnen einer enthaltenen Datei

Klicken Sie mit der rechten Maustaste auf eine `#include`-Anweisung, und wählen Sie **Zum Dokument wechseln** aus. Sie können auch den Cursor auf diese Zeile platzieren und **F12** drücken, um die Datei zu öffnen.

![C&#43; &#43; -Menüoption "Gehe zu Dokument"](../ide/media/go-to-document.png "Gehe zu Dokument")

## <a name="toggle-headercode-file"></a>Umschalten zwischen Header- und Codedatei

Sie können zwischen einer Headerdatei und der entsprechenden Quelldatei wechseln. Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in Ihrer Datei, und wählen Sie **Header-/Codedatei umschalten** aus. Sie können auch **STRG+K**, **STRG+O** drücken.

## <a name="go-to-definitiondeclaration"></a>Gehe zu Definition/Deklaration

Sie können zur Definition eines Codesymbols navigieren, indem Sie mit der rechten Maustaste in den Editor klicken und **Gehe zu Definition** auswählen oder indem Sie **F12** drücken. Sie können auf ähnliche Weise zu einer Deklaration navigieren, indem Sie mit der rechten Maustaste klicken, um das Kontextmenü zu öffnen, oder indem Sie **STRG+F12** drücken.

![C&#43; &#43; gehe zu Definition](../ide/media/go-to-def.png "Gehe zu Definition")

## <a name="go-to"></a>Gehe zu

**Gehe zu** bezieht sich auf Navigationsfeatures, die basierend auf von Ihnen festgelegten Filtern jeweils eine spezifische Art Ergebnis erzielen.

Sie können **Gehe zu** mit **STRG+,** öffnen. Diese Aktion öffnet ein Suchfeld über dem Dokument, das Sie bearbeiten.

![C&#43; &#43; wechseln zu](../ide/media/go-to-cpp.png "Gehe zu")

**Gehe zu** umfasst folgende Suchfilter:

- **Gehe zu Zeile** (**STRG + G**): springt schnell zu einer anderen Zeile im aktuellen Dokument.
- **Gehe zu allen** (**STRG +,** ) oder (**STRG + T**): die Suchergebnisse enthalten alle folgenden Informationen.
- **Gehe zu Datei** (**STRG 1, F**): Suche nach Dateien in der Projekt Mappe.
- **Gehe zu Typ** (**STRG 1, T**): zu den Suchergebnissen gehören:
  - Klassen, Strukturen und Enumerationen.
  - Schnittstellen und Delegaten (nur verwalteter Code).
- **Gehe zu Member** (**STRG 1, M**): zu den Suchergebnissen gehören:
  - Globale Variablen und globale Funktionen.
  - Klassenmembervariablen und Memberfunktionen.
  - Konstanten.
  - Enumerationselemente.
  - Eigenschaften und Ereignisse.
- **Gehe zu Symbol** (**STRG 1, S**): zu den Suchergebnissen gehören:
  - Ergebnisse von „Gehe zu Typ“ und „Gehe zu Member“.
  - Alle verbleibenden C++-Sprachkonstrukte, einschließlich Makros.

Beim ersten Aufruf von **Gehe zu** mit **STRG+** wird **Gehe zu allen** aktiviert (keine Filter für die Suchergebnisse). Sie können dann den gewünschten Filter über die Schaltflächen neben dem Suchfeld auswählen. Sie können einen spezifischen Filter mithilfe der entsprechenden Tastenkombination aufrufen. Dadurch wird das Suchfeld **Gehe zu** geöffnet, der jeweilige Filter ist ausgewählt. Alle Tastenkombinationen sind konfigurierbar.

Wenn Sie einen Textfilter anwenden möchten, starten Sie die Suchabfrage mit dem entsprechenden Zeichen des Filters gefolgt von einem Leerzeichen. (**Gehe zu Zeile** kann den Leerraum optional weglassen.) Diese Textfilter sind verfügbar:

- Gehe zu allen: (kein Textfilter)
- Gehe zu Zeilennummer: :
- Gehe zu Datei: f
- Gehen zu Typ: t
- Gehe zu Member: m
- Gehe zu Symbol: #

Im folgenden Beispiel werden Suchergebnisse des Vorgangs *Gehe zu Datei* mit dem Filter „f“ veranschaulicht:

![C&#43; &#43; -Menü "Gehe zu"](../ide/media/vs2017-go-to-results.png "Gehe zu-Menü")

Geben Sie ein „?“ gefolgt von einem Leerzeichen ein, um die Liste der Textfilter anzuzeigen. Sie können auch über das Menü **Bearbeiten** auf die **Gehe zu**-Befehle zugreifen. Dort können Sie die jeweiligen Tastenkombinationen für **Gehe zu** einsehen.

![C&#43; &#43; -Menü "Gehe zu"](../ide/media/go-to-menu-cpp.png "Gehe zu-Menü")

## <a name="find-or-find-in-files"></a>Suchen oder in Dateien suchen

Mit **Suchen** (**STRG+F**) oder **In Dateien suchen** (**STRG+UMSCHALT+F**) können Sie eine Textsuche in Ihrer Projektmappe durchführen.

Die **Suche** kann auf eine Auswahl, das aktuelle Dokument, alle offenen Dokumente, das aktuelle Projekt oder die gesamte Projektmappe begrenzt werden. Sie können reguläre Ausdrücke und Nur-Text-Suchen verwenden. Alle Übereinstimmungen werden automatisch in der IDE hervorgehoben.

![C&#43; &#43; suchen](../ide/media/find-cpp.png "Suchen")

**In Dateien suchen** ist eine leistungsstärkere Version von **Suchen**, die Ergebnisse im Fenster **Suchergebnisse** anzeigt. Sie können externe Codeabhängigkeiten suchen, nach Dateitypen filtern und vieles mehr.

![C&#43; &#43; in Dateien suchen](../ide/media/find-in-files-cpp.png "In Dateien suchen")

Sie können die Ergebnisse von **In Dateien suchen** in zwei Fenstern sortieren. Sie können Ergebnisse mehrerer Suchen aneinander anfügen. Wählen Sie ein Ergebnis aus, um zu dieser Position in der Datei zu springen.

![C&#43; &#43; in Dateien suchen](../ide/media/vs2017-find-in-files-results.png "In Dateien suchen")

Weitere Informationen finden Sie in der Visual Studio-Dokumentation unter [Find in Files (In Dateien suchen)](/visualstudio/ide/find-in-files).

## <a name="find-all-references"></a>Alle Verweise suchen

Platzieren Sie den Textcursor auf oder direkt hinter das Symbol, klicken Sie mit der rechten Maustaste, und wählen Sie **Alle Verweise suchen** aus, um alle Vorkommnisse des Symbols in Ihrer Codebasis zu suchen. Sie können die Ergebnisse auf verschiedene Weisen filtern, sortieren oder gruppieren. Die Ergebnisse werden inkrementell aufgefüllt. Sie werden als Lese- oder Schreibvorgänge klassifiziert, damit Sie erkennen können, was sich in Ihrer Projektmappe befindet und was sich dagegen in Systemheadern oder anderen Bibliotheken befindet.

![C&#43; &#43; alle Verweise suchen](../ide/media/find-all-references-results-cpp.png "Alle Verweise suchen")

Sie können die Suchergebnisse anhand der folgenden Kategorien gruppieren:

- Projekt, dann Definition
- Nur Definition
- Definition, dann Projekt
- Definition, dann Pfad
- Definition, Projekt, dann Pfad

#### <a name="filter-results"></a>Ergebnisse filtern

Zeigen Sie auf eine Spalte, und klicken Sie auf das angezeigte Filtersymbol, um die Ergebnisse zu filtern. Sie können die Ergebnisse der ersten Spalte Filtern, um beispielsweise Zeichenfolgen und Kommentarverweise zu filtern, die Sie möglicherweise nicht sehen möchten.

![C&#43; &#43; alle Verweise suchen Filter](../ide/media/find-all-references-filters-cpp.png "Suchen aller Verweis Filter")

- **Bestätigte Ergebnisse**: tatsächlicher Code verweist auf das Symbol, nach dem gesucht wird. Beispielsweise gibt die Suche nach einer Memberfunktion namens `Size` alle Verweise auf `Size` zurück, die mit dem Bereich der Klasse übereinstimmt, die `Size` definiert.

- Nicht **bestätigte Ergebnisse**: dieser Filter ist standardmäßig deaktiviert, da er Symbole anzeigt, deren Name übereinstimmt, aber keine tatsächlichen Verweise auf das Symbol sind, nach dem Sie suchen. Wenn Sie zum Beispiel über zwei Klassen verfügen, die eine Memberfunktion namens `Size` definieren, und Sie eine Suche nach `Size` für einen Verweis eines Objekts von `Class1` durchführen, werden alle Verweise auf `Size` von `Class2` als nicht bestätigte Ergebnisse aufgeführt.

- **Nicht verarbeitete Ergebnisse**: die Ausführung **aller Verweis** Vorgänge kann bei größeren Codebasen einige Zeit in Anspruch nehmen, sodass in der Ergebnisliste die Ergebnisse "nicht verarbeitet" angezeigt werden. Nicht verarbeitete Ergebnisse weisen eine Übereinstimmung mit dem Namen des gesuchten Symbols auf, wurden jedoch noch nicht als tatsächliche Codeverweise bestätigt. Sie können diesen Filter aktivieren, um schneller Ergebnisse zu erhalten. Sie sollten sich jedoch bewusst sein, dass einige Ergebnisse möglicherweise keine tatsächlichen Verweise sind.

#### <a name="sort-results"></a>Ergebnisse sortieren

Sie können die Ergebnisse nach einer beliebigen Spalte sortieren, indem Sie auf jeweilige Spalte auswählen. Sie können zwischen auf- und absteigender Reihenfolge wechseln, indem die Spalte ein weiteres Mal auswählen.

## <a name="navigation-bar"></a>Navigationsleiste

Sie können zur Definition eines Typs in einer Datei oder zu Typmembern navigieren, indem Sie die **Navigationsleiste** verwenden, die sich über dem Editorfenster befindet.

![C&#43; &#43; -Navigationsleiste](../ide/media/navbar-cpp.png "Navigationsleiste")

## <a name="see-also"></a>Weitere Informationen

- [Read and understand C++ code (Lesen und Verstehen von C++-Code)](read-and-understand-code-cpp.md)</br>
- [Schreiben und Umgestalten von Code (C++)](read-and-understand-code-cpp.md)</br>
- [Collaborate with Live Share for C++ (Zusammenarbeit über Live Share für C++)](live-share-cpp.md)
