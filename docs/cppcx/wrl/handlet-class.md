---
title: HandleT-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371466"
---
# <a name="handlet-class"></a>HandleT-Klasse

Stellt ein Handle für ein Objekt dar.

## <a name="syntax"></a>Syntax

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parameter

*HandleTraits*<br/>
Eine Instanz der [HandleTraits-Struktur,](handletraits-structure.md) die gemeinsame Merkmale eines Handles definiert.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name     | BESCHREIBUNG
-------- | -----------------------------
`Traits` | Ein Synonym für `HandleTraits`.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                | BESCHREIBUNG
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Initialisiert eine neue Instanz der Klasse `HandleT`.
[HandleT::-Handlet](#tilde-handlet) | Deinitialisiert eine Instanz `HandleT` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                         | BESCHREIBUNG
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Ordnet das angegebene Handle `HandleT` dem aktuellen Objekt zu.
[HandleT::Schließen](#close)     | Schließt das aktuelle `HandleT`-Objekt.
[HandleT::Detach](#detach)   | Trennt das `HandleT` aktuelle Objekt vom zugrunde liegenden Handle.
[HandleT::Get](#get)         | Ruft den Wert des zugrunde liegenden Handles ab.
[HandleT::IsValid](#isvalid) | Gibt an, `HandleT` ob das aktuelle Objekt ein Handle darstellt.

### <a name="protected-methods"></a>Geschützte Methoden

Name                                     | BESCHREIBUNG
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Schließt das aktuelle `HandleT`-Objekt.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                   | BESCHREIBUNG
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator=](#operator-assign) | Verschiebt den Wert `HandleT` des angegebenen `HandleT` Objekts auf das aktuelle Objekt.

### <a name="protected-data-members"></a>Geschützte Datenmember

Name                        | BESCHREIBUNG
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Enthält das Handle, das `HandleT` durch das Objekt dargestellt wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HandleT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>HandleT::-Handlet

Deinitialisiert eine Instanz `HandleT` der Klasse.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT::Attach

Ordnet das angegebene Handle `HandleT` dem aktuellen Objekt zu.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein Handler.

## <a name="handletclose"></a><a name="close"></a>HandleT::Schließen

Schließt das aktuelle `HandleT`-Objekt.

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Das Handle, das `HandleT` dem Strom zugrunde `HandleT` liegt, wird geschlossen, und der wird auf den ungültigen Zustand festgelegt.

Wenn das Handle nicht ordnungsgemäß geschlossen wird, wird eine Ausnahme im aufrufenden Thread ausgelöst.

## <a name="handletdetach"></a><a name="detach"></a>HandleT::Detach

Trennt das `HandleT` aktuelle Objekt vom zugrunde liegenden Handle.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Rückgabewert

Das zugrunde liegende Handle.

### <a name="remarks"></a>Bemerkungen

Wenn dieser Vorgang abgeschlossen `HandleT` ist, wird der Aktuelle auf den ungültigen Zustand festgelegt.

## <a name="handletget"></a><a name="get"></a>HandleT::Get

Ruft den Wert des zugrunde liegenden Handles ab.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handler.

## <a name="handlethandle_"></a><a name="handle"></a>HandleT::handle_

Enthält das Handle, das `HandleT` durch das Objekt dargestellt wird.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>HandleT::HandleT

Initialisiert eine neue Instanz der Klasse `HandleT`.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein Handler.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert ein `HandleT` Objekt, das kein gültiges Handle für ein Objekt ist. Der zweite Konstruktor `HandleT` erstellt ein neues Objekt aus dem Parameter *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT::InternalClose

Schließt das aktuelle `HandleT`-Objekt.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn `HandleT` der Strom erfolgreich geschlossen wurde; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

`InternalClose()` ist `protected`

## <a name="handletisvalid"></a><a name="isvalid"></a>HandleT::IsValid

Gibt an, `HandleT` ob das aktuelle Objekt ein Handle darstellt.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

**true,** `HandleT` wenn der ein Handle darstellt; andernfalls **false**.

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT::operator=

Verschiebt den Wert `HandleT` des angegebenen `HandleT` Objekts auf das aktuelle Objekt.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein rvalue-Verweis auf ein Handle.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `HandleT` das aktuelle Objekt.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang macht `HandleT` das durch den Parameter *h*angegebene Objekt ungültig.
