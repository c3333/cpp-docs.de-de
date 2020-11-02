---
title: pgosweep
description: Verwenden Sie den Befehl „pgosweep“, um Profildaten zur Verwendung bei der profilgesteuerten Optimierung in eine PGC-Datei zu schreiben.
ms.date: 10/23/2020
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.openlocfilehash: be96d0f092ff65867c304ddf5eb41c0754f6e4be
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497178"
---
# <a name="pgosweep"></a>pgosweep

Wird bei der profilgesteuerten Optimierung verwendet, um alle Profildaten aus einem laufenden Programm in die PGC-Datei zu schreiben.

## <a name="syntax"></a>Syntax

> **`pgosweep`** [ *Optionen* ] *Image* *PGC-Datei*

### <a name="parameters"></a>Parameter

*Optionen*\
(Optional) Die gültigen Werte für die *Optionen* lauten wie folgt:

- **`/?`** oder **`/help`** zeigt die Hilfsmeldung an.

- **`/reset`** setzt den Zähler nach dem Sweep auf Null zurück. Dies ist das Standardverhalten.

- **`/pid:n`** führt nur für die angegebene PID einen Sweepvorgang durch. *n* ist die PID.

- **`/wait`** wartet, bis die angegebene PID beendet wurde, bevor die Zähler erfasst werden.

- **`/onlyzero`** speichert keine PGC-Datei. Nur Nullzähler.

- **`/pause`** hält das Sammeln der Zähler für das System an.

- **`/resume`** setzt das Sammeln der Zähler für das System fort.

- **`/noreset`** behält die Zähler in den Laufzeitdatenstrukturen bei.

*image*\
Der vollständige Pfad einer EXE- oder DLL-Datei, die mit der Option [`/GENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [`/FASTGENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) oder [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) erstellt wurde.

*pgcfile*\
Die PGC-Datei, in der dieser Befehl die Datenzähler ausgibt.

## <a name="remarks"></a>Hinweise

Der Befehl **`pgosweep`** kann für Programme verwendet werden, die mit der Option [`/GENPROFILE` oder `/FASTGENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) bzw. mit der veralteten Option [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) erstellt wurden. Durch den Befehl wird ein Programm unterbrochen, und Profildaten werden in eine neue PGC-Datei geschrieben. Standardmäßig setzt der Befehl die Anzahl nach jedem Schreibvorgang zurück. Wenn Sie die Option **`/noreset`** angeben, werden die Werte vom Befehl aufgezeichnet, aber nicht im laufenden Programm zurückgesetzt. Mit dieser Option erhalten Sie doppelte Daten, wenn Sie die Profildaten zu einem späteren Zeitpunkt abrufen.

Eine alternative Verwendungsmöglichkeit von **`pgosweep`** besteht darin, Profilinformationen nur für den normalen Anwendungsbetrieb abzurufen. Sie können **`pgosweep`** beispielsweise kurz nach dem Start der Anwendung ausführen und die Datei verwerfen. Dadurch werden die mit Startkosten verknüpften Profildaten entfernt. Anschließend können Sie **`pgosweep`** ausführen, bevor Sie die Anwendung beenden. Die gesammelten Daten verfügen dann nur über die Profilinformationen aus der Zeit, in der der Benutzer mit dem Programm interagieren konnte.

Wenn Sie eine PGC-Datei benennen (mithilfe des *pgcfile* -Parameters), können Sie das Standardformat *`appname!n.pgc`* verwenden. *n* ist ein steigender numerischer Wert für die einzelnen Dateien. Wenn Sie dieses Format verwenden, sucht der Compiler in der Phase **`/LTCG /USEPROFILE`** oder **`/LTCG:PGO`** automatisch nach diesen Daten. Wenn Sie das Standardformat nicht verwenden, müssen Sie [`pgomgr`](pgomgr.md) verwenden, um die PGC-Dateien zusammenzuführen.

> [!NOTE]
> Sie können dieses Tool nur über eine Developer-Eingabeaufforderung von Visual Studio starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

Informationen zum Erfassen der Profildaten in der ausführbaren Datei finden Sie unter [`PgoAutoSweep`](pgoautosweep.md).

## <a name="example"></a>Beispiel

In diesem Beispielbefehl schreibt **`pgosweep`** die aktuellen Profilinformationen für *`myapp.exe`* in *`myapp!1.pgc`* .

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Weitere Informationen:

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)\
[PgoAutoSweep](pgoautosweep.md)
