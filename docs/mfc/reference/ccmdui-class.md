---
title: CCmdUI-Klasse
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883620"
---
# <a name="ccmdui-class"></a>CCmdUI-Klasse

Wird nur innerhalb eines `ON_UPDATE_COMMAND_UI`-Handlers in einer `CCmdTarget`abgeleiteten Klasse verwendet.

## <a name="syntax"></a>Syntax

```
class CCmdUI
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdUI:: continuerouting](#continuerouting)|Weist den Befehls Routing Mechanismus an, das Routing der aktuellen Nachricht weiter nach unten in der Kette von Handlern durchzuführen.|
|[CCmdUI:: enable](#enable)|Aktiviert oder deaktiviert das Benutzeroberflächen Element für diesen Befehl.|
|[CCmdUI:: setcheck](#setcheck)|Legt den Prüf Zustand des Benutzeroberflächen Elements für diesen Befehl fest.|
|[CCmdUI:: abtradio](#setradio)|Wie die `SetCheck` Member-Funktion, jedoch mit Radiogruppen.|
|[CCmdUI:: SetText](#settext)|Legt den Text für das Benutzeroberflächen Element für diesen Befehl fest.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdUI:: m_nID](#m_nid)|Die ID des Benutzeroberflächen Objekts.|
|[CCmdUI:: m_nIndex](#m_nindex)|Der Index des Benutzeroberflächen Objekts.|
|[CCmdUI:: m_pMenu](#m_pmenu)|Verweist auf das Menü, das durch das `CCmdUI`-Objekt dargestellt wird.|
|[CCmdUI:: m_pOther](#m_pother)|Verweist auf das Fenster Objekt, das die Benachrichtigung gesendet hat.|
|[CCmdUI:: m_pSubMenu](#m_psubmenu)|Verweist auf das enthaltene Untermenü, das durch das `CCmdUI`-Objekt dargestellt wird.|

## <a name="remarks"></a>Bemerkungen

`CCmdUI` verfügt nicht über eine Basisklasse.

Wenn ein Benutzer der Anwendung ein Menü abruft, muss jedes Menü Element wissen, ob es als aktiviert oder deaktiviert angezeigt werden soll. Das Ziel eines Menübefehls bietet diese Informationen durch Implementieren eines ON_UPDATE_COMMAND_UI Handlers. Verwenden Sie für jeden der Befehls Benutzeroberflächen-Objekte in der Anwendung den [Klassen-Assistenten](mfc-class-wizard.md) oder das **Eigenschaften** Fenster (in **Klassenansicht**), um einen Nachrichten Zuordnungs Eintrag und einen Funktionsprototyp für jeden Handler zu erstellen.

Wenn das Menü heruntergeladen wird, sucht das Framework nach den einzelnen ON_UPDATE_COMMAND_UI Handlern und ruft diese auf. Jeder Handler ruft `CCmdUI` Member-Funktionen wie `Enable` und `Check`auf, und das Framework zeigt dann die einzelnen Menü Elemente entsprechend an.

Ein Menü Element kann durch eine Steuer leisten Schaltfläche oder ein anderes Befehls Benutzeroberflächen Objekt ersetzt werden, ohne den Code innerhalb des `ON_UPDATE_COMMAND_UI` Handlers zu ändern.

In der folgenden Tabelle werden die Auswirkungen `CCmdUI`der Element Funktionen auf verschiedene Befehls Benutzeroberflächen Elemente zusammengefasst.

|Benutzeroberflächen Element|Aktivieren|Setcheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Menüelement|Aktiviert oder deaktiviert|Prüft oder nicht Überprüfungen|Überprüfungen mit einem Punkt|Legt Element Text fest.|
|Symbolleistenschaltfläche|Aktiviert oder deaktiviert|SELECT, unselect oder unbestimmt|Identisch mit `SetCheck`|(Nicht vorhanden)|
|Status Leistenbereich|Macht Text sichtbar oder unsichtbar|Legt ein Popup-oder einen normalen Rahmen fest.|Identisch mit `SetCheck`|Bereichs Text festlegen|
|Normale Schaltfläche in `CDialogBar`|Aktiviert oder deaktiviert|Kontrollkästchen zum Überprüfen oder deaktivieren|Identisch mit `SetCheck`|Schaltflächen Text festlegen|
|Normales Steuerelement in `CDialogBar`|Aktiviert oder deaktiviert|(Nicht vorhanden)|(Nicht vorhanden)|Legt Fenster Text fest.|

Weitere Informationen zur Verwendung dieser Klasse finden [Sie unter Aktualisieren von Benutzeroberflächen Objekten](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CCmdUI`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

##  <a name="continuerouting"></a>CCmdUI:: continuerouting

Mit dieser Member-Funktion können Sie den Befehls Routing Mechanismus anweisen, das Routing der aktuellen Nachricht weiter unten in der Kette von Handlern durchzuführen.

```
void ContinueRouting();
```

### <a name="remarks"></a>Bemerkungen

Dabei handelt es sich um eine erweiterte Member-Funktion, die in Verbindung mit einem ON_COMMAND_EX Handler verwendet werden sollte, der false zurückgibt. Weitere Informationen finden Sie unter [Technical Note 6](../../mfc/tn006-message-maps.md).

##  <a name="enable"></a>CCmdUI:: enable

Mit dieser Member-Funktion können Sie das Benutzeroberflächen Element für diesen Befehl aktivieren bzw. deaktivieren.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parameter

*Böller*<br/>
TRUE, um das Element zu aktivieren, false, um es zu deaktivieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI:: m_nID

Die ID des Menü Elements, der Symbolleisten-Schaltfläche oder eines anderen Benutzeroberflächen Objekts, das durch das `CCmdUI` Objekt dargestellt wird.

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI:: m_nIndex

Der Index des Menü Elements, der Symbolleisten-Schaltfläche oder eines anderen Benutzeroberflächen Objekts, das durch das `CCmdUI`-Objekt dargestellt wird.

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI:: m_pMenu

Ein Zeiger (von `CMenu` Typ) auf das Menü, das durch das `CCmdUI`-Objekt dargestellt wird.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn es sich bei dem Element nicht um ein Menü handelt.

##  <a name="m_psubmenu"></a>CCmdUI:: m_pSubMenu

Ein Zeiger (vom Typ `CMenu`) auf das enthaltene Untermenü, das durch das `CCmdUI`-Objekt dargestellt wird.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn es sich bei dem Element nicht um ein Menü handelt. Wenn das Untermenü ein Popup ist, enthält *m_nID* die ID des ersten Elements im Popupmenü. Weitere Informationen finden Sie unter [Technical Note 21](../../mfc/tn021-command-and-message-routing.md).

##  <a name="m_pother"></a>CCmdUI:: m_pOther

Zeiger (vom Typ `CWnd`) auf das Fenster Objekt, z. b. ein Tool oder eine Statusleiste, das die Benachrichtigung gesendet hat.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn das Element ein Menü oder ein Objekt ist, das nicht `CWnd` ist.

##  <a name="setcheck"></a>CCmdUI:: setcheck

Mit dieser Member-Funktion wird das Benutzeroberflächen Element für diesen Befehl auf den entsprechenden Prüf Zustand festgelegt.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parameter

*nPrüfen*<br/>
Gibt den festzulegenden Prüf Zustand an. Wenn 0, wird die Prüfung nicht durchgeführt. bei 1 wird überprüft. und bei 2 wird unbestimmt festgelegt.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion funktioniert für Menü Elemente und Symbolleisten Schaltflächen. Der Status "unbestimmt" gilt nur für Symbolleisten Schaltflächen.

##  <a name="setradio"></a>CCmdUI:: abtradio

Mit dieser Member-Funktion wird das Benutzeroberflächen Element für diesen Befehl auf den entsprechenden Prüf Zustand festgelegt.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parameter

*Böller*<br/>
TRUE, wenn das Element aktiviert werden soll. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion verhält sich wie `SetCheck`, mit dem Unterschied, dass Sie auf Benutzeroberflächen Elementen angewendet wird, die als Teil einer Radiogruppe fungieren. Das Deaktivieren der anderen Elemente in der Gruppe erfolgt nicht automatisch, es sei denn, die Elemente selbst behalten das Verhalten der funkgruppe bei.

##  <a name="settext"></a>CCmdUI:: SetText

Mit dieser Member-Funktion wird der Text des Benutzeroberflächen Elements für diesen Befehl festgelegt.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Ein Zeiger auf eine Text Zeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-MDI](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
