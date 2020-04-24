---
title: Datenbankmakros und globale Variablen
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 6d8bd56c0bfe4f9b35e34d067dd1042ed11066d5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751661"
---
# <a name="database-macros-and-globals"></a>Datenbankmakros und globale Variablen

Die unten aufgeführten Makros und globalen Dateien gelten für ODBC-basierte Datenbankanwendungen. Sie werden nicht mit DAO-basierten Anwendungen verwendet.

Vor MFC 4.2 gaben `AFX_SQL_ASYNC` `AFX_SQL_SYNC` die Makros und asynchronen Operationen die Möglichkeit, anderen Prozessen Zeit zu geben. Ab MFC 4.2 änderte sich die Implementierung dieser Makros, da die MFC-ODBC-Klassen nur synchrone Vorgänge verwendeten. Das `AFX_ODBC_CALL` Makro war neu in MFC 4.2.

### <a name="database-macros"></a>Datenbankmakros

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Ruft eine ODBC-API-Funktion auf, die zurückgibt. `SQL_STILL_EXECUTING` `AFX_ODBC_CALL`ruft die Funktion wiederholt auf, `SQL_STILL_EXECUTING`bis sie nicht mehr zurückgegeben wird.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Ruft `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Ruft eine ODBC-API-Funktion `SQL_STILL_EXECUTING`auf, die nicht zurückgibt.|

### <a name="database-globals"></a>Datenbank-Globals

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Fügt Datenbankunterstützung für eine reguläre MFC-DLL hinzu, die dynamisch mit MFC verknüpft ist.|
|[AfxGetHENV](#afxgethenv)|Ruft ein Handle für die ODBC-Umgebung ab, die derzeit von MFC verwendet wird. Sie können dieses Handle in direkten ODBC-Aufrufen verwenden.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbInitModule

Für MFC-Datenbank (oder DAO) Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft `CWinApp::InitInstance` ist, fügen Sie einen Aufruf zu dieser Funktion in Ihrer regulären MFC-DLL-Funktion hinzu, um die MFC-Datenbank-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Stellen Sie sicher, dass dieser Aufruf vor einem Aufruf der Basisklasse oder einem hinzugefügten Code erfolgt, der auf die MFC-Datenbank-DLL zugreift. Die MFC-Datenbank-DLL ist eine MFC-Erweiterungs-DLL. Damit eine MFC-Erweiterungs-DLL in `CDynLinkLibrary` eine Kette verdrahtet werden kann, muss sie ein `CDynLinkLibrary` Objekt im Kontext jedes Moduls erstellen, das sie verwendet. `AfxDbInitModule`erstellt `CDynLinkLibrary` das Objekt im Kontext Ihrer regulären MFC-DLL, `CDynLinkLibrary` sodass es in die Objektkette der regulären MFC-DLL verdrahtet wird.

### <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

Verwenden Sie dieses Makro, um jede `SQL_STILL_EXECUTING`ODBC-API-Funktion aufzurufen, die zurückgeben kann.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parameter

*SQLFunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie im Windows SDK.

### <a name="remarks"></a>Bemerkungen

`AFX_ODBC_CALL`ruft die Funktion wiederholt auf, bis sie nicht mehr zurückgegeben wird. `SQL_STILL_EXECUTING`

Vor dem `AFX_ODBC_CALL`Aufrufen müssen Sie eine `nRetCode`Variable , vom Typ RETCODE deklarieren.

Beachten Sie, dass die MFC-ODBC-Klassen jetzt nur noch die synchrone Verarbeitung verwenden. Um einen asynchronen Vorgang auszuführen, müssen Sie die `SQLSetConnectOption`ODBC-API-Funktion aufrufen. Weitere Informationen finden Sie im Thema "Ausführen von Funktionen asynchron" im Windows SDK.

### <a name="example"></a>Beispiel

In diesem `AFX_ODBC_CALL` Beispiel `SQLColumns` wird die ODBC-API-Funktion aufzurufen, die `strTableName`eine Liste der Spalten in der Tabelle mit dem Namen . Beachten Sie `nRetCode` die Deklaration und die Verwendung von Recordset-Datenmembern, um Parameter an die Funktion zu übergeben. Das Beispiel veranschaulicht auch das Überprüfen `Check`der Ergebnisse des `CRecordset`Aufrufs mit , einer Memberfunktion der Klasse . Die `prs` Variable ist ein `CRecordset` Zeiger auf ein Objekt, das an anderer Stelle deklariert wird.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

Die Implementierung dieses Makros wurde in MFC 4.2 geändert.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parameter

*Prs*<br/>
Ein Zeiger auf `CRecordset` ein `CDatabase` Objekt oder ein Objekt. Ab MFC 4.2 wird dieser Parameterwert ignoriert.

*SQLFunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie im Windows SDK.

### <a name="remarks"></a>Bemerkungen

`AFX_SQL_ASYNC`ruft einfach das Makro [auf, AFX_ODBC_CALL](#afx_odbc_call) und ignoriert den *prs-Parameter.* In Versionen von MFC vor `AFX_SQL_ASYNC` 4.2 wurde verwendet, um `SQL_STILL_EXECUTING`ODBC-API-Funktionen aufzurufen, die zurückgeben könnten. Wenn eine ODBC-API-Funktion zurückgegeben `SQL_STILL_EXECUTING`wird, würde sie `AFX_SQL_ASYNC` aufrufen. `prs->OnWaitForDataSource`

> [!NOTE]
> Die MFC ODBC-Klassen verwenden jetzt nur noch die synchrone Verarbeitung. Um einen asynchronen Vorgang auszuführen, müssen Sie die `SQLSetConnectOption`ODBC-API-Funktion aufrufen. Weitere Informationen finden Sie im Thema "Ausführen von Funktionen asynchron" im Windows SDK.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

Das `AFX_SQL_SYNC` Makro ruft `SQLFunc`einfach die Funktion auf.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parameter

*SQLFunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu diesen Funktionen finden Sie im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um ODBC-API-Funktionen aufzurufen, die nicht zurückgegeben `SQL_STILL_EXECUTING`werden.

Vor `AFX_SQL_SYNC`dem Aufruf müssen Sie `nRetCode`eine Variable , vom Typ RETCODE deklarieren. Sie können den `nRetCode` Wert von nach dem Makroaufruf überprüfen.

Beachten Sie, `AFX_SQL_SYNC` dass die Implementierung von geändert in MFC 4.2. Da die Überprüfung des Serverstatus `AFX_SQL_SYNC` nicht mehr erforderlich `nRetCode`war, wird einfach ein Wert zu . Anstatt z. B. den Anruf

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

Sie können einfach die Aufgabe

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV

Sie können das zurückgegebene Handle in direkten ODBC-Aufrufen verwenden, aber Sie dürfen das Handle `CDatabase`nicht `CRecordset`schließen oder davon ausgehen, dass das Handle weiterhin gültig und verfügbar ist, nachdem vorhandene - oder abgeleitete Objekte zerstört wurden.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die ODBC-Umgebung, die derzeit von MFC verwendet wird. Kann `SQL_HENV_NULL` sein, wenn keine [CDatabase-Objekte](../../mfc/reference/cdatabase-class.md) und keine [CRecordset-Objekte](../../mfc/reference/crecordset-class.md) verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdb.h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
