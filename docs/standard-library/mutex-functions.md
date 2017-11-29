---
title: '&lt;mutex&gt;-Funktionen und -Variablen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: a81d134a4fb49f9123dbed5b4146976d5c676379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt;-Funktionen und -Variablen
||||  
|-|-|-|  
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|  
|[lock](#lock)|[try_to_lock](#try_to_lock)|  
  
##  <a name="adopt_lock"></a> adopt_lock-Variable  
 Stellt ein Objekt dar, das an die Konstruktoren für [lock_guard](../standard-library/lock-guard-class.md) und [unique_lock](../standard-library/unique-lock-class.md) übergeben werden kann, um anzugeben, dass das ebenfalls an den Konstruktor übergebene Mutex-Objekt gesperrt ist.  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="call_once"></a> call_once  
 Stellt einen Mechanismus zum Aufrufen eines angegebenen aufrufbaren Objekts genau einmal während der Ausführung bereit.  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>Parameter  
 `Flag`  
 Ein [once_flag](../standard-library/once-flag-structure.md)-Objekt, das gewährleistet, dass das aufrufbare Objekt nur einmal aufgerufen wird.  
  
 `F`  
 Ein aufrufbares Objekt.  
  
 `A`  
 Eine Argumentliste.  
  
### <a name="remarks"></a>Hinweise  
 Wenn `Flag` ungültig ist, löst die Funktion ein [system_error](../standard-library/system-error-class.md) mit dem Fehlercode `invalid_argument` aus. Andernfalls verwendet die Vorlagenfunktion ihr `Flag`-Argument, um zu gewährleisten, dass `F(A...)` genau einmal erfolgreich aufgerufen wird, und zwar unabhängig davon, wie oft die Vorlagenfunktion aufgerufen wird. Wenn `F(A...)` durch Auslösen einer Ausnahme beendet wird, war der Aufruf nicht erfolgreich.  
  
##  <a name="defer_lock"></a> defer_lock-Variable  
 Stellt ein Objekt dar, das an den Konstruktor für [unique_lock](../standard-library/unique-lock-class.md) übergeben werden kann. Dies gibt an, dass der Konstruktor das ebenfalls an ihn übergebene Mutex-Objekt nicht sperren darf.  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="lock"></a> lock  
 Versucht, alle Argumente ohne Deadlock zu sperren.  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>Hinweise  
 Die Argumente für die Vorlagenfunktion müssen *Mutex-Typen* sein, sofern nicht Aufrufe von `try_lock` Ausnahmen auslösen könnten.  
  
 Die Funktion sperrt alle Argumente ohne Deadlock durch Aufrufe von `lock`, `try_lock` und `unlock`. Wenn ein Aufruf von `lock` oder `try_lock` eine Ausnahme auslöst, ruft die Funktion auf allen Mutex-Objekten `unlock` auf, die vor dem erneuten Auslösen der Ausnahme erfolgreich gesperrt wurden.  
  
##  <a name="try_to_lock"></a> try_to_lock-Variable  
 Stellt ein Objekt dar, das an den Konstruktor für [unique_lock](../standard-library/unique-lock-class.md) übergeben werden kann, um anzugeben, dass der Konstruktor versuchen muss, das ebenfalls an ihn ohne Blockierung übergebene `mutex` zu entsperren.  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<mutex>](../standard-library/mutex.md)


