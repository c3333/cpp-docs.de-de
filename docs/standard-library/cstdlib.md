---
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 1b20e13a43c5d223332af70a91e096cedc284a43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230051"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

Schließt den C-Standard Bibliotheks Header ein \<stdlib.h> und fügt die verknüpften Namen zum- `std` Namespace hinzu. Durch einschließen dieses Headers wird sichergestellt, dass die mit externer Verknüpfung im C-Standard Bibliotheks Header deklarierten Namen im- `std` Namespace deklariert werden.

> [!NOTE]
> \<stdlib.h>schließt den-Typ nicht ein **`wchar_t`** .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<cstdlib>

**Namespace:** std

## <a name="namespace-and-macros"></a>Namespace und Makros

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>Funktionen nur für die Ausstellung

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>Start-und Beendigungs Funktionen

|Funktion|BESCHREIBUNG|
|-|-|
|[_Exit](#_exit)|Beendet das Programm, ohne debugtoren oder registrierte Funktionen zu verwenden.|
|[abort](#abort)|Beendet das Programm ohne deerdeerdeverwendung.|
|[atexit](#atexit)|Registriert die Funktion für die Programm Beendigung.|
|[exit](#exit)|Zerstört Objekte mit Thread-und statischem Speicher und gibt dann die Steuerung zurück.|
|[at_quick_exit](#at_quick_exit)|Registriert die Funktion ohne Argumente für die Programm Beendigung.|
|[quick_exit](#quick_exit)|Registriert die Funktion mit beibehaltenen Objekten für die Programm Beendigung.|
|[getenv](#getenv)|Siehe C-Standard Bibliotheks Referenz.|
|[System](#system)|Siehe C-Standard Bibliotheks Referenz.|

### <a name="_exit"></a><a name="_exit"></a>_Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>Bemerkungen

Das Programm wird beendet, ohne dass Dekonstruktoren für Objekte der automatischen, Thread-oder statischen Speicherdauer ausgeführt werden und keine Funktionen aufgerufen werden, die an übermittelt werden `atexit()` . Die Funktion `_Exit` ist Signal sicher.

### <a name="abort"></a><a name="abort"></a>Abbruch

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>Bemerkungen

Das Programm wird beendet, ohne dass Dekonstruktoren für Objekte der automatischen, Thread-oder statischen Speicherdauer ausgeführt werden und keine Funktionen aufgerufen werden, die an übermittelt werden `atexit()` . Die Funktion `abort` ist Signal sicher.

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a>at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>Rückgabewert

0 (null), wenn die Registrierung erfolgreich ist, andernfalls ungleich 0 (null).

#### <a name="remarks"></a>Bemerkungen

Die `at_quick_exit()` Funktionen registrieren eine Funktion *func*, die ohne Argumente aufgerufen wird, wenn `quick_exit` aufgerufen wird. Ein Aufruf von `at_quick_exit()` , der nicht vor allen Aufrufen von erfolgt, ist `quick_exit` möglicherweise nicht erfolgreich. Die `at_quick_exit()` Funktionen stellen kein Daten Rennen dar. Die Reihenfolge der Registrierung ist möglicherweise `at_quick_exit` unbestimmt, wenn von mehr als einem Thread aufgerufen wurde. Da `at_quick_exit` sich Registrierungen von den `atexit` Registrierungen unterscheiden, müssen Anwendungen möglicherweise beide Registrierungsfunktionen mit dem gleichen Argument aufzurufen. MSVC unterstützt die Registrierung von mindestens 32 Funktionen.

### <a name="atexit"></a><a name="atexit"></a>atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>Bemerkungen

Die `atexit()` Funktionen registrieren die Funktion, auf die von *Func* verwiesen wird, um beim normalen Programmabbruch ohne Argumente aufgerufen zu werden. Ein-Befehl `atexit()` , der nicht vor einem-Rückruf ausgeführt wird, ist `exit()` möglicherweise nicht erfolgreich. Die `atexit()` Funktionen stellen kein Daten Rennen dar.

#### <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn die Registrierung erfolgreich ist, wenn ein Fehler auftritt.

### <a name="exit"></a><a name="exit"></a>Abstiegs

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>Bemerkungen

Zuerst werden Objekte mit Thread Speicherdauer, die dem aktuellen Thread zugeordnet sind, zerstört.

Als nächstes werden Objekte mit statischer Speicherdauer zerstört, und Funktionen, die durch Aufrufen von registriert `atexit` werden, werden aufgerufen. Automatische Objekte werden nicht zerstört, wenn `exit()` aufgerufen wird. Wenn das Steuerelement eine registrierte, von aufgerufene Funktion verlässt `exit` , weil die Funktion keinen Handler für eine ausgelöste Ausnahme bereitstellt, `std::terminate()` wird aufgerufen. Eine Funktion wird einmal für jedes Mal aufgerufen, wenn Sie registriert wird. Objekte mit automatischer Speicherdauer werden in einem Programm zerstört, dessen `main` Funktion keine automatischen Objekte enthält, und führt den-Befehl aus `exit()` . Das Steuerelement kann direkt an eine solche Funktion übertragen werden `main` , indem eine Ausnahme ausgelöst wird, die in abgefangen wird `main` .

Im nächsten Schritt werden alle Open c-Streams (wie von den in \<cstdio> deklarierten Funktions Signaturen) mit nicht geschriebenen gepufferten Daten geleert, alle geöffneten c-Streams werden geschlossen, und alle durch Aufrufen von erstellten Dateien `tmpfile()` werden entfernt.

Schließlich wird die Steuerung an die Host Umgebung zurückgegeben. Wenn der *Status* 0 (null) oder EXIT_SUCCESS ist, wird eine von der Implementierung definierte Form der erfolgreichen Beendigung des Status zurückgegeben. MSVC gibt den Wert 0 (null) zurück. Wenn der *Status* EXIT_FAILURE ist, gibt MSVC den Wert 3 zurück. Andernfalls gibt MSVC den Wert des *Status* -Parameters zurück.

### <a name="getenv"></a><a name="getenv"></a>getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a>quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>Bemerkungen

Im Allgemeinen werden Funktionen, die durch Aufrufe von registriert `at_quick_exit` werden, in umgekehrter Reihenfolge ihrer Registrierung aufgerufen. Diese Reihenfolge gilt nicht für Funktionen, die registriert werden, nachdem andere registrierte Funktionen bereits aufgerufen wurden. Wenn aufgerufen wird, werden keine Objekte zerstört `quick_exit` . Wenn das Steuerelement eine registrierte, von aufgerufene Funktion verlässt `quick_exit` , weil die Funktion keinen Handler für eine ausgelöste Ausnahme bereitstellt, `std::terminate()` wird aufgerufen. Eine Funktion, die über registriert `at_quick_exit` wird, wird von dem Thread aufgerufen, der aufruft, wobei es sich um `quick_exit` einen anderen Thread als den handelt, der ihn registriert hat. Dies bedeutet, dass registrierte Funktionen nicht von der Identität von Objekten abhängig sind, die über eine Thread Speicherdauer verfügen. Nachdem registrierte Funktionen aufgerufen wurden, `quick_exit` Ruft auf `_Exit(status)` . Die Standarddatei Puffer werden nicht geleert. Die `quick_exit` -Funktion ist Signal sicher, wenn die mit registrierten Funktionen `at_quick_exit` sind.

### <a name="system"></a><a name="system"></a>Anlage

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>Speicher Belegungs Funktionen

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist. MSVC unterstützt die- `aligned_alloc` Funktion nicht. C11 `aligned_alloc()` wurde auf eine Weise angegeben, die nicht mit der Microsoft-Implementierung von kompatibel ist `free()` , nämlich, dass in der `free()` Lage sein muss, stark ausgerichtete Zuweisungen zu verarbeiten.

## <a name="numeric-string-conversions"></a>Numerische Zeichen folgen Konvertierungen

```cpp
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>Multibyte/weite Zeichen folgen-und Zeichen Konvertierungs Funktionen

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="algorithm-functions"></a>Algorithmusfunktionen

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="low-quality-random-number-generation-functions"></a>Funktionen der Zufallszahlengenerierung mit niedriger Qualität

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="absolute-values"></a>Absolute Werte

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="integer-division"></a>Ganzzahldivision

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktionen verfügen über die Semantik, die in der C-Standardbibliothek angegeben ist.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
