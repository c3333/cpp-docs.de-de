---
title: CTooltipManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 4e721740fc100a34ea08dd7ff5f9291eea2d9b36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752165"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager-Klasse

Verwaltet Laufzeitinformationen über QuickInfos. Die `CTooltipManager` -Klasse wird einmal pro Anwendung instanziiert.

## <a name="syntax"></a>Syntax

```
class CTooltipManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|Erstellt ein QuickInfo-Steuerelement für die angegebenen Windows-Steuerelementtypen.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Löscht ein QuickInfo-Steuerelement.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Passt die visuelle Darstellung des QuickInfo-Steuerelements für die angegebenen Windows-Steuerelementtypen an.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Legt den Text und die Beschreibung für ein QuickInfo-Steuerelement fest.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Bemerkungen

Verwenden Sie [die CMFCToolTipCtrl-Klasse](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`und `CTooltipManager` implementieren Sie gemeinsam benutzerdefinierte QuickInfos in Ihrer Anwendung. Ein Beispiel für die Verwendung dieser QuickInfo-Klassen finden Sie im Thema [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) Class.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxtooltipmanager.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::CreateToolTip

Erstellt ein QuickInfo-Steuerelement.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parameter

*pToolTip*<br/>
[out] Ein Verweis auf einen QuickInfo-Zeiger. Sie wird so eingestellt, dass sie auf die neu erstellte QuickInfo zeigen soll, wenn die Funktion zurückkehrt.

*pWndParent*<br/>
[in] Übergeordnetes Element der QuickInfo.

*nType*<br/>
[in] Typ der QuickInfo.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn eine QuickInfo erfolgreich erstellt wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [CTooltipManager::DeleteToolTip](#deletetooltip) aufrufen, um das QuickInfo-Steuerelement zu löschen, das in *pToolTip*zurückübergeben wird.

Der [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) legt die visuellen Anzeigeparameter jeder QuickInfo fest, die er basierend auf dem von *nType* angegebenen QuickInfo-Typ erstellt. Um die Parameter für einen oder mehrere QuickInfo-Typen zu ändern, rufen Sie [CTooltipManager::SetTooltipParams](#settooltipparams)auf.

Gültige QuickInfo-Typen sind in der folgenden Tabelle aufgeführt:

|Tooltip-Typ|Steuerungskategorie|Beispieltypen|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Eine Schaltfläche.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Eine Beschriftungsleiste.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Jedes Steuerelement, das nicht zu einer anderen Kategorie passt.|Keine.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Ein andockbarer Bereich.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Ein Textfeld.|Keine.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Ein Miniframe.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Ein Planer.|Keine.|
|AFX_TOOLTIP_TYPE_RIBBON|Eine Bandleiste.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Ein Registerkartensteuerelement.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Eine Symbolleiste.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Eine Toolbox.|Keine.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip

Löscht ein QuickInfo-Steuerelement.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parameter

*pToolTip*<br/>
[in, out] Ein Verweis auf einen Zeiger auf eine zu zerstörende QuickInfo.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode für jede [CToolTipCtrl-Klasse](../../mfc/reference/ctooltipctrl-class.md) auf, die von [CTooltipManager::CreateToolTip](#createtooltip)erstellt wurde. Das übergeordnete Steuerelement sollte diese `OnDestroy` Methode von seinem Handler aufrufen. Dies ist erforderlich, um die QuickInfo korrekt aus dem Framework zu entfernen. Diese Methode legt *pToolTip* auf NULL fest, bevor sie zurückgegeben wird.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams

Passt die Darstellung des QuickInfo-Steuerelements für die angegebenen Windows-Steuerelementtypen an.

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parameter

*nTypen*<br/>
[in] Gibt Steuerelementtypen an.

*Prtc*<br/>
[in] Laufzeitklasse benutzerdefinierter QuickInfo.

*pParams*<br/>
[in] QuickInfo-Parameter.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt die Laufzeitklasse und die Anfangsparameter fest, die der [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) beim Erstellen von QuickInfos verwendet. Wenn ein Steuerelement [CTooltipManager::CreateToolTip](#createtooltip) aufruft und einen QuickInfo-Typ übergibt, der einer der von *nTypes*angegebenen Typen ist, erstellt der QuickInfo-Manager ein QuickInfo-Steuerelement, das eine Instanz der von *pRTC* angegebenen Laufzeitklasse ist und die von *pParams* angegebenen Parameter an die neue QuickInfo übergibt.

Wenn Sie diese Methode aufrufen, erhalten alle vorhandenen QuickInfo-Besitzer die AFX_WM_UPDATETOOLTIPS Nachricht, und sie müssen ihre QuickInfos mithilfe von [CTooltipManager::CreateToolTip](#createtooltip)neu erstellen.

*nTypes* kann eine beliebige Kombination der gültigen QuickInfo-Typen sein, die [CTooltipManager::CreateToolTip](#createtooltip) verwendet, oder es kann AFX_TOOLTIP_TYPE_ALL sein. Wenn Sie AFX_TOOLTIP_TYPE_ALL übergeben, sind alle QuickInfo-Typen betroffen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `SetTooltipParams` veranschaulicht, `CTooltipManager` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Draw Client-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText

Legt den Text und die Beschreibung für eine QuickInfo fest.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>Parameter

*Pti*<br/>
[in] Ein Zeiger auf ein TOOLINFO-Objekt.

*pToolTip*<br/>
[in, out] Ein Zeiger auf das QuickInfo-Steuerelement, für das der Text und die Beschreibung festgelegt werden sollen.

*nType*<br/>
[in] Gibt den Typ des Steuerelements an, dem diese QuickInfo zugeordnet ist.

*strText*<br/>
[in] Der Text, der als Quickinfo-Text festgelegt werden soll.

*lpszDescr*<br/>
[in] Ein Zeiger auf die Tooltip-Beschreibung. Kann den Wert NULL haben.

### <a name="remarks"></a>Bemerkungen

Der Wert von *nType* muss derselbe Wert wie der *nType-Parameter* von [CTooltipManager::CreateToolTip](#createtooltip) sein, wenn Sie die QuickInfo erstellt haben.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl-Klasse](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo-Klasse](../../mfc/reference/cmfctooltipinfo-class.md)
