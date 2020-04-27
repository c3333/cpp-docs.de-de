---
title: Klasse von "Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168201"
---
# <a name="catlexception-class"></a>Klasse von "Klasse"

Diese Klasse definiert eine ATL-Ausnahme.

## <a name="syntax"></a>Syntax

```cpp
class CAtlException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "".](#catlexception)|Der Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "", "", "HRESULT":](#operator_hresult)|Wandelt das aktuelle-Objekt in einen HRESULT-Wert um.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|["Ception":: m_hr](#m_hr)|Die Variable vom Typ HRESULT, die vom-Objekt erstellt und zum Speichern der Fehlerbedingung verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Ein `CAtlException` -Objekt stellt eine Ausnahme Bedingung dar, die sich auf einen ATL-Vorgang bezieht. Die `CAtlException` -Klasse enthält einen öffentlichen Datenmember, der den Statuscode zur Angabe des Grunds für die Ausnahme und einen Cast Operator speichert, der es Ihnen ermöglicht, die Ausnahme zu behandeln, als ob es sich um ein HRESULT handelt.

Im Allgemeinen wird aufgerufen `AtlThrow` , anstatt ein `CAtlException` -Objekt direkt zu erstellen.

## <a name="requirements"></a>Anforderungen

**Header:** atlexcept. h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>"", "".

Der Konstruktor.

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parameter

*HR*<br/>
Der HRESULT-Fehlercode.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>"", "", "", "HRESULT":

Wandelt das aktuelle-Objekt in einen HRESULT-Wert um.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>"Ception":: m_hr

Der HRESULT-Datenmember.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>Bemerkungen

Der Datenmember, der den Fehlerzustand speichert. Der HRESULT-Wert wird durch den Konstruktor, ["](#catlexception)", "", "", "", ".

## <a name="see-also"></a>Weitere Informationen:

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
