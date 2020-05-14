---
title: Umgebungsvariablen für profilgesteuerte Optimierungen
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195265"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Umgebungsvariablen für profilgesteuerte Optimierungen

Es gibt drei Umgebungsvariablen, die Testszenarios auf einem Image beeinflussen, das mit **/LTCG:PGI** zur profilgesteuerte Optimierung erstellt wurde:

- **PogoSafeMode** gibt an, ob der schnelle oder abgesicherte Modus zur Anwendungsprofilerstellung verwendet werden soll.

- **VCPROFILE_ALLOC_SCALE** fügt zusätzlichen Speicher hinzu, der vom Profiler verwendet wird.

- Mit **VCPROFILE_PATH** können Sie den Ordner angeben, der für PGC-Dateien verwendet wird.

**Die Umgebungsvariablen „PogoSafeMode“ und „VCPROFILE_ALLOC_SCALE“ sind veraltet ab Visual Studio 2015.** Die Linkeroptionen [/GENPROFILE oder /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) und [/USEPROFILE](reference/useprofile.md) geben dasselbe Linkerverhalten wie diese Umgebungsvariablen an.

## <a name="pogosafemode"></a>PogoSafeMode

Diese Umgebungsvariable ist veraltet. Verwenden Sie das Argument **EXACT** oder **NOEXACT** für **/GENPROFILE** oder **/FASTGENPROFILE**, um dieses Verhalten zu steuern.

Löschen Sie die Umgebungsvariable **PogoSafeMode**, oder legen Sie sie fest, um anzugeben, ob der schnelle oder der abgesicherte Modus für die Anwendungsprofilerstellung in x86-Systemen verwendet werden soll.

Die profilgesteuerte Optimierung (Profile-Guided Optimization, PGO) besitzt zwei mögliche Modi während der Profilerstellung: den *schnellen* und den *abgesicherten Modus*. Wenn die Profilerstellung im schnellen Modus stattfindet, werden Datenzähler mithilfe der **INC**-Anweisung vergrößert. Die **INC**-Anweisung ist schneller, jedoch nicht threadsicher. Wenn die Profilerstellung im abgesicherten Modus stattfindet, werden Datenzähler mithilfe der **LOCK INC**-Anweisung vergrößert. Die **LOCK INC**-Anweisung besitzt dieselbe Funktionalität wie die **INC**-Anweisung und ist threadsicher, dabei jedoch langsamer als die **INC**-Anweisung.

Standardmäßig wird PGO-Profilerstellung im schnellen Modus ausgeführt. **PogoSafeMode** ist nur erforderlich, wenn Sie den abgesicherten Modus verwenden möchten.

Für die Ausführung der PGO-Profilerstellung im abgesicherten Modus müssen Sie entweder die Umgebungsvariable **PogoSafeMode** oder den Linkerparameter **/PogoSafeMode** verwenden (abhängig vom System). Wenn Sie die Profilerstellung auf einem x64-Computer ausführen, müssen Sie den Linkerschalter verwenden. Wenn Sie die Profilerstellung auf einem x86-Computer ausführen, können Sie den Linkerparameter verwenden oder die Umgebungsvariable **PogoSafeMode** auf einen beliebigen Wert festlegen, bevor Sie den Optimierungsprozess starten.

### <a name="pogosafemode-syntax"></a>Syntax von PogoSafeMode

> **set PogoSafeMode**[ **=** _Wert_]

Legen Sie **PogoSafeMode** auf einen beliebigen Wert fest, um den abgesicherten Modus zu aktivieren. Wenn Sie die Variable ohne Wert festlegen, löschen Sie einen vorherigen Wert und reaktivieren den schnellen Modus.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

Diese Umgebungsvariable ist veraltet. Verwenden Sie das Argument **MEMMIN** oder **MEMMAX** für **/GENPROFILE** oder **/FASTGENPROFILE**, um dieses Verhalten zu steuern.

Bearbeiten Sie die Umgebungsvariable **VCPROFILE_ALLOC_SCALE**, und ändern Sie Menge des zugeordneten Speichers, der für die Profildaten bestimmt ist. In seltenen Fällen ist nicht ausreichend Speicher verfügbar, um die Sammlung von Profildaten während der Ausführung von Testszenarios zu unterstützen. In solchen Fällen können Sie die Speichermenge durch Festlegen von **VCPROFILE_ALLOC_SCALE** heraufsetzen. Wenn Sie während einer Testausführung eine Fehlermeldung erhalten, laut der der Speicher nicht ausreicht, müssen Sie **VCPROFILE_ALLOC_SCALE** so lange einen höheren Wert zuweisen, bis die Testausführungen ohne solche Fehlermeldungen beendet werden.

### <a name="vcprofile_alloc_scale-syntax"></a>Syntax von VCPROFILE_ALLOC_SCALE

> **set VCPROFILE_ALLOC_SCALE**[ __=__ *Wert_der_Größenordnung*]

Der Parameter *Wert_der_Größenordnung* ist ein Skalierungsfaktor für die Speichermenge, die Sie für die Ausführung von Testszenarios bereitstellen möchten.  Der Standard ist 1. Der folgende Befehl legt den Skalierungsfaktor beispielsweise auf 2 fest:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

Mit der Umgebungsvariablen **VCPROFILE_PATH** geben Sie das Verzeichnis an, in dem PGC-Dateien erstellt werden sollen. PGC-Dateien werden standardmäßig im selben Verzeichnis erstellt wie die Binärdatei, für die ein Profil erstellt wird. Wenn Sie Profilszenarios auf einem anderen Computer als dem durchführen, auf dem die Binärdatei erstellt wurde, ist der absolute Pfad der Binärdatei nicht vorhanden. In einem solchen Fall können Sie **VCPROFILE_PATH** auf einen Pfad festlegen, der auf dem Zielcomputer vorhanden ist.

### <a name="vcprofile_path-syntax"></a>Syntax von VCPROFILE_PATH

> **set VCPROFILE_PATH**[ **=** _Pfad_]

Legen Sie den Parameter *Pfad* auf den Verzeichnispfad fest, dem die PGC-Dateien hinzugefügt werden sollen. Der folgende Befehl legt den Ordner beispielsweise auf C:\profile fest:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Siehe auch

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)<br/>
[/GENPROFILE, /FASTGENPROFILE (Generieren eines Instrumentierungsbuilds für die Profilerstellung)](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
