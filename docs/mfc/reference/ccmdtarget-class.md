---
title: CCmdTarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426000"
---
# <a name="ccmdtarget-class"></a>CCmdTarget-Klasse

Die Basisklasse für die Microsoft Foundation Class-Bibliothek Message-Map-Architektur.

## <a name="syntax"></a>Syntax

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Erstellt ein `CCmdTarget`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Zeigt den Cursor als Sanduhr Cursor an.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Bewirkt, dass eine durch ein OLE-Verb angegebene Aktion ausgeführt wird.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Ermöglicht die OLE-Automatisierung für das `CCmdTarget` Objekt.|
|[CCmdTarget::EnableConnections](#enableconnections)|Aktiviert das Auslösen von Ereignissen über Verbindungspunkte.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Aktiviert die Typbibliothek eines Objekts.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Kehrt zum vorherigen Cursor zurück.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Listet die OLE-Verben eines Objekts auf.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Gibt einen Zeiger auf das `CCmdTarget` Objekt zurück, das dem `IDispatch` Zeiger zugeordnet ist.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Ruft die ID der primären Dispatchschnittstelle ab.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Gibt einen Zeiger auf das `IDispatch` Objekt zurück, das dem `CCmdTarget`-Objekt zugeordnet ist.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Ruft die Anzahl der Schnittstellen für Typinformationen ab, die ein Objekt bereitstellt.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Ruft die Typenbeschreibung ab, die der angegebenen GUID entspricht.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Ruft einen Zeiger auf eine Typbibliothek ab.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Ruft den Typbibliotheks Cache ab.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Aktiviert den Aufruf der Automatisierungs Methode.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Gibt einen Wert ungleich 0 zurück, wenn eine Automatisierungsfunktion einen Wert zurückgeben soll.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Leitet befehlsnachrichten weiter und sendet Sie.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Bereinigt, nachdem der letzte OLE-Verweis freigegeben wurde.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Stellt den Sanduhr Cursor wieder her.|

## <a name="remarks"></a>Hinweise

Eine Meldungs Zuordnung leitet Befehle oder Meldungen an die Element Funktionen weiter, die Sie schreiben, um Sie zu behandeln. (Ein Befehl ist eine Meldung von einem Menü Element, einer Befehls Schaltfläche oder einer Zugriffstaste.)

Zu den `CCmdTarget` von gehören [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)und [CFrameWnd](../../mfc/reference/cframewnd-class.md). Wenn Sie beabsichtigen, eine neue Klasse für die Verarbeitung von Nachrichten zu verarbeiten, leiten Sie die Klasse von einer dieser `CCmdTarget`abgeleiteten Klassen ab. Eine Klasse wird nur selten direkt von `CCmdTarget` abgeleitet.

Eine Übersicht über die Befehlsziele und das `OnCmdMsg`-Routing finden Sie unter [Befehlsziele](../../mfc/command-targets.md), [Befehlsrouting](../../mfc/command-routing.md) und [Zuordnen von Meldungen](../../mfc/mapping-messages.md).

`CCmdTarget` enthält Member-Funktionen, die die Anzeige eines Sanduhr Cursors verarbeiten. Zeigen Sie den Sanduhr Cursor an, wenn Sie erwarten, dass ein Befehl ein merkbares Zeitintervall für die Ausführung benötigt.

Dispatchzuordnungen, ähnlich wie bei Nachrichten Zuordnungen, werden verwendet, um OLE-Automatisierungs `IDispatch` Funktionalität verfügbar zu machen Wenn Sie diese Schnittstelle verfügbar machen, können andere Anwendungen (z. b. Visual Basic) Ihre Anwendung aufzurufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

##  <a name="beginwaitcursor"></a>CCmdTarget:: beginwaitcursor

Mit dieser Funktion können Sie den Cursor als Sanduhr anzeigen, wenn Sie erwarten, dass ein Befehl ein merkbares Zeitintervall für die Ausführung benötigt.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Funktion auf, um den Benutzer anzuzeigen, dass er ausgelastet ist, z. b. Wenn ein `CDocument` Objekt in eine Datei lädt oder speichert.

Die Aktionen von `BeginWaitCursor` sind außerhalb eines einzelnen Nachrichten Handlers nicht immer wirksam, weil andere Aktionen, wie z. b. `OnSetCursor` Behandlung, den Cursor ändern können.

Ruft `EndWaitCursor` auf, um den vorherigen Cursor wiederherzustellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget:: CCmdTarget

Erstellt ein `CCmdTarget`-Objekt.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget::D ooleverb

Bewirkt, dass eine durch ein OLE-Verb angegebene Aktion ausgeführt wird.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Numerischer Bezeichner des Verbs.

*lpMsg*<br/>
Ein Zeiger auf die [msg](/windows/win32/api/winuser/ns-winuser-msg) -Struktur, die das Ereignis beschreibt (z. b. ein Doppelklick), das das Verb aufgerufen hat.

*hWndParent*<br/>
Das Handle des Dokumentfensters, das das Objekt enthält.

*lpRect*<br/>
Ein Zeiger auf die [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die die Koordinaten (in Pixel) enthält, die das umschließende Rechteck eines Objekts in *hwndParent*definieren.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls false.

### <a name="remarks"></a>Hinweise

Bei dieser Member-Funktion handelt es sich im Grunde um eine Implementierung von [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Die möglichen Aktionen werden von [CCmdTarget:: enumoleversb](#enumoleverbs)aufgezählt.

##  <a name="enableautomation"></a>CCmdTarget:: enableautomation

Diese Funktion wird aufgerufen, um die OLE-Automatisierung für ein Objekt zu aktivieren.

```
void EnableAutomation();
```

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel vom Konstruktor des Objekts aufgerufen und sollte nur aufgerufen werden, wenn eine dispatchmap für die Klasse deklariert wurde. Weitere Informationen zur Automatisierung finden Sie in den Artikeln [Automation Clients](../../mfc/automation-clients.md) and [Automation Servers](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>CCmdTarget:: enableconnections

Aktiviert das Auslösen von Ereignissen über Verbindungspunkte.

```
void EnableConnections();
```

### <a name="remarks"></a>Hinweise

Um Verbindungspunkte zu aktivieren, müssen Sie diese Member-Funktion im Konstruktor ihrer abgeleiteten Klasse abrufen.

##  <a name="enabletypelib"></a>CCmdTarget:: enabletypelib

Aktiviert die Typbibliothek eines Objekts.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Hinweise

Nennen Sie diese Member-Funktion im Konstruktor des `CCmdTarget`von abgeleiteten Objekts, wenn Sie Typinformationen bereitstellt.

##  <a name="endwaitcursor"></a>CCmdTarget:: endwaitcursor

Aufrufen Sie diese Funktion, nachdem Sie die `BeginWaitCursor` Member-Funktion aufgerufen haben, um vom Sanduhr Cursor zum vorherigen Cursor zurückzukehren.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Hinweise

Das Framework ruft diese Member-Funktion auch auf, nachdem Sie den Sanduhr Cursor aufgerufen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget:: enumoleversb

Listet die OLE-Verben eines Objekts auf.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parameter

*ppenumOleVerb*<br/>
Ein Zeiger auf einen Zeiger auf eine [IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) -Schnittstelle.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Objekt mindestens ein OLE-Verb unterstützt (in diesem Fall \* *ppumoleverb* auf eine `IEnumOLEVERB` Enumeratorschnittstelle verweist), andernfalls false.

### <a name="remarks"></a>Hinweise

Bei dieser Member-Funktion handelt es sich im Grunde um eine Implementierung von [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>CCmdTarget:: fromidispatch

Mit dieser Funktion können Sie einen `IDispatch` Zeiger, der von Automatisierungs Element Funktionen einer Klasse empfangen wurde, in das `CCmdTarget` Objekt zuordnen, das die Schnittstellen des `IDispatch` Objekts implementiert.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parameter

*lpDispatch*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `CCmdTarget`-Objekt, das mit *lpdispatch*verknüpft ist. Diese Funktion gibt NULL zurück, wenn das `IDispatch` Objekt nicht als Microsoft Foundation Class-`IDispatch` Objekt erkannt wird.

### <a name="remarks"></a>Hinweise

Das Ergebnis dieser Funktion ist die Umkehrung eines Aufrufes `GetIDispatch`der Element Funktion.

##  <a name="getdispatchiid"></a>CCmdTarget:: getdispatchiid

Ruft die ID der primären Dispatchschnittstelle ab.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parameter

*pIID*<br/>
Ein Zeiger auf eine Schnittstellen-ID (eine [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls false. Bei erfolgreicher Ausführung wird \* *piid* auf die primäre Dispatch-Schnittstellen-ID festgelegt.

### <a name="remarks"></a>Hinweise

Abgeleitete Klassen sollten diese Element Funktion überschreiben (wenn Sie nicht überschrieben wird, `GetDispatchIID` false zurückgibt). Siehe [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>CCmdTarget:: getidispatch

Rufen Sie diese Member-Funktion auf, um den `IDispatch` Zeiger aus einer Automatisierungs Methode abzurufen, die entweder einen `IDispatch`-Zeiger zurückgibt oder einen `IDispatch` Zeiger als Verweis annimmt.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parameter

*bAddRef*<br/>
Gibt an, ob der Verweis Zähler für das Objekt Inkrement erhöht werden soll.

### <a name="return-value"></a>Rückgabewert

Der `IDispatch` Zeiger, der dem-Objekt zugeordnet ist.

### <a name="remarks"></a>Hinweise

Bei Objekten, die `EnableAutomation` in ihren Konstruktoren aufzurufen, sodass Sie automatisiert werden, gibt diese Funktion einen Zeiger auf die Foundation Class-Implementierung von `IDispatch` zurück, die von Clients verwendet wird, die über die `IDispatch`-Schnittstelle kommunizieren. Wenn Sie diese Funktion aufrufen, wird automatisch ein Verweis auf den-Zeiger hinzugefügt, daher ist es nicht erforderlich, [IUnknown:: adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)aufzurufen.

##  <a name="gettypeinfocount"></a>CCmdTarget:: gettypeingefocount

Ruft die Anzahl der Schnittstellen für Typinformationen ab, die ein Objekt bereitstellt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Schnittstellen für die Typinformationen.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert im Grunde [IDispatch:: gettypeingefocount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Abgeleitete Klassen sollten diese Funktion überschreiben, um die angegebene Anzahl von Schnittstellen für Typinformationen zurückzugeben (entweder 0 oder 1). Wenn Sie nicht überschrieben wird, gibt `GetTypeInfoCount` 0 zurück. Um dies zu überschreiben, verwenden Sie das [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) -Makro, das ebenfalls `GetTypeLib` und `GetTypeLibCache`implementiert.

##  <a name="gettypeinfoofguid"></a>CCmdTarget:: gettypeingefoof-ID

Ruft die Typenbeschreibung ab, die der angegebenen GUID entspricht.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parameter

*lcid*<br/>
Ein Gebiets Schema Bezeichner (`LCID`).

*guid*<br/>
Der [GUID](/previous-versions/cc317743(v%3dmsdn.10)) der Typbeschreibung.

*ppTypeInfo*<br/>
Zeiger auf einen Zeiger auf die `ITypeInfo`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT, das den Erfolg oder Misserfolg des Aufrufes angibt. Bei erfolgreicher Ausführung zeigt \* *pptypeinfo* auf die Schnittstelle für die Typinformation.

##  <a name="gettypelib"></a>CCmdTarget:: gettypelib

Ruft einen Zeiger auf eine Typbibliothek ab.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Parameter

*lcid*<br/>
Ein Gebietsschemabezeichner (LCID).

*ppTypeLib*<br/>
Ein Zeiger auf einen Zeiger auf die `ITypeLib`-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT, das den Erfolg oder Misserfolg des Aufrufes angibt. Bei erfolgreicher Ausführung verweist \* *pptypelib* auf die Schnittstelle der Typbibliothek.

### <a name="remarks"></a>Hinweise

Abgeleitete Klassen sollten diese Element Funktion überschreiben (wenn Sie nicht überschrieben wird, `GetTypeLib` TYPE_E_CANTLOADLIBRARY) zurückgibt. Verwenden Sie das [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) -Makro, das ebenfalls `GetTypeInfoCount` und `GetTypeLibCache`implementiert.

##  <a name="gettypelibcache"></a>CCmdTarget:: gettypelibcache

Ruft den Typbibliotheks Cache ab.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CTypeLibCache` -Objekt.

### <a name="remarks"></a>Hinweise

Abgeleitete Klassen sollten diese Element Funktion überschreiben (wenn Sie nicht überschrieben wird, `GetTypeLibCache` NULL zurückgibt). Verwenden Sie das [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) -Makro, das ebenfalls `GetTypeInfoCount` und `GetTypeLib`implementiert.

##  <a name="isinvokeallowed"></a>CCmdTarget:: isinvokeallowed

Diese Funktion wird von der MFC-Implementierung von `IDispatch::Invoke` aufgerufen, um zu bestimmen, ob eine bestimmte Automatisierungs Methode (durch *DISPID*gekennzeichnet) aufgerufen werden kann.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*dispid*<br/>
Eine Dispatch-ID.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode aufgerufen werden kann, andernfalls false.

### <a name="remarks"></a>Hinweise

Wenn `IsInvokeAllowed` true zurückgibt, ruft `Invoke` die-Methode auf. Andernfalls schlägt `Invoke` fehl, und es wird E_UNEXPECTED zurückgegeben.

Abgeleitete Klassen können diese Funktion überschreiben, um geeignete Werte zurückzugeben (wenn Sie nicht überschrieben werden, `IsInvokeAllowed` true zurückgibt). Siehe insbesondere [COleControl:: isinvokeallowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>CCmdTarget:: isresultexpfiziert

Verwenden Sie `IsResultExpected`, um zu überprüfen, ob ein Client einen Rückgabewert des Aufrufes einer Automatisierungsfunktion erwartet.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn eine Automatisierungsfunktion einen Wert zurückgeben soll. andernfalls 0.

### <a name="remarks"></a>Hinweise

Die OLE-Schnittstelle stellt Informationen an MFC bereit, um zu bestimmen, ob der Client das Ergebnis eines Funktions Aufrufes verwendet oder ignoriert, und MFC verwendet diese Informationen wiederum, um das Ergebnis eines Aufruf`IsResultExpected`zu bestimmen. Wenn die Produktion eines Rückgabewerts Zeit-oder ressourcenintensiv ist, können Sie die Effizienz steigern, indem Sie diese Funktion vor dem Berechnen des Rückgabewerts aufrufen.

Diese Funktion gibt 0 (null) nur einmal zurück, sodass Sie gültige Rückgabewerte von anderen Automatisierungsfunktionen erhalten, wenn Sie Sie von der vom Client aufgerufenen Automatisierungsfunktion aufrufen.

`IsResultExpected` gibt einen Wert ungleich 0 (null) zurück, wenn er aufgerufen wird, wenn kein Automatisierungs Funktionsaufruf ausgeführt wird.

##  <a name="oncmdmsg"></a>CCmdTarget:: OnCmdMsg

Wird vom Framework aufgerufen, um Befehls Meldungen weiterzuleiten und zu verteilen und um das Update von Benutzeroberflächen Objekten der Befehle zu verarbeiten.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Enthält die Befehls-ID.

*nCode*<br/>
Identifiziert den Befehls Benachrichtigungs Code. Weitere Informationen zu den Werten für *nCode*finden Sie unter " **Hinweise** ".

*pExtra*<br/>
Wird gemäß dem Wert von *nCode*verwendet. Weitere Informationen zu *pextra*finden Sie unter " **Hinweise** ".

*pHandlerInfo*<br/>
Wenn nicht NULL, füllt `OnCmdMsg` die *pTARGET* -und *PMF* -Elemente der *phandlerinfo* -Struktur aus, anstatt den Befehl zu verteilen. In der Regel sollte dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Meldung verarbeitet wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Dies ist die wichtigste Implementierungs Routine der Framework-Befehls Architektur.

Zur Laufzeit sendet `OnCmdMsg` einen Befehl an andere Objekte oder verarbeitet den Befehl selbst durch Aufrufen der Stamm Klasse `CCmdTarget::OnCmdMsg`, die die tatsächliche Nachrichten-Zuordnungs Suche durchführt. Eine umfassende Beschreibung des Standard Befehls Routings finden Sie unter [Themen zur Nachrichten Behandlung und-Zuordnung](../../mfc/message-handling-and-mapping.md).

In seltenen Fällen können Sie diese Element Funktion überschreiben, um das Standard Befehls Routing des Frameworks zu erweitern. Ausführliche Informationen zur Befehls Routing Architektur finden Sie in der [technischen Notiz 21](../../mfc/tn021-command-and-message-routing.md) .

Wenn Sie `OnCmdMsg`überschreiben, müssen Sie den entsprechenden Wert für *nCode*, den Befehls Benachrichtigungs Code und *pextra*angeben, die vom Wert von *nCode*abhängig sind. In der folgenden Tabelle sind die entsprechenden Werte aufgeführt:

|*ncodewert*|*pextra* -Wert|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>CCmdTarget:: OnFinalRelease

Wird von Framework aufgerufen, wenn der letzte OLE-Verweis zum oder aus dem-Objekt freigegeben wird.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese Funktion, um für diese Situation eine spezielle Behandlung bereitzustellen. Die Standard Implementierung löscht das-Objekt.

##  <a name="restorewaitcursor"></a>CCmdTarget:: restorewaitcursor

Mit dieser Funktion können Sie den entsprechenden Sanduhr Cursor nach dem Ändern des System Cursors wiederherstellen (z. b. Nachdem ein Meldungs Feld während eines langen Vorgangs geöffnet und dann geschlossen wurde).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-ACDual](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver-Klasse](../../mfc/reference/coledispatchdriver-class.md)
