---
title: CRT-Bibliotheksfunktionen
description: Liste der Dateien, die die Microsoft C-Laufzeitbibliotheken enthalten, sowie die zugehörigen Compileroptionen und Präprozessordirektiven.
ms.date: 09/03/2020
ms.topic: conceptual
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
ms.openlocfilehash: 0e0d34c1121f0bf4e2fdfabc521e0365084761eb
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589782"
---
# <a name="crt-library-features"></a>CRT-Bibliotheksfunktionen

In diesem Thema werden die verschiedenen LIB-Dateien erläutert, die die C-Laufzeitbibliotheken sowie ihre zugeordneten Compileroptionen und Präprozessordirektiven bilden.

## <a name="c-run-time-libraries-crt"></a>C-Laufzeitbibliotheken (CRT)

Die CRT (C Run-time Library, C-Laufzeitbibliothek) ist Bestandteil der C++-Standardbibliothek, die die ISO C99-Standardbibliothek umfasst. Die Visual C++-Bibliotheken, die die CRT implementieren, unterstützen die Entwicklung von nativem Code und Mischungen aus nativem und verwaltetem Code. Alle Versionen der CRT unterstützen Multithreaded-Entwicklung. Die meisten Bibliotheken unterstützen sowohl statisches Linken (Binden), um die Bibliothek direkt in Ihren Code einzubinden, oder dynamisches Linken, damit in Ihrem Code allgemeine DLL-Dateien verwendet werden können.

Ab Visual Studio 2015 wurde die CRT in neue Binärdateien umgestaltet. Die UCRT (Universal CRT) enthält die Funktionen und globalen Elemente, die durch die Standard-C99 CRT-Bibliothek exportiert werden. Die UCRT ist nun eine Windows-Komponente und wird als Bestandteil von Windows 10 bereitgestellt. Die statische Bibliothek, die DLL-Importbibliothek und die Headerdateien für die UCRT sind jetzt im Windows 10 SDK zu finden. Wenn Sie Visual C++ installieren, installiert Visual Studio-Setup die Teilmenge des Windows 10 SDKs, die erforderlich ist, um die UCRT verwenden zu können. Sie können die UCRT unter jeder Version von Windows verwenden, die von Visual Studio 2015 und späteren Versionen unterstützt wird. Sie können die URCT über vcredist für unterstützte Versionen von Windows neu verteilen, die nicht Windows 10 sind. Weitere Informationen finden Sie unter [Verteilen von Visual C++-Dateien](../windows/redistributing-visual-cpp-files.md).

In der folgenden Tabelle sind die Bibliotheken aufgelistet, die die UCRT implementieren.

| Bibliothek | Zugehörige DLL | Merkmale | Option | Präprozessordirektiven |
|--|--|--|--|--|
| *`libucrt.lib`* | Keine | Bindet die UCRT statisch in Ihren Code ein. | **`/MT`** | `_MT` |
| *`libucrtd.lib`* | Keine | Die Debugversion der UCRT für statisches Linken. Nicht neu verteilbar. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`ucrt.lib`* | *`ucrtbase.dll`* | DLL-Importbibliothek für die UCRT. | **`/MD`** | `_MT`, `_DLL` |
| *`ucrtd.lib`* | *`ucrtbased.dll`* | DLL-Importbibliothek für die Debugversion der UCRT. Nicht neu verteilbar. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

Die vcruntime-Bibliothek enthält Visual C++-CRT-implementierungsspezifischen Code, beispielsweise Ausnahmebehandlungs- und Debugunterstützung, Laufzeitprüfungen und Typinformationen, Implementierungsdetails und bestimmte erweiterte Bibliotheksfunktionen. Diese Bibliothek ist speziell entsprechend der Version des verwendeten Compilers.

In der folgenden Tabelle sind die Bibliotheken aufgelistet, die die vcruntime-Bibliothek implementieren.

| Bibliothek | Zugehörige DLL | Merkmale | Option | Präprozessordirektiven |
|--|--|--|--|--|
| *`libvcruntime.lib`* | Keine | Wird statisch in Ihren Code eingebunden. | **`/MT`** | `_MT` |
| *`libvcruntimed.lib`* | Keine | Die Debugversion für statisches Linken. Nicht neu verteilbar. | **`/MTd`** | `_MT`, `_DEBUG` |
| *`vcruntime.lib`* | *`vcruntime<version>.dll`* | DLL-Importbibliothek für die vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`vcruntimed.lib`* | *`vcruntime<version>d.dll`* | DLL-Importbibliothek für die Debug-vcruntime. Nicht neu verteilbar. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

> [!NOTE]
> Beim Refactoring der ucrt wurden die Concurrency Runtime Funktionen in verschoben, die dem *`concrt140.dll`* Redistributable-Paket C++ hinzugefügt wurden. Diese DLL ist für parallele C++-Container und -Algorithmen wie `concurrency::parallel_for` erforderlich. Darüber hinaus ist diese DLL unter Windows XP für die C++-Standardbibliothek zur Unterstützung von Synchronisierungsprimitiven erforderlich, da Windows XP über keine Bedingungsvariablen verfügt.

Der Code, von dem die CRT initialisiert wird, befindet sich in einer von mehreren Bibliotheken, je nachdem, ob die CRT-Bibliothek statisch oder dynamisch gebunden wird oder als systemeigener, verwalteter oder gemischter Code vorliegt. Dieser Code verwaltet den CRT-Start, die interne threadbezogene Dateninitialisierung und die Beendigung. Der Code ist speziell entsprechend der Version des verwendeten Compilers. Diese Bibliothek wird immer statisch gebunden, auch wenn eine dynamisch gebundene UCRT verwendet wird.

In der folgenden Tabelle sind die Bibliotheken aufgelistet, die die CRT-Initialisierung und -Beendigung implementieren.

| Bibliothek | Merkmale | Option | Präprozessordirektiven |
|--|--|--|--|
| *`libcmt.lib`* | Bindet den systemeigenen CRT-Startcode statisch in Ihren Code ein. | **`/MT`** | `_MT` |
| *`libcmtd.lib`* | Bindet die Debugversion des systemeigenen CRT-Startcode statisch ein. Nicht neu verteilbar. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcrt.lib`* | Statische Bibliothek für den systemeigenen CRT-Startcode zur Verwendung mit DLL UCRT und vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`msvcrtd.lib`* | Statische Bibliothek für die Debugversion des systemeigenen CRT-Startcodes zur Verwendung mit DLL UCRT und vcruntime. Nicht neu verteilbar. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |
| *`msvcmrt.lib`* | Statische Bibliothek für den gemischten systemeigenen und verwalteten CRT-Startcode zur Verwendung mit DLL UCRT und vcruntime. | **`/clr`** |  |
| *`msvcmrtd.lib`* | Statische Bibliothek für die Debugversion des gemischten systemeigenen und verwalteten CRT-Startcodes zur Verwendung mit DLL UCRT und vcruntime. Nicht neu verteilbar. | **`/clr`** |  |
| *`msvcurt.lib`* | **Veraltet** Statische Bibliothek für die ausschließlich verwaltete CRT. | **`/clr:pure`** |  |
| *`msvcurtd.lib`* | **Veraltet** Statische Bibliothek für die Debugversion der ausschließlich verwalteten CRT. Nicht neu verteilbar. | **`/clr:pure`** |  |

Wenn Sie das Programm über die Befehlszeile ohne eine Compileroption verknüpfen, die eine C-Lauf Zeit Bibliothek angibt, verwendet der Linker die statisch verknüpften CRT-Bibliotheken: *`libcmt.lib`* , *`libvcruntime.lib`* und *`libucrt.lib`* .

Die Verwendung der statisch verknüpften CRT bedeutet, dass alle von der C-Laufzeitbibliothek gespeicherten Zustandsinformationen für diese CRT-Instanz lokal sind. Wenn Sie z. b. verwenden, [`strtok`](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) Wenn Sie eine statisch verknüpfte CRT verwenden, ist die Position des `strtok` Parsers nicht mit dem Zustand verknüpft, der `strtok` im Code im selben Prozess verwendet wird (jedoch in einer anderen DLL oder exe), der mit einer anderen Instanz der statischen CRT verknüpft ist. Im Gegensatz dazu teilen dynamisch verknüpfte CRT den Zustand für sämtlichen Code innerhalb eines Prozesses, der dynamisch mit der CRT verknüpft ist. Bei den neuen sichereren Versionen dieser Funktionen wie `strtok_s` tritt dieses Problem nicht auf.

Da eine durch das Verknüpfen mit einer statischen CRT erstellten DLL ihren eigenen CRT-Zustand besitzt, wird in einer DLL das statische Verknüpfen mit einer CRT nicht empfohlen, es sei denn, dass die daraus resultierenden Konsequenzen verstanden werden und erwünscht sind. Wenn Sie z. b. [`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md) in einer ausführbaren Datei aufzurufen, die die dll lädt, die mit ihrer eigenen statischen CRT verknüpft ist, werden alle vom Code in der dll generierten Hardware Ausnahmen vom Konvertierungsprogramm nicht abgefangen, aber Hardware Ausnahmen, die vom Code in der Haupt ausführbaren Datei generiert werden, werden abgefangen.

Wenn Sie den- **`/clr`** Compilerschalter verwenden, wird der Code mit der statischen Bibliothek msvcmrt. lib verknüpft. Die statische Bibliothek stellt einen Proxy zwischen dem verwalteten Code und der systemeigenen CRT bereit. Die statisch verknüpfte CRT ( **`/MT`** oder Optionen) kann nicht mit verwendet werden **`/MTd`** **`/clr`** . Verwenden Sie stattdessen die dynamisch verknüpften Bibliotheken ( **`/MD`** oder **`/MDd`** ). Die reinen verwalteten CRT-Bibliotheken sind in Visual Studio 2015 als veraltet markiert und werden in Visual Studio 2017 nicht unterstützt.

Weitere Informationen zur Verwendung der CRT mit **`/clr`** finden Sie unter [gemischte (Native und verwaltete)](../dotnet/mixed-native-and-managed-assemblies.md)Assemblys.

Um eine Debugversion der Anwendung zu erstellen, [`_DEBUG`](../c-runtime-library/debug.md) muss das-Flag definiert sein, und die Anwendung muss mit einer Debugversion einer dieser Bibliotheken verknüpft sein. Weitere Informationen zur Verwendung der Debugversionen der Bibliotheksdateien finden Sie unter [CRT-Debugverfahren](/visualstudio/debugger/crt-debugging-techniques).

Diese Version der CRT ist nicht vollständig mit dem Standard C99 konform. In Versionen vor Visual Studio 2019, Version 16,8, \<tgmath.h> wird der-Header nicht unterstützt. In allen Versionen werden die `CX_LIMITED_RANGE` -und- `FP_CONTRACT` pragma-Makros nicht unterstützt. Für bestimmte Elemente, etwa die Bedeutung von Parameterbezeichnern in Standard-E/A-Funktionen, werden standardmäßig frühere Interpretationen verwendet. Sie können **`/Zc`** die compilerübereinstimmungs Optionen verwenden und Linkeroptionen angeben, um einige Aspekte der Bibliotheks Konformität zu steuern.

## <a name="c-standard-library"></a>C++-Standardbibliothek

| C++-Standardbibliothek | Merkmale | Option | Präprozessordirektiven |
|--|--|--|--|
| *`libcpmt.lib`* | Multithreaded, statischer Link | **`/MT`** | `_MT` |
| *`msvcprt.lib`* | Multithreaded, dynamischer Link (Import Bibliothek für *`msvcp<version>.dll`* ) | **`/MD`** | `_MT`, `_DLL` |
| *`libcpmtd.lib`* | Multithreaded, statischer Link | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcprtd.lib`* | Multithreaded, dynamischer Link (Import Bibliothek für *`msvcp<version>d.dll`* ) | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

Wenn Sie eine Releaseversion des Projekts erstellen, wird eine der grundlegenden C-Laufzeitbibliotheken ( *`libcmt.lib`* , *`msvcmrt.lib`* , *`msvcrt.lib`* ) standardmäßig verknüpft, abhängig von der ausgewählten Compileroption (Multithreaded, dll, **`/clr`** ). Wenn Sie eine der [Headerdateien der C++-Standardbibliothek](../standard-library/cpp-standard-library-header-files.md) in den Code einfügen, wird von Visual C++ eine C++-Standardbibliothek automatisch zur Kompilierzeit eingebunden. Beispiel:

```cpp
#include <ios>
```

Für die binäre Kompatibilität kann mehr als eine DLL-Datei von einer einzelnen Importbibliothek angegeben werden. Versionsupdates führen womöglich *dot-Bibliotheken* ein, separate DLLs, die neue Bibliotheksfunktionen enthalten. Beispielsweise wurde Visual Studio 2017 Version 15,6 eingeführt *`msvcp140_1.dll`* , um zusätzliche Standard Bibliotheksfunktionen zu unterstützen, ohne die von unterstützte ABI zu unterbrechen *`msvcp140.dll`* . Die *`msvcprt.lib`* Import Bibliothek, die im Toolset für Visual Studio 2017 Version 15,6 enthalten ist, unterstützt beide DLLs, und Vcredist für diese Version installiert beide DLLs. Sobald eine dot-Bibliothek geliefert wird, verfügt sie über eine feste ABI und wird nie über eine Abhängigkeit auf einer späteren dot-Bibliothek verfügen.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Welche Probleme gibt es, wenn in einer Anwendung mehrere CRT-Version verwendet werden?

Jedes ausführbare Image (EXE oder DLL) kann mit einer eigenen statisch verknüpften CRT versehen sein oder dynamisch mit einer CRT verknüpft werden. Ob die Version der CRT statisch enthalten ist oder dynamisch von einem bestimmten Image geladen wird, hängt von der Version der Tools und Bibliotheken ab, mit denen es erstellt wurde. In einem einzelnen Prozess können mehrere EXE- und DLL-Images geladen werden, die jeweils mit einer eigenen CRT ausgestattet sind. Jede dieser CRTs kann unterschiedliche Zuweisungen, interne Strukturlayouts und Speicherverhältnisse aufweisen. Dies bedeutet, dass der belegte Arbeitsspeicher, CRT-Ressourcen oder Klassen, die über eine DLL-Grenze übergeben werden, Probleme bei der Verwaltung des Arbeitsspeichers, der internen statischen Verwendung oder der Layoutinterpretation verursachen kann bzw. können. Welcher CRT-Deallokator wird beispielsweise verwendet, wenn eine Klasse in einer DLL zugewiesen ist, jedoch an eine andere DLL übergeben und von dieser gelöscht wird? Die verursachten Fehler können von geringfügigen bis hin zu unmittelbar schwerwiegenden Fehlern reichen, weshalb von einer direkten Übertragung solcher Ressourcen strengstens abgeraten wird.

Eine Vielzahl dieser Probleme kann vermieden werden, wenn Sie stattdessen ABI-Technologien (Application Binary Interface) verwenden, da diese als stabil und versionierbar gelten. Entwerfen Sie Ihre DLL-Exportschnittstellen so, dass Informationen nach Wert übergeben werden oder der Arbeitsspeicher optimiert wird, der von der aufrufenden Funktion übergeben und nicht lokal zugewiesen und an den Aufrufer zurückgegeben wird. Verwenden Sie marshallingtechniken, um strukturierte Daten zwischen ausführbaren Bildern zu kopieren. Kapseln Sie Ressourcen lokal, und lassen Sie nur die Bearbeitung über Handles oder Funktionen zu, die Sie Clients verfügbar machen.

Einige dieser Probleme können auch vermieden werden, wenn alle Images in Ihrem Prozess die gleiche dynamisch geladene CRT-Version verwenden. Um sicherzustellen, dass alle-Komponenten dieselbe DLL-Version der CRT verwenden, erstellen Sie Sie mithilfe der **`/MD`** -Option, und verwenden Sie das gleiche Compilertoolset und die gleichen Eigenschaften Einstellungen.

Gehen Sie vorsichtig vor, wenn Ihr Programm bestimmte CRT-Ressourcen über dll-Grenzen hinweg übergibt. Ressourcen wie Datei Handles, Gebiets Schemas und Umgebungsvariablen können Probleme verursachen, auch wenn die gleiche Version der CRT verwendet wird. Weitere Informationen zu diesen Problemen und den jeweiligen Lösungsmöglichkeiten finden Sie unter [Potential Errors Passing CRT Objects Across DLL Boundaries](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Weitere Informationen

- [C-Lauf Zeit Bibliotheks Referenz](../c-runtime-library/c-run-time-library-reference.md)
