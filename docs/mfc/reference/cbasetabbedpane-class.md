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
ms.openlocfilehash: ce7c48263ed511545757c94d61552e6206e74a00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352856"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane-Klasse

Erweitert die Funktionalität von [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) , um die Erstellung von Fenstern im Registerkartenformat zu unterstützen

## <a name="syntax"></a>Syntax

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Fügt einem Registerkartenbereich eine neue Registerkarte hinzu.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Gibt an, ob ein leerer Registerkartenbereich zerstört werden kann.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Wendet Tabstoppeinstellungen, die aus der Registrierung geladen werden, auf einen Registerkartenbereich an.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Bestimmt, ob der Bereich schweben kann. (Überschreibt [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Legt fest, ob die Beschriftung für den Registerkartenbereich denselben Text wie die aktive Registerkarte anzeigen soll.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Überschreibt [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Konvertiert einen oder mehrere andockbare Bereiche in MDI-Tabbed-Dokumente.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Aktiviert oder deaktiviert die Möglichkeit des Registerkartenbereichs, Beschriftungstext mit dem Beschriftungstext auf der aktiven Registerkarte zu synchronisieren.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Stellt die interne Registerkartenreihenfolge in einem Standardzustand wieder her.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Gibt einen Bereich zurück, der sich in einer Registerkarte befindet, wenn die Registerkarte durch einen nullbasierten Registerkartenindex identifiziert wird.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Gibt einen Bereich zurück, der durch die Bereichs-ID identifiziert wird.|
|[CBaseTabbedPane::FloatTab](#floattab)|Hebt die Verankerung eines Bereichs auf, aber nur, wenn der Bereich sich auf einer lösbaren Registerkarte befindet.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Gibt die Standardreihenfolge der Registerkarten im Bereich zurück.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Ruft einen Zeiger auf die zuerst angezeigte Registerkarte ab.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Ruft die für den Bereich zulässige Mindestgröße ab. (Überschreibt [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Gibt ein Handle an das Bereichssymbol zurück. (Überschreibt [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Gibt eine Liste der Bereiche zurück, die im Registerkartenbereich enthalten sind.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Gibt die umgrenzenden Rechtecke für den oberen und unteren Tabstoppbereich zurück.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Gibt die Anzahl der Registerkarten in einem Registerkartenfenster zurück.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Ruft das zugrunde liegende (umschlossene) Registerkartenfenster ab.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Gibt die Anzahl der angezeigten Registerkarten zurück.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Legt fest, ob der Registerkartenbereich in den Auto-Hide-Modus geschaltet werden kann.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Legt fest, ob der Registerkartenbereich ausgeblendet ist, wenn nur eine Registerkarte angezeigt wird.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Wird intern während der Serialisierung verwendet.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Berechnet die Layoutinformationen für den Bereich neu. (Überschreibt [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Entfernt einen Bereich aus dem Registerkartenbereich.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Wird intern während der Serialisierung verwendet.|
|`CBaseTabbedPane::Serialize`|(Überschreibt [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Wird intern während der Serialisierung verwendet.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Legt fest, ob die Registerkarten-Steuerleiste automatisch zerstört wird.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Schaltet den Andockbereich zwischen dem angezeigten und dem automatischen Ausblendmodus um. (Überschreibt [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::ShowTab](#showtab)|Zeigt eine Registerkarte an oder blendet sie aus.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist eine abstrakte Klasse und kann nicht instanziiert werden. Es implementiert die Dienste, die allen Arten von Registerkartenbereichen gemeinsam sind.

Derzeit enthält die Bibliothek zwei abgeleitete Registerkartenbereichsklassen: [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) und [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Ein `CBaseTabbedPane` Objekt umschließt einen Zeiger auf ein [CMFCBaseTabCtrl-Klassenobjekt.](../../mfc/reference/cmfcbasetabctrl-class.md) [Die CMFCBaseTabCtrl-Klasse](../../mfc/reference/cmfcbasetabctrl-class.md) wird dann zu einem untergeordneten Fenster des Registerkartenbereichs.

Weitere Informationen zum Erstellen von Registerkartenbereichen finden Sie unter [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)und [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::AddTab

Fügt einem Registerkartenbereich eine neue Registerkarte hinzu.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parameter

*pNewBar*<br/>
[in, out] Ein Zeiger auf den hinzuzufügenden Bereich. Dieser Zeiger kann ungültig werden, nachdem Sie diese Methode aufrufen. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

*bVisible*<br/>
[in] TRUE, um die Registerkarte sichtbar zu machen; andernfalls FALSE.

*bSetActive*<br/>
[in] TRUE, um die Registerkarte zur aktiven Registerkarte zu machen; andernfalls FALSE.

*bAbnehmbar*<br/>
[in] TRUE, um die Registerkarte abnehmbar zu machen; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich erfolgreich als Registerkarte hinzugefügt und dabei nicht zerstört wurde. FALSE, wenn der hinzugefügte Bereich `CBaseTabbedPane`ein Objekt vom Typ ist. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um einen Bereich als neue Registerkarte in einem Registerkartenbereich hinzuzufügen. Wenn *pNewBar* auf ein `CBaseTabbedPane`Objekt vom Typ zeigt, werden alle Registerkarten in den Registerkartenbereich kopiert, und dann wird *pNewBar* zerstört. Daher wird *pNewBar* zu einem ungültigen Zeiger und sollte nicht verwendet werden.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Gibt an, ob ein leerer Registerkartenbereich zerstört werden kann.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein leerer Tabbed-Bereich zerstört werden kann; andernfalls FALSE. Die Standardimplementierung gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Wenn ein leerer Registerkartenbereich nicht zerstört werden darf, blendet das Framework stattdessen den Bereich aus.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Lädt Tabstoppeinstellungen aus der Registrierung und wendet sie auf einen Registerkartenbereich an.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parameter

*bUseTabIndizes*<br/>
[in] Dieser Parameter wird intern vom Framework verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn Dockingstatusinformationen aus der Registrierung neu geladen werden. Die Methode ruft Informationen zur Registerkartenreihenfolge und zu Dentabnamen für einen Registerkartenbereich ab.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat

Gibt an, ob der Registerkartenbereich schweben kann.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich schweben kann; andernfalls FALSE.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Legt fest, ob die Beschriftung für den Registerkartenbereich denselben Text wie die aktive Registerkarte anzeigen soll.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Beschriftungstext des Registerkartenbereichs auf den Text der aktiven Registerkarte festgelegt ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Methode wird verwendet, um zu bestimmen, ob der Text, der in der Beschriftung des Registerkartenbereichs angezeigt wird, die Beschriftung der aktiven Registerkarte dupliziert. Sie können diese Funktionalität aktivieren oder deaktivieren, indem Sie [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)aufrufen.

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Konvertiert einen oder mehrere andockbare Bereiche in MDI-Tabbed-Dokumente.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parameter

*bActiveTabOnly*<br/>
[in] Wenn Sie einen Registerkartenbereich konvertieren, geben Sie TRUE an, um nur die aktive Registerkarte zu konvertieren. Geben Sie FALSE an, um alle Registerkarten im Bereich zu konvertieren.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane

Trennt einen Bereich aus dem Registerkartenbereich.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in] Zeigen Sie auf den Bereich, um den Bereich zu trennen.

*bHide*<br/>
[in] Boolescher Parameter, der angibt, ob das Framework den Bereich ausblendet, nachdem er getrennt wurde.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Framework den Bereich erfolgreich trennt; FALSE, wenn *pBar* NULL ist oder auf einen Bereich verweist, der sich nicht im Registerkartenbereich befindet.

### <a name="remarks"></a>Bemerkungen

Das Framework schwebt den getrennten Bereich nach Möglichkeit. Weitere Informationen finden Sie unter [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Aktiviert oder deaktiviert die Möglichkeit des Registerkartenbereichs, Beschriftungstext mit dem Beschriftungstext auf der aktiven Registerkarte zu synchronisieren.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die Beschriftung des Registerkartenbereichs mit der aktiven Tabstoppbeschriftung zu synchronisieren; andernfalls FALSE.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Stellt die interne Registerkartenreihenfolge in einem Standardzustand wieder her.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn das Framework eine Outlook-Leiste in einen Anfangszustand wiederherstellt.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Gibt einen Bereich zurück, der durch die Bereichs-ID identifiziert wurde.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parameter

*uBarID*<br/>
[in] Gibt die ID des zu suchenden Bereichs an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Bereich, wenn er gefunden wurde; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode vergleicht alle Registerkarten im Bereich und gibt die Registerkarte mit der ID zurück, die durch den Parameter *uBarID* angegeben wird.

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Gibt einen Bereich zurück, der sich in einer Registerkarte befindet.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parameter

*nTabNum*<br/>
[in] Gibt den nullbasierten Index der abzurufenden Registerkarte an.

*bGetWrappedBar*<br/>
[in] TRUE, um das zugrunde liegende (umschlossene) Fenster des Bereichs anstelle des Bereichs selbst zurückzugeben; andernfalls FALSE. Dies gilt nur für Bereiche, die von [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)abgeleitet wurden.

### <a name="return-value"></a>Rückgabewert

Wenn der Bereich gefunden wird, wird ein gültiger Zeiger auf den gesuchten Bereich zurückgegeben. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Bereich abzurufen, der sich in der Registerkarte befindet, die durch den Parameter *nTabNum* angegeben wird.

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab

Hebt die Verankerung eines Bereichs auf, aber nur, wenn der Bereich sich auf einer lösbaren Registerkarte befindet.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in, out] Ein Zeiger auf den zu schwebenden Bereich.

*nTabID*<br/>
[in] Gibt den nullbasierten Index der Registerkarte an, die schweben soll.

*dockMethode*<br/>
[in] Gibt die Methode an, die verwendet werden soll, um den Bereich float enden zu lassen. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.

*bHide*<br/>
[in] TRUE, um den Bereich vor dem Floating auszublenden; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich überlauft wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um einen Bereich freizugeben, der sich derzeit in einer abnehmbaren Registerkarte befindet.

Wenn Sie einen Bereich programmgesteuert trennen möchten, geben Sie DM_SHOW für den Parameter *dockMethod* an. Wenn Sie den Bereich an der gleichen Position schweben lassen möchten, an der er zuvor schwebte, geben Sie DM_DBL_CLICK als *dockMethod-Parameter* an.

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Gibt die Standardreihenfolge der Registerkarten im Bereich zurück.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Rückgabewert

Ein `CArray` Objekt, das die Standardreihenfolge der Registerkarten im Bereich angibt.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn eine Outlook-Leiste auf einen Anfangszustand zurückgesetzt wird.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Ruft einen Zeiger auf die zuerst angezeigte Registerkarte ab.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parameter

*iTabNum*<br/>
[in] Ein Verweis auf eine ganze Zahl. Diese Methode schreibt den nullbasierten Index der ersten angezeigten Registerkarte in diesen Parameter oder -1, wenn keine angezeigte Registerkarte gefunden wird.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Zeiger auf die erste angezeigte Registerkarte; andernfalls NULL.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Ruft die für den Bereich zulässige Mindestgröße ab.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
[out] Ein `CSize` Objekt, das mit der minimal zulässigen Größe gefüllt ist.

### <a name="remarks"></a>Bemerkungen

Wenn die konsistente Handhabung der minimalen Bereichsgrößen aktiv ist ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), wird die *Größe* mit der für die aktive Registerkarte zulässigen Mindestgröße gefüllt. Andernfalls wird die *Größe* mit dem Rückgabewert [von CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)gefüllt.

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Ruft die für den Bereich zulässige Mindestgröße ab.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
[out] Ein `CSize` Objekt, das mit der minimal zulässigen Größe gefüllt ist.

### <a name="remarks"></a>Bemerkungen

Wenn die konsistente Handhabung der minimalen Bereichsgrößen aktiv ist ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), wird die *Größe* mit der für die aktive Registerkarte zulässigen Mindestgröße gefüllt. Andernfalls wird die *Größe* mit dem Rückgabewert [von CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)gefüllt.

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::GetPaneList

Gibt eine Liste der Bereiche zurück, die im Registerkartenbereich enthalten sind.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
[out] Eine, `CObList` die mit den Bereichen gefüllt ist, die im Registerkartenbereich enthalten sind.

*pRTCFilter*<br/>
[in] Wenn es sich nicht um NULL handelt, enthält die zurückgegebene Liste nur Bereiche, die der angegebenen Laufzeitklasse angehören.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Gibt die umgrenzenden Rechtecke für den oberen und unteren Tabstoppbereich zurück.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parameter

*rectTabAreaTop*<br/>
[out] Empfängt die Bildschirmkoordinaten des oberen Tab-Bereichs.

*rectTabAreaBottom*<br/>
[out] Empfängt die Bildschirmkoordinaten des unteren Tab-Bereichs.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die umgrenzenden Rechtecke in Bildschirmkoordinaten für den oberen und unteren Tabbereich zu bestimmen.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Gibt die Anzahl der Registerkarten in einem Registerkartenfenster zurück.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Registerkarten im Registerkartenbereich.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Ruft das zugrunde liegende (umschlossene) Registerkartenfenster ab.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zugrunde liegende Registerkartenfenster.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Gibt die Anzahl der sichtbaren Registerkarten zurück.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der sichtbaren Registerkarten, die größer oder gleich Null ist.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der sichtbaren Registerkarten im Registerkartenbereich zu bestimmen.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Bestimmt, ob der Bereich im Registerkartenformat automatisch in den Hintergrundmodus gewechselt werden kann.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich in den Autohide-Modus geschaltet werden kann; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn der Autohide-Modus deaktiviert ist, wird auf der Beschriftung des Registerkartenbereichs keine Pin-Schaltfläche angezeigt.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Legt fest, ob der Registerkartenbereich ausgeblendet ist, wenn nur eine Registerkarte angezeigt wird.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Registerkartenfenster nicht angezeigt wird, wenn nur eine Registerkarte sichtbar ist. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn der Bereich nicht angezeigt wird, weil nur eine Registerkarte geöffnet ist, können Sie diese Methode aufrufen, um zu bestimmen, ob der Registerkartenbereich ordnungsgemäß funktioniert.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::RemovePane

Entfernt einen Bereich aus dem Registerkartenbereich.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in, out] Ein Zeiger auf den Bereich, den aus dem Registerkartenbereich entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Bereich erfolgreich aus dem Registerkartenbereich entfernt wurde und der Registerkartenbereich weiterhin gültig ist. FALSE, wenn der letzte Bereich aus dem Registerkartenbereich entfernt wurde und der Registerkartenbereich kurz vor dem Zerstören steht. Wenn der Rückgabewert FALSE ist, verwenden Sie den Registerkartenbereich nicht mehr.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den durch den *parameter pBar* angegebenen Bereich aus dem Registerkartenbereich zu entfernen.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Legt fest, ob die Registerkarten-Steuerleiste automatisch zerstört wird.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*bAutoDestroy*<br/>
[in] TRUE, wenn der Registerkartenbereich dynamisch erstellt wurde und Sie seine Lebensdauer nicht steuern; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Legen Sie den Auto-Destroy-Modus auf TRUE fest, wenn Sie einen Registerkartenbereich dynamisch erstellen und die Lebensdauer nicht steuern. Wenn der Auto-Destroy-Modus TRUE ist, wird der Registerkartenbereich automatisch vom Framework zerstört.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::ShowTab

Zeigt eine Registerkarte an oder blendet sie aus.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in] Ein Zeiger auf den Bereich, der ein- oder ausgeblendet werden soll.

*bShow*<br/>
[in] TRUE, um den Bereich anzuzeigen; FALSE, um den Bereich auszublenden.

*bDelay*<br/>
[in] TRUE, um die Anpassung des Tab-Layouts zu verzögern; andernfalls FALSE.

*bAktivieren*<br/>
[in] TRUE, um die Registerkarte zur aktiven Registerkarte zu machen; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Registerkarte entweder angezeigt oder erfolgreich ausgeblendet wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Methode aufrufen, wird ein Bereich angezeigt oder ausgeblendet, abhängig vom Wert des *Parameters bShow.* Wenn Sie eine Registerkarte ausblenden und sie die letzte sichtbare Registerkarte im zugrunde liegenden Registerkartenfenster ist, wird der Registerkartenbereich ausgeblendet. Wenn Sie eine Registerkarte anzeigen, wenn zuvor keine Registerkarten sichtbar waren, wird der Registerkartenbereich angezeigt.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Berechnet die Layoutinformationen für den Bereich neu.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Bereich unverankert ist, benachrichtigt diese Methode das Framework, die Größe des Bereichs auf die aktuelle Größe des Miniframes zu ändern.

Wenn der Bereich angedockt ist, bewirkt diese Methode nichts.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Legt den Auto-Hide-Modus für abnehmbare Bereiche im Registerkartenbereich fest.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parameter

*bMode*<br/>
[in] TRUE, um den Auto-Hide-Modus zu aktivieren; FALSE, um den regulären Andockmodus zu aktivieren.

*dwAlignment*<br/>
[in] Gibt die Ausrichtung des zu erstellenden automatischen Ausblendbereichs an. Eine Liste möglicher Werte finden Sie unter [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[in, out] Ein Zeiger auf die aktuelle Symbolleiste zum automatischen Ausblenden. Kann den Wert NULL haben.

*bUseTimer*<br/>
[in] Gibt an, ob der Effekt zum automatischen Ausblenden verwendet werden soll, wenn der Benutzer den Bereich in den Auto-Ausblendmodus wechselt, oder ob der Bereich sofort ausgeblendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Symbolleiste, die beim Wechseln in den Auto-Hide-Modus erstellt wird, oder NULL, wenn keine Symbolleiste erstellt wird.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn ein Benutzer die Pin-Schaltfläche wählt, um den Registerkartenbereich in den automatischen Ausblendmodus oder in den regulären Andockmodus zu wechseln.

Der Auto-Hide-Modus wird für jeden abnehmbaren Bereich im Registerkartenbereich festgelegt. Bereiche, die nicht abnehmbar sind, werden ignoriert. Weitere Informationen finden Sie unter [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Rufen Sie diese Methode auf, um einen Registerkartenbereich programmgesteuert in den auto-hide-Modus zu wechseln. Der Bereich muss an das Hauptrahmenfenster angedockt werden ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) muss einen gültigen Zeiger auf den [CPaneDivider](../../mfc/reference/cpanedivider-class.md)zurückgeben).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)
