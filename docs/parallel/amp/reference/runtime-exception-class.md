---
title: runtime_exception-Klasse
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336798"
---
# <a name="runtime_exception-class"></a>runtime_exception-Klasse

Der Basistyp für Ausnahmen in der C++ Accelerated Massive Parallelism (AMP)-Bibliothek.

### <a name="syntax"></a>Syntax

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[runtime_exception Konstruktor](#ctor)|Initialisiert eine neue Instanz der Klasse `runtime_exception`.|
|[Runtime_exception Destruktor](#dtor)|Zerstört das `runtime_exception`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get_error_code](#get_error_code)|Gibt den Fehlercode zurück, der die Ausnahme verursacht hat.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator=](#operator_eq)|Kopiert den Inhalt des angegebenen `runtime_exception`-Objekts in dieses Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`exception`

`runtime_exception`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** amprt.h

**Namespace:** Parallelität

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>runtime_exception Konstruktor

Initialisiert eine neue Instanz der Klasse.

### <a name="syntax"></a>Syntax

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parameter

*_Message*<br/>
Eine Beschreibung des Fehlers, das diese Ausnahme verursacht hat.

*_Hresult*<br/>
Der HRESULT-Wert des Fehlers, der diese Ausnahme verursacht hat.

*_Other*<br/>
Das zu kopierende `runtime_exception`-Objekt.

### <a name="return-value"></a>Rückgabewert

Das `runtime_exception`-Objekt.

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>Runtime_exception Destruktor

Zerstört das Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

Gibt den Fehlercode zurück, der die Ausnahme verursacht hat.

### <a name="syntax"></a>Syntax

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der HRESULT-Wert des Fehlers, der diese Ausnahme verursacht hat.

## <a name="operator"></a><a name="operator_eq"></a>Operator=

Kopiert den Inhalt des angegebenen `runtime_exception`-Objekts in dieses Objekt.

### <a name="syntax"></a>Syntax

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das zu kopierende `runtime_exception`-Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `runtime_exception`-Objekt.

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
