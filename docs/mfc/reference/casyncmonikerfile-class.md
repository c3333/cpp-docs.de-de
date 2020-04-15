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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376997"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile-Klasse

Stellt Funktionalität für die Verwendung von asynchronen Monikern in ActiveX-Steuerelementen (früher OLE-Steuerelemente) bereit.

## <a name="syntax"></a>Syntax

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Erstellt ein `CAsyncMonikerFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncMonikerFile::Schließen](#close)|Schließt und gibt alle Ressourcen frei.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Ruft einen Zeiger auf die asynchrone Übertragungsbindung ab.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Ruft das Format der Daten im Stream ab.|
|[CAsyncMonikerFile::Öffnen](#open)|Öffnet eine Datei asynchron.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Erstellt ein COM-Objekt, das `IBindStatusCallback`implementiert.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Wird von der OLE-Systembibliothek aufgerufen, um Informationen über den Typ der zu erstellenden Bindung anzufordern.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Wird von der OLE-Systembibliothek aufgerufen, um die Priorität der Bindung abzuerhalten.|
|[CAsyncMonikerFile::OnDataVerfügbar](#ondataavailable)|Wird aufgerufen, um Daten bereitzustellen, sobald sie dem Client während asynchroner Bindungsvorgänge zur Verfügung stehen.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Wird aufgerufen, wenn die Ressourcen niedrig sind.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Wird aufgerufen, um den Fortschritt beim Datendownloadvorgang anzuzeigen.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Wird aufgerufen, wenn die Bindung gestartet wird.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Wird aufgerufen, wenn die asynchrone Übertragung beendet wird.|

## <a name="remarks"></a>Bemerkungen

Abgeleitet von [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), die wiederum von [COleStreamFile](../../mfc/reference/colestreamfile-class.md)abgeleitet wird, `CAsyncMonikerFile` verwendet die [IMoniker-Schnittstelle,](/windows/win32/api/objidl/nn-objidl-imoniker) um asynchron auf jeden Datenstrom zuzugreifen, einschließlich des asynchronen Ladens von Dateien von einer URL. Bei den Dateien kann es sich um Datenpfadeigenschaften von ActiveX-Steuerelementen handeln.

Asynchrone Moniker werden hauptsächlich in internetfähigen Anwendungen und ActiveX-Steuerelementen verwendet, um eine reaktionsfähige Benutzeroberfläche bei Dateiübertragungen bereitzustellen. Ein Paradebeispiel hierfür ist die Verwendung von [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) zum Bereitstellen asynchroner Eigenschaften für ActiveX-Steuerelemente. Das `CDataPathProperty` Objekt erhält wiederholt einen Rückruf, um die Verfügbarkeit neuer Daten während eines langwierigen Eigenschaftenaustauschprozesses anzuzeigen.

Weitere Informationen zur Verwendung asynchroner Moniker und ActiveX-Steuerelemente in Internetanwendungen finden Sie in den folgenden Artikeln:

- [Erste Schritte im Internet: Asynchrone Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Erste Schritte im Internet: ActiveX-Steuerelemente](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

Erstellt ein `CAsyncMonikerFile`-Objekt.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Bemerkungen

Die `IBindHost` Schnittstelle wird nicht erstellt. `IBindHost`wird nur verwendet, wenn `Open` Sie sie in der Memberfunktion bereitstellen.

Eine Beschreibung der `IBindHost` Benutzeroberfläche finden Sie im Windows SDK.

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Schließen

Rufen Sie diese Funktion auf, um alle Ressourcen zu schließen und freizugeben.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Kann auf ungeöffnete oder bereits geschlossene Dateien aufgerufen werden.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

Erstellt ein COM-Objekt, das `IBindStatusCallback`implementiert.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Parameter

*pUnkControlling*<br/>
Ein Zeiger auf das Steuern `IUnknown`unbekannt (die äußere ) oder NULL, wenn Aggregation nicht verwendet wird.

### <a name="return-value"></a>Rückgabewert

Wenn *pUnkControlling* nicht NULL ist, gibt die `IUnknown` Funktion einen Zeiger `IBindStatusCallback`auf das Innere auf einem neuen COM-Objekt zurück, das unterstützt. Wenn `pUnkControlling` NULL ist, gibt die Funktion `IUnknown` einen Zeiger auf `IBindStatusCallback`einen auf einem neuen COM-Objekt zurück, das unterstützt.

### <a name="remarks"></a>Bemerkungen

`CAsyncMonikerFile`erfordert ein COM-Objekt, das `IBindStatusCallback`implementiert. MFC implementiert ein solches Objekt und ist aggregierend. Sie können `CreateBindStatusCallback` überschreiben, um Ihr eigenes COM-Objekt zurückzugeben. Ihr COM-Objekt kann die MFC-Implementierung aggregieren, indem es mit dem von Ihrem COM-Objekt unbekannten Controlling aufruft. `CreateBindStatusCallback` COM-Objekte, `CCmdTarget` die mit der COM-Unterstützung implementiert wurden, können das Steuern unbekannte mithilfe `CCmdTarget::GetControllingUnknown`abrufen.

Alternativ kann Ihr COM-Objekt an die MFC-Implementierung delegieren, indem es aufruft. `CreateBindStatusCallback( NULL )`

[CAsyncMonikerFile::Aufrufe](#open) `CreateBindStatusCallback`öffnen .

Weitere Informationen zu asynchronen Monikern und asynchroner Bindung finden Sie in der [IBindStatusCallback-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) und [wie asynchrone Bindung und Speicherarbeit funktionieren.](/windows/win32/Stg/how-asynchronous-binding-and-storage-work) Eine Erläuterung der Aggregation finden Sie unter [Aggregation](/windows/win32/com/aggregation). Alle drei Themen befinden sich im Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo

Wird vom Client eines asynchronen Monikers aufgerufen, um dem asynchronen Moniker mitzuteilen, wie er binden möchte.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Rückgabewert

Ruft die Einstellungen `IBindStatusCallBack`für ab. Eine Beschreibung der `IBindStatusCallback` Benutzeroberfläche finden Sie im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung legt fest, dass die Bindung asynchron ist, ein Speichermedium (einen Stream) verwendet und das Datenpushmodell verwendet wird. Überschreiben Sie diese Funktion, wenn Sie das Verhalten der Bindung ändern möchten.

Ein Grund dafür wäre, das Data-Pull-Modell anstelle des Data-Push-Modells zu binden. In einem Data-Pull-Modell steuert der Client den Bindungsvorgang, und der Moniker stellt dem Client nur Daten bereit, wenn er gelesen wird. In einem Data-Push-Modell steuert der Moniker den asynchronen Bindungsvorgang und benachrichtigt den Client kontinuierlich, wenn neue Daten verfügbar sind.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding

Rufen Sie diese Funktion auf, um einen Zeiger auf die asynchrone Übertragungsbindung abzurufen.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IBinding` die Schnittstelle, die bereitgestellt wird, wenn die asynchrone Übertragung beginnt. Gibt NULL zurück, wenn die Übertragung aus irgendeinem Grund nicht asynchron erfolgen kann.

### <a name="remarks"></a>Bemerkungen

Auf diese Weise können Sie den `IBinding` Datenübertragungsprozess über `IBinding::Abort`die `IBinding::Pause`Schnittstelle `IBinding::Resume`steuern, z. B. mit , und .

Eine Beschreibung der `IBinding` Benutzeroberfläche finden Sie im Windows SDK.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Rufen Sie diese Funktion auf, um das Format der Daten im Stream abzurufen.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Windows-Struktur [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) für den aktuell geöffneten Stream. Gibt NULL zurück, wenn der Moniker nicht gebunden wurde, wenn er nicht asynchron ist oder wenn der asynchrone Vorgang nicht gestartet wurde.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority

Wird vom Client eines asynchronen Monikers aufgerufen, wenn der Bindungsprozess beginnt, die Dem Thread für den Bindungsvorgang angegebene Priorität zu erhalten.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Rückgabewert

Die Priorität, bei der die asynchrone Übertragung stattfindet. Eines der Standardflags für Threadprioritäten: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL und THREAD_PRIORITY_TIME_CRITICAL. Eine Beschreibung dieser Werte finden Sie in der Windows-Funktion [SetThreadPriority.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="remarks"></a>Bemerkungen

`GetPriority`sollte nicht direkt aufgerufen werden. THREAD_PRIORITY_NORMAL wird von der Standardimplementierung zurückgegeben.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataVerfügbar

Ein asynchroner Monikerruft, `OnDataAvailable` um Daten für den Client bereitzustellen, sobald er verfügbar ist, während asynchroner Bindungsvorgänge.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Parameter

*dwSize*<br/>
Der kumulative Betrag (in Bytes) der seit Beginn der Bindung verfügbaren Daten. Kann Null sein, was darauf hinweist, dass die Datenmenge für den Vorgang nicht relevant ist oder dass kein bestimmter Betrag verfügbar wurde.

*bscfFlag*<br/>
Ein BSCF-Enumerationswert. Kann einer oder mehrere der folgenden Werte sein:

- BSCF_FIRSTDATANOTIFICATION Identifiziert den `OnDataAvailable` ersten Aufruf für einen bestimmten Bindungsvorgang.

- BSCF_INTERMEDIATEDATANOTIFICATION Identifiziert einen `OnDataAvailable` Zwischenaufruf für einen Bindungsvorgang.

- BSCF_LASTDATANOTIFICATION Identifiziert den `OnDataAvailable` letzten Aufruf für einen Bindungsvorgang.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Im folgenden Beispiel finden Sie eine Beispielimplementierung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource

Wird vom Moniker aufgerufen, wenn die Ressourcen niedrig sind.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `GetBinding( )-> Abort( )`sruft auf.

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress

Wird vom Moniker wiederholt aufgerufen, um den aktuellen Fortschritt dieses Bindungsvorgangs anzuzeigen, in der Regel in angemessenen Intervallen während eines längeren Vorgangs.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Parameter

*ulProgress*<br/>
Gibt den aktuellen Fortschritt des Bindungsvorgangs relativ zu dem in *ulProgressMax*angegebenen erwarteten Maximum an.

*ulProgressMax*<br/>
Gibt den erwarteten Maximalwert von *ulProgress* für die Dauer von Aufrufen `OnProgress` für diesen Vorgang an.

*ulStatusCode*<br/>
Enthält zusätzliche Informationen zum Fortschritt des Bindungsvorgangs. Gültige Werte werden `BINDSTATUS` der Enumeration entnommen. Mögliche Werte finden Sie in den Hinweisen.

*szStatusText*<br/>
Informationen über den aktuellen Fortschritt, abhängig vom Wert von *ulStatusCode*. Mögliche Werte finden Sie in den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Mögliche Werte für *ulStatusCode* (und den *szStatusText* für jeden Wert) sind:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |Der Bindungsvorgang sucht die Ressource, an die das Objekt oder den Speicher gebunden ist. Der *szStatusText* gibt den Anzeigenamen der gesuchten Ressource an (z. B. "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |Der Bindungsvorgang stellt eine Verbindung mit der Ressource her, an die das Objekt oder den Speicher gebunden ist. Der *szStatusText* gibt den Anzeigenamen der Ressource an, mit der eine Verbindung hergestellt wird (z. B. eine IP-Adresse).  |
|BINDSTATUS_SENDINGREQUEST|Der Bindungsvorgang fordert das Objekt oder den Speicher an, an den gebunden ist. Der *szStatusText* gibt den Anzeigenamen des Objekts an (z. B. einen Dateinamen).|
|BINDSTATUS_REDIRECTING  |Der Bindungsvorgang wurde an einen anderen Datenspeicherort umgeleitet. Der *szStatusText* stellt den Anzeigenamen des neuen Datenspeicherorts bereit.  |
|BINDSTATUS_USINGCACHEDCOPY  |Der Bindungsvorgang ruft das angeforderte Objekt oder den angeforderten Speicher aus einer zwischengespeicherten Kopie ab. Der *szStatusText* ist NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |Der Bindungsvorgang hat mit dem Empfang des Objekts oder Speichers begonnen, an den gebunden ist. Der *szStatusText* gibt den Anzeigenamen des Datenspeicherorts an.|
|BINDSTATUS_DOWNLOADINGDATA  |Der Bindungsvorgang empfängt weiterhin das Objekt oder den Speicher, an den gebunden ist. Der *szStatusText* gibt den Anzeigenamen des Datenspeicherorts an.  |
|BINDSTATUS_ENDDOWNLOADDATA  |Der Bindungsvorgang hat den Empfang des Objekts oder Speichers beendet, an den gebunden ist. Der *szStatusText* gibt den Anzeigenamen des Datenspeicherorts an.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Eine Instanz des Objekts, an das gebunden wird, wird gerade erstellt. Der *szStatusText* stellt die CLSID des neuen Objekts im Zeichenfolgenformat bereit, sodass der Client den Bindungsvorgang bei Bedarf abbrechen kann.  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding

Überschreiben Sie diese Funktion in ihren abgeleiteten Klassen, um Aktionen auszuführen, wenn die Bindung gestartet wird.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom Moniker zurückgerufen. Bei der Standardimplementierung wird keine Aktion ausgeführt.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding

Wird vom Moniker am Ende des Bindungsvorgangs aufgerufen.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Parameter

*Hresult*<br/>
Ein HRESULT, das der Fehler- oder Warnwert ist.

*szErrort*<br/>
Eine Zeichenfolge, die den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um Aktionen auszuführen, wenn die Übertragung beendet wird. Standardmäßig gibt die `IBinding`Funktion frei.

Eine Beschreibung der `IBinding` Benutzeroberfläche finden Sie im Windows SDK.

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Öffnen

Rufen Sie diese Memberfunktion auf, um eine Datei asynchron zu öffnen.

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

*lpszURL*<br/>
Ein Zeiger auf die Datei, die asynchron geöffnet werden soll. Die Datei kann eine beliebige gültige URL oder ein gültiger Dateiname sein.

*pError*<br/>
Ein Zeiger auf die Dateiausnahmen. Im Falle eines Fehlers wird er auf die Ursache festgelegt.

*pMoniker*<br/>
Ein Zeiger auf die asynchrone `IMoniker`Monikerschnittstelle , ein präziser Moniker, der die Kombination aus `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`dem dokumenteigenen Moniker ist, den Sie mit abrufen können, und einem Moniker, der aus dem Pfadnamen erstellt wurde. Das Steuerelement kann diesen Moniker zum Binden verwenden, aber dies ist nicht der Moniker, den das Steuerelement speichern soll.

*pBindHost*<br/>
Ein Zeiger auf `IBindHost` die Schnittstelle, die verwendet wird, um den Moniker aus einem potenziell relativen Pfadnamen zu erstellen. Wenn der Bindungshost ungültig ist oder keinen Moniker enthält, wird der Aufruf standardmäßig auf `Open(lpszFileName,pError)`. Eine Beschreibung der `IBindHost` Benutzeroberfläche finden Sie im Windows SDK.

*pServiceProvider*<br/>
Ein Zeiger auf die `IServiceProvider`-Schnittstelle. Wenn der Dienstanbieter ungültig ist oder den `IBindHost`Dienst nicht für `Open(lpszFileName,pError)`bereitstellen kann, wird der Aufruf standardmäßig auf .

*pUnbekannt*<br/>
Ein Zeiger auf die `IUnknown`-Schnittstelle. Wenn `IServiceProvider` gefunden wird, fragt `IBindHost`die Funktion nach ab. Wenn der Dienstanbieter ungültig ist oder den `IBindHost`Dienst nicht für `Open(lpszFileName,pError)`bereitstellen kann, wird der Aufruf standardmäßig auf .

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Datei erfolgreich geöffnet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dieser Aufruf initiiert den Bindungsprozess.

Sie können eine URL oder einen Dateinamen für den Parameter *lpszURL* verwenden. Beispiel:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- oder -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Siehe auch

[CMonikerFile-Klasse](../../mfc/reference/cmonikerfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile-Klasse](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty-Klasse](../../mfc/reference/cdatapathproperty-class.md)
