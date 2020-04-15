---
title: CPaneDivider-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: 41fa3204712749a3b1123a20d31b01ba8b5fbaa4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364121"
---
# <a name="cpanedivider-class"></a>CPaneDivider-Klasse

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

Die `CPaneDivider` Klasse teilt zwei Bereiche, teilt zwei Gruppen von Bereichen oder trennt eine Gruppe von Bereichen vom Clientbereich des Hauptrahmenfensters.

## <a name="syntax"></a>Syntax

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Überschreibt [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Überschreibt [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Überschreibt [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Überschreibt [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Überschreibt [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[CPaneDivider::Bewegen](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider::Serialisieren](#serialize)|(Überschreibt `CBasePane::Serialize`.)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Gibt die Liste der Bereiche zurück, die sich in der [CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md)befinden. Diese Methode sollte nur für Standardbereichsteiler aufgerufen werden.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Gibt die Liste der Bereichsteiler zurück, die sich in der [CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md)befinden. Diese Methode sollte nur für Standardbereichsteiler aufgerufen werden.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Gibt die Standardbreite in Pixeln aller Bereichsteiler in der Anwendung an.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Enthält einen Zeiger auf die Laufzeitklasseninformationen zu einem `CPaneDivider`-derived-Objekt.|

## <a name="remarks"></a>Bemerkungen

Das Framework `CPaneDivider` erstellt Objekte automatisch, wenn ein Bereich angedockt ist.

Es gibt zwei Arten von Bereichsteilern:

- Eine Standardbereichstrennwand wird erstellt, wenn eine Gruppe von Bereichen an eine Seite des Hauptrahmenfensters angedockt ist. Die Standardbereichsteilergruppe enthält einen Zeiger auf die [CPaneContainerManager-Klasse](../../mfc/reference/cpanecontainermanager-class.md) und leitet die meisten Vorgänge für die Gruppe von Bereichen (z. B. Ändern der Größe eines Bereichs oder Andocken eines anderen Bereichs oder Containers) an den Container-Manager um. Jeder Andockbereich verwaltet einen Zeiger auf den Standardbereichsteiler.

- Ein normaler Scheibenteiler teilt nur zwei Bereiche in einen Container. Weitere Informationen finden Sie unter [CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt den Abruf eines `CPaneDivider`-Objekts aus einem `CWorkspaceBar`-Objekt. Dieser Codeausschnitt ist Teil des [MDI Tabs Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)\
&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;€&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;€&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxPaneDivider.h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider::SetAutoHideMode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parameter

[in] *bMode*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parameter

[in] *p*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parameter

[in] *barContainerManager*<br/>
[in] *bOuterEdge*<br/>
[in] *pTargetBar*<br/>
[in] *dwAlignment*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parameter

[in] *pWndToDock*<br/>
[in] *ptMouse*<br/>
[in] *rectResult*<br/>
[in] *bDrawTab*<br/>
[in] *ppTargetBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parameter

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividercreateex"></a><a name="createex"></a>CPaneDivider::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parameter

[in] *dwStyleEx*<br/>
[in] *dwStyle*<br/>
[in] *rect*<br/>
[in] *pParentWnd*<br/>
[in] *nID*<br/>
[in] *pContext*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider::DoesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>
[in] *bLeftBar*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parameter

[in] *nID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider::GetPaneDividers

Gibt die Liste der Bereichsteiler zurück, die sich in der [CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md)befinden. Diese Methode sollte nur für Standardbereichsteiler aufgerufen werden.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parameter

*lstSliders*<br/>
[out] Enthält die Liste der Bereichsteiler, die sich im Bereichscontainer befinden.

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte nur für Standardbereichsteiler aufgerufen werden. Eine Standardbereichsteilerung ist eine Trennlinie, die die Größe des gesamten Bereichscontainers ändert.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider::GetPanes

Gibt die Liste der Bereiche zurück, die sich in der [CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md)befinden. Diese Methode sollte nur aufgerufen werden, um Standardbereichsteiler abzurufen.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parameter

*lstBars*<br/>
[out] Enthält die Liste der Bereiche, die sich im Bereichscontainer befinden.

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte nur für Standardbereichsteiler aufgerufen werden. Eine Standardbereichsteilerung ist eine Trennlinie, die die Größe des gesamten Bereichscontainers ändert.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerinit"></a><a name="init"></a>CPaneDivider::Init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parameter

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

[in] *pBarToInsert*<br/>
[in] *pTargetBar*<br/>
[in] *dwAlignment*<br/>
[in] *lpRect*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider::IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth

Gibt die Standardbreite (in Pixel) aller Bereichsteiler in der Anwendung an.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a>CPaneDivider::Bewegen

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parameter

[in] *ptOffset*<br/>
[in] *bAdjustLayout*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC

Enthält einen Zeiger auf Laufzeitklasseninformationen `CPaneDivider`zu einem -abgeleiteten Objekt.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diese Membervariable fest, wenn Sie einen benutzerdefinierten Bereichsteiler erstellen. Dadurch kann das Framework den Bereichsteiler erstellen, wenn der Bereich gezeichnet wird.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, `m_pSliderRTC` wie die Membervariable festgelegt wird:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>
[in] *bShow*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parameter

[in] *pBarToReplace*<br/>
[in] *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parameter

[in] *rectNeu*<br/>
[in] *hdwp*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider::Serialisieren

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

[in] *ar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider::ShowWindow

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parameter

[in] *nCmdShow*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parameter

[in] *pDockingBar*<br/>
[in] *pTabbedBar*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPaneContainerManager-Klasse](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer-Klasse](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager-Klasse](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane-Klasse](../../mfc/reference/cbasepane-class.md)
