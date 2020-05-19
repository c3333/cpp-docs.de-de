---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552241"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` speichert die aktuellen Profilindikatorinformationen in eine Datei, und setzt die Indikatoren dann zurück. Verwenden Sie die Funktion während des Trainings zur profilgesteuerten Optimierung, um alle Profildaten aus dem laufenden Programm für die spätere Verwendung im Optimierungsbuild in eine `.pgc`-Datei zu schreiben.

## <a name="syntax"></a>Syntax

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parameter

*name*<br/>
Hierbei handelt es sich um eine identifizierende Zeichenfolge für die gespeicherte `.pgc`-Datei.

## <a name="remarks"></a>Hinweise

Sie können `PgoAutoSweep` in Ihrer Anwendung aufrufen, um die Profildaten jederzeit während der Anwendungsausführung zu speichern und zurückzusetzen. In einem instrumentierten Build erfasst `PgoAutoSweep` die aktuellen Profilerstellungsdaten, speichert sie in einer Datei und setzt die Profilindikatoren zurück. Dies entspricht dem Aufrufen des [pgosweep](pgosweep.md)-Befehls an einem bestimmten Punkt in der ausführbaren Datei. In einem optimierten Build wird für `PgoAutoSweep` kein Vorgang durchgeführt.

Die gespeicherten Profilindikatordaten werden in einer Datei mit dem Namen *Basisname*-*Name*!*Wert*.pgc gespeichert, wobei *Basisname* für den Basisnamen der ausführbaren Datei steht, *Name* für den an `PgoAutoSweep`übergebenen Parameter und *Wert* für einen eindeutigen Wert, in der Regel eine stetig steigende Zahl, um Dateinamenkonflikte zu vermeiden.

Die von `PgoAutoSweep` erstellten `.pgc`-Dateien müssen in einer `.pgd`-Datei zusammengeführt werden, die zum Erstellen einer optimierten ausführbaren Datei verwendet werden soll. Sie können den [pgomgr](pgomgr.md)-Befehl verwenden, um den Merge durchzuführen.

Sie können den Namen der zusammengeführten `.pgd`-Datei während des Optimierungsbuilds an den Linker übergeben, indem Sie das Argument **PGD=** _Dateiname_ für die Linkeroption [/USEPROFILE](reference/useprofile.md) oder die veraltete Linkeroption **/PGD** verwenden. Wenn Sie die `.pgc`-Dateien in einer Datei mit dem Namen *Basisname*.pgd zusammenführen, müssen Sie den Dateinamen nicht in der Befehlszeile angeben, da der Linker diesen Dateinamen standardmäßig übernimmt.

Die `PgoAutoSweep`-Funktion verwaltet die Threadsicherheitseinstellung, die beim Erstellen des instrumentierten Builds angegeben wird. Wenn Sie die Standardeinstellung verwenden oder das Argument **NOEXACT** für die Linkeroption [/GENPROFILE oder /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) angeben, sind Aufrufe von `PgoAutoSweep` nicht threadsicher. Das **EXACT**-Argument erstellt eine threadsichere und präzisere, aber auch langsamere instrumentierte ausführbare Datei.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

Die ausführbare Datei muss die Datei „pgobootrun.lib“ in den verknüpften Bibliotheken enthalten. Diese Datei ist in Ihrer Visual Studio-Installation im Verzeichnis der VC-Bibliotheken für jede unterstützte Architektur enthalten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `PgoAutoSweep` verwendet, um an unterschiedlichen Punkten während der Ausführung zwei `.pgc`-Dateien zu erstellen. Die erste enthält Daten, die das Laufzeitverhalten beschreibt, bis `count` 3 entspricht. Die zweite enthält die Daten, die nach diesem Punkt bis direkt vor dem Beenden der Anwendung gesammelt wurden.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

Kompilieren Sie in einer Developer-Eingabeaufforderung den Code in eine Objektdatei, indem Sie den folgenden Befehl verwenden:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Generieren Sie dann mithilfe des folgenden Befehls einen instrumentierten Build für das Training:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Führen Sie die instrumentierte ausführbare Datei aus, um die Trainingsdaten zu erfassen. Die Datenausgaben durch die Aufrufe von `PgoAutoSweep` werden in Dateien mit den Namen „pgoautosweep-func1!1.pgc“ und „pgoautosweep-func2!1.pgc“ gespeichert. Die Ausgabe des Programms sollte während der Ausführung wie folgt aussehen:

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

Führen Sie die gespeicherten Daten in einer Profiltrainings-Datenbank zusammen, indem Sie den Befehl **pgomgr** ausführen:

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

Die Ausgabe dieses Befehls sieht in etwa folgendermaßen aus:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Nun können Sie diese Trainingsdaten verwenden, um einen optimierten Build zu generieren. Verwenden Sie diesen Befehl, um die optimierte ausführbare Datei zu erstellen:

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>Siehe auch

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
