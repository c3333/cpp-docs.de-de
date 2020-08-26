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
ms.openlocfilehash: 0dc53bce8b43677e7fe0aa1787d1adcc16a560c4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837526"
---
# <a name="database-macros-and-globals"></a>Datenbankmakros und globale Variablen

Die unten aufgeführten Makros und Globals gelten für ODBC-basierte Datenbankanwendungen. Sie werden nicht mit DAO-basierten Anwendungen verwendet.

Vor MFC 4,2 haben die Makros `AFX_SQL_ASYNC` und `AFX_SQL_SYNC` asynchrone Vorgänge eine Gelegenheit, anderen Prozessen Zeit zu geben. Ab MFC 4,2 hat sich die Implementierung dieser Makros geändert, da die MFC-ODBC-Klassen nur synchrone Vorgänge verwendeten. Das Makro `AFX_ODBC_CALL` war neu in MFC 4,2.

### <a name="database-macros"></a>Daten Bank Makros

|Name|Beschreibung|
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Ruft eine ODBC-API-Funktion auf, die zurückgibt `SQL_STILL_EXECUTING` . `AFX_ODBC_CALL` Ruft die Funktion wiederholt auf, bis Sie nicht mehr zurückgegeben wird `SQL_STILL_EXECUTING` .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Ruft `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Ruft eine ODBC-API-Funktion auf, die nicht zurückgibt `SQL_STILL_EXECUTING` .|

### <a name="database-globals"></a>Daten Bank Globals

|Name|Beschreibung|
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Fügt eine Datenbankunterstützung für eine reguläre MFC-DLL hinzu, die dynamisch mit MFC verknüpft ist.|
|[AfxGetHENV](#afxgethenv)|Ruft ein Handle für die ODBC-Umgebung ab, die derzeit von MFC verwendet wird. Sie können dieses Handle in direkten ODBC-Aufrufen verwenden.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a> AfxDbInitModule

Fügen Sie für MFC-Datenbankunterstützung (oder DAO) eine reguläre MFC-DLL hinzu, die dynamisch mit MFC verknüpft ist. Fügen Sie dieser Funktion in der regulären MFC-DLL-Funktion einen-Rückruf hinzu, `CWinApp::InitInstance` um die MFC-Datenbank-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Stellen Sie sicher, dass dieser-Vorgang vor jedem Basisklassen-oder zusätzlichen Code erfolgt, der auf die MFC-Datenbank-dll zugreift. Die MFC-Datenbank-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine Kette eingebunden werden `CDynLinkLibrary` kann, muss Sie `CDynLinkLibrary` im Kontext jedes Moduls, das Sie verwenden wird, ein-Objekt erstellen. `AfxDbInitModule` erstellt das `CDynLinkLibrary` -Objekt im regulären MFC-DLL-Kontext, sodass es in die `CDynLinkLibrary` Objekt Kette der regulären MFC-DLL eingebunden wird.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a> AFX_ODBC_CALL

Verwenden Sie dieses Makro, um beliebige ODBC-API-Funktionen aufzurufen, `SQL_STILL_EXECUTING` die zurückgeben können

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parameter

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Bemerkungen

`AFX_ODBC_CALL` Ruft die Funktion wiederholt auf, bis Sie nicht mehr zurückgegeben wird `SQL_STILL_EXECUTING` .

Vor `AFX_ODBC_CALL` dem Aufrufen von müssen Sie eine Variable `nRetCode` vom Typ RETCODE deklarieren.

Beachten Sie, dass die MFC-ODBC-Klassen jetzt nur die synchrone Verarbeitung verwenden. Um einen asynchronen Vorgang auszuführen, müssen Sie die ODBC-API-Funktion aufruft `SQLSetConnectOption` . Weitere Informationen finden Sie im Thema zum asynchronen Ausführen von Funktionen in der Windows SDK.

### <a name="example"></a>Beispiel

In diesem Beispiel `AFX_ODBC_CALL` wird verwendet, um die `SQLColumns` ODBC-API-Funktion aufzurufen, die eine Liste der Spalten in der Tabelle zurückgibt, die von benannt wird `strTableName` . Beachten Sie die Deklaration von `nRetCode` und die Verwendung von Recordset-Datenmembern, um Parameter an die Funktion zu übergeben. Das Beispiel veranschaulicht auch das Überprüfen der Ergebnisse des Aufrufens mit `Check` , einer Member-Funktion der-Klasse `CRecordset` . Die-Variable `prs` ist ein Zeiger auf ein- `CRecordset` Objekt, das an anderer Stelle deklariert wird.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a> AFX_SQL_ASYNC

Die Implementierung dieses Makros wurde in MFC 4,2 geändert.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parameter

*PRS*<br/>
Ein Zeiger auf ein- `CRecordset` Objekt oder ein- `CDatabase` Objekt. Ab MFC 4,2 wird dieser Parameterwert ignoriert.

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Bemerkungen

`AFX_SQL_ASYNC` Ruft einfach das Makro [AFX_ODBC_CALL](#afx_odbc_call) auf und ignoriert den *PRS* -Parameter. In Versionen von MFC vor 4,2 `AFX_SQL_ASYNC` wurde verwendet, um ODBC-API-Funktionen aufzurufen, die möglicherweise zurückgeben `SQL_STILL_EXECUTING` . Wenn eine ODBC-API-Funktion zurückgegeben hat `SQL_STILL_EXECUTING` , wird `AFX_SQL_ASYNC` aufgerufen `prs->OnWaitForDataSource` .

> [!NOTE]
> Die MFC-ODBC-Klassen verwenden jetzt nur die synchrone Verarbeitung. Um einen asynchronen Vorgang auszuführen, müssen Sie die ODBC-API-Funktion aufruft `SQLSetConnectOption` . Weitere Informationen finden Sie im Thema zum asynchronen Ausführen von Funktionen in der Windows SDK.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXDB. h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a> AFX_SQL_SYNC

Das- `AFX_SQL_SYNC` Makro ruft einfach die-Funktion auf `SQLFunc` .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parameter

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu diesen Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um ODBC-API-Funktionen aufzurufen, die nicht zurückgeben `SQL_STILL_EXECUTING` .

Vor `AFX_SQL_SYNC` dem Aufrufen von müssen Sie eine Variable `nRetCode` vom Typ RETCODE deklarieren. Sie können den Wert von nach dem Makro-Befehl überprüfen `nRetCode` .

Beachten Sie, dass sich die Implementierung von `AFX_SQL_SYNC` in MFC 4,2 geändert hat. Da die Überprüfung des Serverstatus nicht mehr erforderlich ist, wird `AFX_SQL_SYNC` von einfach ein Wert zugewiesen `nRetCode` . Beispielsweise anstelle des Aufrufes

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

Sie können einfach die Zuweisung erstellen.

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXDB. h

## <a name="afxgethenv"></a><a name="afxgethenv"></a> AFXGetHENV

Sie können das zurückgegebene Handle in direkten ODBC-Aufrufen verwenden, aber Sie dürfen das Handle nicht schließen oder davon ausgehen, dass das Handle weiterhin gültig und verfügbar ist, nachdem vorhandene `CDatabase` oder von `CRecordset` abgeleitete Objekte zerstört wurden.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die ODBC-Umgebung, die zurzeit von MFC verwendet wird. Kann sein, `SQL_HENV_NULL` Wenn keine [CDatabase](../../mfc/reference/cdatabase-class.md) -Objekte vorhanden sind und keine [CRecordset](../../mfc/reference/crecordset-class.md) -Objekte verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXDB. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
