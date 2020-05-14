---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341196"
---
# <a name="pgosweep"></a>pgosweep

Wird in der profilgesteuerte Optimierung verwendet, um alle Profildaten aus einem laufenden Programm in die PGC-Datei zu schreiben

## <a name="syntax"></a>Syntax

> **pgosweep** [*Optionen*] *Image-* *pgc-Datei*

### <a name="parameters"></a>Parameter

*options*<br/>
(Optional) Die gültigen Werte für die *Optionen* lauten wie folgt:

- **/?** oder **/help** zeigt die Hilfemeldung an.

- **/noreset** behält die Anzahl in den Laufzeitdatenstrukturen bei.

*Bild*<br/>
Der vollständiger Pfad einer EXE- oder DLL-Datei, die mithilfe der Option [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) oder [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) erstellt wurde

*pgcfile*<br/>
Die PGC-Datei, in der dieser Befehl die Datenanzahl ausgibt

## <a name="remarks"></a>Hinweise

Der **pgosweep**-Befehl funktioniert für Programme, die mit der Option [/GENPROFILE oder /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) oder der veralteten [/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md)-Option erstellt wurden. Durch den Befehl wird ein Programm unterbrochen und Profildaten in eine neue PGC-Datei geschrieben. Standardmäßig setzt der Befehl die Anzahl nach jedem Schreibvorgang zurück. Wenn Sie die **/noreset**-Option angeben, werden die Werte vom Befehl aufgezeichnet, aber nicht im laufenden Programm zurückgesetzt. Mit dieser Option erhalten Sie doppelte Daten, wenn Sie die Profildaten zu einem späteren Zeitpunkt abrufen.

Eine Alternative zu **pgosweep** besteht darin, Profilinformationen nur für den normalen Anwendungsbetrieb abzurufen. Sie können beispielsweise **pgosweep** kurz nach Start der Anwendung ausführen und die Datei verwerfen. Dadurch werden die mit den Startkosten zugeordneten Profildaten entfernt. Anschließend können Sie **pgosweep** ausführen, bevor Sie die Anwendung beenden. Die gesammelten Daten verfügen dann nur über die Profilinformationen aus der Zeit, in der der Benutzer mit dem Programm interagieren konnte.

Wenn Sie eine PGC-Datei benennen (mithilfe des *pgcfile*-Parameters), können Sie das Standardformat *appname!n*.pgc verwenden. Wenn Sie dieses Format verwenden, sucht der Compiler automatisch nach diesen Daten in der Phase **/LTCG /USEPROFILE** oder **/LTCG:PGO**. Wenn Sie das Standardformat nicht verwenden, müssen Sie [pgomgr](pgomgr.md) verwenden, um die PGC-Dateien zusammenzuführen.

> [!NOTE]
> Sie können dieses Tool nur über eine Visual Studio-Developer-Eingabeaufforderung starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

Informationen zum Erfassen der Profildaten in der ausführbaren Datei finden Sie unter [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Beispiel

In diesem Beispielbefehl werden von **pgosweep** die aktuellen Profilinformationen für „myapp.exe“ in „myapp!1.pgc“ geschrieben.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Siehe auch

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
