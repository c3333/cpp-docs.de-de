---
title: '&lt;exception&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: f71c03e0c0a2e7ea4f37a85e85628ccf630ea317
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368724"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; typedefs

## <a name="exception_ptr"></a><a name="exception_ptr"></a>exception_ptr

Ein Typ, der einen Zeiger auf eine Ausnahme beschreibt.

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Bemerkungen

Eine nicht angegebene interne Klasse, die verwendet wird, um den Typ `exception_ptr` zu implementieren.

Verwenden Sie ein `exception_ptr`-Objekt, um auf die aktuelle Ausnahme oder eine Instanz einer vom Benutzer angegebenen Ausnahme zu verweisen. In der Microsoft-Implementierung wird eine Ausnahme von einer [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record)-Struktur dargestellt. Jedes `exception_ptr`-Objekt enthält ein Ausnahmeverweisfeld, das auf eine Kopie der `EXCEPTION_RECORD`-Struktur zeigt, die die Ausnahme darstellt.

Wenn Sie eine `exception_ptr`-Variable deklarieren, wird die Variable keiner Ausnahme zugeordnet. Das heißt, das Ausnahmeverweisfeld ist NULL. Ein solches `exception_ptr`-Objekt wird als *null exception_ptr* bezeichnet.

Verwenden Sie die Funktion `current_exception` oder `make_exception_ptr`, um eine Ausnahme einem `exception_ptr`-Objekt zuzuweisen. Wenn Sie einer `exception_ptr`-Variable eine Ausnahme zuweisen, zeigt das Ausnahmeverweisfeld der Variable auf eine Kopie der Ausnahme. Ist nicht genügend Arbeitsspeicher zum Kopieren der Ausnahme vorhanden, zeigt das Ausnahmeverweisfeld auf eine Kopie einer [std::bad_alloc](../standard-library/bad-alloc-class.md)-Ausnahme. Wenn `current_exception` die `make_exception_ptr` oder-Funktion die Ausnahme aus einem anderen `terminate` Grund nicht kopieren kann, ruft die Funktion die CRT-Funktion auf, um den aktuellen Prozess zu beenden.

Trotz seines Namens ist ein `exception_ptr`-Objekt nicht selbst ein Zeiger. Es folgt keiner Zeigersemantik und kann nicht mit Zeigermemberzugriff (`->`) oder Dereferenzierung (*)-Operatoren verwendet werden. Das `exception_ptr`-Objekt weist keine öffentlichen Datenmember oder Memberfunktionen auf.

**Vergleiche:**

Sie können den Gleichheitsoperator (`==`) und den Ungleichheitsoperator (`!=`) verwenden, um zwei `exception_ptr`-Objekte zu vergleichen. Die Operatoren vergleichen nicht den Binärwert (Bitmuster) der `EXCEPTION_RECORD`-Strukturen, die die Ausnahmen darstellen. Stattdessen vergleichen die Operatoren die Adressen im Ausnahmeverweisfeld der `exception_ptr`-Objekte. Folglich sind ein NULL-`exception_ptr` und der NULL-Wert gleichwertig.

## <a name="terminate_handler"></a><a name="terminate_handler"></a>terminate_handler

Der Typ beschreibt einen Zeiger auf eine Funktion, die zur Verwendung als `terminate_handler` geeignet ist.

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Zeiger auf eine Funktion, die zur Verwendung als terminate-Handler geeignet ist.

### <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung von `terminate_handler` finden Sie unter [set_terminate](../standard-library/exception-functions.md#set_terminate).

## <a name="unexpected_handler"></a><a name="unexpected_handler"></a>unexpected_handler

Der Typ beschreibt einen Zeiger auf eine Funktion, die zur Verwendung als `unexpected_handler` geeignet ist.

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung von `unexpected_handler` finden Sie unter [set_unexpected](../standard-library/exception-functions.md#set_unexpected).
