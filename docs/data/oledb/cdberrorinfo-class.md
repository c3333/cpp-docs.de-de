---
title: CDBErrorInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: d8fa41b3a06acb8f28334658f2494295593b99be
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502517"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo-Klasse

Bietet Unterstützung für die OLE DB Fehler Verarbeitung mithilfe der OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Gibt alle Fehlerinformationen zurück, die in einem Fehler Daten Satz enthalten sind.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Ruft [IErrorRecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) auf, um grundlegende Informationen zum angegebenen Fehler zurückzugeben.|
|[GetCustomErrorObject](#getcustomerrorobject)|Ruft [IErrorRecords:: getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) auf, um einen Zeiger auf eine Schnittstelle für ein benutzerdefiniertes Fehler Objekt zurückzugeben.|
|[GetErrorInfo](#geterrorinfo)|Ruft [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) auf, um einen `IErrorInfo` Schnittstellen Zeiger auf den angegebenen Datensatz zurückzugeben.|
|[GetErrorParameters](#geterrorparameters)|Ruft [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) auf, um die Fehler Parameter zurückzugeben.|
|[GetErrorRecords](#geterrorrecords)|Ruft Fehler Datensätze für das angegebene Objekt ab.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle gibt einen oder mehrere Fehler Datensätze an den Benutzer zurück. Nennen Sie zuerst [CDBErrorInfo:: geterrorrecords](#geterrorrecords) , um die Anzahl der Fehler Datensätze abzurufen. Rufen Sie dann eine der Zugriffs Funktionen (z. b. [CDBErrorInfo:: getallerrorinfo](#getallerrorinfo)) auf, um Fehlerinformationen für jeden Datensatz abzurufen.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a> CDBErrorInfo:: getallerrorinfo

Gibt alle Typen von Fehlerinformationen zurück, die in einem Fehler Daten Satz enthalten sind.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>Parameter

*ulrecordnum*<br/>
in Die null basierte Nummer des Datensatzes, für den Fehlerinformationen zurückgegeben werden sollen.

*lcid*<br/>
in Die Gebiets Schema-ID für die zurück zugegenden Fehlerinformationen.

*pbstrDescription*<br/>
vorgenommen Ein Zeiger auf eine Textbeschreibung des Fehlers oder NULL, wenn das Gebiets Schema nicht unterstützt wird. Siehe Hinweise.

*pbstrausource*<br/>
vorgenommen Ein Zeiger auf eine Zeichenfolge, die den Namen der Komponente enthält, die den Fehler generiert hat.

*pguid*<br/>
vorgenommen Ein Zeiger auf die GUID der Schnittstelle, die den Fehler definiert hat.

*pdwhelpcontext*<br/>
vorgenommen Ein Zeiger auf die Hilfe Kontext-ID für den Fehler.

*pbstrauhelpfile*<br/>
vorgenommen Ein Zeiger auf eine Zeichenfolge, die den Pfad zur Hilfedatei enthält, in der der Fehler beschrieben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich. Weitere Rückgabewerte finden Sie unter [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

### <a name="remarks"></a>Bemerkungen

Der Ausgabewert von *pbstrdescription* wird intern durch Aufrufen von abgerufen `IErrorInfo::GetDescription` , wodurch der Wert auf NULL festgelegt wird, wenn das Gebiets Schema nicht unterstützt wird, oder wenn die beiden folgenden Bedingungen zutreffen:

1. der Wert von *LCID* ist nicht US-Englisch und

1. der Wert von *LCID* entspricht nicht dem Wert, der von GetUserDefaultLCID zurückgegeben wurde.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> CDBErrorInfo:: getbasicerrorinfo

Ruft [IErrorRecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) auf, um grundlegende Informationen zum Fehler zurückzugeben, z. b. den Rückgabecode und die anbieterspezifische Fehlernummer.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) in der *OLE DB-Programmier Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a> CDBErrorInfo:: getcustomerrorobject

Ruft [IErrorRecords:: getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) auf, um einen Zeiger auf eine Schnittstelle für ein benutzerdefiniertes Fehler Objekt zurückzugeben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a> CDBErrorInfo:: GetErrorInfo

Ruft [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) auf, um einen [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) -Schnittstellen Zeiger auf den angegebenen Datensatz zurückzugeben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parameter

Siehe [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a> CDBErrorInfo:: GetErrorParameters

Ruft [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) auf, um die Fehler Parameter zurückzugeben.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a> CDBErrorInfo:: geterrorrecords

Ruft Fehler Datensätze für das angegebene Objekt ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parameter

*Kro*<br/>
in Eine Schnittstelle zu dem Objekt, für das Fehler Datensätze zu erhalten sind.

*IID*<br/>
in Die IID der Schnittstelle, die dem Fehler zugeordnet ist.

*pcrecords*<br/>
vorgenommen Ein Zeiger auf die (eine-basierte) Anzahl von Fehler Datensätzen.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Form der-Funktion, wenn Sie überprüfen möchten, welche Schnittstelle die Fehlerinformationen erhalten soll. Andernfalls verwenden Sie die zweite Form.

## <a name="see-also"></a>Weitere Informationen

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
