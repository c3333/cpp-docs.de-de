---
title: IErrorRecordsImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: 40ac0b248e1e90dae29a787d59f6ded9581aca70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210599"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl-Klasse

Implementiert die [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstelle OLE DB und fügt Datensätze zu einem Datenmember ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) vom Typ "-Datenelement" **<** `RecordClass` **>** hinzu und ruft Sie ab.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von `IErrorRecordsImpl`abgeleitete Klasse.

*Recordclass*<br/>
Eine-Klasse, die ein OLE DB Fehler Objekt darstellt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Ruft die Fehlerbeschreibungs-Zeichenfolge aus einem Fehler Daten Satz ab.|
|[GetErrorGUID](#geterrorguid)|Ruft die Fehler-GUID aus einem Fehler Daten Satz ab.|
|[GetErrorHelpContext](#geterrorhelpcontext)|Ruft die Hilfe Kontext-ID aus einem Fehler Daten Satz ab.|
|[GetErrorHelpFile](#geterrorhelpfile)|Ruft den vollständigen Pfadnamen der Hilfedatei aus einem Fehler Daten Satz ab.|
|[GetErrorSource](#geterrorsource)|Ruft den Fehler Quell Code aus einem Fehler Daten Satz ab.|

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[Adderrorrecords](#adderrorrecord)|Fügt dem OLE DB Error-Objekt einen Datensatz hinzu.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Gibt grundlegende Informationen zum Fehler zurück, z. b. den Rückgabecode und die anbieterspezifische Fehlernummer.|
|[GetCustomErrorObject](#getcustomerrorobject)|Gibt einen Zeiger auf eine-Schnittstelle für ein benutzerdefiniertes Fehler Objekt zurück.|
|[GetErrorInfo](#geterrorinfo)|Gibt einen [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstellen Zeiger für den angegebenen Datensatz zurück.|
|[GetErrorParameters](#geterrorparameters)|Gibt die Fehler Parameter zurück.|
|[GetRecordCount](#getrecordcount)|Gibt die Anzahl von Datensätzen im OLE DB Datensatz-Objekt zurück.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_rgErrors](#rgerrors)|Ein Array von Fehler Datensätzen.|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a>IErrorRecordsImpl:: geterrordescriptionstring

Ruft die Fehlerbeschreibungs-Zeichenfolge aus einem Fehler Daten Satz ab.

### <a name="syntax"></a>Syntax

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parameter

*rcurrerror*<br/>
Ein `ERRORINFO` Datensatz in einer `IErrorInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den Fehler beschreibt.

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a>IErrorRecordsImpl:: geterrorguid

Ruft die Fehler-GUID aus einem Fehler Daten Satz ab.

### <a name="syntax"></a>Syntax

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parameter

*rcurrerror*<br/>
Ein `ERRORINFO` Datensatz in einer `IErrorInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf eine GUID für den Fehler.

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a>IErrorRecordsImpl:: geterrorhelpcontext

Ruft die Hilfe Kontext-ID aus einem Fehler Daten Satz ab.

### <a name="syntax"></a>Syntax

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parameter

*rcurrerror*<br/>
Ein `ERRORINFO` Datensatz in einer `IErrorInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Die Hilfe Kontext-ID für den Fehler.

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a>IErrorRecordsImpl:: geterrorhelpfile

Ruft den Pfadnamen der Hilfedatei aus einem Fehler Daten Satz ab.

### <a name="syntax"></a>Syntax

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parameter

*rcurrerror*<br/>
Ein `ERRORINFO` Datensatz in einer `IErrorInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine Zeichenfolge, die den Pfadnamen der Hilfedatei für den Fehler enthält.

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a>IErrorRecordsImpl:: geterrorsource

Ruft den Quellcode ab, der den Fehler von einem Fehler Daten Satz verursacht hat.

### <a name="syntax"></a>Syntax

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parameter

*rcurrerror*<br/>
Ein `ERRORINFO` Datensatz in einer `IErrorInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine Zeichenfolge, die den Quellcode für den Fehler enthält.

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a>IErrorRecordsImpl:: adderrorrecord

Fügt dem OLE DB Error-Objekt einen Datensatz hinzu.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: adderrorrecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>IErrorRecordsImpl:: getbasicerrorinfo

Gibt grundlegende Informationen zum Fehler zurück, z. b. den Rückgabecode und die anbieterspezifische Fehlernummer.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) in der *OLE DB-Programmier Referenz*.

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a>IErrorRecordsImpl:: getcustomerrorobject

Gibt einen Zeiger auf eine-Schnittstelle für ein benutzerdefiniertes Fehler Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a>IErrorRecordsImpl:: GetErrorInfo

Gibt einen [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstellen Zeiger für den angegebenen Datensatz zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parameter

Siehe [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a>IErrorRecordsImpl:: GetErrorParameters

Gibt die Fehler Parameter zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a>IErrorRecordsImpl:: GetRecordCount

Gibt die Anzahl von Datensätzen im OLE DB Datensatz-Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a>IErrorRecordsImpl:: m_rgErrors

Ein Array von Fehler Datensätzen.

### <a name="syntax"></a>Syntax

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
