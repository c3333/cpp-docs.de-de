---
title: RoInitializeWrapper-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371226"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper-Klasse

Initialisiert die Windows-Runtime.

## <a name="syntax"></a>Syntax

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Bemerkungen

`RoInitializeWrapper`ist eine Bequemlichkeit, die die Windows-Runtime initialisiert und ein HRESULT zurückgibt, das angibt, ob der Vorgang erfolgreich war. Da der Klassendestruktor `::Windows::Foundation::Uninitialize` `RoInitializeWrapper` aufrufe, müssen Instanzen von im globalen oder obersten Bereich deklariert werden.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                                    | BESCHREIBUNG
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Initialisiert eine neue Instanz der Klasse `RoInitializeWrapper`.
[RoInitializeWrapper::'RoInitializeWrapper](#tilde-roinitializewrapper) | Zerstört die aktuelle Instanz `RoInitializeWrapper` der Klasse.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                       | BESCHREIBUNG
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Ruft das vom `RoInitializeWrapper` Konstruktor erstellte HRESULT ab.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`RoInitializeWrapper`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>RoInitializeWrapper::HRESULT()

Ruft den Vom letzten `RoInitializeWrapper` Konstruktor erzeugten HRESULT-Wert ab.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Initialisiert eine neue Instanz der Klasse `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parameter

*Flaggen*<br/>
Eine der RO_INIT_TYPE-Enumerationen, die die unterstützungsmittelbestimmt angibt, die von der Windows-Runtime bereitgestellt wird.

### <a name="remarks"></a>Bemerkungen

Die `RoInitializeWrapper` Klasse `Windows::Foundation::Initialize(flags)`ruft auf .

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::'RoInitializeWrapper

Die Initialisierung der Windows-Runtime wird nicht mehr verwendet.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Bemerkungen

Die `RoInitializeWrapper` Klasse `Windows::Foundation::Uninitialize()`ruft auf .
