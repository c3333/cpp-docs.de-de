---
title: 3. Funktionen der Runtimebibliothek
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370276"
---
# <a name="3-run-time-library-functions"></a>3. Laufzeitbibliotheksfunktionen

In diesem Abschnitt werden die OpenMP C- und C++-Laufzeitbibliotheksfunktionen beschrieben. Der Header ** \<omp.h>** deklariert zwei Typen, mehrere Funktionen, die zum Steuern und Abfragen der parallelen Ausführungsumgebung verwendet werden können, und Sperrfunktionen, die zum Synchronisieren des Zugriffs auf Daten verwendet werden können.

Der `omp_lock_t` Typ ist ein Objekttyp, der darstellen kann, dass eine Sperre verfügbar ist oder dass ein Thread eine Sperre besitzt. Diese Sperren werden als *einfache Sperren*bezeichnet.

Der `omp_nest_lock_t` Typ ist ein Objekttyp, der entweder darstellen kann, dass eine Sperre verfügbar ist, oder sowohl die Identität des Threads, der die Sperre besitzt, als auch eine *Verschachtelungsanzahl* (siehe unten). Diese Sperren werden als *verschachtelbare Sperren*bezeichnet.

Die Bibliotheksfunktionen sind externe Funktionen mit "C"-Verknüpfung.

Die Beschreibungen in diesem Kapitel sind in die folgenden Themen unterteilt:

- [Ausführungsumgebungsfunktionen](#31-execution-environment-functions)
- [Sperrfunktionen](#32-lock-functions)
- [Timing-Routinen](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 Ausführungsumgebungsfunktionen

Die in diesem Abschnitt beschriebenen Funktionen wirken sich auf Threads, Prozessoren und die parallele Umgebung aus:

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads Funktion

Die `omp_set_num_threads` Funktion legt die Standardanzahl von Threads fest, die `num_threads` für spätere parallele Regionen verwendet werden sollen, die keine Klausel angeben. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Der Wert des Parameters *num_threads* muss eine positive ganze Zahl sein. Seine Wirkung hängt davon ab, ob die dynamische Anpassung der Anzahl der Threads aktiviert ist. Einen umfassenden Regelsatz über die `omp_set_num_threads` Interaktion zwischen der Funktion und der dynamischen Anpassung von Threads finden Sie in [Abschnitt 2.3](2-directives.md#23-parallel-construct).

Diese Funktion hat die oben beschriebenen Effekte, wenn `omp_in_parallel` sie von einem Teil des Programms aufgerufen wird, in dem die Funktion Null zurückgibt. Wenn sie von einem Teil des Programms `omp_in_parallel` aufgerufen wird, in dem die Funktion einen Wert ungleich Null zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Dieser Aufruf hat `OMP_NUM_THREADS` Vorrang vor der Umgebungsvariablen. Der Standardwert für die Anzahl der Threads, `omp_set_num_threads` der durch `OMP_NUM_THREADS` Aufrufen oder Festlegen der Umgebungsvariablen festgelegt werden kann, kann für eine einzelne `parallel` Direktive explizit überschrieben werden, indem die Klausel angegeben wird. `num_threads`

Weitere Informationen finden Sie [unter omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- [omp_set_dynamic](#317-omp_set_dynamic-function) Funktion
- [omp_get_dynamic](#318-omp_get_dynamic-function) Funktion
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) Umgebungsvariable
- [num_threads-Klausel](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads Funktion

Die `omp_get_num_threads` Funktion gibt die Anzahl der Threads zurück, die sich derzeit im Team befinden, das den parallelen Bereich ausführt, von dem aus sie aufgerufen wird. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Die `num_threads` Klausel, `omp_set_num_threads` die Funktion `OMP_NUM_THREADS` und die Umgebungsvariable steuern die Anzahl der Threads in einem Team.

Wenn die Anzahl der Threads vom Benutzer nicht explizit festgelegt wurde, ist der Standardwert implementierungsdefiniert. Diese Funktion bindet an die `parallel` nächste einschließende Direktive. Wenn diese Funktion aus einem seriellen Teil eines Programms oder aus einer verschachtelten parallelen Region aufgerufen wird, die serialisiert ist, gibt diese Funktion 1 zurück.

Weitere Informationen finden Sie [unter omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads Funktion

Die `omp_get_max_threads` Funktion gibt eine ganze Zahl zurück, die garantiert mindestens so groß ist wie die Anzahl der Threads, die verwendet würden, um ein Team zu bilden, wenn an diesem Punkt im Code ein paralleler Bereich ohne `num_threads` Klausel angezeigt würde. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Im Folgenden wird eine Untergrenze `omp_get_max_threads`für den Wert von:

> *Threads-used-for-next-Team* <= `omp_get_max_threads`

Beachten Sie, dass, `num_threads` wenn eine andere parallele Region die Klausel verwendet, um `omp_get_max_threads` eine bestimmte Anzahl von Threads anzufordern, die Garantie für die untere Grenze des Ergebnisses nicht mehr gilt.

Der `omp_get_max_threads` Rückgabewert der Funktion kann verwendet werden, um dynamisch ausreichend Speicher für alle Threads im Team zuzuweisen, das im nächsten parallelen Bereich gebildet wird.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num Funktion

Die `omp_get_thread_num` Funktion gibt die Threadnummer des Threads zurück, der die Funktion ausführt. Die Threadnummer liegt `omp_get_num_threads()`zwischen 0 und -1, einschließlich. Der Hauptthread des Teams ist Thread 0.

Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Wenn aus einer seriellen Region aufgerufen wird, `omp_get_thread_num` gibt 0 zurück. Wenn diese Funktion innerhalb eines verschachtelten parallelen Bereichs aufgerufen wird, der serialisiert ist, gibt diese Funktion 0 zurück.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function) Funktion

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs Funktion

Die `omp_get_num_procs` Funktion gibt die Anzahl der Prozessoren zurück, die dem Programm zum Zeitpunkt des Aufrufs der Funktion zur Verfügung stehen. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel Funktion

Die `omp_in_parallel` Funktion gibt einen Wert ungleich Null zurück, wenn er innerhalb der dynamischen Ausdehnung eines parallel ausgeführten parallel ausgeführten parallelen Bereichs aufgerufen wird. Andernfalls wird 0 zurückgegeben. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Diese Funktion gibt einen Wert ungleich Null zurück, wenn er innerhalb einer Parallelregion aufgerufen wird, einschließlich verschachtelter Bereiche, die serialisiert werden.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic Funktion

Die `omp_set_dynamic` Funktion aktiviert oder deaktiviert die dynamische Anpassung der Anzahl der Threads, die für die Ausführung paralleler Regionen verfügbar sind. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Wenn *dynamic_threads* zu einem Wert ungleich Null ausgewertet wird, kann die Anzahl der Threads, die zum Ausführen bevorstehender paralleler Regionen verwendet werden, automatisch von der Laufzeitumgebung angepasst werden, um Die Systemressourcen optimal zu nutzen. Daher ist die Anzahl der vom Benutzer angegebenen Threads die maximale Threadanzahl. Die Anzahl der Threads im Team, die einen parallelen Bereich ausführen, bleibt `omp_get_num_threads` für die Dauer dieser parallelen Region festgelegt und wird von der Funktion gemeldet.

Wenn *dynamic_threads* auf 0 ausgewertet wird, ist die dynamische Anpassung deaktiviert.

Diese Funktion hat die oben beschriebenen Effekte, wenn `omp_in_parallel` sie von einem Teil des Programms aufgerufen wird, in dem die Funktion Null zurückgibt. Wenn sie von einem Teil des Programms `omp_in_parallel` aufgerufen wird, in dem die Funktion einen Wert ungleich Null zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Ein Aufruf `omp_set_dynamic` an hat `OMP_DYNAMIC` Vorrang vor der Umgebungsvariablen.

Der Standardwert für die dynamische Anpassung von Threads ist implementierungsdefiniert. Daher sollten Benutzercodes, die für die korrekte Ausführung von einer bestimmten Anzahl von Threads abhängen, dynamische Threads explizit deaktivieren. Implementierungen sind nicht erforderlich, um die Anzahl der Threads dynamisch anzupassen, aber sie müssen die Schnittstelle bereitstellen, um die Portabilität über alle Plattformen hinweg zu unterstützen.

#### <a name="microsoft-specific"></a>Microsoft-spezifisch

Die aktuelle `omp_get_dynamic` Unterstützung `omp_set_dynamic` von und ist wie folgt:

Der Eingabeparameter, `omp_set_dynamic` der nicht auf die Threadingrichtlinie wirkt, ändert sich nicht und ändert die Anzahl der Threads nicht. `omp_get_num_threads`gibt immer entweder die benutzerdefinierte Nummer zurück, sofern diese festgelegt ist, oder die Standardthreadnummer. Deaktiviert in der `omp_set_dynamic(0)` aktuellen Microsoft-Implementierung das dynamische Threading, sodass der vorhandene Threadsatz für den folgenden parallelen Bereich wiederverwendet werden kann. `omp_set_dynamic(1)`aktiviert dynamisches Threading, indem der vorhandene Threadsatz verworfen und ein neuer Satz für den kommenden parallelen Bereich erstellt wird. Die Anzahl der Threads im neuen Satz entspricht dem alten Satz und `omp_get_num_threads`basiert auf dem Rückgabewert von . Verwenden Sie `omp_set_dynamic(0)` daher für eine optimale Leistung die vorhandenen Threads wiederverwenden.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic Funktion

Die `omp_get_dynamic` Funktion gibt einen Wert ungleich Null zurück, wenn die dynamische Anpassung von Threads aktiviert ist, und gibt andernfalls 0 zurück. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Wenn die Implementierung keine dynamische Anpassung der Anzahl der Threads implementiert, gibt diese Funktion immer 0 zurück. Weitere Informationen finden Sie [unter omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- Eine Beschreibung der dynamischen Gewindeanpassung finden Sie [unter omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested Funktion

Die `omp_set_nested` Funktion aktiviert oder deaktiviert verschachtelte Parallelität. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Wenn *geschachtelt* auf 0 ausgewertet wird, ist die geschachtelte Parallelität deaktiviert, was der Standardwert ist, und verschachtelte parallele Bereiche werden serialisiert und vom aktuellen Thread ausgeführt. Andernfalls ist die verschachtelte Parallelität aktiviert, und parallele Regionen, die verschachtelt sind, können zusätzliche Threads bereitstellen, um verschachtelte Teams zu bilden.

Diese Funktion hat die oben beschriebenen Effekte, wenn `omp_in_parallel` sie von einem Teil des Programms aufgerufen wird, in dem die Funktion Null zurückgibt. Wenn sie von einem Teil des Programms `omp_in_parallel` aufgerufen wird, in dem die Funktion einen Wert ungleich Null zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Dieser Aufruf hat `OMP_NESTED` Vorrang vor der Umgebungsvariablen.

Wenn geschachtelte Parallelität aktiviert ist, ist die Anzahl der Threads, die zum Ausführen verschachtelter paralleler Bereiche verwendet werden, implementierungsdefiniert. Daher ist es OpenMP-kompatiblen Implementierungen erlaubt, verschachtelte parallele Regionen zu serialisieren, auch wenn geschachtelte Parallelität aktiviert ist.

#### <a name="cross-references"></a>Querverweise

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested Funktion

Die `omp_get_nested` Funktion gibt einen Wert ungleich Null zurück, wenn die geschachtelte Parallelität aktiviert ist, und 0, wenn sie deaktiviert ist. Weitere Informationen zur verschachtelten Parallelität finden Sie unter [omp_set_nested](#319-omp_set_nested-function). Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Wenn eine Implementierung keine geschachtelte Parallelität implementiert, gibt diese Funktion immer 0 zurück.

## <a name="32-lock-functions"></a>3.2 Sperrfunktionen

Die in diesem Abschnitt beschriebenen Funktionen bearbeiten Sperren, die für die Synchronisierung verwendet werden.

Für die folgenden Funktionen muss die `omp_lock_t`Sperrvariable den Typ haben. Auf diese Variable darf nur über diese Funktionen zugegriffen werden. Alle Sperrfunktionen erfordern ein Argument, `omp_lock_t` das über einen Zeiger zum Typ verfügt.

- Die [omp_init_lock-Funktion](#321-omp_init_lock-and-omp_init_nest_lock-functions) initialisiert eine einfache Sperre.
- Die [omp_destroy_lock-Funktion](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) entfernt eine einfache Sperre.
- Die [omp_set_lock-Funktion](#323-omp_set_lock-and-omp_set_nest_lock-functions) wartet, bis eine einfache Sperre verfügbar ist.
- Die [omp_unset_lock-Funktion](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) löst eine einfache Sperre.
- Die [omp_test_lock-Funktion](#325-omp_test_lock-and-omp_test_nest_lock-functions) testet eine einfache Sperre.

Für die folgenden Funktionen muss die `omp_nest_lock_t`Sperrvariable den Typ haben.  Auf diese Variable darf nur über diese Funktionen zugegriffen werden. Alle verschachtelbaren Sperrfunktionen erfordern ein `omp_nest_lock_t` Argument, das über einen Zeiger zum Typ verfügt.

- Die [omp_init_nest_lock-Funktion](#321-omp_init_lock-and-omp_init_nest_lock-functions) initialisiert eine verschachtelbare Sperre.
- Die [omp_destroy_nest_lock-Funktion](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) entfernt eine verschachtelbare Sperre.
- Die [omp_set_nest_lock-Funktion](#323-omp_set_lock-and-omp_set_nest_lock-functions) wartet, bis eine verschachtelte Sperre verfügbar ist.
- Die [omp_unset_nest_lock-Funktion](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) löst eine verschachtelbare Sperre.
- Die [omp_test_nest_lock-Funktion](#325-omp_test_lock-and-omp_test_nest_lock-functions) testet eine verschachtelbare Sperre.

Die OpenMP-Sperrfunktionen greifen so auf die Sperrvariable zu, dass sie immer den aktuellsten Wert der Sperrvariablen lesen und aktualisieren. Daher ist es nicht erforderlich, dass ein OpenMP-Programm explizite `flush` Direktiven enthält, um sicherzustellen, dass der Wert der Sperrvariablen zwischen verschiedenen Threads konsistent ist. (Es kann erforderlich `flush` sein, dass Richtlinien die Werte anderer Variablen konsistent machen.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock- und omp_init_nest_lock Funktionen

Diese Funktionen bieten die einzige Möglichkeit, eine Sperre zu initialisieren. Jede Funktion initialisiert die Sperre, die der *Parametersperre* zugeordnet ist, für die Verwendung in anstehenden Aufrufen. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Der Anfangszustand wird entsperrt (d. h., kein Thread besitzt die Sperre). Bei einer verschachtelbaren Sperre ist die anfängliche Verschachtelungsanzahl Null. Es ist nicht konform, eine dieser Routinen mit einer Bereitsinitialen-Sperrvariablen aufzurufen.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock- und omp_destroy_nest_lock Funktionen

Diese Funktionen stellen sicher, dass die *Sperre* der zu Sperren variablen Nichtinitialisierung ist. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Es ist nicht konform, eine dieser Routinen mit einer Sperrvariablen aufzurufen, die nicht initialisiert oder entsperrt ist.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock- und omp_set_nest_lock-Funktionen

Jede dieser Funktionen blockiert den Thread, der die Funktion ausführt, bis die angegebene Sperre verfügbar ist, und legt dann die Sperre fest. Eine einfache Sperre ist verfügbar, wenn sie entsperrt ist. Eine verschachtelbare Sperre ist verfügbar, wenn sie entsperrt ist oder bereits im Besitz des Threads ist, der die Funktion ausführt. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Bei einer einfachen Sperre muss `omp_set_lock` das Argument für die Funktion auf eine initialisierte Sperrvariable verweisen. Der Besitz der Sperre wird dem Thread gewährt, der die Funktion ausführt.

Bei einer verschachtelbaren Sperre `omp_set_nest_lock` muss das Argument für die Funktion auf eine initialisierte Sperrvariable verweisen. Die Verschachtelungsanzahl wird erhöht, und der Thread wird dem Sperrthread gewährt oder behält den Besitz der Sperre bei.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock- und omp_unset_nest_lockFunktionen

Diese Funktionen bieten die Möglichkeit, den Besitz einer Sperre freizugeben. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Das Argument für jede dieser Funktionen muss auf eine initialisierte Sperrvariable verweisen, die dem Thread gehört, der die Funktion ausführt. Das Verhalten ist nicht definiert, wenn der Thread nicht über diese Sperre gehört.

Bei einer einfachen `omp_unset_lock` Sperre löst die Funktion den Thread, der die Funktion ausführt, aus dem Besitz der Sperre.

Bei einer verschachtelbaren Sperre dekrementiert die `omp_unset_nest_lock` Funktion die Verschachtelungsanzahl und gibt den Thread, der die Funktion ausführt, aus dem Besitz der Sperre, wenn die resultierende Anzahl Null ist.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock- und omp_test_nest_lock Funktionen

Diese Funktionen versuchen, eine Sperre festzulegen, blockieren jedoch nicht die Ausführung des Threads. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Das Argument muss auf eine initialisierte Sperrvariable verweisen. Diese Funktionen versuchen, eine Sperre auf `omp_set_lock` `omp_set_nest_lock`die gleiche Weise wie und festzulegen, mit der Ausnahme, dass sie die Ausführung des Threads nicht blockieren.

Bei einer einfachen `omp_test_lock` Sperre gibt die Funktion einen Wert ungleich Null zurück, wenn die Sperre erfolgreich festgelegt wurde. Andernfalls wird Null zurückgegeben.

Bei einer verschachtelbaren Sperre gibt die `omp_test_nest_lock` Funktion die neue Verschachtelungsanzahl zurück, wenn die Sperre erfolgreich festgelegt wurde. Andernfalls wird Null zurückgegeben.

## <a name="33-timing-routines"></a>3.3 Timing-Routinen

Die in diesem Abschnitt beschriebenen Funktionen unterstützen einen tragbaren Wanduhr-Timer:

- Die [omp_get_wtime-Funktion](#331-omp_get_wtime-function) gibt die verstrichene Wand-Uhr-Zeit zurück.
- Die [omp_get_wtick-Funktion](#332-omp_get_wtick-function) gibt Sekunden zwischen aufeinanderfolgenden Takten zurück.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime Funktion

Die `omp_get_wtime` Funktion gibt einen Gleitkommawert mit doppelter Genauigkeit zurück, der der verstrichenen Wanduhrzeit in Sekunden seit einiger "Zeit in der Vergangenheit" entspricht.  Die tatsächliche "Zeit in der Vergangenheit" ist willkürlich, aber es ist garantiert, dass sich während der Ausführung des Anwendungsprogramms nicht ändert. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Es wird erwartet, dass die Funktion verwendet wird, um verstrichene Zeiten zu messen, wie im folgenden Beispiel gezeigt:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Die zurückgegebenen Zeiten sind "pro Thread", d. h., sie müssen nicht global konsistent über alle Threads hinweg sein, die an einer Anwendung teilnehmen.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick Funktion

Die `omp_get_wtick` Funktion gibt einen Gleitkommawert mit doppelter Genauigkeit zurück, der der Anzahl der Sekunden zwischen aufeinanderfolgenden Takten entspricht. Das Format sieht folgendermaßen aus:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
