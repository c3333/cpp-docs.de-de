---
title: CDataSource-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: f94cd631f1c6febdc07d53f84803b1203f4116bc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502539"
---
# <a name="cdatasource-class"></a>CDataSource-Klasse

Entspricht einem OLE DB-Datenquellen Objekt, das eine Verbindung über einen Anbieter mit einer Datenquelle darstellt.

## <a name="syntax"></a>Syntax

```cpp
class CDataSource
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[Schließen](#close)|Schließen der Verbindung.|
|[GetInitializationString](#getinitializationstring)|Ruft die Initialisierungs Zeichenfolge der Datenquelle ab, die derzeit geöffnet ist.|
|[GetProperties](#getproperties)|Ruft die Werte der Eigenschaften ab, die derzeit für die verbundene Datenquelle festgelegt sind.|
|[GetProperty](#getproperty)|Ruft den Wert einer einzelnen Eigenschaft ab, die derzeit für die verbundene Datenquelle festgelegt ist.|
|[Öffnen](#open)|Erstellt eine Verbindung mit einem Anbieter (Datenquelle) mithilfe `CLSID` `ProgID` von, oder einem `CEnumerator` Moniker, der vom Aufrufer bereitgestellt wird.|
|[OpenFromFileName](#openfromfilename)|Öffnet eine Datenquelle aus einer Datei, die durch den vom Benutzer bereitgestellten Dateinamen angegeben wird.|
|[OpenFromInitializationString](#openfrominitializationstring)|Öffnet die Datenquelle, die durch eine Initialisierungs Zeichenfolge angegeben wird.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Ermöglicht es dem Benutzer, eine zuvor erstellte Daten Verknüpfungs Datei auszuwählen, um die entsprechende Datenquelle zu öffnen.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Öffnet ein Datenquellen Objekt mit dem Dialogfeld Daten Link.|

## <a name="remarks"></a>Bemerkungen

Eine oder mehrere Daten Bank Sitzungen können für eine einzelne Verbindung erstellt werden. Diese Sitzungen werden durch dargestellt `CSession` . Sie müssen [CDataSource:: Open](#open) abrufen, um die Verbindung zu öffnen, bevor Sie eine Sitzung mit erstellen `CSession::Open` .

Ein Beispiel für die Verwendung von finden Sie unter Beispiel für die Verwendung von `CDataSource` . [CatDB](../../overview/visual-cpp-samples.md)

## <a name="cdatasourceclose"></a><a name="close"></a> CDataSource:: Close

Schließt die Verbindung, indem der Zeiger freigegeben wird `m_spInit` .

### <a name="syntax"></a>Syntax

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a> CDataSource:: getinitializationstring

Ruft die Initialisierungs Zeichenfolge einer Datenquelle ab, die derzeit geöffnet ist.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Parameter

*pinitializationstring*<br/>
vorgenommen Ein Zeiger auf die Initialisierungs Zeichenfolge.

*bincludepassword*<br/>
[in] **`true`** Wenn die Zeichenfolge ein Kennwort enthält; andernfalls **`false`** .

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Die resultierende Initialisierungs Zeichenfolge kann verwendet werden, um diese Datenquellen Verbindung später erneut zu öffnen.

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a> CDataSource:: GetProperties

Gibt die für das verbundene Datenquellen Objekt angeforderten Eigenschaften Informationen zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Parameter

Siehe [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) in der *OLE DB Programmierer-Referenz* im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Um eine einzelne Eigenschaft zu erhalten, verwenden Sie [GetProperty](#getproperty).

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a> CDataSource:: GetProperty

Gibt den Wert einer angegebenen Eigenschaft für das verbundene Datenquellen Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die den Eigenschaften Satz identifiziert, für den die Eigenschaft zurückgegeben werden soll.

*PROPID*<br/>
in Die eigen schafts-ID für die zurück zugebende Eigenschaft.

*pvariant*<br/>
vorgenommen Ein Zeiger auf die Variante, bei `GetProperty` der den Wert der-Eigenschaft zurückgibt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie " [GetProperties](#getproperties)", um mehrere Eigenschaften zu erhalten.

## <a name="cdatasourceopen"></a><a name="open"></a> CDataSource:: Open

Öffnet eine Verbindung mit einer Datenquelle mit einem- `CLSID` ,- `ProgID` oder- `CEnumerator` Moniker oder fordert den Benutzer zu einem Serverlocatorpunkt-Dialogfeld auf.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>Parameter

*CLSID*<br/>
in Der `CLSID` des Datenanbieters.

*pPropSet*<br/>
in Ein Zeiger auf ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, das Eigenschaften und Werte enthält, die festgelegt werden sollen. Informationen zu [Eigenschafts Sätzen und Eigenschafts Gruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz* im Windows SDK.

*nPropertySets*<br/>
in Die Anzahl von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die im *ppropset* -Argument übergeben werden.

*pName*<br/>
[in] Der Name der Datenbank, zu der eine Verbindung hergestellt werden soll.

*pusername*<br/>
[in] Der Name des Benutzers.

*pPassword*<br/>
[in] Das Benutzerkennwort.

*ninitmode*<br/>
[in] Initialisierungsmodus der Datenbank. Eine Liste gültiger Initialisierungs Modi finden Sie unter [Initialisierungs Eigenschaften](/previous-versions/windows/desktop/ms723127(v=vs.85))in der *OLE DB-Programmier Referenz* im Windows SDK. Wenn *ninitmode* gleich NULL ist, ist kein Initialisierungs Modus im Eigenschaften Satz enthalten, der zum Öffnen der Verbindung verwendet wird.

*szprogid*<br/>
[in] Ein Programmbezeichner.

*Enumerator*<br/>
in Ein [cenenumerator](../../data/oledb/cenumerator-class.md) -Objekt, das zum Abrufen eines Monikers zum Öffnen der Verbindung verwendet wird, wenn der Aufrufer keinen angibt `CLSID` .

*hWnd*<br/>
[in] Handle für das Fenster, das als das übergeordnete Element des Dialogfelds festgelegt werden soll. Wenn Sie die Funktions Überladung verwenden, die den *HWND* -Parameter verwendet, werden automatisch Dienst Komponenten aufgerufen. Weitere Informationen finden Sie in den hinweisen.

*dwpromptoptions*<br/>
[in] Bestimmt den Stil des anzuzeigenden Locatordialogfelds. Mögliche Werte sind in Msdasc.h aufgeführt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Die-Methoden Überladung, die den *HWND* -Parameter verwendet, öffnet ein Datenquellen Objekt mit den Dienst Komponenten in oledb32.dll; Diese DLL enthält die Implementierung von Dienst Komponenten Features wie z. b. Ressourcen Pooling, automatische Transaktions Eintragung usw. Weitere Informationen finden Sie in der OLE DB-Referenz im [OLE DB Programmierer-Handbuch](/previous-versions/windows/desktop/ms713643(v=vs.85)).

Die Methoden Überladungen, die den *HWND* -Parameter nicht verwenden, öffnen ein Datenquellen Objekt, ohne die Dienst Komponenten in oledb32.dll zu verwenden. Ein [CDataSource](../../data/oledb/cdatasource-class.md) -Objekt, das mit diesen Funktions Überladungen geöffnet wird, kann keine der Funktionen von Dienst Komponenten nutzen.

### <a name="example"></a>Beispiel

Der folgende Code zeigt, wie eine Jet 4.0-Datenquelle mit OLE DB-Vorlagen geöffnet werden kann. Die Jet-Datenquelle wird OLE DB-Datenquelle behandelt. Der-Befehl benötigt jedoch `Open` zwei Eigenschaften Sätze: einen für DBPROPSET_DBINIT und den anderen für DBPROPSET_JETOLEDB_DBINIT, sodass Sie DBPROP_JETOLEDB_DATABASEPASSWORD festlegen können.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a> CDataSource:: openfromfilename

Öffnet eine Datenquelle aus einer Datei, die durch den vom Benutzer bereitgestellten Dateinamen angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Parameter

*szFilename*<br/>
[in] Der Name einer Datei, in der Regel eine Datenquellenverbindungsdatei (UDL-Datei).

Weitere Informationen zu Daten Verknüpfungs Dateien (UDL-Dateien) finden Sie unter Übersicht über die [Daten Link-API](/previous-versions/windows/desktop/ms718102(v=vs.85)) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet ein Datenquellenobjekt mit den Dienstkomponenten im oledb32.dll; Diese DLL enthält die Implementierung von Dienstkomponentenfeatures wie z. B. Ressourcenpooling, automatische Transaktionseintragung usw. Weitere Informationen finden Sie in der OLE DB-Referenz im [OLE DB Programmierer-Handbuch](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a> CDataSource:: OpenFromInitializationString

Öffnet eine Datenquelle, die von der vom Benutzer bereitgestellten Initialisierungs Zeichenfolge angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Parameter

*szinitializationstring*<br/>
in Die Initialisierungs Zeichenfolge.

*"f promptforinfo"*<br/>
in Wenn dieses Argument auf festgelegt ist **`true`** , `OpenFromInitializationString` wird die DBPROP_INIT_PROMPT-Eigenschaft auf DBPROMPT_COMPLETEREQUIRED festgelegt, wodurch angegeben wird, dass der Benutzer nur aufgefordert wird, wenn weitere Informationen benötigt werden. Dies ist nützlich für Situationen, in denen die Initialisierungs Zeichenfolge eine Datenbank angibt, für die ein Kennwort erforderlich ist, aber die Zeichenfolge nicht das Kennwort enthält. Wenn Sie versuchen, eine Verbindung mit der Datenbank herzustellen, wird der Benutzer zur Eingabe eines Kennworts (oder anderer fehlender Informationen) aufgefordert.

Der Standardwert ist. **`false`** dieser gibt an, dass der Benutzer nie aufgefordert wird (legt DBPROP_INIT_PROMPT auf DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet ein Datenquellenobjekt mit den Dienstkomponenten im oledb32.dll; Diese DLL enthält die Implementierung von Dienstkomponentenfeatures wie z. B. Ressourcenpooling, automatische Transaktionseintragung usw.

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a> CDataSource:: openwithpromptfilename

Mit dieser Methode wird dem Benutzer ein Dialogfeld angezeigt und anschließend eine Datenquelle mithilfe der vom Benutzer angegebenen Datei geöffnet.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Parameter

*hWnd*<br/>
[in] Handle für das Fenster, das als das übergeordnete Element des Dialogfelds festgelegt werden soll.

*dwpromptoptions*<br/>
[in] Bestimmt den Stil des anzuzeigenden Locatordialogfelds. Mögliche Werte sind in Msdasc.h aufgeführt.

*szInitialDirectory*<br/>
[in] Das im Locatordialogfeld anzuzeigende Ausgangsverzeichnis.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet ein Datenquellenobjekt mit den Dienstkomponenten im oledb32.dll; Diese DLL enthält die Implementierung von Dienstkomponentenfeatures wie z. B. Ressourcenpooling, automatische Transaktionseintragung usw. Weitere Informationen finden Sie in der OLE DB-Referenz im [OLE DB Programmierer-Handbuch](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a> CDataSource:: openwithservicecomponents

Öffnet ein Datenquellenobjekt mithilfe der Dienstkomponenten in „oledb32.dll“.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>Parameter

*CLSID*<br/>
in Der `CLSID` eines Datenanbieters.

*szprogid*<br/>
[in] Programm-ID eines Datenanbieters.

*ppropset*<br/>
in Ein Zeiger auf ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, das Eigenschaften und Werte enthält, die festgelegt werden sollen. Informationen zu [Eigenschafts Sätzen und Eigenschafts Gruppen](/previous-versions/windows/desktop/ms713696(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz* im Windows SDK. Wenn das Datenquellenobjekt initialisiert wird, müssen die Eigenschaften zur Eigenschaftsquelle „Datenquelle“ gehören. Wenn die gleiche Eigenschaft in *ppropset*mehrmals angegeben wird, ist der verwendete Wert Anbieter spezifisch. Wenn *ulpropsets* NULL ist, wird dieser Parameter ignoriert.

*ulpropsets*<br/>
in Die Anzahl von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die im *ppropset* -Argument übergeben werden. Wenn dieser Wert 0 (null) ist, ignoriert der Anbieter *ppropset*.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Methode öffnet ein Datenquellenobjekt mit den Dienstkomponenten im oledb32.dll; Diese DLL enthält die Implementierung von Dienstkomponentenfeatures wie z. B. Ressourcenpooling, automatische Transaktionseintragung usw. Weitere Informationen finden Sie in der OLE DB-Referenz im [OLE DB Programmierer-Handbuch](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
