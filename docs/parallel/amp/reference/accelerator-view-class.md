---
title: accelerator_view-Klasse
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 0020acfda7b506bf9f0547b9daedff34d80204f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182758"
---
# <a name="accelerator_view-class"></a>accelerator_view-Klasse

Stellt die Abstraktion eines virtuellen Geräts für einen datenparallelen C++ AMP-Beschleuniger dar.

## <a name="syntax"></a>Syntax

```cpp
class accelerator_view;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[accelerator_view-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `accelerator_view`-Klasse.|
|[~ accelerator_view-Dekonstruktor](#dtor)|Zerstört das `accelerator_view`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[create_marker](#create_marker)|Gibt ein future-Objekt zurück, um den Abschluss aller Befehle nachzuverfolgen, die bis jetzt zu diesem `accelerator_view`-Objekt gesendet wurden.|
|[Flächen](#flush)|Sendet alle ausstehenden Befehle, die im `accelerator_view`-Objekt zur Ausführung der Zugriffstaste in die Warteschlange gestellt werden.|
|[get_accelerator](#get_accelerator)|Gibt das `accelerator`-Objekt für das `accelerator_view`-Objekt zurück.|
|[get_is_auto_selection](#get_is_auto_selection)|Gibt einen booleschen Wert zurück, der angibt, ob die Laufzeit automatisch eine entsprechende Zugriffstaste auswählt, wenn das `accelerator_view` Objekt an ein [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)-Objekt übermittelt wird.|
|[get_is_debug](#get_is_debug)|Gibt einen booleschen Wert zurück, der angibt, ob für das `accelerator_view`-Objekt die DEBUG-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.|
|[get_queuing_mode](#get_queuing_mode)|Gibt den Queuingmodus für das `accelerator_view`-Objekt zurück.|
|[get_version](#get_version)|Gibt die Version des `accelerator_view`-Objekts zurück.|
|[Warte](#wait)|Wartet, bis alle an das `accelerator_view`-Objekt gesendeten Befehle abgeschlossen sind.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator! =](#operator_neq)|Vergleicht dieses `accelerator_view` -Objekt mit einem anderen und gibt zurück, **`false`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`true`** .|
|[Operator =](#operator_eq)|Kopiert den Inhalt des angegebenen `accelerator_view`-Objekts in dieses Objekt.|
|[Operator = =](#operator_eq_eq)|Vergleicht dieses `accelerator_view` -Objekt mit einem anderen und gibt zurück, **`true`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`false`** .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[getreten](#accelerator)|Ruft das `accelerator`-Objekt für das `accelerator_view`-Objekt ab.|
|[is_auto_selection](#is_auto_selection)|Ruft einen booleschen Wert ab, der angibt, ob die Laufzeit automatisch eine entsprechende Zugriffstaste auswählt, wenn das- `accelerator_view` Objekt an eine [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)wird.|
|[is_debug](#is_debug)|Ruft einen booleschen Wert ab, der angibt, ob für das `accelerator_view`-Objekt die DEBUG-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.|
|[queuing_mode](#queuing_mode)|Ruft den Queuingmodus für das `accelerator_view`-Objekt ab.|
|[version](#version)|Ruft die Version der Zugriffstaste ab.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`accelerator_view`

### <a name="remarks"></a>Bemerkungen

Ein `accelerator_view`-Objekt stellt eine logische, isolierte Ansicht einer Zugriffstaste dar. Ein einzelnes physisches Berechnungsgerät kann über viele logische, isolierte `accelerator_view`-Objekte verfügen. Jede Zugriffstaste verfügt über ein Standard-`accelerator_view`-Objekt. Zusätzliche `accelerator_view`-Objekte können erstellt werden.

Physische Geräte können für viele Clientthreads freigegeben werden. Clientthreads können dasselbe `accelerator_view`-Objekt einer Zugriffstaste kooperativ verwenden oder jeder Client kann mit einem Berechnungsgerät über ein unabhängiges `accelerator_view`-Objekt zur Abgrenzung gegenüber anderen Clientthreads kommunizieren.

Ein `accelerator_view` Objekt kann einen von zwei [queuing_mode Enumerationsstatus](concurrency-namespace-enums-amp.md#queuing_mode) aufweisen. Wenn der Queuingmodus `immediate` ist, werden Befehle wie `copy` und `parallel_for_each` an das entsprechende Zugriffstastengerät gesendet, sobald sie zum Aufrufer zurückkehren. Wenn der Queuingmodus `deferred` ist, werden solche Befehle in die Warteschlange einer Befehlswarteschlange gestellt, die dem `accelerator_view`-Objekt entspricht. Die Befehle werden erst an das Gerät gesendet, wenn `flush()` aufgerufen wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amprt. h

**Namespace:** Parallelität

## <a name="accelerator"></a><a name="accelerator"></a>getreten

Ruft das Accelerator-Objekt für das accelerator_view Objekt ab.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

Initialisiert eine neue Instanz der accelerator_view-Klasse, indem ein vorhandenes-Objekt kopiert wird `accelerator_view` .

### <a name="syntax"></a>Syntax

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Das zu kopierende `accelerator_view`-Objekt.

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

Gibt ein future-Objekt zurück, um den Abschluss aller Befehle nachzuverfolgen, die bis jetzt zu diesem `accelerator_view`-Objekt gesendet wurden.

### <a name="syntax"></a>Syntax

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Rückgabewert

Ein future-Objekt zum Nachverfolgen des Abschlusses aller Befehle, die bis jetzt zu diesem `accelerator_view`-Objekt gesendet wurden.

## <a name="flush"></a>flush

Sendet alle ausstehenden Befehle, die in accelerator_view die Warteschlange eingereiht wurden, zur Ausführung an die Zugriffstaste.

### <a name="syntax"></a>Syntax

```cpp
void flush();
```

### <a name="return-value"></a>Rückgabewert

Gibt zurück **`void`** .

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

Gibt das Accelerator-Objekt für das accelerator_view Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Rückgabewert

Das Accelerator-Objekt für das accelerator_view Objekt.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

Gibt einen booleschen Wert zurück, der angibt, ob die Laufzeit automatisch eine entsprechende Zugriffstaste auswählt, wenn die accelerator_view an einen [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)-Wert übermittelt wird.

### <a name="syntax"></a>Syntax

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Laufzeit automatisch eine entsprechende Zugriffstaste auswählt. andernfalls **`false`** .

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Gibt einen booleschen Wert zurück, der angibt, ob für das accelerator_view Objekt die Debug-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.

### <a name="syntax"></a>Syntax

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der angibt, ob für das- `accelerator_view` Objekt die Debug-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

Gibt den queuingmodus für das accelerator_view Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Rückgabewert

Der queuingmodus für das- `accelerator_view` Objekt.

## <a name="get_version"></a><a name="get_version"></a>get_version

Gibt die Version der accelerator_view zurück.

### <a name="syntax"></a>Syntax

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version der `accelerator_view`.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

Ruft einen booleschen Wert ab, der angibt, ob die Laufzeit automatisch eine entsprechende Zugriffstaste auswählt, wenn die accelerator_view an einen [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)-Wert übermittelt wird.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Ruft einen booleschen Wert ab, der angibt, ob für das accelerator_view Objekt die Debug-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>Operator! =

Vergleicht dieses accelerator_view Objekt mit einem anderen und gibt zurück, **`false`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`true`** .

### <a name="syntax"></a>Syntax

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Das `accelerator_view` Objekt, das mit diesem verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`false`**, wenn die beiden Objekte identisch sind. andernfalls **`true`** .

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Kopiert den Inhalt des angegebenen accelerator_view Objekts in dieses Objekt.

### <a name="syntax"></a>Syntax

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Das `accelerator_view`-Objekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das geänderte `accelerator_view` Objekt.

## <a name="operator"></a><a name="operator_eq_eq"></a>Operator = =

Vergleicht dieses accelerator_view Objekt mit einem anderen und gibt zurück, **`true`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`false`** .

### <a name="syntax"></a>Syntax

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parameter

*außer*<br/>
Das `accelerator_view` Objekt, das mit diesem verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die beiden Objekte identisch sind. andernfalls **`false`** .

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

Ruft den queuingmodus für das accelerator_view Objekt ab.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Ruft die Version des accelerator_view ab.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

Wartet, bis alle Befehle, die an das accelerator_view Objekt übermittelt wurden, beendet werden.

### <a name="syntax"></a>Syntax

```cpp
void wait();
```

### <a name="return-value"></a>Rückgabewert

Gibt zurück **`void`** .

### <a name="remarks"></a>Bemerkungen

Wenn das [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) ist `immediate` , wird diese Methode sofort zurückgegeben, ohne zu blockieren.

## <a name="accelerator_view"></a><a name="dtor"></a>~ accelerator_view

Zerstört das accelerator_view-Objekt.

### <a name="syntax"></a>Syntax

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
