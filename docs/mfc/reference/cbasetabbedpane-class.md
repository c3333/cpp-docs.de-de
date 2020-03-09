---
title: CBaseTabbedPane-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883659"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane-Klasse

Erweitert die Funktionalität von [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) , um die Erstellung von Fenstern im Registerkartenformat zu unterstützen

## <a name="syntax"></a>Syntax

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cbasetabbedpane:: addTab](#addtab)|Fügt eine neue Registerkarte zu einem Bereich im Registerkarten Format hinzu.|
|[Cbasetabbedpane:: allowdestroyemptytabbedpane](#allowdestroyemptytabbedpane)|Gibt an, ob ein leerer Bereich im Registerkarten Format zerstört werden kann.|
|[Cbasetabbedpane:: applyrestoredtabinfo](#applyrestoredtabinfo)|Wendet Tabulator Einstellungen, die aus der Registrierung geladen werden, in einen Bereich im Registerkarten Format an.|
|[Cbasetabbedpane:: canfloat](#canfloat)|Bestimmt, ob der Bereich float werden kann. (Überschreibt [cbasepane:: canfloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[Cbasetabbedpane:: cansetcaptiontextbacktabname](#cansetcaptiontexttotabname)|Bestimmt, ob die Beschriftung für den Bereich im Registerkarten Format denselben Text wie die aktive Registerkarte anzeigen soll.|
|[Cbasetabbedpane:: convertumtabbeddocument](#converttotabbeddocument)|(Überschreibt [CDockablePane:: convertumtabbeddocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[Cbasetabbedpane::D etachpane](#detachpane)|Konvertiert einen oder mehrere andockbare Bereiche in MDI-Dokumente im Register Format.|
|[Cbasetabbedpane:: enablesetcaptiontexttoken Name](#enablesetcaptiontexttotabname)|Aktiviert oder deaktiviert die Fähigkeit des Bereichs im Registerkarten Format, Beschriftungs Text mit dem Bezeichnungs Text auf der aktiven Registerkarte zu synchronisieren.|
|[Cbasetabbedpane:: filldefaulttabsorderarray](#filldefaulttabsorderarray)|Stellt die interne Aktivier Reihenfolge in einem Standardzustand wieder her.|
|[Cbasetabbedpane:: findbarbytabnumber](#findbarbytabnumber)|Gibt einen Bereich zurück, der sich auf einer Registerkarte befindet, wenn die Registerkarte durch einen NULL basierten Registerkarten Index identifiziert wird.|
|||
|[Cbasetabbedpane:: findpanebyid](#findpanebyid)|Gibt einen Bereich zurück, der durch die Bereichs-ID identifiziert wird.|
|[Cbasetabbedpane:: floattab](#floattab)|Hebt die Verankerung eines Bereichs auf, aber nur, wenn der Bereich sich auf einer lösbaren Registerkarte befindet.|
|[Cbasetabbedpane:: getdefaulttabsorder](#getdefaulttabsorder)|Gibt die Standard Reihenfolge der Registerkarten im Bereich zurück.|
|[Cbasetabbedpane:: getfirstvisibletab](#getfirstvisibletab)|Ruft einen Zeiger auf die erste angezeigte Registerkarte ab.|
|[Cbasetabbedpane:: getminsize](#getminsize)|Ruft die minimal zulässige Größe für den Bereich ab. (Überschreibt [CPANE:: getminsize](../../mfc/reference/cpane-class.md#getminsize).)|
|[Cbasetabbedpane:: getpaneicon](#getpaneicon)|Gibt ein Handle für das Bereichs Symbol zurück. (Überschreibt [cbasepane:: getpaneicon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[Cbasetabbedpane:: getpanelist](#getpanelist)|Gibt eine Liste der Bereiche zurück, die im Bereich im Registerkarten Format enthalten sind.|
|[Cbasetabbedpane:: gettabarea](#gettabarea)|Gibt die Begrenzungs Rechtecke für den oberen und unteren Tabstopp Bereich zurück.|
|[Cbasetabbedpane:: gettabsnum](#gettabsnum)|Gibt die Anzahl der Registerkarten in einem Registerkarten Fenster zurück.|
|[Cbasetabbedpane:: getunderlyingwindow](#getunderlyingwindow)|Ruft das zugrunde liegende (umschließte) Registerkarten Fenster ab.|
|[Cbasetabbedpane:: getvisibletabsnum](#getvisibletabsnum)|Gibt die Anzahl der angezeigten Registerkarten zurück.|
|[Cbasetabbedpane:: hasautohidemode](#hasautohidemode)|Bestimmt, ob der Bereich im Registerkarten Format in den Modus für automatisches ausblenden gewechselt werden kann.|
|[Cbasetabbedpane:: ishidesintons ab](#ishidesingletab)|Bestimmt, ob der Bereich im Registerkarten Format ausgeblendet wird, wenn nur eine Registerkarte angezeigt wird.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Wird intern während der Serialisierung verwendet.|
|[Cbasetabbedpane:: Neuberechnen](#recalclayout)|Berechnet Layoutinformationen für den Bereich neu. (Überschreibt [CPANE:: Neuberechnung](../../mfc/reference/cpane-class.md#recalclayout).)|
|[Cbasetabbedpane:: removepane](#removepane)|Entfernt einen Bereich aus dem Bereich im Registerkarten Format.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Wird intern während der Serialisierung verwendet.|
|`CBaseTabbedPane::Serialize`|(Überschreibt [CDockablePane:: Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Wird intern während der Serialisierung verwendet.|
|[Cbasetabbedpane:: abtauwechseln](#setautodestroy)|Bestimmt, ob die Steuerleiste im Registerkarten Format automatisch zerstört wird.|
|[Cbasetabbedpane:: abtautehidemode](#setautohidemode)|Schaltet den Andock Bereich zwischen dem angezeigten und dem automatisch Ausblend baren Modus um. (Überschreibt [CDockablePane:: abtautrehidemode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[Cbasetabbedpane:: showTab](#showtab)|Blendet eine Registerkarte ein oder aus.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist eine abstrakte Klasse und kann nicht instanziiert werden. Es implementiert die Dienste, die allen Arten von Bereichen im Registerkarten Format gemeinsam sind.

Die Bibliothek enthält derzeit zwei abgeleitete Bereichs Klassen im Registerkarten Format: [ctabbedpane-Klasse](../../mfc/reference/ctabbedpane-class.md) und [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md).

Ein `CBaseTabbedPane`-Objekt umschließt einen Zeiger auf ein [cmfcbasetabctrl-Klassen](../../mfc/reference/cmfcbasetabctrl-class.md) Objekt. Die [cmfcbasetabctrl-Klasse](../../mfc/reference/cmfcbasetabctrl-class.md) wird dann zu einem untergeordneten Fenster des Bereichs im Registerkarten Format.

Weitere Informationen zum Erstellen von Bereichen im Registerkarten Format finden Sie unter [CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md), [ctabbedpane](../../mfc/reference/ctabbedpane-class.md)-Klasse und [CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxbasetabbedpane. h

##  <a name="addtab"></a>Cbasetabbedpane:: addTab

Fügt eine neue Registerkarte zu einem Bereich im Registerkarten Format hinzu.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parameter

*pnewbar*<br/>
[in, out] Ein Zeiger auf den hinzu zufügenden Bereich. Dieser Zeiger wird möglicherweise ungültig, nachdem Sie diese Methode aufgerufen haben. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

*bvisible*<br/>
in TRUE, um die Registerkarte sichtbar zu machen. andernfalls false.

*bsetactive*<br/>
in TRUE, um die Registerkarte als aktive Registerkarte zu ändern. andernfalls false.

*bdetaerbar*<br/>
in TRUE, damit die Registerkarte getrennt wird. andernfalls false.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich erfolgreich als Registerkarte hinzugefügt wurde und im Prozess nicht zerstört wurde. FALSE, wenn der hinzugefügte Bereich ein Objekt vom Typ `CBaseTabbedPane`ist. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie einen Bereich als neue Registerkarte in einem Bereich im Registerkarten Format hinzufügen. Wenn *pnewbar* auf ein Objekt vom Typ `CBaseTabbedPane`zeigt, werden alle zugehörigen Registerkarten in den Bereich im Registerkarten Format kopiert, und dann wird *pnewbar* zerstört. Daher wird *pnewbar* zu einem ungültigen Zeiger und sollte nicht verwendet werden.

##  <a name="allowdestroyemptytabbedpane"></a>Cbasetabbedpane:: allowdestroyemptytabbedpane

Gibt an, ob ein leerer Bereich im Registerkarten Format zerstört werden kann.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein leerer Bereich im Registerkarten Format zerstört werden kann. andernfalls false. Die Standard Implementierung gibt immer true zurück.

### <a name="remarks"></a>Bemerkungen

Wenn ein leerer Bereich im Registerkarten Format nicht zerstört werden darf, verbirgt das Framework stattdessen den Bereich.

##  <a name="applyrestoredtabinfo"></a>Cbasetabbedpane:: applyrestoredtabinfo

Lädt Tabulator Einstellungen aus der Registrierung und wendet Sie auf einen Bereich im Registerkarten Format an.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parameter

*"buabtabindexes"*<br/>
in Dieser Parameter wird intern vom Framework verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn die Andock Zustandsinformationen aus der Registrierung erneut geladen werden. Die-Methode ruft Informationen zu Aktivier Reihenfolge und Registerkarten Namen für einen Bereich im Register Format ab.

##  <a name="canfloat"></a>Cbasetabbedpane:: canfloat

Gibt an, ob der Bereich im Registerkarten Format float werden kann.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich float werden kann. andernfalls false.

##  <a name="cansetcaptiontexttotabname"></a>Cbasetabbedpane:: cansetcaptiontextbacktabname

Bestimmt, ob die Beschriftung für den Bereich im Registerkarten Format denselben Text wie die aktive Registerkarte anzeigen soll.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Beschriftungs Text des Bereichs im Registerkarten Format auf den Text der aktiven Registerkarte festgelegt ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Die-Methode wird verwendet, um zu bestimmen, ob der Text, der im Bereich im Registerkarten Bereich angezeigt wird, die Bezeichnung der aktiven Registerkarte dupliziert. Sie können diese Funktion aktivieren oder deaktivieren, indem Sie [cbasetabbedpane:: enablesetcaptiontexttotabname](#enablesetcaptiontexttotabname)aufrufen.

##  <a name="converttotabbeddocument"></a>Cbasetabbedpane:: convertumtabbeddocument

Konvertiert einen oder mehrere andockbare Bereiche in MDI-Dokumente im Register Format.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parameter

*bactivetabonly*<br/>
in Beim Konvertieren eines Bereichs im Registerkarten Format geben Sie true an, um nur die aktive Registerkarte zu konvertieren. Geben Sie false an, um alle Registerkarten im Bereich zu konvertieren.

##  <a name="detachpane"></a>Cbasetabbedpane::D etachpane

Trennt einen Bereich aus dem Bereich im Registerkarten Format.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

*pbar*<br/>
in Zeiger auf den Bereich, der getrennt werden soll.

*Bhide*<br/>
in Boolescher Parameter, der angibt, ob das Framework den Bereich nach dem Trennen ausblendet.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Framework den Bereich erfolgreich trennt. FALSE, wenn *pbar* NULL ist oder auf einen Bereich verweist, der nicht im Registerkarten Bereich angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Das Framework schwebt nach Möglichkeit im getrennten Bereich. Weitere Informationen finden Sie unter [cbasepane:: canfloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>Cbasetabbedpane:: enablesetcaptiontexttoken Name

Aktiviert oder deaktiviert die Fähigkeit des Bereichs im Registerkarten Format, Beschriftungs Text mit dem Bezeichnungs Text auf der aktiven Registerkarte zu synchronisieren.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in TRUE, um die Beschriftung des Registerkarten Bereichs mit der Titelleiste der aktiven Registerkarte zu synchronisieren. andernfalls false.

##  <a name="filldefaulttabsorderarray"></a>Cbasetabbedpane:: filldefaulttabsorderarray

Stellt die interne Aktivier Reihenfolge in einem Standardzustand wieder her.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn das Framework eine Outlook-Leiste in einem Anfangszustand wiederherstellt.

##  <a name="findpanebyid"></a>Cbasetabbedpane:: findpanebyid

Gibt einen Bereich zurück, der durch die Pane-ID identifiziert wird.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parameter

*ubarid*<br/>
in Gibt die ID des zu suchenden Bereichs an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Bereich, wenn er gefunden wurde. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode vergleicht alle Registerkarten im Bereich und gibt die mit der ID zurück, die durch den *ubarid* -Parameter angegeben wird.

##  <a name="findbarbytabnumber"></a>Cbasetabbedpane:: findbarbytabnumber

Gibt einen Bereich zurück, der sich auf einer Registerkarte befindet.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parameter

*ntabnum*<br/>
in Gibt den NULL basierten Index der abzurufenden Registerkarte an.

*bgetwrappedbar*<br/>
in TRUE, wenn das zugrunde liegende (umschließte) Fenster des Bereichs anstelle des Bereichs selbst zurückgegeben werden soll. andernfalls false. Dies gilt nur für Bereiche, die von [cdockablepaneadapter](../../mfc/reference/cdockablepaneadapter-class.md)abgeleitet werden.

### <a name="return-value"></a>Rückgabewert

Wenn der Bereich gefunden wird, wird ein gültiger Zeiger auf den Bereich zurückgegeben, der gesucht wird. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Bereich abzurufen, der sich auf der durch den *ntabnum* -Parameter angegebenen Registerkarte befindet.

##  <a name="floattab"></a>Cbasetabbedpane:: floattab

Hebt die Verankerung eines Bereichs auf, aber nur, wenn der Bereich sich auf einer lösbaren Registerkarte befindet.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

*pbar*<br/>
[in, out] Ein Zeiger auf den Bereich, um zu schweben.

*ntabid*<br/>
in Gibt den NULL basierten Index der zu gleitenden Registerkarte an.

*dockmethod*<br/>
in Gibt die Methode an, die verwendet werden soll, um den Bereich zu ändern. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

*Bhide*<br/>
in TRUE, um den Bereich vor dem Gleit Komma ausblenden. andernfalls false.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich angezeigt wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie einen Bereich, der sich zurzeit in einer ablösbaren Registerkarte befindet, float.

Wenn Sie einen Bereich Programm gesteuert trennen möchten, geben Sie DM_SHOW für den Parameter " *dockmethod* " an. Wenn Sie den Bereich an derselben Position, an der er zuvor platziert hat, in den Bereich verschieben möchten, geben Sie DM_DBL_CLICK als *dockmethod* -Parameter an.

##  <a name="getdefaulttabsorder"></a>Cbasetabbedpane:: getdefaulttabsorder

Gibt die Standard Reihenfolge der Registerkarten im Bereich zurück.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Rückgabewert

Ein `CArray`-Objekt, das die Standard Reihenfolge der Registerkarten im Bereich angibt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn eine Outlook-Leiste auf einen Ausgangszustand zurückgesetzt wird.

##  <a name="getfirstvisibletab"></a>Cbasetabbedpane:: getfirstvisibletab

Ruft einen Zeiger auf die erste angezeigte Registerkarte ab.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parameter

*itabnum*<br/>
in Ein Verweis auf eine ganze Zahl. Diese Methode schreibt den NULL basierten Index der ersten angezeigten Registerkarte in diesen Parameter oder-1, wenn keine angezeigte Registerkarte gefunden wird.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Zeiger auf die erste angezeigte Registerkarte; andernfalls NULL.

##  <a name="getminsize"></a>Cbasetabbedpane:: getminsize

Ruft die minimal zulässige Größe für den Bereich ab.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parameter

*size*<br/>
vorgenommen Ein `CSize`-Objekt, das mit der minimal zulässigen Größe aufgefüllt ist.

### <a name="remarks"></a>Bemerkungen

Wenn die konsistente Verarbeitung der minimalen Fenstergrößen aktiv ist ( [CPANE:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), wird die *Größe* mit der minimal zulässigen Größe für die aktive Registerkarte aufgefüllt. andernfalls wird die *Größe* mit dem Rückgabewert von [CPANE:: getminsize](../../mfc/reference/cpane-class.md#getminsize)aufgefüllt.

##  <a name="getpaneicon"></a>Cbasetabbedpane:: getpaneicon

Ruft die minimal zulässige Größe für den Bereich ab.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parameter

*size*<br/>
vorgenommen Ein `CSize`-Objekt, das mit der minimal zulässigen Größe aufgefüllt ist.

### <a name="remarks"></a>Bemerkungen

Wenn die konsistente Verarbeitung der minimalen Fenstergrößen aktiv ist ( [CPANE:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), wird die *Größe* mit der minimal zulässigen Größe für die aktive Registerkarte aufgefüllt. andernfalls wird die *Größe* mit dem Rückgabewert von [CPANE:: getminsize](../../mfc/reference/cpane-class.md#getminsize)aufgefüllt.

##  <a name="getpanelist"></a>Cbasetabbedpane:: getpanelist

Gibt eine Liste der Bereiche zurück, die im Bereich im Registerkarten Format enthalten sind.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parameter

*LST*<br/>
vorgenommen Eine `CObList`, die mit den Bereichen gefüllt ist, die im Registerkarten Bereich enthalten sind.

*prtcfilter*<br/>
in Wenn der Wert nicht NULL ist, enthält die zurückgegebene Liste nur Bereiche, die der angegebenen Lauf Zeit Klasse entsprechen.

##  <a name="gettabarea"></a>Cbasetabbedpane:: gettabarea

Gibt die Begrenzungs Rechtecke für den oberen und unteren Tabstopp Bereich zurück.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parameter

*recttabareon*<br/>
vorgenommen Empfängt die Bildschirm Koordinaten des oberen Registerkarten Bereichs.

*recttabareabottom*<br/>
vorgenommen Empfängt die Bildschirm Koordinaten des unteren Registerkarten Bereichs.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie die Begrenzungs Rechtecke in Bildschirm Koordinaten für die oberen und unteren Registerkarten Bereiche bestimmen.

##  <a name="gettabsnum"></a>Cbasetabbedpane:: gettabsnum

Gibt die Anzahl der Registerkarten in einem Registerkarten Fenster zurück.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Registerkarten im Bereich im Registerkarten Format.

##  <a name="getunderlyingwindow"></a>Cbasetabbedpane:: getunderlyingwindow

Ruft das zugrunde liegende (umschließte) Registerkarten Fenster ab.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zugrunde liegende Registerkarten Fenster.

##  <a name="getvisibletabsnum"></a>Cbasetabbedpane:: getvisibletabsnum

Gibt die Anzahl der sichtbaren Registerkarten zurück.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der sichtbaren Registerkarten, die größer oder gleich 0 (null) ist.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie die Anzahl der sichtbaren Registerkarten im Bereich im Registerkarten Format ermitteln.

##  <a name="hasautohidemode"></a>Cbasetabbedpane:: hasautohidemode

Bestimmt, ob der Bereich im Registerkartenformat automatisch in den Hintergrundmodus gewechselt werden kann.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich in den Automatisches Ausblenden-Modus gewechselt werden kann. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn der Modus für automatisches ausblenden deaktiviert ist, wird keine PIN-Schaltfläche auf der Titelleiste im Registerkarten Format angezeigt.

##  <a name="ishidesingletab"></a>Cbasetabbedpane:: ishidesintons ab

Bestimmt, ob der Bereich im Registerkarten Format ausgeblendet wird, wenn nur eine Registerkarte angezeigt wird.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Registerkarten Fenster nicht angezeigt wird, wenn nur eine Registerkarte angezeigt wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn der Bereich nicht angezeigt wird, weil nur eine Registerkarte geöffnet ist, können Sie mit dieser Methode ermitteln, ob der Bereich im Registerkarten Format ordnungsgemäß funktioniert.

##  <a name="removepane"></a>Cbasetabbedpane:: removepane

Entfernt einen Bereich aus dem Bereich im Registerkarten Format.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parameter

*pbar*<br/>
[in, out] Ein Zeiger auf den Bereich, der aus dem Bereich im Registerkarten Format entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich erfolgreich aus dem Bereich im Registerkarten Format entfernt wurde und der Bereich im Registerkarten Format noch gültig ist. FALSE, wenn der letzte Bereich aus dem Bereich im Registerkarten Format entfernt wurde und der Bereich im Registerkarten Format zerstört werden soll. Wenn der Rückgabewert FALSE ist, verwenden Sie nicht den Bereich im Registerkarten Format.

### <a name="remarks"></a>Bemerkungen

Aufrufen Sie diese Methode, um den Bereich zu entfernen, der durch den *pbar* -Parameter aus dem Registerkarten Bereich angegeben wird.

##  <a name="setautodestroy"></a>Cbasetabbedpane:: abtauwechseln

Bestimmt, ob die Steuerleiste im Registerkarten Format automatisch zerstört wird.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*Bauto zerstören*<br/>
in TRUE, wenn der Bereich im Registerkarten Format dynamisch erstellt wurde und ihre Lebensdauer nicht kontrolliert wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Legen Sie den Modus für automatische Zerstörung auf true fest, wenn Sie einen Bereich im Registerkarten Format dynamisch erstellen und die Lebensdauer nicht kontrollieren. Wenn der Modus für automatische Zerstörung den Wert true hat, wird der Bereich im Registerkarten Format automatisch durch das Framework zerstört.

##  <a name="showtab"></a>Cbasetabbedpane:: showTab

Blendet eine Registerkarte ein oder aus.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*pbar*<br/>
in Ein Zeiger auf den Bereich, der angezeigt oder ausgeblendet werden soll.

*bShow*<br/>
in TRUE, um den Bereich anzuzeigen. FALSE, um den Bereich auszublenden.

*bdelay*<br/>
in TRUE, wenn die Anpassung des Registerkarten Layouts verzögert werden soll. andernfalls false.

*bactivate*<br/>
in TRUE, um die Registerkarte als aktive Registerkarte zu ändern. andernfalls false.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Registerkarte erfolgreich angezeigt oder ausgeblendet wurde. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, wird ein Bereich je nach Wert des *bShow* -Parameters entweder angezeigt oder ausgeblendet. Wenn Sie eine Registerkarte ausblenden und es sich um die letzte sichtbare Registerkarte im zugrunde liegenden Registerkarten Fenster handelt, wird der Bereich im Registerkarten Format ausgeblendet. Wenn Sie eine Registerkarte anzeigen, wenn zuvor keine Registerkarten angezeigt wurden, wird der Bereich im Registerkarten Format angezeigt.

##  <a name="recalclayout"></a>Cbasetabbedpane:: Neuberechnen

Berechnet Layoutinformationen für den Bereich neu.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Bereich unverankert ist, benachrichtigt diese Methode das Framework, die Größe des Bereichs auf die aktuelle Größe des Mini Rahmens zu ändern.

Wenn der Bereich angedockt ist, führt diese Methode keine Aktion aus.

##  <a name="setautohidemode"></a>Cbasetabbedpane:: abtautehidemode

Legt den Modus für das automatische Ausblenden von trennbaren Bereichen im Registerkarten Bereich fest.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parameter

*bmode*<br/>
in TRUE, wenn der Modus für Automatisches Ausblenden aktiviert werden soll. FALSE zum Aktivieren des regulären Andock Modus.

*dwalignment*<br/>
in Gibt die Ausrichtung des Bereichs für Automatisches Ausblenden an, der erstellt werden soll. Eine Liste möglicher Werte finden Sie unter [CPANE:: muvebyalignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pcurrrauumhidebar*<br/>
[in, out] Ein Zeiger auf die aktuelle automatisch ausblenden-Symbolleiste. Kann den Wert NULL haben.

*"bustitimer"*<br/>
in Gibt an, ob der automatische Ausblend Effekt verwendet werden soll, wenn der Benutzer den Bereich in den Modus für automatisches ausblenden wechselt, oder um den Bereich sofort auszublenden.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die automatisch Ausblend Bare Symbolleiste, die erstellt wird, wenn in den Modus für automatisches ausblenden gewechselt wird, oder NULL, wenn keine Symbolleiste erstellt wird.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn ein Benutzer die PIN-Schaltfläche auswählt, um den Bereich im Registerkarten Format in den Modus für automatisches ausblenden oder den regulären Docking Modus zu wechseln.

Der Modus für Automatisches Ausblenden wird für jeden ablösbaren Bereich im Bereich im Registerkarten Format festgelegt. Bereiche, die nicht lösbar sind, werden ignoriert. Weitere Informationen finden Sie unter [cmfcbasetabctrl:: enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Mit dieser Methode können Sie einen Bereich im Registerkarten Format Programm gesteuert in den Modus für automatisches ausblenden wechseln. Der Bereich muss an das Hauptrahmen Fenster angedockt werden ( [CDockablePane:: getdefaultpanedivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) muss einen gültigen Zeiger auf den [cpanedivider](../../mfc/reference/cpanedivider-class.md)zurückgeben).

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
