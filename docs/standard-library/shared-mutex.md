---
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: 5dfb0e858bb412daf159ee9efc7dcc13be690886
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336725"
---
# <a name="ltshared_mutex"></a>&lt;shared_mutex>

Der &lt;shared_mutex>-Header stellt Synchronisierungsprimitive zum Schutz freigegebener Daten bereit, auf die von mehreren Threads zugegriffen werden kann. Zusätzlich zu der exklusiven Zugriffssteuerung, die von Mutex-Klassen bereitgestellt wird, ermöglichen die gemeinsamen Mutex-Klassen auch den gemeinsamen Besitz durch mehrere Threads für den nicht exklusiven Zugriff. Gemeinsame Mutexe können verwendet werden, um Ressourcen zu steuern, die von mehreren Threads gelesen werden können, ohne dass eine Racebedingung verursacht wird, aber ausschließlich von einem einzelnen Thread geschrieben werden müssen.

Der &lt;Header shared_mutex> `shared_mutex` definiert `shared_timed_mutex`die Klassen `shared_lock`und , `swap` die Klassenvorlage und die Vorlagenfunktion für die gemeinsame Mutex-Unterstützung.

|Klassen|BESCHREIBUNG|
|-------------|-----------------|
|[shared_mutex Klasse](#class_shared_mutex)|Einen gemeinsamer Mutex-Typ, der von einem Agent exklusiv gesperrt oder nicht exklusiv von mehreren Agents gemeinsam verwendet werden kann.|
|[shared_timed_mutex-Klasse](#class_shared_timed_mutex)|Einen gemeinsamer zeitgesteuerter Mutex-Typ, der von einem Agent exklusiv gesperrt oder nicht exklusiv von mehreren Agents gemeinsam verwendet werden kann.|
|[shared_lock-Klasse](#class_shared_lock)|Eine Klassenvorlage, die einen freigegebenen Mutex umschließt, um zeitgezeitende Sperrvorgänge und nicht-exklusive Freigabe durch mehrere Agenten zu unterstützen.|

|Functions|BESCHREIBUNG|
|---------------|-----------------|
|[swap](#function_swap)|Vertauscht den Inhalt von gemeinsamen Mutex-Objekten, auf die die Funktionsparameter verweisen.|

## <a name="syntax"></a>Syntax

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Bemerkungen

Eine Instanz von Klasse `shared_mutex` ist ein *gemeinsamer Mutex-Typ*, ein Typ, der den gemeinsamen Besitz eines Mutex innerhalb eines Bereichs steuert. Ein gemeinsamer Mutex-Typ erfüllt alle Anforderungen eines Mutex-Typs sowie Member zur Unterstützung des gemeinsamem nicht exklusiven Besitzes.

Ein gemeinsamer Mutex unterstützt die zusätzlichen Methoden `lock_shared`, `unlock_shared` und `try_lock_shared`:

- Die `lock_shared`-Methode blockiert den aufrufenden Thread, bis der Thread den gemeinsamen Besitz des Mutex erlangt.

- Die `unlock_shared`-Methode gibt den Besitz des Mutex frei, in dem der aufrufende Thread steht.

- Die `try_lock_shared`-Methode versucht, ohne Blockierung in den Besitz des Mutex zu gelangen. Sein Rückgabetyp ist in **bool** konvertierbar und **true,** wenn die Methode Besitz erlangt, aber ansonsten **false**ist.

Die Klasse `shared_timed_mutex` ist ein *gemeinsamer zeitgesteuerter Mutex-Typ*, ein Typ, der die Anforderungen eines gemeinsamen Mutex-Typs und eines zeitgesteuerten Mutex-Typs erfüllt.

Ein gemeinsamer zeitgesteuerter Mutex-Typ unterstützt die zusätzlichen Methoden `try_lock_shared_for` und `try_lock_shared_until`:

- Die `try_lock_shared_for`-Methode versucht, den gemeinsamen Besitz des Mutex abzurufen, bis die vom Parameter angegebene Dauer verstrichen ist. Wenn die Dauer nicht positiv ist, entspricht die Methode `try_lock_shared`. Die Methode gibt nicht innerhalb der angegebenen Dauer zurück, sofern der gemeinsame Besitz nicht abgerufen wird. Der Rückgabewert ist **true,** wenn die Methode Besitz erlangt, aber ansonsten **false**ist.

- Die `try_lock_shared_until` Methode versucht, den gemeinsamen Besitz des Mutex abrufen, bis die angegebene absolute Zeit abgelaufen ist. Wenn die angegebene Zeit bereits verstrichen ist, entspricht die Methode `try_lock_shared`. Die Methode gibt nicht vor der angegebenen Zeit zurück, wenn der gemeinsame Besitz nicht abgerufen wird. Der Rückgabewert ist **true,** wenn die Methode Besitz erlangt, aber ansonsten **false**ist.

Die `shared_lock` Klassenvorlage erweitert die Unterstützung für zeitnahe sperren und den Besitzübergang auf einen freigegebenen Mutex. Der Besitz des Mutex kann bei oder nach der Erstellung abgerufen und an ein anderes `shared_lock`-Objekt übertragen werden. Objekte vom Typ `shared_lock` können verschoben, aber nicht kopiert werden.

> [!WARNING]
> Ab Visual Studio 2015 basieren die Synchronisierungstypen der C++-Standardbibliothek auf Windows-Synchronisierungsprimitiven und verwenden ConcRT nicht mehr (außer wenn die Zielplattform Windows XP ist). Die in &lt;shared_mutex> definierten Typen sollten nicht mit ConcRT-Typen oder -Funktionen verwendet werden.

## <a name="classes"></a>Klassen

### <a name="shared_mutex-class"></a><a name="class_shared_mutex"></a> shared_mutex-Klasse

Klasse `shared_mutex` implementiert einen nicht rekursiven Mutex mit gemeinsamer Besitzsemantik.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

### <a name="shared_timed_mutex-class"></a><a name="class_shared_timed_mutex"></a>shared_timed_mutex Klasse

Klasse `shared_timed_mutex` implementiert einen nicht rekursiven Mutex mit gemeinsamer Besitz-Semantik, die den Anforderungen eines zeitgesteuerten Mutex-Typs entspricht.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

### <a name="shared_lock-class"></a><a name="class_shared_lock"></a> shared_lock-Klasse

Die `shared_lock` Klassenvorlage steuert den gemeinsamen Besitz eines freigegebenen Mutex-Objekts innerhalb eines Bereichs. Bei dem Vorlagenparameter muss es sich um einen gemeinsamen Mutex-Typ handeln.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Functions

### <a name="swap"></a><a name="function_swap"></a>Swap

Tauscht die `shared_lock`-Objekte.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Tauscht den Inhalt von zwei `shared_lock`-Objekten aus. Identisch mit `x.swap(y)`.

## <a name="requirements"></a>Anforderungen

**Header:** &lt;shared_mutex>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[Header-Dateien-Referenz](../standard-library/cpp-standard-library-header-files.md)\
[&lt;mutex>](../standard-library/mutex.md)
