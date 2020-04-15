---
title: lock-Klasse
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: ea09dd3d4a2eaf4cf7708d09509cfecfa4a6c6d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373076"
---
# <a name="lock-class"></a>lock-Klasse

Diese Klasse automatisiert die Verwendung einer Sperre zum Synchronisieren des Zugriffs auf ein Objekt aus mehreren Threads.  Wenn es gebaut wird, erhält es das Schloss und wenn es zerstört wird, löst es die Sperre.

## <a name="syntax"></a>Syntax

```cpp
ref class lock;
```

## <a name="remarks"></a>Bemerkungen

`lock`ist nur für CLR-Objekte verfügbar und kann nur im CLR-Code verwendet werden.

Intern verwendet <xref:System.Threading.Monitor> die Sperrklasse den Zugriff. Weitere Informationen finden Sie im Artikel, auf den verwiesen wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[Sperre::lock](#lock)|Erstellt ein `lock` Objekt, das optional darauf wartet, die Sperre für immer oder gar nicht für immer zu erhalten.|
|[lock::~lock](#tilde-lock)|Zerstört ein `lock` Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|---------|-----------|
|[lock::acquire](#acquire)|Erwirbt eine Sperre für ein Objekt, die optional darauf wartet, die Sperre für immer, für einen bestimmten Zeitraum oder gar nicht zu erhalten.|
|[lock::is_locked](#is-locked)|Gibt an, ob eine Sperre gehalten wird.|
|[lock::release](#release)|Gibt eine Sperre frei.|
|[lock::try_acquire](#try-acquire)|Erwirbt eine Sperre für ein Objekt, wartet auf `bool` eine bestimmte Zeit und gibt eine zurück, um den Erfolg der Erfassung zu melden, anstatt eine Ausnahme auszulösen.|

### <a name="public-operators"></a>Öffentliche Betreiber

|Name|BESCHREIBUNG|
|---------|-----------|
|[Sperre::operator&nbsp;bool](#operator-bool)|Operator für `lock` die Verwendung in einem bedingten Ausdruck.|
|[lock::operator==](#operator-equality)|Gleichheitsoperator.|
|[Sperre::operator!=](#operator-inequality)|Inequality-Operator.|

## <a name="requirements"></a>Anforderungen

**Headerdatei** \<msclr-lock.h>

**Namespace** msclr

## <a name="locklock"></a><a name="lock"></a>Sperre::lock

Erstellt ein `lock` Objekt, das optional darauf wartet, die Sperre für immer oder gar nicht für immer zu erhalten.

```cpp
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

### <a name="parameters"></a>Parameter

*_object*<br/>
Das zu sperrende Objekt.

*_timeout*<br/>
Timeoutwert in Millisekunden <xref:System.TimeSpan>oder als .

### <a name="exceptions"></a>Ausnahmen

Wird <xref:System.ApplicationException> ausgelöst, wenn die Sperrerfassung nicht vor dem Timeout auftritt.

### <a name="remarks"></a>Bemerkungen

Die ersten drei Formen des Konstruktors `_object` versuchen, innerhalb des angegebenen <xref:System.Threading.Timeout.Infinite> Timeoutzeitraums (oder wenn keine spezifiziert ist) eine Sperre zu erhalten.

Die vierte Form des Konstruktors erhält `_object`keine Sperre für . `lock_later`ist Mitglied der [lock_when.](../dotnet/lock-when-enum.md) Verwenden Sie [lock::acquire](../dotnet/lock-acquire.md) oder [lock::try_acquire,](../dotnet/lock-try-acquire.md) um die Sperre in diesem Fall zu erhalten.

Die Sperre wird automatisch aufgehoben, wenn der Destruktor aufgerufen wird.

`_object`kann nicht <xref:System.Threading.ReaderWriterLock>sein .  Ist dies der Fall, wird ein Compilerfehler angezeigt.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet. Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist. Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet dann auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_lock.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="locklock"></a><a name="tilde-lock"></a>Sperre::-Lock

Zerstört ein `lock` Objekt.

```cpp
~lock();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor ruft [lock::release](../dotnet/lock-release.md)auf.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet.  Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist.  Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet dann auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_dtor.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockacquire"></a><a name="acquire"></a>Sperre::erwerben

Erwirbt eine Sperre für ein Objekt, die optional darauf wartet, die Sperre für immer, für einen bestimmten Zeitraum oder gar nicht zu erhalten.

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parameter

*_timeout*<br/>
Timeoutwert in Millisekunden <xref:System.TimeSpan>oder als .

### <a name="exceptions"></a>Ausnahmen

Wird <xref:System.ApplicationException> ausgelöst, wenn die Sperrerfassung nicht vor dem Timeout auftritt.

### <a name="remarks"></a>Bemerkungen

Wenn kein Timeoutwert angegeben wird, lautet <xref:System.Threading.Timeout.Infinite>das Standardtimeout .

Wenn bereits eine Sperre erworben wurde, führt diese Funktion nichts aus.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet.  Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist. Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet dann auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockis_locked"></a><a name="is-locked"></a>Sperre::is_locked

Gibt an, ob eine Sperre gehalten wird.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn eine Sperre `false` gehalten wird, andernfalls.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet.  Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist.  Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind, und wartet auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_is_locked.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l.is_locked()) { // check if we got the lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>Sperre::operator bool

Operator für `lock` die Verwendung in einem bedingten Ausdruck.

```cpp
operator bool();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn eine Sperre `false` gehalten wird, andernfalls.

### <a name="remarks"></a>Bemerkungen

Dieser Operator konvertiert `_detail_class::_safe_bool` tatsächlich in `bool` die sicherer als weil es nicht in einen integralen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet.  Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist. Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_op_bool.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l) { // use bool operator to check for lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockrelease"></a><a name="release"></a>Sperre::Release

Gibt eine Sperre frei.

```cpp
void release();
```

### <a name="remarks"></a>Bemerkungen

Wenn keine Sperre gehalten `release` wird, tut nichts.

Sie müssen diese Funktion nicht explizit aufrufen. Wenn `lock` ein Objekt den Gültigkeitsbereich verlässt, ruft `release`sein Destruktor auf.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet. Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist. Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet dann auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_release.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="locktry_acquire"></a><a name="try-acquire"></a>Sperre::try_acquire

Erwirbt eine Sperre für ein Objekt, wartet auf `bool` eine bestimmte Zeit und gibt eine zurück, um den Erfolg der Erfassung zu melden, anstatt eine Ausnahme auszulösen.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parameter

*_timeout*<br/>
Timeoutwert in Millisekunden <xref:System.TimeSpan>oder als .

### <a name="return-value"></a>Rückgabewert

`true`wenn die Sperre `false` erworben wurde, andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn bereits eine Sperre erworben wurde, führt diese Funktion nichts aus.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer Klasse über mehrere Threads hinweg verwendet. Die Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf seine internen Daten für jeden Thread konsistent ist. Der Hauptanwendungsthread verwendet eine Sperre für dieselbe Instanz der Klasse, um regelmäßig zu überprüfen, ob Workerthreads noch vorhanden sind. Die Hauptanwendung wartet dann auf den Vorgang, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

```cpp
// msl_lock_try_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator"></a><a name="operator-equality"></a>Sperre::operator==

Gleichheitsoperator.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das auf Gleichheit zu prüfende Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `true` `t` zurück, wenn es sich `false` andernfalls um das Objekt der Sperre handelt.

### <a name="example"></a>Beispiel

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="lockoperator"></a><a name="operator-inequality"></a>Sperre::operator!=

Inequality-Operator.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Zu vergleichende Objekt für Ungleichheit.

### <a name="return-value"></a>Rückgabewert

Gibt `true` `t` zurück, wenn er sich `false` vom Objekt der Sperre unterscheidet.

### <a name="example"></a>Beispiel

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```
