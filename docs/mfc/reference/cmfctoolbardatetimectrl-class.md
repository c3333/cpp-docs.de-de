---
title: CMFCToolBarDateTimeCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372177"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl-Klasse

Eine Symbolleistenschaltfläche, die ein Datums- und Uhrzeitauswahlsteuerelement enthält.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Erstellt ein `CMFCToolBarDateTimeCtrl`-Objekt.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Gibt an, ob ein Benutzer die Schaltfläche während der Anpassung dehnen kann. (Überschreibt [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::Kopierenvon](#copyfrom)|Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche. (Überschreibt [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Für die zukünftige Verwendung reserviert.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopiert Text aus der Symbolleistenschaltfläche in ein Menü.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Ruft das `CMFCToolBarDateTimeCtrl` erste Objekt in der Anwendung ab, das über die angegebene Befehls-ID verfügt.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Gibt einen Zeiger auf das Datums- und Uhrzeitauswahlsteuerelement zurück.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Ruft den Fensterhandle ab, der der Symbolleistenschaltfläche zugeordnet ist. (Überschreibt [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Ruft die ausgewählte Uhrzeit aus einem Datums- und Uhrzeitauswahlsteuerelement ab und fügt sie in eine angegebene [SYSTEMTIME-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) ein.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Gibt die ausgewählte Zeit von der Zeitauswahlsteuerungsschaltfläche zurück, die über eine angegebene Befehls-ID verfügt.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Bestimmt, ob ein Rahmen der Schaltfläche angezeigt wird, wenn ein Benutzer die Schaltfläche auswählt. (Überschreibt [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Gibt an, ob die Schaltfläche die [WM_COMMAND-Nachricht](/windows/win32/menurc/wm-command) verarbeitet. (Überschreibt [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Wird vom Framework aufgerufen, wenn die Schaltfläche zu einem Dialogfeld **Anpassen** hinzugefügt wird. (Überschreibt [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Wird vom Framework aufgerufen, um die Größe der Schaltfläche für den angegebenen Gerätekontext und Andockstatus zu berechnen. (Überschreibt [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird. (Überschreibt [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Wird vom Framework aufgerufen, wenn der Benutzer auf das Steuerelement klickt. (Überschreibt [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_CTLCOLOR Nachricht verarbeitet. (Überschreibt [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Wird vom Framework aufgerufen, um die Schaltfläche mithilfe der angegebenen Stile und Optionen zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Wird vom Framework aufgerufen, um **Commands** die Schaltfläche im Befehlsbereich des Dialogfelds **Anpassen** zu zeichnen. (Überschreibt [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Wird vom Framework aufgerufen, wenn sich die globale Schriftart geändert hat. (Überschreibt [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste verschoben wird. (Überschreibt [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Wird vom Framework aufgerufen, wenn die Schaltfläche sichtbar oder unsichtbar wird. (Überschreibt [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste ihre Größe oder Position ändert und diese Änderung dazu führt, dass die Schaltfläche die Größe ändert. (Überschreibt [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste den QuickInfo-Text aktualisiert. (Überschreibt [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Liest dieses Objekt aus einem Archiv oder schreibt es in ein Archiv (Überschreibt [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Legt den Stil der Symbolleistenschaltfläche fest. (Überschreibt [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Legt die Uhrzeit und das Datum im Zeitauswahlsteuerelement fest.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Legt die Uhrzeit und das Datum in allen Instanzen des Zeitauswahlsteuerelements fest, die über eine angegebene Befehls-ID verfügen.|

## <a name="remarks"></a>Bemerkungen

Ein Beispiel für die Verwendung eines Datums- und Zeitauswahlsteuerelements finden Sie im Beispielprojekt ToolbarDateTimePicker. Informationen zum Hinzufügen von Steuerschaltflächen zu Symbolleisten finden Sie unter [Exemplarische Vorgehensweise: Einstecken von Steuerelementen auf Symbolleisten](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Gibt an, ob ein Benutzer die Schaltfläche während der Anpassung dehnen kann.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig erlaubt das Framework dem Benutzer nicht, eine Symbolleistenschaltfläche während der Anpassung zu dehnen. Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), indem der Benutzer während der Anpassung eine Datums- und Uhrzeitsymbolleistenschaltfläche erweitern kann.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Erstellt und initialisiert ein [CMFCToolBarDateTimeCtrl-Objekt.](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die Steuerelement-ID.

*iImage*<br/>
[in] Der Index des Bildes im `CMFCToolBarImages` Objekt der Symbolleiste.

*dwStyle*<br/>
[in] Der Stil `CMFCToolBarDateTimeCtrlImpl` des Fensters, das erstellt wird, wenn ein Benutzer auf die Schaltfläche klickt.

*iWidth*<br/>
[in] Die Breite des Steuerelements in Pixel.

### <a name="remarks"></a>Bemerkungen

Dieses Objekt wird auf das Systemdatum und die Systemzeit initialisiert. Der Fensterstil des `CMFCToolBarDateTimeCtrlImpl` internen Objekts enthält den *Parameter dwStyle* und die WS_CHILD- und WS_VISIBLE-Formatvorlagen. Sie können diese Stile `CMFCToolBarDateTimeCtrl::SetStyle`nicht ändern, indem Sie . Verwenden `SetStyle` Sie diese Datei, um den Stil des Steuerelements `CMFCToolBarDateTimeCtrl` zu ändern.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCToolBarDateTimeCtrl` wie ein Objekt der Klasse erstellt wird. Dieser Codeausschnitt ist Teil des [Toolbar Date Time Picker-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::Kopierenvon

Kopiert die Eigenschaften einer anderen Symbolleistenschaltfläche in die aktuelle Schaltfläche.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Ein Verweis auf die Quellschaltfläche, aus der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine weitere Symbolleistenschaltfläche in diese Symbolleistenschaltfläche zu kopieren. *src* muss vom `CMFCToolBarDateTimeCtrl`Typ sein.

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

Kopiert Text aus der Symbolleistenschaltfläche in ein Menü.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parameter

*menuButton*<br/>
[in] Ein Verweis auf die Zielmenüschaltfläche.

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), indem die Zeichenfolgenressource geladen wird, die der Befehls-ID des Steuerelements zugeordnet ist. Weitere Informationen zu Zeichenfolgenressourcen finden Sie unter [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Ruft das `CMFCToolBarDateTimeCtrl` erste Objekt in der Anwendung ab, das über die angegebene Befehls-ID verfügt.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Die Befehls-ID der abzurufenden Schaltfläche.

### <a name="return-value"></a>Rückgabewert

Das `CMFCToolBarDateTimeCtrl` erste Objekt in der Anwendung, das die `CMFCToolBarDateTimeCtrl` angegebene Befehls-ID hat, oder NULL, wenn keine Objekte die angegebene Befehls-ID haben.

### <a name="remarks"></a>Bemerkungen

Diese gemeinsame Dienstprogrammmethode wird von Methoden wie [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) und [CMFCToolBarTimeTimeCtrl::GetTimeAll](#gettimeall) verwendet, um die Uhrzeit und das Datum aller Instanzen des Zeitauswahlsteuerelements festzulegen oder abzubekommen, die über eine angegebene Befehls-ID verfügen.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Gibt einen Zeiger auf das Datums- und Uhrzeitauswahlsteuerelement zurück.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf Datum s and Time Picker-Steuerelement; oder NULL, wenn das Steuerelement nicht vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Die `CMFCToolBarDateTimeCtrl` Klasse initialisiert `m_pWndDateTime` den Datenmember, `CMFCToolBarDateTimeCtrl` wenn Sie ein Objekt in eine Symbolleiste einfügen.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

Ruft den Fensterhandle ab, der der Symbolleistenschaltfläche zugeordnet ist.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Rückgabewert

Das Fensterhandle, das der Schaltfläche Datums- und Uhrzeitsymbolleiste zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die [CMFCToolBarButton::GetHwnd-Methode.](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime

Ruft die ausgewählte Zeit aus dem zugeordneten Datums- und Uhrzeitauswahlsteuerelement ab und legt sie in eine angegebene [SYSTEMTIME-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parameter

*timeDest*<br/>
[out] Bei der ersten Überladung ein [COleDateTime-Class-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das die Systemzeitinformationen empfängt. In der zweiten Überladung ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Systemzeitinformationen empfängt.

*pTimeDest*<br/>
[out] Ein Zeiger auf die [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) um die Systemzeitinformationen zu erhalten. Darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Bei der ersten Überladung ungleich Null, wenn die Zeit erfolgreich in das [COleDateTime-Klassenobjekt](../../atl-mfc-shared/reference/coledatetime-class.md) geschrieben wurde. andernfalls 0. Bei der zweiten und dritten Überladung ist der Rückgabewert ein DWORD, das dem dwFlag-Member entspricht, der in der [NMDATETIMECHANGE-Struktur](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Die Methode legt das [NMDATETIMECHANGE-Strukturelement](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) dwFlags fest, um anzugeben, ob die Datums- und Uhrzeitauswahl auf ein Datum und eine Uhrzeit festgelegt ist. Wenn der Wert GDT_NONE entspricht, wird `no date` das Steuerelement auf Status festgelegt und verwendet den DTS_SHOWNONE-Stil. Wenn der zurückgegebene Wert GDT_VALID entspricht, wird die Systemzeit erfolgreich am Zielspeicherort gespeichert.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Gibt die vom Benutzer ausgewählte Zeit aus der Schaltfläche zeitauswahlsteuerelement mit einer angegebenen Befehls-ID zurück.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Gibt die Befehls-ID einer Symbolleistenschaltfläche an.

*timeDest*<br/>
[out] Bei der ersten Überladung ein [COleDateTime-Class-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das die Systemzeitinformationen empfängt. In der zweiten Überladung ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Systemzeitinformationen empfängt.

*pTimeDest*<br/>
[out] Ein Zeiger auf die [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) um die Systemzeitinformationen zu erhalten. Darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Wenn das Framework keine Symbolleistenschaltfläche finden kann, die der Befehls-ID *uiCmd*entspricht, ist der Rückgabewert bei der ersten Überladung Null, und GDT_NONE in den anderen Überladungen. Wenn die Symbolleistenschaltfläche gefunden wird, entspricht der Rückgabewert mit dem Rückgabewert eines Aufrufs von [CMFCToolBarDateTimeCtrl::GetTime](#gettime) auf dieser Schaltfläche. Ein Rückgabewert von Null oder GDT_NONE kann auftreten, wenn die `GetTime` Schaltfläche gefunden wird, was darauf hinweist, dass der Aufruf von nicht ein gültiges Datum aus einem anderen Grund zurückgegeben hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode sucht nach einer Symbolleistenschaltfläche, die über die angegebene Befehls-ID verfügt und [die CMFCToolBarDateTimeCtrl::GetTime-Methode](#gettime) auf dieser Schaltfläche aufruft.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Bestimmt, ob ein Rahmen der Schaltfläche angezeigt wird, wenn ein Benutzer die Schaltfläche auswählt.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine Schaltfläche den Rahmen anzeigt, wenn diese ausgewählt ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt einen Wert ungleich Null zurück, wenn das Steuerelement sichtbar ist.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Gibt an, ob die Schaltfläche die [WM_COMMAND-Nachricht](/windows/win32/menurc/wm-command) verarbeitet.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parameter

*iNotifyCode*<br/>
[in] Die dem Befehl zugeordnete Benachrichtigung.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Schaltfläche die WM_COMMAND Nachricht verarbeitet, oder FALSE, um anzuzeigen, dass die Nachricht von der übergeordneten Symbolleiste behandelt werden soll.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn es eine [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht an das übergeordnete Fenster senden soll.

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) durch Verarbeitung der [DTN_DATETIMECHANGE-Benachrichtigung.](/windows/win32/Controls/dtn-datetimechange) Es aktualisiert den internen Zeitstatus und `CMFCToolBarDateTimeCtrl` aktualisiert die Zeiteigenschaft aller Objekte mit derselben Befehls-ID.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Wird vom Framework aufgerufen, wenn die Schaltfläche zu einem Dialogfeld **Anpassen** hinzugefügt wird.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), indem die Eigenschaften aus dem ersten Datums- und Uhrzeitsteuerelement in eine Symbolleiste kopiert werden, die dieselbe Befehls-ID wie dieses Objekt hat. Diese Methode bewirkt nichts, wenn keine Symbolleiste über eine Datums- und Uhrzeitsteuerung verfügt, die dieselbe Befehls-ID wie dieses Objekt hat.

Weitere Informationen zum Dialogfeld **Anpassen** finden Sie unter [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Wird vom Framework aufgerufen, wenn die Schaltfläche in eine neue Symbolleiste eingefügt wird.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Das neue übergeordnete Fenster.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), indem das interne `CMFCToolBarDateTimeCtrlImpl` Objekt neu erstellt wird.

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick

Wird vom Framework aufgerufen, wenn der Benutzer auf das Steuerelement klickt.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
[in] Nicht verwendet.

*bDelay*<br/>
[in] Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche die Klicknachricht verarbeitet; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), indem ein `CMFCToolBarDateTimeCtrlImpl` Wert ungleich Null zurückgegeben wird, wenn das interne Objekt sichtbar ist.

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste eine WM_CTLCOLOR Nachricht verarbeitet.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Der Gerätekontext, der die Schaltfläche anzeigt.

*nCtlColor*<br/>
[in] Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Handle für den globalen Pinsel, den das Framework verwendet, um den Hintergrund der Schaltfläche zu malen.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Basisklassenimplementierung [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), indem die Text- und Hintergrundfarben des bereitgestellten Gerätekontexts auf die globalen Text- bzw. Hintergrundfarben gesetzt werden.

Weitere Informationen zu globalen Optionen, die Für Ihre Anwendung verfügbar sind, finden Sie unter [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Wird vom Framework aufgerufen, wenn sich die globale Schriftart geändert hat.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), indem die Schriftart des Steuerelements in die Der globalen Schriftart geändert wird.

Weitere Informationen zu globalen Optionen, die Für Ihre Anwendung verfügbar sind, finden Sie unter [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste verschoben wird.

```
virtual void OnMove();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Standardklassenimplementierung ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), `CMFCToolBarDateTimeCtrlImpl` indem die Position des internen Objekts aktualisiert wird.

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

Wird vom Framework aufgerufen, wenn die Schaltfläche sichtbar oder unsichtbar wird.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
[in] Gibt an, ob die Schaltfläche sichtbar ist. Wenn dieser Parameter TRUE ist, ist die Schaltfläche sichtbar. Andernfalls ist die Schaltfläche nicht sichtbar.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)), indem die Schaltfläche angezeigt wird, wenn *bShow* TRUE ist. Andernfalls blendet diese Methode die Schaltfläche aus.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste ihre Größe oder Position ändert und diese Änderung dazu führt, dass die Schaltfläche die Größe ändert.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parameter

*iSize*<br/>
[in] Die neue Breite der Schaltfläche in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Methode überschreibt die Standardklassenimplementierung ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)), indem `CMFCToolBarDateTimeCtrlImpl` die Größe und Position des internen Objekts aktualisiert wird.

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

Wird vom Framework aufgerufen, wenn die übergeordnete Symbolleiste den QuickInfo-Text aktualisiert.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Das übergeordnete Fenster.

*iButtonIndex*<br/>
[in] Der nullbasierte Index der Schaltfläche in der übergeordneten Schaltflächenauflistung.

*wndToolTip*<br/>
[in] Das Steuerelement, das den QuickInfo-Text anzeigt.

*Str*<br/>
[out] Ein `CString` Objekt, das den aktualisierten QuickInfo-Text empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode den QuickInfo-Text aktualisiert. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode erweitert die Basisklassenimplementierung ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)), indem der der Schaltfläche zugeordnete QuickInfo-Text angezeigt wird. Wenn die Schaltfläche nicht horizontal angedockt ist, führt diese Methode nichts aus und gibt FALSE zurück.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime

Legt die Uhrzeit und das Datum im Zeitauswahlsteuerelement fest.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parameter

*timeNeu*<br/>
[in] In der ersten Version ein Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) Class-Objekt, das die Zeit enthält, für die das Steuerelement festgelegt wird. In der zweiten Version ein Zeiger auf ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Zeit enthält, für die das Steuerelement festgelegt wird.

*pTimeNew*<br/>
[in] Ein Zeiger auf die [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die Zeit enthält, für die das Steuerelement festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Legt die Uhrzeit in einem Datums- und Uhrzeitauswahlsteuerelement fest, indem [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)aufgerufen wird.

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Legt die Uhrzeit und das Datum in allen Instanzen des Zeitauswahlsteuerelements fest, die über eine angegebene Befehls-ID verfügen.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parameter

*uiCmd*<br/>
[in] Gibt die Befehls-ID einer Symbolleistenschaltfläche an.

*timeNeu*<br/>
[in] In der ersten Version ein [COleDateTime-Class-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das die Zeit enthält, für die das Steuerelement festgelegt wird. In der zweiten Version ein Zeiger auf ein [CTime-Objekt,](../../atl-mfc-shared/reference/ctime-class.md) das die Zeit enthält, für die das Steuerelement festgelegt wird.

*pTimeNew*<br/>
[in] Ein Zeiger auf die [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die die Zeit enthält, für die das Steuerelement festgelegt wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sucht nach einer Symbolleistenschaltfläche mit der angegebenen Befehls-ID und legt die Uhrzeit in einem Datums- und Uhrzeitauswahlsteuerelement fest, indem [CMFCToolBarDateTimeCtrl::SetTime](#settime)aufgerufen wird.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
