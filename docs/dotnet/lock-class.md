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
ms.openlocfilehash: 7b2f187ec940af95523d0bbfb9265d7d9d6f69e8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508645"
---
# <a name="lock-class"></a>lock-Klasse

Diese Klasse automatisiert das Ausführen einer Sperre für die Synchronisierung des Zugriffs auf ein Objekt aus mehreren Threads.  Beim Konstruieren wird die Sperre angefordert, und wenn Sie gelöscht wird, wird die Sperre freigegeben.

## <a name="syntax"></a>Syntax

```cpp
ref class lock;
```

## <a name="remarks"></a>Bemerkungen

`lock` ist nur für CLR-Objekte verfügbar und kann nur in CLR-Code verwendet werden.

Intern wird von der Lock-Klasse verwendet <xref:System.Threading.Monitor> , um den Zugriff zu synchronisieren. Weitere Informationen finden Sie im referenzierten Artikel.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|---------|-----------|
|[Lock:: Lock](#lock)|Erstellt ein- `lock` Objekt, das optional darauf wartet, die Sperre für einen bestimmten Zeitraum dauerhaft zu erhalten, oder überhaupt nicht.|
|[lock::~lock](#tilde-lock)|Zerstört ein- `lock` Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|---------|-----------|
|[lock::acquire](#acquire)|Ruft eine Sperre für ein Objekt ab, wobei optional darauf gewartet wird, dass die Sperre für einen bestimmten Zeitraum (oder gar nicht) erhalten bleiben soll.|
|[lock::is_locked](#is-locked)|Gibt an, ob eine Sperre aufrechterhalten wird.|
|[lock::release](#release)|Gibt eine Sperre frei.|
|[lock::try_acquire](#try-acquire)|Ruft eine Sperre für ein Objekt ab, die auf einen angegebenen Zeitraum wartet und einen zurückgibt, **`bool`** um den Erfolg des Erwerbs zu melden, anstatt eine Ausnahme auszulösen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|---------|-----------|
|[Lock:: Operator &nbsp; bool](#operator-bool)|Operator für die Verwendung von `lock` in einem bedingten Ausdruck.|
|[lock::operator==](#operator-equality)|Gleichheits Operator.|
|[Lock:: Operator! =](#operator-inequality)|Ungleichheits Operator.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Headerdatei** \<msclr\lock.h>

**Namespace** -msclr

## <a name="locklock"></a><a name="lock"></a> Lock:: Lock

Erstellt ein- `lock` Objekt, das optional darauf wartet, die Sperre für einen bestimmten Zeitraum dauerhaft zu erhalten, oder überhaupt nicht.

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
Timeout Wert in Millisekunden oder als <xref:System.TimeSpan> .

### <a name="exceptions"></a>Ausnahmen

Wird ausgelöst, <xref:System.ApplicationException> Wenn die Sperre nicht vor dem Timeout erfolgt.

### <a name="remarks"></a>Bemerkungen

Die ersten drei Formen des Konstruktors versuchen, `_object` innerhalb des angegebenen Timeout Zeitraums eine Sperre zu erhalten (oder <xref:System.Threading.Timeout.Infinite> Wenn kein Wert angegeben ist).

Die vierte Form des Konstruktors erhält keine Sperre für `_object` . `lock_later` ist ein Member der [Lock_when](../dotnet/lock-when-enum.md)Enumeration. Verwenden Sie [Lock::](#acquire) Abruf oder [Lock:: try_acquire](#try-acquire) , um die Sperre in diesem Fall zu erhalten.

Die Sperre wird automatisch freigegeben, wenn der Dekonstruktor aufgerufen wird.

`_object` darf nicht sein <xref:System.Threading.ReaderWriterLock> .  Wenn dies der Fall ist, führt dies zu einem Compilerfehler.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet. Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist. Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet dann auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="locklock"></a><a name="tilde-lock"></a> Lock:: ~ Lock

Zerstört ein- `lock` Objekt.

```cpp
~lock();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor ruft [Lock:: Release](#release)auf.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet.  Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist.  Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet dann auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="lockacquire"></a><a name="acquire"></a> Lock:: Abruf

Ruft eine Sperre für ein Objekt ab, wobei optional darauf gewartet wird, dass die Sperre für einen bestimmten Zeitraum (oder gar nicht) erhalten bleiben soll.

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
Timeout Wert in Millisekunden oder als <xref:System.TimeSpan> .

### <a name="exceptions"></a>Ausnahmen

Wird ausgelöst, <xref:System.ApplicationException> Wenn die Sperre nicht vor dem Timeout erfolgt.

### <a name="remarks"></a>Bemerkungen

Wenn kein Timeout Wert angegeben wird, ist das Standard Timeout <xref:System.Threading.Timeout.Infinite> .

Wenn bereits eine Sperre eingerichtet wurde, führt diese Funktion keine Aktion aus.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet.  Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist. Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet dann auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="lockis_locked"></a><a name="is-locked"></a> Lock:: is_locked

Gibt an, ob eine Sperre aufrechterhalten wird.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn eine Sperre aufrechterhalten wird; **`false`** andernfalls.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet.  Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist.  Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um in regelmäßigen Abständen zu überprüfen, ob noch Arbeitsthreads vorhanden sind, und wartet auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a> Lock:: Operator bool

Operator für die Verwendung von `lock` in einem bedingten Ausdruck.

```cpp
operator bool();
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn eine Sperre aufrechterhalten wird; **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Dieser Operator konvertiert tatsächlich in `_detail_class::_safe_bool` , was sicherer als ist, **`bool`** weil er nicht in einen ganzzahligen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet.  Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist. Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet auf den Abschluss, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="lockrelease"></a><a name="release"></a> Lock:: Release

Gibt eine Sperre frei.

```cpp
void release();
```

### <a name="remarks"></a>Bemerkungen

Wenn keine Sperre aufrechterhalten wird, führt keine Aktion aus `release` .

Diese Funktion muss nicht explizit aufgerufen werden. Wenn ein- `lock` Objekt den Gültigkeitsbereich verlässt, ruft der Dekonstruktor auf `release` .

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet. Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist. Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet dann auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a> Lock:: try_acquire

Ruft eine Sperre für ein Objekt ab, die auf einen angegebenen Zeitraum wartet und einen zurückgibt, **`bool`** um den Erfolg des Erwerbs zu melden, anstatt eine Ausnahme auszulösen.

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
Timeout Wert in Millisekunden oder als <xref:System.TimeSpan> .

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Sperre abgerufen wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn bereits eine Sperre eingerichtet wurde, führt diese Funktion keine Aktion aus.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine einzelne Instanz einer-Klasse für mehrere Threads verwendet. Die-Klasse verwendet eine Sperre für sich selbst, um sicherzustellen, dass der Zugriff auf die internen Daten für jeden Thread konsistent ist. Der Hauptanwendungs Thread verwendet eine Sperre für dieselbe Instanz der-Klasse, um regelmäßig zu überprüfen, ob noch Arbeitsthreads vorhanden sind. Die Hauptanwendung wartet dann auf das Beenden, bis alle Arbeitsthreads ihre Aufgaben abgeschlossen haben.

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

## <a name="lockoperator"></a><a name="operator-equality"></a> Lock:: Operator = =

Gleichheits Operator.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parameter

*t*<br/>
Das auf Gleichheit zu prüfende Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt **`true`** zurück `t` , wenn mit dem-Objekt der Sperre identisch ist, **`false`** andernfalls.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a> Lock:: Operator! =

Ungleichheits Operator.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parameter

*t*<br/>
Das Objekt, das auf Ungleichheit verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt **`true`** zurück `t` , wenn vom-Objekt der Sperre abweicht, **`false`** andernfalls.

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
