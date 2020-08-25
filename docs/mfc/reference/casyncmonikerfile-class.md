---
title: CAsyncMonikerFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: 259d31b9c1e198b326ba616481dbbf5315225546
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845938"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile-Klasse

Stellt Funktionalität für die Verwendung von asynchronen Monikern in ActiveX-Steuerelementen (früher OLE-Steuerelemente) bereit.

## <a name="syntax"></a>Syntax

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CAsyncMonikerFile:: CAsyncMonikerFile](#casyncmonikerfile)|Erstellt ein `CAsyncMonikerFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CAsyncMonikerFile:: Close](#close)|Schließt und gibt alle Ressourcen frei.|
|[CAsyncMonikerFile:: GetBinding](#getbinding)|Ruft einen Zeiger auf die asynchrone Übertragungs Bindung ab.|
|[CAsyncMonikerFile:: getformatetc](#getformatetc)|Ruft das Format der Daten im Stream ab.|
|[CAsyncMonikerFile:: Open](#open)|Öffnet eine Datei asynchron.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CAsyncMonikerFile:: Aufrufs](#createbindstatuscallback)|Erstellt ein COM-Objekt, das implementiert `IBindStatusCallback` .|
|[CAsyncMonikerFile:: getbindinfo](#getbindinfo)|Wird von der OLE-Systembibliothek aufgerufen, um Informationen über den Typ der zu erstellenden Bindung anzufordern.|
|[CAsyncMonikerFile:: GetPriority](#getpriority)|Wird von der OLE-Systembibliothek aufgerufen, um die Priorität der Bindung zu erhalten.|
|[CAsyncMonikerFile:: ondataavailable](#ondataavailable)|Wird aufgerufen, um Daten bereitzustellen, die während der asynchronen Bindungs Vorgänge für den Client verfügbar sind.|
|[CAsyncMonikerFile:: onlowresource](#onlowresource)|Wird aufgerufen, wenn die Ressourcen niedrig sind.|
|[CAsyncMonikerFile:: OnProgress](#onprogress)|Wird aufgerufen, um den Fortschritt beim Herunterladen von Daten anzugeben.|
|[CAsyncMonikerFile:: onstartbinding](#onstartbinding)|Wird aufgerufen, wenn die Bindung gestartet wird.|
|[CAsyncMonikerFile:: onstopbinding](#onstopbinding)|Wird aufgerufen, wenn die asynchrone Übertragung beendet wird.|

## <a name="remarks"></a>Bemerkungen

Wird von [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)abgeleitet, das wiederum von [colestreamfile](../../mfc/reference/colestreamfile-class.md)abgeleitet ist, `CAsyncMonikerFile` die [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) -Schnittstelle verwendet, um asynchron auf einen beliebigen Datenstream zuzugreifen, einschließlich der asynchronen Dateien aus einer URL. Die Dateien können Datenpfad-Eigenschaften von ActiveX-Steuerelementen sein.

Asynchrone Moniker werden hauptsächlich in Internet fähigen Anwendungen und ActiveX-Steuerelementen verwendet, um während der Übertragung von Dateien eine reaktionsfähige Benutzeroberfläche bereitzustellen. Ein gutes Beispiel hierfür ist die Verwendung von [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) , um asynchrone Eigenschaften für ActiveX-Steuerelemente bereitzustellen. Das `CDataPathProperty` Objekt erhält wiederholt einen Rückruf, um die Verfügbarkeit neuer Daten während eines langen Eigenschaften Austauschvorgangs anzugeben.

Weitere Informationen zur Verwendung von asynchronen Monikern und ActiveX-Steuerelementen in Internet Anwendungen finden Sie in den folgenden Artikeln:

- [Internet First-Schritte: asynchrone Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Internet First-Schritte: ActiveX-Steuerelemente](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxole. h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a> CAsyncMonikerFile:: CAsyncMonikerFile

Erstellt ein `CAsyncMonikerFile`-Objekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Bemerkungen

Die-Schnittstelle wird nicht erstellt `IBindHost` . `IBindHost` wird nur verwendet, wenn Sie ihn in der `Open` Member-Funktion bereitstellen.

Eine Beschreibung der- `IBindHost` Schnittstelle finden Sie in der Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a> CAsyncMonikerFile:: Close

Mit dieser Funktion können Sie alle Ressourcen schließen und freigeben.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Kann bei nicht geöffneten oder bereits geschlossenen Dateien aufgerufen werden.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a> CAsyncMonikerFile:: Aufrufs

Erstellt ein COM-Objekt, das implementiert `IBindStatusCallback` .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parameter

*punkcontrolling*<br/>
Ein Zeiger auf den steuernden, der den Wert "unknown" steuert (der äußere `IUnknown` ) oder NULL, wenn keine Aggregation verwendet wird.

### <a name="return-value"></a>Rückgabewert

Wenn der Wert für " *punkcontrolling* " nicht NULL ist, gibt die Funktion einen Zeiger auf den inneren `IUnknown` in einem neuen COM-Objekt zurück `IBindStatusCallback` Wenn `pUnkControlling` NULL ist, gibt die Funktion einen Zeiger auf ein- `IUnknown` Objekt in einem neuen COM-Objekt zurück, das unterstützt `IBindStatusCallback` .

### <a name="remarks"></a>Bemerkungen

`CAsyncMonikerFile` erfordert ein COM-Objekt, das implementiert `IBindStatusCallback` . MFC implementiert ein solches Objekt und kann aggregiert werden. Sie können `CreateBindStatusCallback` überschreiben, um ein eigenes com-Objekt zurückzugeben. Das COM-Objekt kann die Implementierung von MFC durch Aufrufen von `CreateBindStatusCallback` mit dem kontrollierten unbekannten Ihres com-Objekts aggregieren. Com-Objekte, die mit der com-Unterstützung implementiert werden, `CCmdTarget` können den Steuerungs unbekannten mit Abrufen `CCmdTarget::GetControllingUnknown`

Alternativ kann das COM-Objekt durch Aufrufen von an die MFC-Implementierung delegieren `CreateBindStatusCallback( NULL )` .

[CAsyncMonikerFile:: Open](#open) -Aufrufe `CreateBindStatusCallback` .

Weitere Informationen zu asynchronen Monikern und asynchroner Bindung finden Sie in der [ibindstatus-Callback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) -Schnittstelle und in der [Funktionsweise der asynchronen Bindung und Speicherung](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Eine Erläuterung der Aggregation finden Sie unter [Aggregation](/windows/win32/com/aggregation). Alle drei Themen sind im Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a> CAsyncMonikerFile:: getbindinfo

Wird vom Client eines asynchronen Monikers aufgerufen, um den asynchronen Moniker zu informieren, wie er gebunden werden soll.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Rückgabewert

Ruft die Einstellungen für ab `IBindStatusCallBack` . Eine Beschreibung der- `IBindStatusCallback` Schnittstelle finden Sie in der Windows SDK.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung legt fest, dass die Bindung asynchron ist, ein Speichermedium (ein Stream) verwendet und das datenpushmodell verwendet werden soll. Überschreiben Sie diese Funktion, wenn Sie das Verhalten der Bindung ändern möchten.

Ein Grund hierfür wäre das Binden der Verwendung des Data-Pull-Modells anstelle des datenpushmodells. In einem datenpull-Modell wird der Bindungs Vorgang vom Client gesteuert, und der Moniker stellt beim Lesen nur Daten für den Client bereit. Bei einem datenpushmodell steuert der Moniker den asynchronen Bindungs Vorgang und benachrichtigt den Client kontinuierlich, wenn neue Daten verfügbar sind.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a> CAsyncMonikerFile:: GetBinding

Rufen Sie diese Funktion auf, um einen Zeiger auf die asynchrone Übertragungs Bindung abzurufen.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die- `IBinding` Schnittstelle, die beim Beginn der asynchronen Übertragung angegeben wird Gibt NULL zurück, wenn die Übertragung aus irgendeinem Grund nicht asynchron erfolgen kann.

### <a name="remarks"></a>Bemerkungen

Dies ermöglicht es Ihnen, den Datenübertragungs Prozess über die- `IBinding` Schnittstelle zu steuern, z `IBinding::Abort` . b. mit, `IBinding::Pause` und `IBinding::Resume` .

Eine Beschreibung der- `IBinding` Schnittstelle finden Sie in der Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a> CAsyncMonikerFile:: getformatetc

Rufen Sie diese Funktion auf, um das Format der Daten im Stream abzurufen.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Windows-Struktur [Format usw](/windows/win32/api/objidl/ns-objidl-formatetc) . für den aktuell geöffneten Stream. Gibt NULL zurück, wenn der Moniker nicht gebunden wurde, wenn er nicht asynchron ist, oder, wenn der asynchrone Vorgang nicht begonnen wurde.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a> CAsyncMonikerFile:: GetPriority

Wird vom Client eines asynchronen Monikers aufgerufen, da der Bindungsprozess mit dem Empfang der Priorität beginnt, die dem Thread für den Bindungs Vorgang zugewiesen ist.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Rückgabewert

Die Priorität, mit der die asynchrone Übertragung stattfindet. Eines der Standardflags für die Thread Priorität: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL und THREAD_PRIORITY_TIME_CRITICAL. Eine Beschreibung dieser Werte finden Sie unter der Windows-Funktion [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) .

### <a name="remarks"></a>Bemerkungen

`GetPriority` sollte nicht direkt aufgerufen werden. THREAD_PRIORITY_NORMAL wird von der Standard Implementierung zurückgegeben.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a> CAsyncMonikerFile:: ondataavailable

Ein asynchroner Moniker ruft `OnDataAvailable` auf, um dem Client Daten zur Verfügung zu stellen, die während der asynchronen Bindungs Vorgänge verfügbar sind.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parameter

*dwSize*<br/>
Der kumulative Betrag der Daten (in Bytes), die seit dem Anfang der Bindung verfügbar sind. Kann NULL sein, um anzugeben, dass die Datenmenge für den Vorgang nicht relevant ist, oder dass kein bestimmter Betrag verfügbar wurde.

*bscfflag*<br/>
Ein BSCF-Enumerationswert. Kann einen oder mehrere der folgenden Werte aufweisen:

- BSCF_FIRSTDATANOTIFICATION identifiziert den ersten-Aufrufe `OnDataAvailable` für einen angegebenen Bindungs Vorgang.

- BSCF_INTERMEDIATEDATANOTIFICATION identifiziert einen zwischengeschalteten-Rückruf `OnDataAvailable` für einen Bindungs Vorgang.

- BSCF_LASTDATANOTIFICATION identifiziert den letzten- `OnDataAvailable` Aufrufvorgang für einen Bindungs Vorgang.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Im folgenden Beispiel finden Sie eine Beispiel Implementierung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a> CAsyncMonikerFile:: onlowresource

Wird vom Moniker aufgerufen, wenn die Ressourcen niedrig sind.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung ruft auf `GetBinding( )-> Abort( )` .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a> CAsyncMonikerFile:: OnProgress

Wird vom Moniker wiederholt aufgerufen, um den aktuellen Status dieses Bindungs Vorgangs anzugeben, in der Regel in angemessenen Intervallen während eines langwierigen Vorgangs.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parameter

*ulprogress*<br/>
Gibt den aktuellen Status des Bindungs Vorgangs relativ zum erwarteten maximalen Wert an, der in *ulprogressmax*angegeben wird.

*ulprogressmax*<br/>
Gibt den erwarteten maximalen Wert von *ulprogress* für die Dauer von Aufrufen von `OnProgress` für diesen Vorgang an.

*ulstatus Code*<br/>
Stellt zusätzliche Informationen zum Fortschritt des Bindungs Vorgangs bereit. Gültige Werte stammen aus der- `BINDSTATUS` Enumeration. Mögliche Werte finden Sie in den Hinweisen.

*szStatusText*<br/>
Informationen zum aktuellen Status, abhängig vom Wert von *ulstatuscode*. Mögliche Werte finden Sie in den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Mögliche Werte für *ulstatucode* (und " *szstatustext* " für jeden Wert) sind:

| Wert | Beschreibung |
|--|--|
| BINDSTATUS_FINDINGRESOURCE | Beim Bindungs Vorgang wird die Ressource gefunden, die das Objekt oder den Speicher enthält, an das gebunden wird. *Szstatustext* stellt den anzeigen amen der gesuchten Ressource bereit (z. b. "www.Microsoft.com"). |
| BINDSTATUS_CONNECTING | Der Bindungs Vorgang stellt eine Verbindung mit der Ressource her, die das Objekt oder den Speicher enthält, an das gebunden wird. Der Anzeige Name der Ressource, mit der eine Verbindung hergestellt wird (z. b. eine IP-Adresse), wird von *szstatustext* bereitstellt. |
| BINDSTATUS_SENDINGREQUEST | Der Bindungs Vorgang fordert das Objekt oder den Speicher an, an das gebunden wird. *Szstatustext* stellt den anzeigen amen des Objekts bereit (z. b. einen Dateinamen). |
| BINDSTATUS_REDIRECTING | Der Bindungs Vorgang wurde an einen anderen Daten Speicherort umgeleitet. *Szstatustext* stellt den anzeigen amen des neuen Datenspeicher Orts bereit. |
| BINDSTATUS_USINGCACHEDCOPY | Der Bindungs Vorgang ruft das angeforderte Objekt oder den Speicher aus einer zwischengespeicherten Kopie ab. Der *szstatustext* ist NULL. |
| BINDSTATUS_BEGINDOWNLOADDATA | Der Bindungs Vorgang hat begonnen, das Objekt oder den Speicher zu empfangen, an das gebunden wird. *Szstatustext* gibt den anzeigen amen des Datenspeicher Orts an. |
| BINDSTATUS_DOWNLOADINGDATA | Der Bindungs Vorgang empfängt weiterhin das Objekt oder den Speicher, an das gebunden wird. *Szstatustext* gibt den anzeigen amen des Datenspeicher Orts an. |
| BINDSTATUS_ENDDOWNLOADDATA | Der Bindungs Vorgang hat das Empfangen des Objekts oder Speichers abgeschlossen, an das gebunden wird. *Szstatustext* gibt den anzeigen amen des Datenspeicher Orts an. |
| BINDSTATUS_CLASSIDAVAILABLE | Eine Instanz des Objekts, an das gebunden wird, wird gerade erstellt. Der *szstatustext* stellt die CLSID des neuen Objekts im Zeichen folgen Format bereit und ermöglicht es dem Client, den Bindungs Vorgang, falls gewünscht, abzubrechen. |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a> CAsyncMonikerFile:: onstartbinding

Überschreiben Sie diese Funktion in den abgeleiteten Klassen, um beim Starten der Bindung Aktionen auszuführen.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom Moniker zurück aufgerufen. Bei der Standardimplementierung wird keine Aktion ausgeführt.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a> CAsyncMonikerFile:: onstopbinding

Wird vom Moniker am Ende des Bindungs Vorgangs aufgerufen.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parameter

*HRESULT*<br/>
Ein HRESULT, das den Fehler-oder Warnungs Wert ist.

*szerrort*<br/>
Eine Zeichenfolge, die den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um Aktionen auszuführen, wenn die Übertragung beendet wird. Standardmäßig gibt die-Funktion frei `IBinding` .

Eine Beschreibung der- `IBinding` Schnittstelle finden Sie in der Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a> CAsyncMonikerFile:: Open

Mit dieser Member-Funktion können Sie eine Datei asynchron öffnen.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*lpszurl*<br/>
Ein Zeiger auf die Datei, die asynchron geöffnet werden soll. Bei der Datei kann es sich um eine beliebige gültige URL oder Dateinamen handeln

*pError*<br/>
Ein Zeiger auf die Datei Ausnahmen. Wenn ein Fehler auftritt, wird er auf die Ursache festgelegt.

*pmoniker*<br/>
Ein Zeiger auf die asynchrone monikerschnittstelle `IMoniker` , ein präziser Moniker, der die Kombination aus dem eigenen Moniker des Dokuments ist, den Sie mit abrufen können `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)` , und einem Moniker, der aus dem Pfadnamen erstellt wurde. Das Steuerelement kann diesen Moniker für die Bindung verwenden, aber dies ist nicht der Moniker, der vom Steuerelement gespeichert werden soll.

*pbindhost*<br/>
Ein Zeiger auf die- `IBindHost` Schnittstelle, die verwendet wird, um den Moniker aus einem potenziell relativen Pfadnamen zu erstellen. Wenn der Bindungs Host ungültig ist oder keinen Moniker bereitstellt, wird als Standardwert verwendet `Open(lpszFileName,pError)` . Eine Beschreibung der- `IBindHost` Schnittstelle finden Sie in der Windows SDK.

*pServiceProvider*<br/>
Ein Zeiger auf die `IServiceProvider`-Schnittstelle. Wenn der Dienstanbieter ungültig ist oder den Dienst für nicht bereitstellt `IBindHost` , wird als Standardwert verwendet `Open(lpszFileName,pError)` .

*pUnknown*<br/>
Ein Zeiger auf die `IUnknown`-Schnittstelle. Wenn `IServiceProvider` gefunden wird, fragt die Funktion nach ab `IBindHost` . Wenn der Dienstanbieter ungültig ist oder den Dienst für nicht bereitstellt `IBindHost` , wird als Standardwert verwendet `Open(lpszFileName,pError)` .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Datei erfolgreich geöffnet wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dieser Befehl initiiert den Bindungsprozess.

Sie können eine URL oder einen Dateinamen für den *lpszurl* -Parameter verwenden. Beispiel:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- oder -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CMonikerFile-Klasse](../../mfc/reference/cmonikerfile-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile-Klasse](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty-Klasse](../../mfc/reference/cdatapathproperty-class.md)
