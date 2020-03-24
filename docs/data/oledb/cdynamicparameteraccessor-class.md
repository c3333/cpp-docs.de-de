---
title: CDynamicParameterAccessor-Klasse
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: 9c326c337ff210ef9de26b3fd88c0d853832b260
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211867"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor-Klasse

Ähnlich wie [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) , ruft festzulegende Parameterinformationen aber durch Aufrufen der [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) -Schnittstelle ab.

## <a name="syntax"></a>Syntax

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|Der Konstruktor.|
|[GetParam](#getparam)|Ruft die Parameterdaten aus dem Puffer ab.|
|[GetParamCount](#getparamcount)|Ruft die Anzahl von Parametern im Accessor ab.|
|[GetParamIO](#getparamio)|Ermittelt, ob der angegebene Parameter ein Eingabe- oder ein Ausgabeparameter ist.|
|[GetParamLength](#getparamlength)|Ruft die Länge des angegebenen Parameters ab, der im Puffer gespeichert ist.|
|[GetParamName](#getparamname)|Ruft den Namen eines angegebenen Parameters ab.|
|[GetParamStatus](#getparamstatus)|Ruft den Status des angegebenen Parameters ab, der im Puffer gespeichert ist.|
|[GetParamString](#getparamstring)|Ruft die Zeichenfolgendaten Status des angegebenen Parameters ab, der im Puffer gespeichert ist.|
|[GetParamType](#getparamtype)|Ruft den Datentyp eines angegebenen Parameters ab.|
|[SetParam](#setparam)|Verwendet die Parameterdaten, um den Puffer festzulegen.|
|[SetParamLength](#setparamlength)|Legt die Länge des angegebenen Parameters fest, der im Puffer gespeichert ist.|
|[SetParamStatus](#setparamstatus)|Legt den Status des angegebenen Parameters fest, der im Puffer gespeichert ist.|
|[SetParamString](#setparamstring)|Legt die Zeichenfolgendaten des angegebenen Parameters fest, der im Puffer gespeichert ist.|

## <a name="remarks"></a>Bemerkungen

Der Anbieter muss `ICommandWithParameters` unterstützen, damit der Consumer diese Klasse verwenden kann.

Die Parameterinformationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Sie rufen Parameterdaten aus dem Puffer ab, indem Sie [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) und [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)verwenden.

Ein Beispiel für die Verwendung dieser Klasse zum Ausführen einer SQL Server gespeicherten Prozedur und zum Ermitteln der Ausgabeparameter Werte finden Sie im Beispielcode [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) im [Microsoft vcsamples](https://github.com/Microsoft/VCSamples) -Repository auf GitHub.

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a>CDynamicParameterAccessor:: CDynamicParameterAccessor

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>Parameter

*eblobhandling*<br/>
Gibt an, wie die BLOB-Daten verarbeitet werden sollen. Der Standardwert ist DBBLOBHANDLING_DEFAULT. Unter [CDynamicAccessor:: setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) finden Sie eine Beschreibung der dbblobhandlingenum-Werte.

*nblobsize*<br/>
Die maximale BLOB-Größe in Bytes. Spaltendaten über diesen Wert werden als BLOB behandelt. Der Standardwert ist 8.000. Weitere Informationen finden Sie unter [CDynamicAccessor:: setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) .

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur BLOB-Behandlung finden Sie im [CDynamicAccessor:: CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) -Konstruktor.

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a>CDynamicParameterAccessor:: GetParam

Ruft die nicht-Zeichen folgen Daten für einen angegebenen Parameter aus dem Parameter Puffer ab.

### <a name="syntax"></a>Syntax

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>Parameter

*ctype*<br/>
Ein Vorlagen Parameter, bei dem es sich um den-Datentyp handelt.

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pparamname*<br/>
in Der Parameter Name.

*pData*<br/>
vorgenommen Der Zeiger auf den Arbeitsspeicher, der die Daten enthält, die aus dem Puffer abgerufen wurden.

### <a name="return-value"></a>Rückgabewert

Für nicht auf Vorlagen basierende Versionen verweist auf den Speicher, der die aus dem Puffer abgerufenen Daten enthält. Bei Vorlagen Versionen wird bei Fehler **true** oder **false** zurückgegeben.

Verwenden Sie `GetParam`, um nicht-Zeichenfolge-Parameterdaten aus dem Puffer abzurufen. Verwenden Sie [getparamstring](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) , um Zeichen folgen Parameterdaten aus dem Puffer abzurufen.

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a>CDynamicParameterAccessor:: getparamcount

Ruft die Anzahl der im Puffer gespeicherten Parameter ab.

### <a name="syntax"></a>Syntax

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Parameter.

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a>CDynamicParameterAccessor:: getparamio

Ermittelt, ob der angegebene Parameter ein Eingabe- oder ein Ausgabeparameter ist.

### <a name="syntax"></a>Syntax

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pparamio*<br/>
Ein Zeiger auf die Variable, die den `DBPARAMIO` Typ (Eingabe oder Ausgabe) des angegebenen Parameters enthält. Nachfolgend ist diese Definition gezeigt:

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a>CDynamicParameterAccessor:: getparamlength

Ruft die Länge des angegebenen Parameters ab, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pLength*<br/>
vorgenommen Ein Zeiger auf die Variable, die die Länge des angegebenen Parameters in Bytes enthält.

### <a name="remarks"></a>Bemerkungen

Die erste außer Kraft Setzung gibt bei Erfolg **true** oder **false** zurück. Die zweite außer Kraft Setzung verweist auf den Arbeitsspeicher, der die Länge des Parameters enthält.

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a>CDynamicParameterAccessor:: getparamname

Ruft den Namen des angegebenen Parameters ab.

### <a name="syntax"></a>Syntax

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

### <a name="return-value"></a>Rückgabewert

Der Name des angegebenen Parameters.

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a>CDynamicParameterAccessor:: getparamstatus

Ruft den Status des angegebenen Parameters ab, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pstatus*<br/>
vorgenommen Ein Zeiger auf die Variable, die den DBStatus-Status des angegebenen Parameters enthält. Informationen zu DBStatus-Werten finden Sie unter [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz*, oder suchen Sie in der Datei "OleDb. h" nach DBStatus.

### <a name="remarks"></a>Bemerkungen

Die erste außer Kraft Setzung gibt bei Erfolg **true** oder **false** zurück. Die zweite außer Kraft Setzung verweist auf den Speicher, der den Status des angegebenen Parameters enthält.

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a>CDynamicParameterAccessor:: getparamstring

Ruft die Zeichenfolgendaten Status des angegebenen Parameters ab, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*stroutput*<br/>
vorgenommen Die ANSI (`CSimpleStringA`)-oder Unicode-Zeichen folgen Daten des angegebenen Parameters (`CSimpleStringW`). Übergeben Sie einen Parameter vom Typ `CString`, z. b.:

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
vorgenommen Ein Zeiger auf die ANSI (**char**)-oder Unicode (**WCHAR**)-Zeichen folgen Daten des angegebenen Parameters.

*pmaxlen*<br/>
vorgenommen Ein Zeiger auf die Größe des Puffers, auf den von *pbuffer* verwiesen wird (in Zeichen, einschließlich des abschließenden NULL-Zeichens).

### <a name="remarks"></a>Bemerkungen

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

Wenn *pbuffer* den Wert NULL hat, legt diese Methode die erforderliche Puffergröße im Speicher fest, auf den *pmaxlen* zeigt, und gibt **true** zurück, ohne die Daten zu kopieren.

Diese Methode schlägt fehl, wenn der Puffer *pbuffer* nicht groß genug ist, um die gesamte Zeichenfolge zu enthalten.

Verwenden Sie `GetParamString`, um Zeichen folgen Parameterdaten aus dem Puffer abzurufen. Verwenden Sie [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) , um nicht-Zeichenfolge-Parameterdaten aus dem Puffer abzurufen.

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a>CDynamicParameterAccessor:: GetParamType

Ruft den Datentyp eines angegebenen Parameters ab.

### <a name="syntax"></a>Syntax

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pType*<br/>
vorgenommen Ein Zeiger auf die Variable, die den Datentyp des angegebenen Parameters enthält.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a>CDynamicParameterAccessor:: SetParam

Legt den Parameter Puffer mithilfe der angegebenen Daten (nicht-Zeichenfolge) fest.

### <a name="syntax"></a>Syntax

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parameter

*ctype*<br/>
Ein Vorlagen Parameter, bei dem es sich um den-Datentyp handelt.

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Beispiel:

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pparamname*<br/>
in Der Parameter Name.

*pData*<br/>
in Der Zeiger auf den Arbeitsspeicher, der die Daten enthält, die in den Puffer geschrieben werden sollen.

*status*<br/>
in Der Status der DBStatus-Spalte. Informationen zu DBStatus-Werten finden Sie unter [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz*, oder suchen Sie in der Datei "OleDb. h" nach DBStatus.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

Verwenden Sie `SetParam`, um nicht-Zeichen folgen Parameterdaten im Puffer festzulegen. Verwenden Sie [setparamstring](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) , um Zeichen folgen Parameterdaten im Puffer festzulegen.

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a>CDynamicParameterAccessor:: setparamlength

Legt die Länge des angegebenen Parameters fest, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*length*<br/>
in Die Länge des angegebenen Parameters in Byte.

### <a name="remarks"></a>Bemerkungen

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a>CDynamicParameterAccessor:: setparamstatus

Legt den Status des angegebenen Parameters fest, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*status*<br/>
in Der DBStatus-Status des angegebenen Parameters. Informationen zu DBStatus-Werten finden Sie unter [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz*, oder suchen Sie in der Datei "OleDb. h" nach DBStatus.

### <a name="remarks"></a>Bemerkungen

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a>CDynamicParameterAccessor:: setparamstring

Legt die Zeichenfolgendaten des angegebenen Parameters fest, der im Puffer gespeichert ist.

### <a name="syntax"></a>Syntax

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parameter

*nparam*<br/>
in Die Parameter Nummer (Offset von 1). Der Parameter 0 ist für Rückgabewerte reserviert. Die Parameter Nummer ist der Index des Parameters, der auf der Reihenfolge des SQL-oder gespeicherten Prozedur Aufrufes basiert. Ein Beispiel finden Sie unter [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pstring*<br/>
in Ein Zeiger auf die ANSI (**char**)-oder Unicode (**WCHAR**)-Zeichen folgen Daten des angegebenen Parameters. Siehe DBStatus in "OleDb. h".

*status*<br/>
in Der DBStatus-Status des angegebenen Parameters. Informationen zu DBStatus-Werten finden Sie unter [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz*, oder suchen Sie in der Datei "OleDb. h" nach DBStatus.

### <a name="remarks"></a>Bemerkungen

Gibt bei Erfolg **true** oder **false** bei einem Fehler zurück.

`SetParamString` schlägt fehl, wenn Sie versuchen, eine Zeichenfolge festzulegen, die größer als die für *pstring*angegebene maximale Größe ist.

Verwenden Sie `SetParamString`, um Zeichen folgen Parameterdaten im Puffer festzulegen. Verwenden Sie [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) , um nicht-Zeichen folgen Parameterdaten im Puffer festzulegen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor-Klasse](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor-Klasse](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor-Klasse](../../data/oledb/cmanualaccessor-class.md)
