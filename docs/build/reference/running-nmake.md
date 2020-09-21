---
title: Ausführen von NMAKE
description: Erfahren Sie mehr über das Ausführen von NMAKE.
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: c2327e13e59ebf9df1ecba6fa66c6354641768ee
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743138"
---
# <a name="running-nmake"></a>Ausführen von NMAKE

## <a name="syntax"></a>Syntax

> **NMAKE** [*Option* ...] [*Makros* ...] [*Ziele* ...] [ **\@** _Befehlsdatei_ ...]

## <a name="remarks"></a>Bemerkungen

NMAKE erstellt nur angegebene *Ziele* oder, wenn keine angegeben ist, das erste Ziel im Makefile. Beim ersten Makefile-Ziel kann es sich um ein [pseudotarget](description-blocks.md#pseudotargets) -Ziel handeln, das andere Ziele erstellt. NMAKE verwendet Makefiles, die mit **/F**angegeben wurden, oder wenn **/F** nicht angegeben ist, die Makefile-Datei im aktuellen Verzeichnis. Wenn kein Makefile-Wert angegeben wird, werden mithilfe von Rückschluss Regeln Befehlszeilen *Ziele*erstellt.

Die *Befehlsdatei-* Textdatei (oder Antwortdatei) enthält Befehlszeilen Eingaben. Andere Eingaben können der \@ *Befehlsdatei*vorangestellt oder folgen. Ein Pfad ist zulässig. In der *Befehlsdatei*werden Zeilenumbrüche als Leerzeichen behandelt. Schließen Sie Makro Definitionen in Anführungszeichen ein, wenn Sie Leerzeichen enthalten.

## <a name="nmake-options"></a>NMAKE-Optionen

NMAKE-Optionen werden in der folgenden Tabelle beschrieben. Den Optionen wird entweder ein Schrägstrich ( `/` ) oder ein Bindestrich ( `-` ) vorangestellt. die Groß-/Kleinschreibung wird nicht beachtet. Verwenden [`!CMDSWITCHES`](makefile-preprocessing-directives.md) Sie, um Options Einstellungen in einem Makefile-oder in Tools.ini zu ändern.

| Option | Zweck |
| ------------ | ------------- |
| **/A** | Erzwingt das Erstellen aller ausgewerteten Ziele, auch wenn Sie nicht veraltet sind, im Vergleich zu abhängigen Elementen. Erzwingt keine Builds von nicht verknüpften Zielen. |
| **/B** | Erzwingt den Build, auch wenn Zeitstempel gleich sind. Wird nur für schnelle Systeme empfohlen (Auflösung von zwei Sekunden oder weniger). |
| **/C** | Unterdrückt die Standardausgabe, einschließlich nicht schwerwiegender NMAKE-Fehler oder-Warnungen, Zeitstempel und NMAKE-Copyright Meldung. Unterdrückt Warnungen, die von **/K**ausgegeben werden. |
| **/D** | Zeigt die Zeitstempel der einzelnen ausgewerteten Ziele und abhängigen und eine Meldung an, wenn ein Ziel nicht vorhanden ist. Nützlich bei **/P** für das Debuggen eines Makefile-Vorgangs. Verwenden `!CMDSWITCHES` Sie, um **/D** für einen Teil eines Makefile festzulegen oder zu löschen. |
| **/E** | Bewirkt, dass Umgebungsvariablen Makefile-Makro Definitionen überschreiben. |
| **/Errorreport** [ **keine** &#124; **Aufforderung** &#124; **Warteschlange** &#124; **senden** ] | Veraltet. [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen für die Berichterstellung. |
| **/F** *Dateiname* | Gibt den *Dateinamen* als Makefile an. Leerzeichen oder Tabstopps können dem *filename*vorangestellt werden. Geben Sie **/F** einmal für jedes Makefile an. Um ein Makefile-Zeichen aus der Standardeingabe anzugeben, geben Sie einen Bindestrich ( `-` ) für *Dateiname*an, und beenden Sie Tastatureingaben entweder mit **F6** oder **STRG + Z**. |
| **/G** | Zeigt die in der Direktive enthaltenen Makefiles an `!INCLUDE` . Weitere Informationen finden Sie unter [Makefile-Vorverarbeitungs Direktiven](makefile-preprocessing-directives.md). |
| **/Help**, **/?** | Zeigt eine kurze Zusammenfassung der NMAKE-Befehlszeilen Syntax an. |
| **/I** | Ignoriert Exitcodes von allen Befehlen. Verwenden Sie, um **/I** für einen Teil eines Makefile festzulegen oder zu löschen `!CMDSWITCHES` . Um Exitcodes für einen Teil eines Makefile zu ignorieren, verwenden Sie einen Dash ( `-` )-Befehlsmodifizierer oder [`.IGNORE`](dot-directives.md) . Überschreibt **/K** , wenn beide angegeben sind. |
| **/K** | Setzt das aufbauen von nicht verknüpften Abhängigkeiten fort, wenn ein Befehl einen Fehler zurückgibt. Gibt außerdem eine Warnung aus und gibt einen Exitcode von 1 zurück. Standardmäßig wird NMAKE angehalten, wenn ein beliebiger Befehl einen Exitcode ungleich NULL zurückgibt. Warnungen von **/K** werden von **/C**unterdrückt. **/I** überschreibt **/K** , wenn beide angegeben sind. |
| **/N** | Zeigt Befehle an, führt Sie jedoch nicht aus. Vorverarbeitung-Befehle werden ausgeführt. Zeigt keine Befehle in rekursiven NMAKE-Aufrufen an. Nützlich zum Debuggen von Makefiles und Überprüfen von Zeitstempeln. Verwenden Sie, um **/N** für einen Teil eines Makefile festzulegen oder zu löschen `!CMDSWITCHES` . |
| **/NOLOGO** | Unterdrückt die NMAKE-Copyright Meldung. |
| **/P** | Zeigt Informationen (Makro Definitionen, Rückschluss Regeln, Ziele, [`.SUFFIXES`](dot-directives.md) Liste) für die Standardausgabe an und führt dann den Build aus. Wenn kein Makefile-oder Befehlszeilen Ziel vorhanden ist, werden nur Informationen angezeigt. Verwenden Sie with **/D** , um ein Makefile zu debuggen. |
| **/Q** | Überprüft die Zeitstempel von Zielen. führt den Build nicht aus. Gibt einen Exitcode von 0 (null) zurück, wenn alle Ziele auf dem neuesten Stand sind, und einen Exitcode ungleich NULL, wenn ein Ziel veraltet ist. Preprocessing-Befehle werden ausgeführt. Nützlich, wenn NMAKE aus einer Batchdatei ausgeführt wird. |
| **/R** | Löscht die `.SUFFIXES` Liste und ignoriert Rückschluss Regeln und Makros, die in der Tools.ini Datei definiert oder vordefiniert sind. |
| **/S** | Unterdrückt die Anzeige der ausgeführten Befehle. Verwenden Sie den Befehlsmodifizierer oder, um die Anzeige im Rahmen eines Makefiles zu unterdrücken **\@** [`.SILENT`](dot-directives.md) . Verwenden Sie, um **/S** für einen Teil eines Makefile festzulegen oder zu löschen `!CMDSWITCHES` . |
| **/T** | Aktualisiert Zeitstempel von Befehlszeilen Zielen (oder dem ersten Makefile-Ziel) und führt Vorverarbeitungs Befehle aus, führt den Build jedoch nicht aus. |
| **/U** | Muss in Verbindung mit **/N**verwendet werden. Sichert Inline-NMAKE-Dateien, damit die **/N** -Ausgabe als Batchdatei verwendet werden kann. |
| **/X** *Dateiname* | Sendet die NMAKE-Fehlerausgabe an den *Dateinamen* statt an den Standardfehler. Leerzeichen oder Tabstopps können dem *filename*vorangestellt werden. Um die Fehlerausgabe an die Standardausgabe zu senden, geben Sie einen Bindestrich ( `-` ) als *Dateinamen*an. Hat keine Auswirkung auf die Ausgabe von Befehlen auf Standardfehler. |
| **/Y** | Deaktiviert die Rückschluss Regeln für den Batch Modus. Wenn diese Option ausgewählt ist, werden alle Rückschluss Regeln für den Batch Modus als reguläre Inferenz Regeln behandelt. |

## <a name="toolsini-and-nmake"></a>Tools.ini und NMAKE

NMAKE liest Tools.ini vor dem Lesen von Makefiles, es sei denn, **/R** wird verwendet. Er sucht zuerst im aktuellen Verzeichnis nach Tools.ini und dann in dem Verzeichnis, das von der init-Umgebungsvariablen angegeben wird. Der Abschnitt für NMAKE-Einstellungen in der Initialisierungsdatei beginnt mit `[NMAKE]` und kann beliebige Makefile-Informationen enthalten. Geben Sie einen Kommentar in einer separaten Zeile an, beginnend mit einem Nummern Zeichen ( `#` ).

## <a name="exit-codes-from-nmake"></a>Exitcodes von NMAKE

NMAKE gibt die folgenden Exitcodes zurück:

| Code | Bedeutung |
| ---------- | ------------- |
| 0 | Kein Fehler (möglicherweise eine Warnung) |
| 1 | Unvollständiger Build (wird nur ausgegeben, wenn **/K** verwendet wird) |
| 2 | Programmfehler, möglicherweise aufgrund eines der folgenden Probleme:<br /> : Syntax Fehler in Makefile<br /> -Ein Fehler oder Exitcode von einem Befehl<br /> -Eine Unterbrechung durch den Benutzer |
| 4 | System Fehler – nicht genügend Arbeitsspeicher |
| 255 | Das Ziel ist nicht auf dem neuesten Stand (wird nur ausgegeben, wenn **/Q** verwendet wird). |

## <a name="see-also"></a>Weitere Informationen

[NMAKE-Referenz](nmake-reference.md)
