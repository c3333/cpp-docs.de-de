---
title: CAtlException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318996"
---
# <a name="catlexception-class"></a>CAtlException-Klasse

Diese Klasse definiert eine ATL-Ausnahme.

## <a name="syntax"></a>Syntax

```
class CAtlException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|Der Konstruktor.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|Gibt das aktuelle Objekt in einen HRESULT-Wert um.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|Die Variable vom Typ HRESULT, die vom Objekt erstellt und zum Speichern der Fehlerbedingung verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Ein `CAtlException` Objekt stellt eine Ausnahmebedingung dar, die sich auf einen ATL-Vorgang bezieht. Die `CAtlException` Klasse enthält einen öffentlichen Datenmember, der den Statuscode speichert, der den Grund für die Ausnahme angibt, und einen Umwandlungsoperator, mit dem Sie die Ausnahme wie ein HRESULT behandeln können.

Im Allgemeinen rufen `AtlThrow` Sie ein `CAtlException` Objekt auf, anstatt es direkt zu erstellen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Der Konstruktor.

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parameter

*Hr*<br/>
Der HRESULT-Fehlercode.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::operator HRESULT

Gibt das aktuelle Objekt in einen HRESULT-Wert um.

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException::m_hr

Das HRESULT-Datenelement.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Bemerkungen

Das Datenelement, das die Fehlerbedingung speichert. Der HRESULT-Wert wird vom Konstruktor [CAtlException::CAtlException](#catlexception)festgelegt.

## <a name="see-also"></a>Siehe auch

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
