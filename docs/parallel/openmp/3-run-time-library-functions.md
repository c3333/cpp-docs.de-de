---
title: 3. Funktionen der Runtimebibliothek
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 6155eb87bd7a1a0533caf99afb3db8417854df30
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424170"
---
# <a name="3-run-time-library-functions"></a>3. Lauf Zeit Bibliotheksfunktionen

In diesem Abschnitt werden die Funktionen von OpenMP C und C++ der Lauf Zeit Bibliothek beschrieben. Der Header **\<OMP. h >** deklariert zwei Typen, mehrere Funktionen, die verwendet werden können, um die parallele Ausführungsumgebung zu steuern und abzufragen, und Sperr Funktionen, die verwendet werden können, um den Zugriff auf Daten zu synchronisieren.

Der Typ `omp_lock_t` ist ein Objekttyp, der darstellen kann, dass eine Sperre verfügbar ist, oder dass ein Thread eine Sperre besitzt. Diese Sperren werden als *einfache sperren*bezeichnet.

Der Typ `omp_nest_lock_t` ist ein Objekttyp, der eine Sperre darstellen kann, oder sowohl die Identität des Threads, der die Sperre besitzt, als auch eine Schachtelungs *Anzahl* (unten beschrieben). Diese Sperren werden als " *netzfeste Sperren*" bezeichnet.

Die Bibliotheksfunktionen sind externe Funktionen mit der Verknüpfung "C".

Die Beschreibungen in diesem Kapitel sind in folgende Themen unterteilt:

- [Funktionen der Ausführungsumgebung](#31-execution-environment-functions)
- [Lock-Funktionen](#32-lock-functions)
- [Zeit Steuerungs Routinen](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3,1 Funktionen der Ausführungsumgebung

Die in diesem Abschnitt beschriebenen Funktionen beeinflussen und überwachen Threads, Prozessoren und die parallele Umgebung:

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads Funktion

Die `omp_set_num_threads`-Funktion legt die Standard Anzahl von Threads fest, die für spätere parallele Bereiche verwendet werden, die keine `num_threads`-Klausel angeben. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Der Wert des-Parameters *num_threads* muss eine positive ganze Zahl sein. Seine Auswirkung hängt davon ab, ob die dynamische Anpassung der Thread Anzahl aktiviert ist. Eine umfassende Reihe von Regeln zur Interaktion zwischen der `omp_set_num_threads`-Funktion und der dynamischen Anpassung von Threads finden Sie im [Abschnitt 2,3](2-directives.md#23-parallel-construct).

Diese Funktion hat die oben beschriebenen Effekte, wenn Sie von einem Teil des Programms aufgerufen wird, wobei die `omp_in_parallel`-Funktion 0 (null) zurückgibt. Wenn Sie von einem Teil des Programms aufgerufen wird, in dem die `omp_in_parallel`-Funktion einen Wert ungleich 0 (null) zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Dieser Aufrufe hat Vorrang vor der `OMP_NUM_THREADS`-Umgebungsvariablen. Der Standardwert für die Anzahl der Threads, die durch Aufrufen von `omp_set_num_threads` oder durch Festlegen der `OMP_NUM_THREADS`-Umgebungsvariable festgelegt werden können, kann in einer einzelnen `parallel` Direktive explizit überschrieben werden, indem die `num_threads`-Klausel angegeben wird.

Weitere Informationen finden Sie unter [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- [omp_set_dynamic](#317-omp_set_dynamic-function) -Funktion
- [omp_get_dynamic](#318-omp_get_dynamic-function) -Funktion
- Umgebungsvariable [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct) -Klausel

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads-Funktion

Die `omp_get_num_threads`-Funktion gibt die Anzahl der Threads zurück, die derzeit in dem Team ausgeführt werden, von dem der parallele Bereich ausgeführt wird. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Die `num_threads`-Klausel, die `omp_set_num_threads`-Funktion und die `OMP_NUM_THREADS`-Umgebungsvariable steuern die Anzahl der Threads in einem Team.

Wenn die Anzahl der Threads nicht explizit vom Benutzer festgelegt wurde, wird der Standardwert von der Implementierung definiert. Diese Funktion bindet an die nächstgelegene einschließende `parallel`-Direktive. Diese Funktion gibt 1 zurück, wenn Sie von einem seriellen Teil eines Programms oder aus einem nicht serialisierten geschachtelte parallel-Bereich aufgerufen wird.

Weitere Informationen finden Sie unter [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads-Funktion

Die `omp_get_max_threads`-Funktion gibt eine Ganzzahl zurück, die garantiert mindestens so groß ist wie die Anzahl der Threads, die zum bilden eines Teams verwendet werden, wenn ein paralleler Bereich ohne `num_threads`-Klausel an diesem Punkt im Code zu sehen ist. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Der folgende Ausdruck drückt eine untere Grenze für den Wert `omp_get_max_threads`aus:

> *Threads-used-für-Next-Team* <= `omp_get_max_threads`

Beachten Sie Folgendes: Wenn ein anderer paralleler Bereich die `num_threads`-Klausel verwendet, um eine bestimmte Anzahl von Threads anzufordern, ist die Garantie für die untere Grenze des Ergebnisses von `omp_get_max_threads` nicht mehr enthalten.

Der Rückgabewert der `omp_get_max_threads` Funktion kann verwendet werden, um für alle Threads im Team, die in der nächsten parallelen Region gebildet werden, ausreichend Speicherplatz zuzuweisen.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num-Funktion

Die `omp_get_thread_num`-Funktion gibt die Thread Nummer des Threads, der die Funktion ausführt, innerhalb des Teams zurück. Die Thread Nummer liegt zwischen 0 und `omp_get_num_threads()`-1 (einschließlich). Der Master Thread des Teams ist Thread 0.

Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Wenn Sie von einem seriellen Bereich aus aufgerufen wird, gibt `omp_get_thread_num` 0 zurück. Wenn Sie aus einem geschachtelten parallelen Bereich aufgerufen wird, der serialisiert wird, gibt diese Funktion 0 zurück.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function) -Funktion

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs-Funktion

Die `omp_get_num_procs`-Funktion gibt die Anzahl der Prozessoren zurück, die für das Programm verfügbar sind, wenn die Funktion aufgerufen wird. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel-Funktion

Die `omp_in_parallel`-Funktion gibt einen Wert ungleich 0 (null) zurück, wenn Sie innerhalb des dynamischen Umfangs eines parallel ausgeführten parallelen Bereichs aufgerufen wird. Andernfalls wird 0 zurückgegeben. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Diese Funktion gibt einen Wert ungleich 0 (null) zurück, wenn Sie von innerhalb eines parallel ausgeführten Bereichs aufgerufen wird, einschließlich geschachtelter Bereiche, die serialisiert werden.

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic-Funktion

Die `omp_set_dynamic`-Funktion aktiviert oder deaktiviert die dynamische Anpassung der Anzahl von Threads, die für die Ausführung paralleler Regionen verfügbar sind. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Wenn *dynamic_threads* den Wert ungleich 0 (null) ergibt, wird die Anzahl der Threads, die für die Ausführung bevorstehender paralleler Regionen verwendet werden, möglicherweise automatisch von der Laufzeitumgebung angepasst, um die Systemressourcen optimal zu nutzen. Folglich ist die Anzahl der Threads, die vom Benutzer angegeben werden, die maximale Thread Anzahl. Die Anzahl der Threads im Team, die einen parallelen Bereich ausführen, bleibt für die Dauer dieses parallelen Bereichs fest und wird von der `omp_get_num_threads` Funktion gemeldet.

Wenn *dynamic_threads* als 0 (null) ausgewertet wird, ist die dynamische Anpassung deaktiviert.

Diese Funktion hat die oben beschriebenen Effekte, wenn Sie von einem Teil des Programms aufgerufen wird, wobei die `omp_in_parallel`-Funktion 0 (null) zurückgibt. Wenn Sie von einem Teil des Programms aufgerufen wird, in dem die `omp_in_parallel`-Funktion einen Wert ungleich 0 (null) zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Ein `omp_set_dynamic`-Aufrufe hat Vorrang vor der `OMP_DYNAMIC`-Umgebungsvariablen.

Der Standardwert für die dynamische Anpassung von Threads ist Implementierungs definiert. Folglich sollten Benutzercodes, die von einer bestimmten Anzahl von Threads für die korrekte Ausführung abhängen, dynamische Threads explizit deaktivieren. Implementierungen sind nicht erforderlich, um die Möglichkeit zur dynamischen Anpassung der Anzahl von Threads bereitzustellen. Sie müssen jedoch die Schnittstelle bereitstellen, um die Portabilität auf allen Plattformen zu unterstützen.

#### <a name="microsoft-specific"></a>Microsoft-spezifisch

Die aktuelle Unterstützung von `omp_get_dynamic` und `omp_set_dynamic` sieht wie folgt aus:

Der Eingabeparameter für `omp_set_dynamic` wirkt sich nicht auf die Threading Richtlinie aus und ändert nicht die Anzahl der Threads. `omp_get_num_threads` gibt immer entweder die benutzerdefinierte Zahl zurück, wenn diese festgelegt ist, oder die Standard Thread Nummer. In der aktuellen Microsoft-Implementierung deaktiviert `omp_set_dynamic(0)` dynamisches Threading, sodass der vorhandene Satz von Threads für den folgenden parallelen Bereich wieder verwendet werden kann. `omp_set_dynamic(1)` schaltet dynamisches Threading ein, indem der vorhandene Satz von Threads verworfen und eine neue Menge für die bevorstehende parallele Region erstellt wird. Die Anzahl der Threads im neuen Satz entspricht dem alten Satz und basiert auf dem Rückgabewert `omp_get_num_threads`. Verwenden Sie daher `omp_set_dynamic(0)`, um die vorhandenen Threads wiederzuverwenden, um die bestmögliche Leistung zu erzielen.

#### <a name="cross-references"></a>Querverweise

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic-Funktion

Die `omp_get_dynamic`-Funktion gibt einen Wert ungleich 0 (null) zurück, wenn die dynamische Anpassung der Threads aktiviert ist, und gibt andernfalls 0 zurück. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Wenn die Implementierung keine dynamische Anpassung der Anzahl von Threads implementiert, gibt diese Funktion immer 0 (null) zurück. Weitere Informationen finden Sie unter [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Querverweise

- Eine Beschreibung der dynamischen Thread Anpassung finden Sie unter [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested-Funktion

Die `omp_set_nested`-Funktion aktiviert oder deaktiviert die zusammengeführte Parallelität. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Wenn *der* Wert für "Null" auf 0 (null) ausgewertet wird, wird die nicht-Standard Parallelität deaktiviert. Andernfalls ist die untergeordnete Parallelität aktiviert, und parallele Bereiche, die eingebettet sind, können zusätzliche Threads bereitstellen, um die Bildung von Netz Teams zu bilden.

Diese Funktion hat die oben beschriebenen Effekte, wenn Sie von einem Teil des Programms aufgerufen wird, wobei die `omp_in_parallel`-Funktion 0 (null) zurückgibt. Wenn Sie von einem Teil des Programms aufgerufen wird, in dem die `omp_in_parallel`-Funktion einen Wert ungleich 0 (null) zurückgibt, ist das Verhalten dieser Funktion nicht definiert.

Dieser Aufrufe hat Vorrang vor der `OMP_NESTED`-Umgebungsvariablen.

Wenn die gestreamte Parallelität aktiviert ist, wird die Anzahl der Threads, die für die Ausführung von gemusteten parallelen Bereichen verwendet werden, von der Implementierung definiert Demzufolge können mit OpenMP kompatible Implementierungen auch dann, wenn die gemutete Parallelität aktiviert ist, auch bei aktivierter Parallelität auch bei aktivierter Parallelität eine Serialisierung

#### <a name="cross-references"></a>Querverweise

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested-Funktion

Die `omp_get_nested`-Funktion gibt einen Wert ungleich 0 (null) zurück, wenn die statische Parallelität aktiviert ist, und 0, wenn Sie deaktiviert ist. Weitere Informationen über die unter [omp_set_nested](#319-omp_set_nested-function). Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Wenn eine-Implementierung keine unter-und Parallelität implementiert, gibt diese Funktion immer 0 (null) zurück.

## <a name="32-lock-functions"></a>3,2 Sperr Funktionen

Die in diesem Abschnitt beschriebenen Funktionen bearbeiten sperren, die für die Synchronisierung verwendet werden.

Für die folgenden Funktionen muss die Lock-Variable den Typ `omp_lock_t`haben. Auf diese Variable darf nur über diese Funktionen zugegriffen werden. Alle Sperr Funktionen erfordern ein Argument, das einen Zeiger auf `omp_lock_t` Typ aufweist.

- Die [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) Funktion initialisiert eine einfache Sperre.
- Die [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) -Funktion entfernt eine einfache Sperre.
- Die [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) -Funktion wartet, bis eine einfache Sperre verfügbar ist.
- Die [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) -Funktion gibt eine einfache Sperre frei.
- Die [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) -Funktion testet eine einfache Sperre.

Für die folgenden Funktionen muss die Lock-Variable den Typ `omp_nest_lock_t`haben.  Auf diese Variable darf nur über diese Funktionen zugegriffen werden. Alle für die Funktion erforderlichen Sperr Funktionen erfordern ein Argument, das einen Zeiger auf `omp_nest_lock_t`-Typ aufweist.

- Die [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) -Funktion initialisiert eine Sperre für eine Sperre.
- Die [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) -Funktion entfernt eine nicht ordnungs eine Sperre.
- Die [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) -Funktion wartet, bis eine nicht verfügbare Sperre verfügbar ist.
- Die [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) -Funktion gibt eine nicht stabile Sperre frei.
- Die [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) -Funktion testet eine nicht stabile Sperre.

Die OpenMP-Sperr Funktionen greifen so auf die Sperr Variable zu, dass Sie immer den aktuellsten Wert der Sperr Variablen lesen und aktualisieren. Daher ist es nicht erforderlich, dass ein OpenMP-Programm explizite `flush` Direktiven einschließt, um sicherzustellen, dass der Wert der Sperr Variablen zwischen verschiedenen Threads konsistent ist. (Möglicherweise müssen `flush` Direktiven die Werte anderer Variablen konsistent machen.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock-und omp_init_nest_lock Funktionen

Diese Funktionen stellen die einzige Möglichkeit dar, eine Sperre zu initialisieren. Jede Funktion initialisiert die Sperre, die der Parameter *Sperre* für die Verwendung in bevorstehenden aufrufen zugeordnet ist. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

Der Anfangszustand ist entsperrt (d. h., kein Thread besitzt die Sperre). Bei einer verschachtelten Sperre beträgt die anfängliche Schachtelungs Anzahl 0 (null). Es ist nicht kompatibel, eine dieser Routinen mit einer Sperr Variablen aufzurufen, die bereits initialisiert wurde.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock-und omp_destroy_nest_lock Funktionen

Diese Funktionen stellen sicher, dass die, auf die die Sperre variabler *Sperre* verweist, nicht initialisiert ist. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Es ist nicht kompatibel, eine dieser Routinen mit einer Sperr Variablen aufzurufen, die nicht initialisiert oder entsperrt ist.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3-Funktionen von omp_set_lock und omp_set_nest_lock

Jede dieser Funktionen blockiert den Thread, der die Funktion ausführt, bis die angegebene Sperre verfügbar ist, und legt dann die Sperre fest. Eine einfache Sperre ist verfügbar, wenn Sie entsperrt ist. Eine gesperrte Sperre ist verfügbar, wenn Sie entsperrt ist, oder wenn Sie bereits im Besitz des Threads ist, der die Funktion ausführt. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Für eine einfache Sperre muss das Argument für die `omp_set_lock`-Funktion auf eine initialisierte Sperr Variable verweisen. Der Besitz der Sperre wird dem Thread erteilt, der die Funktion ausführt.

Bei einer nicht stabilen Sperre muss das Argument für die `omp_set_nest_lock`-Funktion auf eine initialisierte Sperr Variable verweisen. Die Schachtelungs Anzahl wird inkrementiert, und dem Thread wird der Besitz der Sperre erteilt oder beibehalten.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock und omp_unset_nest_lock Funktionen

Diese Funktionen bieten die Möglichkeit, den Besitz einer Sperre freizugeben. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Das Argument für jede dieser Funktionen muss auf eine initialisierte Sperr Variable verweisen, die sich im Besitz des Threads befindet, der die Funktion ausführt. Das Verhalten ist nicht definiert, wenn der Thread diese Sperre nicht besitzt.

Bei einer einfachen Sperre gibt die `omp_unset_lock`-Funktion den Thread, der die Funktion ausführt, vom Besitz der Sperre frei.

Bei einer geschachtelten Sperre wird die Schachtelungs Anzahl von der `omp_unset_nest_lock` Funktion verringert, und der Thread, der die Funktion ausführt, wird vom Besitz der Sperre freigegeben, wenn der resultierende Zähler Null ist.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5-Funktionen von omp_test_lock und omp_test_nest_lock

Diese Funktionen versuchen, eine Sperre festzulegen, blockieren aber nicht die Ausführung des Threads. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Das-Argument muss auf eine initialisierte Sperr Variable verweisen. Diese Funktionen versuchen, eine Sperre auf die gleiche Weise wie `omp_set_lock` und `omp_set_nest_lock`festzulegen, mit dem Unterschied, dass die Ausführung des Threads nicht blockiert wird.

Bei einer einfachen Sperre gibt die `omp_test_lock`-Funktion einen Wert ungleich 0 (null) zurück, wenn die Sperre erfolgreich festgelegt wurde. Andernfalls wird 0 (null) zurückgegeben.

Bei einer verschachtelten Sperre gibt die `omp_test_nest_lock`-Funktion die neue Schachtelungs Anzahl zurück, wenn die Sperre erfolgreich festgelegt wurde. Andernfalls wird 0 (null) zurückgegeben.

## <a name="33-timing-routines"></a>3,3-Zeit Steuerungs Routinen

Die in diesem Abschnitt beschriebenen Funktionen unterstützen einen portablen Wall-Clock-Timer:

- Die [omp_get_wtime](#331-omp_get_wtime-function) -Funktion gibt die verstrichene Wand Uhrzeit zurück.
- Die [omp_get_wtick](#332-omp_get_wtick-function) -Funktion gibt Sekunden zwischen aufeinander folgenden Takt Einheiten zurück.

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime-Funktion

Die `omp_get_wtime`-Funktion gibt einen Gleit Komma Wert mit doppelter Genauigkeit zurück, der der verstrichenen Zeit in Sekunden seit der "Zeit in der Vergangenheit" entspricht.  Die tatsächliche "Zeit in der Vergangenheit" ist willkürlich, aber es wird garantiert, dass Sie während der Ausführung des Anwendungsprogramms nicht geändert wird. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Es wird erwartet, dass die-Funktion verwendet wird, um verstrichene Zeiten zu messen, wie im folgenden Beispiel gezeigt:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Die zurückgegebenen Zeiten sind "Thread Weise", bei dem Sie nicht für alle Threads, die an einer Anwendung beteiligt sind, Global konsistent sein müssen.

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick-Funktion

Die `omp_get_wtick`-Funktion gibt einen Gleit Komma Wert mit doppelter Genauigkeit zurück, der der Anzahl von Sekunden zwischen aufeinander folgenden Takt Intervallen entspricht. Es wird folgendes Format verwendet:

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
