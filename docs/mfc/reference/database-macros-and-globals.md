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
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426270"
---
# <a name="database-macros-and-globals"></a>Datenbankmakros und globale Variablen

Die unten aufgeführten Makros und Globals gelten für ODBC-basierte Datenbankanwendungen. Sie werden nicht mit DAO-basierten Anwendungen verwendet.

Vor MFC 4,2 haben die Makros `AFX_SQL_ASYNC` und `AFX_SQL_SYNC` den asynchronen Vorgängen die Möglichkeit gegeben, Zeit für andere Prozesse zu liefern. Ab MFC 4,2 hat sich die Implementierung dieser Makros geändert, da die MFC-ODBC-Klassen nur synchrone Vorgänge verwendeten. Das Makro `AFX_ODBC_CALL` war neu in MFC 4,2.

### <a name="database-macros"></a>Daten Bank Makros

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Ruft eine ODBC-API-Funktion auf, die `SQL_STILL_EXECUTING`zurückgibt. `AFX_ODBC_CALL` Ruft die Funktion wiederholt auf, bis Sie `SQL_STILL_EXECUTING`nicht mehr zurückgibt.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Ruft `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Ruft eine ODBC-API-Funktion auf, die `SQL_STILL_EXECUTING`nicht zurückgibt.|

### <a name="database-globals"></a>Daten Bank Globals

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Fügt eine Datenbankunterstützung für eine reguläre MFC-DLL hinzu, die dynamisch mit MFC verknüpft ist.|
|[AFXGetHENV](#afxgethenv)|Ruft ein Handle für die ODBC-Umgebung ab, die derzeit von MFC verwendet wird. Sie können dieses Handle in direkten ODBC-Aufrufen verwenden.|

## <a name="afxdbinitmodule"></a>AfxDbInitModule

Fügen Sie für MFC-Datenbankunterstützung (oder DAO) eine reguläre MFC-DLL hinzu, die dynamisch mit MFC verknüpft ist, und fügen Sie in der `CWinApp::InitInstance`-Funktion Ihrer regulären MFC-DLL einen-aufrufsbefehl zum Initialisieren der MFC-Datenbank-dll hinzu

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Hinweise

Stellen Sie sicher, dass dieser-Vorgang vor jedem Basisklassen-oder zusätzlichen Code erfolgt, der auf die MFC-Datenbank-dll zugreift. Die MFC-Datenbank-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine `CDynLinkLibrary` Kette eingebunden werden kann, muss Sie ein `CDynLinkLibrary`-Objekt im Kontext jedes Moduls erstellen, das Sie verwenden wird. `AfxDbInitModule` erstellt das `CDynLinkLibrary`-Objekt im regulären Kontext der MFC-DLL, sodass es in die `CDynLinkLibrary`-Objekt Kette der regulären MFC-DLL eingebunden wird.

### <a name="requirements"></a>Voraussetzungen

**Header:** \<afxdll_. h >

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL

Verwenden Sie dieses Makro, um beliebige ODBC-API-Funktionen aufzurufen, die `SQL_STILL_EXECUTING`zurückgeben.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parameter

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Hinweise

`AFX_ODBC_CALL` Ruft die Funktion wiederholt auf, bis Sie `SQL_STILL_EXECUTING`nicht mehr zurückgibt.

Vor dem Aufrufen von `AFX_ODBC_CALL`müssen Sie eine Variable, `nRetCode`, vom Typ "RETCODE" deklarieren.

Beachten Sie, dass die MFC-ODBC-Klassen jetzt nur die synchrone Verarbeitung verwenden. Um einen asynchronen Vorgang auszuführen, müssen Sie die ODBC-API-Funktion `SQLSetConnectOption`abrufen. Weitere Informationen finden Sie im Thema zum asynchronen Ausführen von Funktionen in der Windows SDK.

### <a name="example"></a>Beispiel

In diesem Beispiel wird `AFX_ODBC_CALL` verwendet, um die `SQLColumns` ODBC-API-Funktion aufzurufen, die eine Liste der Spalten in der Tabelle zurückgibt, die von `strTableName`benannt wird. Beachten Sie die Deklaration von `nRetCode` und die Verwendung von Recordset-Datenmembern, um Parameter an die Funktion zu übergeben. Das Beispiel veranschaulicht auch das Überprüfen der Ergebnisse des Aufrufens mit `Check`, einer Member-Funktion der Klasse `CRecordset`. Die Variable `prs` ist ein Zeiger auf ein `CRecordset` Objekt, das an anderer Stelle deklariert wird.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Voraussetzungen

**Header:** AFXDB. h

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC

Die Implementierung dieses Makros wurde in MFC 4,2 geändert.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parameter

*PRS*<br/>
Ein Zeiger auf ein `CRecordset` Objekt oder ein `CDatabase` Objekt. Ab MFC 4,2 wird dieser Parameterwert ignoriert.

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu ODBC-API-Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Hinweise

`AFX_SQL_ASYNC` einfach das Makro [AFX_ODBC_CALL](#afx_odbc_call) aufruft und den *PRS* -Parameter ignoriert. In MFC-Versionen vor 4,2 wurde `AFX_SQL_ASYNC` zum Abrufen von ODBC-API-Funktionen verwendet, die möglicherweise `SQL_STILL_EXECUTING`zurückgeben. Wenn eine ODBC-API-Funktion `SQL_STILL_EXECUTING`zurückgegeben hat, würde `AFX_SQL_ASYNC` `prs->OnWaitForDataSource`aufruft.

> [!NOTE]
>  Die MFC-ODBC-Klassen verwenden jetzt nur die synchrone Verarbeitung. Um einen asynchronen Vorgang auszuführen, müssen Sie die ODBC-API-Funktion `SQLSetConnectOption`abrufen. Weitere Informationen finden Sie im Thema zum asynchronen Ausführen von Funktionen in der Windows SDK.

### <a name="requirements"></a>Voraussetzungen

  **Header** AFXDB. h

##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC

Das `AFX_SQL_SYNC`-Makro ruft einfach die-Funktion `SQLFunc`auf.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parameter

*Sqlfunc*<br/>
Eine ODBC-API-Funktion. Weitere Informationen zu diesen Funktionen finden Sie unter Windows SDK.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Makro, um ODBC-API-Funktionen aufzurufen, die keine `SQL_STILL_EXECUTING`zurückgeben.

Vor dem Aufrufen von `AFX_SQL_SYNC`müssen Sie eine Variable, `nRetCode`, vom Typ "RETCODE" deklarieren. Sie können den Wert von `nRetCode` nach dem Makro-Befehl überprüfen.

Beachten Sie, dass die Implementierung von `AFX_SQL_SYNC` in MFC 4,2 geändert wurde. Da die Überprüfung des Serverstatus nicht mehr erforderlich ist, weist `AFX_SQL_SYNC` `nRetCode`einfach einen Wert zu. Beispielsweise anstelle des Aufrufes

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

Sie können einfach die Zuweisung erstellen.

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Voraussetzungen

  **Header** AFXDB. h

##  <a name="afxgethenv"></a>AFXGetHENV

Sie können das zurückgegebene Handle in direkten ODBC-Aufrufen verwenden, aber Sie dürfen das Handle nicht schließen oder davon ausgehen, dass das Handle weiterhin gültig und verfügbar ist, nachdem alle vorhandenen `CDatabase`-oder `CRecordset`abgeleiteten Objekte zerstört wurden.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Rückgabewert

Das Handle für die ODBC-Umgebung, die zurzeit von MFC verwendet wird. Kann `SQL_HENV_NULL` werden, wenn keine [CDatabase](../../mfc/reference/cdatabase-class.md) -Objekte vorhanden sind und keine [CRecordset](../../mfc/reference/crecordset-class.md) -Objekte verwendet werden.

### <a name="requirements"></a>Voraussetzungen

  **Header** AFXDB. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
