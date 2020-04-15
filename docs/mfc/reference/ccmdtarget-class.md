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
ms.openlocfilehash: 5ee4101302322a5212a80b32f095cdd13d9769e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352289"
---
# <a name="ccmdtarget-class"></a>CCmdTarget-Klasse

Die Basisklasse für die Nachrichtenzuordnungsarchitektur der Microsoft Foundation-Klassenbibliothek.

## <a name="syntax"></a>Syntax

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Erstellt ein `CCmdTarget`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Zeigt den Cursor als Sanduhrcursor an.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Bewirkt, dass eine von einem OLE-Verb angegebene Aktion ausgeführt wird.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Ermöglicht die OLE-Automatisierung für das `CCmdTarget` Objekt.|
|[CCmdTarget::EnableConnections](#enableconnections)|Aktiviert das Auslösen von Ereignis über Verbindungspunkte.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Aktiviert die Typbibliothek eines Objekts.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Kehrt zum vorherigen Cursor zurück.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Zählt die OLE-Verben eines Objekts auf.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Gibt einen Zeiger `CCmdTarget` auf das `IDispatch` Objekt zurück, das dem Zeiger zugeordnet ist.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Ruft die primäre Dispatchschnittstellen-ID ab.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Gibt einen Zeiger `IDispatch` auf das `CCmdTarget` dem Objekt zugeordnete Objekt zurück.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Ruft die Anzahl der Typinformationsschnittstellen ab, die ein Objekt bereitstellt.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Ruft die Typenbeschreibung ab, die der angegebenen GUID entspricht.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Ruft einen Zeiger auf eine Typbibliothek ab.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Ruft den Typbibliothekscache ab.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Aktiviert den Aufruf von Automatisierungsmethoden.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Gibt einen Wert ungleich Null zurück, wenn eine Automatisierungsfunktion einen Wert zurückgeben soll.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Routen und löst Befehlsmeldungen aus.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Bereinigt, nachdem der letzte OLE-Verweis freigegeben wurde.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Stellt den Sanduhrcursor wieder her.|

## <a name="remarks"></a>Bemerkungen

Eine Meldungszuordnung leitet Befehle oder Nachrichten an die Mitgliedsfunktionen weiter, die Sie schreiben, um sie zu verarbeiten. (Ein Befehl ist eine Nachricht von einem Menüelement, einer Befehlsschaltfläche oder einer Beschleunigertaste.)

Wichtige Frameworkklassen, `CCmdTarget` die von [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)und [CFrameWnd](../../mfc/reference/cframewnd-class.md)abgeleitet wurden. Wenn Sie beabsichtigen, dass eine neue Klasse Nachrichten verarbeitet, `CCmdTarget`leiten Sie die Klasse von einer dieser -abgeleiteten Klassen ab. Sie werden selten eine `CCmdTarget` Klasse direkt ableiten.

Eine Übersicht über Befehlsziele `OnCmdMsg` und Routing finden Sie unter [Befehlsziele](../../mfc/command-targets.md), [Befehlsrouting](../../mfc/command-routing.md)und Zuordnung von [Nachrichten](../../mfc/mapping-messages.md).

`CCmdTarget`enthält Memberfunktionen, die die Anzeige eines Sanduhrcursors verarbeiten. Zeigen Sie den Sanduhrcursor an, wenn Sie erwarten, dass ein Befehl ein spürbares Zeitintervall für die Ausführung in Anspruch nimmt.

Dispatch-Maps werden ähnlich wie Nachrichtenzuordnungen `IDispatch` verwendet, um OLE-Automatisierungsfunktionen verfügbar zu machen. Durch das Aussetzen dieser Schnittstelle können andere Anwendungen (z. B. Visual Basic) in Ihre Anwendung aufrufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor

Rufen Sie diese Funktion auf, um den Cursor als Sanduhr anzuzeigen, wenn Sie erwarten, dass ein Befehl ein spürbares Zeitintervall einnimmt.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Funktion auf, um dem Benutzer `CDocument` anzuzeigen, dass er ausgelastet ist, z. B. wenn ein Objekt eine Datei lädt oder speichert.

Die Aktionen `BeginWaitCursor` von sind nicht immer außerhalb eines einzelnen `OnSetCursor` Nachrichtenhandlers wirksam, da andere Aktionen, z. B. die Verarbeitung, den Cursor ändern könnten.

Rufen `EndWaitCursor` Sie auf, um den vorherigen Cursor wiederherzustellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget

Erstellt ein `CCmdTarget`-Objekt.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb

Bewirkt, dass eine von einem OLE-Verb angegebene Aktion ausgeführt wird.

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
Zeiger auf die [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die das Ereignis beschreibt (z. B. einen Doppelklick), der das Verb aufgerufen hat.

*hWndEltern*<br/>
Das Handle des Dokumentfensters, das das Objekt enthält.

*lpRect*<br/>
Zeiger auf die [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Koordinaten in Pixel enthält, die das umgrenzende Rechteck eines Objekts in *hwndParent*definieren.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist im Grunde eine Implementierung von [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Die möglichen Aktionen werden von [CCmdTarget::EnumOleVerbs](#enumoleverbs)aufgezählt.

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation

Rufen Sie diese Funktion auf, um die OLE-Automatisierung für ein Objekt zu aktivieren.

```
void EnableAutomation();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der Regel vom Konstruktor des Objekts aufgerufen und sollte nur aufgerufen werden, wenn eine Dispatchzuordnung für die Klasse deklariert wurde. Weitere Informationen zur Automatisierung finden Sie in den Artikeln [Automation Clients](../../mfc/automation-clients.md) und [Automation Servers](../../mfc/automation-servers.md).

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections

Aktiviert das Auslösen von Ereignis über Verbindungspunkte.

```
void EnableConnections();
```

### <a name="remarks"></a>Bemerkungen

Um Verbindungspunkte zu aktivieren, rufen Sie diese Memberfunktion im Konstruktor Ihrer abgeleiteten Klasse auf.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib

Aktiviert die Typbibliothek eines Objekts.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion im `CCmdTarget`Konstruktor Ihres -derived-Objekts auf, wenn sie Typinformationen bereitstellt.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor

Rufen Sie diese Funktion `BeginWaitCursor` auf, nachdem Sie die Memberfunktion aufgerufen haben, um vom Sanduhrcursor zum vorherigen Cursor zurückzukehren.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Memberfunktion auch auf, nachdem sie den Sanduhrcursor aufgerufen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs

Zählt die OLE-Verben eines Objekts auf.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parameter

*ppenumOleVerb*<br/>
Ein Zeiger auf einen Zeiger auf eine [IEnumOLEVERB-Schnittstelle.](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Objekt mindestens ein OLE-Verb unterstützt (in diesem Fall \* zeigt *ppenumOleVerb* auf eine `IEnumOLEVERB` Enumerator-Schnittstelle), andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ist im Grunde eine Implementierung von [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::FromIDispatch

Rufen Sie diese `IDispatch` Funktion auf, um einen Zeiger, der `CCmdTarget` von Automatisierungsmemberfunktionen einer `IDispatch` Klasse empfangen wird, dem Objekt zuzuordnen, das die Schnittstellen des Objekts implementiert.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parameter

*lpDispatch*<br/>
Ein Zeiger auf ein `IDispatch` -Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CCmdTarget` das Objekt, das *lpDispatch*zugeordnet ist. Diese Funktion gibt `IDispatch` NULL zurück, wenn das `IDispatch` Objekt nicht als Microsoft Foundation Class-Objekt erkannt wird.

### <a name="remarks"></a>Bemerkungen

Das Ergebnis dieser Funktion ist die Umkehrung `GetIDispatch`eines Aufrufs der Memberfunktion .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID

Ruft die primäre Dispatchschnittstellen-ID ab.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parameter

*pIID*<br/>
Ein Zeiger auf eine Schnittstellen-ID (eine [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE. Bei Erfolg \* wird *pIID* auf die primäre Dispatchschnittstellen-ID festgelegt.

### <a name="remarks"></a>Bemerkungen

Abgeleitete Klassen sollten diese Memberfunktion überschreiben `GetDispatchIID` (wenn nicht überschrieben, gibt FALSE zurück). Siehe [COleControl](../../mfc/reference/colecontrol-class.md).

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch

Rufen Sie diese Memberfunktion auf, um den `IDispatch` Zeiger `IDispatch` von einer `IDispatch` Automatisierungsmethode abzurufen, die entweder einen Zeiger zurückgibt oder einen Zeiger als Verweis verwendet.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parameter

*bAddRef*<br/>
Gibt an, ob die Referenzanzahl für das Objekt erhöht werden soll.

### <a name="return-value"></a>Rückgabewert

Der `IDispatch` dem Objekt zugeordnete Zeiger.

### <a name="remarks"></a>Bemerkungen

Für Objekte, `EnableAutomation` die ihre Konstruktoren aufrufen und sie automatisiert aktivieren, gibt diese `IDispatch` Funktion einen Zeiger auf `IDispatch` die Foundation Class-Implementierung zurück, der von Clients verwendet wird, die über die Schnittstelle kommunizieren. Wenn Sie diese Funktion aufrufen, wird automatisch ein Verweis auf den Zeiger hinzugefügt, sodass es nicht erforderlich ist, einen Aufruf von [IUnknown::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)zu tätigen.

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount

Ruft die Anzahl der Typinformationsschnittstellen ab, die ein Objekt bereitstellt.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Typinformationsschnittstellen.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert im Grunde [iDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Abgeleitete Klassen sollten diese Funktion überschreiben, um die Anzahl der bereitgestellten Typinformationsschnittstellen (entweder 0 oder 1) zurückzugeben. Wenn nicht überschrieben, `GetTypeInfoCount` gibt 0 zurück. Um zu überschreiben, verwenden Sie das `GetTypeLib` `GetTypeLibCache` [IMPLEMENT_OLETYPELIB-Makro,](../../mfc/reference/type-library-access.md#implement_oletypelib) das auch implementiert und .

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid

Ruft die Typenbeschreibung ab, die der angegebenen GUID entspricht.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parameter

*lcid*<br/>
Ein Gebietsschema-Bezeichner ( `LCID`).

*guid*<br/>
Die [GUID](/previous-versions/cc317743(v%3dmsdn.10)) der Typbeschreibung.

*ppTypeInfo*<br/>
Zeiger auf einen Zeiger `ITypeInfo` auf die Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT, das den Erfolg oder Misserfolg des Aufrufs angibt. Bei Erfolg \* verweist *ppTypeInfo* auf die Typinformationsschnittstelle.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib

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
Ein Zeiger auf einen Zeiger `ITypeLib` auf die Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT, das den Erfolg oder Misserfolg des Aufrufs angibt. Bei Erfolg \* verweist *ppTypeLib* auf die Typbibliotheksschnittstelle.

### <a name="remarks"></a>Bemerkungen

Abgeleitete Klassen sollten diese Memberfunktion überschreiben `GetTypeLib` (wenn nicht überschrieben, gibt TYPE_E_CANTLOADLIBRARY zurück). Verwenden Sie das IMPLEMENT_OLETYPELIB-Makro, `GetTypeLibCache`das auch implementiert [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) `GetTypeInfoCount` wird, und .

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache

Ruft den Typbibliothekscache ab.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CTypeLibCache`-Objekt.

### <a name="remarks"></a>Bemerkungen

Abgeleitete Klassen sollten diese Memberfunktion überschreiben `GetTypeLibCache` (wenn nicht überschrieben, gibt NULL zurück). Verwenden Sie das IMPLEMENT_OLETYPELIB-Makro, `GetTypeLib`das auch implementiert [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) `GetTypeInfoCount` wird, und .

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed

Diese Funktion wird von der `IDispatch::Invoke` MFC-Implementierung aufgerufen, um zu bestimmen, ob eine bestimmte Automatisierungsmethode (identifiziert durch *dispid*) aufgerufen werden kann.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Eine Dispatch-ID.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode aufgerufen werden kann, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn `IsInvokeAllowed` TRUE `Invoke` zurückgegeben wird, wird die Methode aufruft. andernfalls `Invoke` schlägt sie fehl und gibt E_UNEXPECTED zurück.

Abgeleitete Klassen können diese Funktion überschreiben, um `IsInvokeAllowed` geeignete Werte zurückzugeben (wenn nicht überschrieben, gibt TRUE zurück). Siehe insbesondere [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected

Verwenden `IsResultExpected` Sie diese Verwendung, um festzustellen, ob ein Client einen Rückgabewert von seinem Aufruf an eine Automatisierungsfunktion erwartet.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Automatisierungsfunktion einen Wert zurückgeben soll; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die OLE-Schnittstelle liefert MFC Informationen darüber, ob der Client das Ergebnis eines Funktionsaufrufs verwendet oder ignoriert, `IsResultExpected`und MFC verwendet diese Informationen wiederum, um das Ergebnis eines Aufrufs von zu bestimmen. Wenn die Produktion eines Rückgabewerts zeit- oder ressourcenintensiv ist, können Sie die Effizienz erhöhen, indem Sie diese Funktion aufrufen, bevor Sie den Rückgabewert berechnen.

Diese Funktion gibt 0 nur einmal zurück, sodass Sie gültige Rückgabewerte von anderen Automatisierungsfunktionen erhalten, wenn Sie sie von der Automatisierungsfunktion aufrufen, die der Client aufgerufen hat.

`IsResultExpected`gibt einen Wert ungleich Null zurück, wenn ein Automatisierungsfunktionsaufruf nicht ausgeführt wird.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg

Wird vom Framework aufgerufen, um Befehlsmeldungen weiterzuleiten und zu versenden und die Aktualisierung von Befehlsbenutzeroberflächenobjekten zu verarbeiten.

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
Identifiziert den Befehlsbenachrichtigungscode. Weitere Informationen zu Werten für *nCode*finden Sie unter **Hinweise** .

*pExtra*<br/>
Wird entsprechend dem Wert von *nCode*verwendet. Weitere Informationen zu *pExtra*finden Sie unter **Hinweise** .

*pHandlerInfo*<br/>
Wenn nicht `OnCmdMsg` NULL, füllt die *pTarget-* und *pmf-Member* der *pHandlerInfo-Struktur* aus, anstatt den Befehl zu senden. In der Regel sollte dieser Parameter NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies ist die Hauptimplementierungsroutine der Frameworkbefehlsarchitektur.

Zur Laufzeit `OnCmdMsg` wird ein Befehl an andere Objekte gesendet oder der `CCmdTarget::OnCmdMsg`Befehl selbst verarbeitet, indem die root-Klasse aufgerufen wird, die die eigentliche Nachrichtenzuordnungssuche ausführt. Eine vollständige Beschreibung des Standardbefehlsroutings finden Sie unter [Nachrichtenbehandlung und Zuordnungsthemen](../../mfc/message-handling-and-mapping.md).

In seltenen Fällen sollten Sie diese Memberfunktion überschreiben, um die Standardbefehlsrouting des Frameworks zu erweitern. Ausführliche Informationen zur Befehlsrouting-Architektur finden Sie in [Technical Note 21.](../../mfc/tn021-command-and-message-routing.md)

Wenn Sie `OnCmdMsg`überschreiben, müssen Sie den entsprechenden Wert für *nCode*, den Befehlsbenachrichtigungscode und *pExtra*angeben, der vom Wert von *nCode*abhängt. In der folgenden Tabelle sind die entsprechenden Werte aufgeführt:

|*nCode-Wert*|*pExtra-Wert*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease

Wird vom Framework aufgerufen, wenn der letzte OLE-Verweis auf oder aus dem Objekt freigegeben wird.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine spezielle Handhabung für diese Situation bereitzustellen. Die Standardimplementierung löscht das Objekt.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor

Rufen Sie diese Funktion auf, um den entsprechenden Sanduhrcursor wiederherzustellen, nachdem sich der Systemcursor geändert hat (z. B. nachdem ein Meldungsfeld geöffnet und dann geschlossen wurde, während er sich mitten in einem längeren Vorgang befindet).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel ACDUAL](../../overview/visual-cpp-samples.md)<br/>
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
