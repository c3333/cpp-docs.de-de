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
ms.openlocfilehash: 5f411890575c07e471b02c423aa42ec5bf51ac0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352279"
---
# <a name="ccmdui-class"></a>CCmdUI-Klasse

Wird nur innerhalb `ON_UPDATE_COMMAND_UI` eines `CCmdTarget`Handlers in einer -derived-Klasse verwendet.

## <a name="syntax"></a>Syntax

```
class CCmdUI
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdUI::WeiterRouting](#continuerouting)|Weist den Befehlsroutingmechanismus an, die aktuelle Nachricht weiterhin über die Kette der Handler weiterzuleiten.|
|[CCmdUI::Aktivieren](#enable)|Aktiviert oder deaktiviert das Benutzeroberflächenelement für diesen Befehl.|
|[CCmdUI::SetCheck](#setcheck)|Legt den Prüfstatus des Benutzeroberflächenelements für diesen Befehl fest.|
|[CCmdUI::SetRadio](#setradio)|Wie `SetCheck` die Memberfunktion, arbeitet aber auf Funkgruppen.|
|[CCmdUI::SetText](#settext)|Legt den Text für das Benutzeroberflächenelement für diesen Befehl fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|Die ID des Benutzeroberflächenobjekts.|
|[CCmdUI::m_nIndex](#m_nindex)|Der Index des Benutzeroberflächenobjekts.|
|[CCmdUI::m_pMenu](#m_pmenu)|Zeigt auf das Menü, das durch das Objekt dargestellt wird. `CCmdUI`|
|[CCmdUI::m_pOther](#m_pother)|Zeigt auf das Fensterobjekt, das die Benachrichtigung gesendet hat.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Zeigt auf das enthaltene Untermenü, das durch das Objekt dargestellt wird. `CCmdUI`|

## <a name="remarks"></a>Bemerkungen

`CCmdUI`hat keine Basisklasse.

Wenn ein Benutzer Ihrer Anwendung ein Menü herunterzieht, muss jedes Menüelement wissen, ob es als aktiviert oder deaktiviert angezeigt werden soll. Das Ziel eines Menübefehls stellt diese Informationen bereit, indem ein ON_UPDATE_COMMAND_UI-Handler implementiert wird. Verwenden Sie für jedes der Benutzeroberflächenobjekte in Ihrer Anwendung das Fenster [Klassenassistent](mfc-class-wizard.md) oder **Eigenschaften** (in **der Klassenansicht**), um für jeden Handler einen Nachrichtenzuordnungseintrag und einen Funktionsprototyp zu erstellen.

Wenn das Menü heruntergezogen wird, sucht das Framework nach jedem `CCmdUI` ON_UPDATE_COMMAND_UI Handler `Enable` `Check`und ruft ihn auf, jeder Handler ruft Memberfunktionen wie und auf, und das Framework zeigt dann jedes Menüelement entsprechend an.

Ein Menüelement kann durch eine Steuerleistenschaltfläche oder ein anderes Befehlsbenutzeroberflächenobjekt ersetzt werden, ohne den Code innerhalb des `ON_UPDATE_COMMAND_UI` Handlers zu ändern.

Die folgende Tabelle fasst `CCmdUI`die Auswirkungen der Memberfunktionen auf verschiedene Befehlsbenutzeroberflächenelemente zusammen.

|Benutzeroberflächenelement|Aktivieren|SetCheck|SetRadio|Settext|
|--------------------------|------------|--------------|--------------|-------------|
|Menüelement|Aktiviert oder deaktiviert|Schecks oder Unchecks|Prüfungen mit einem Punkt|Legt Elementtext fest|
|Symbolleistenschaltfläche|Aktiviert oder deaktiviert|Wählt, deaktiviert oder unbestimmt|Identisch mit `SetCheck`|(Nicht vorhanden)|
|Status-Bar-Bereich|Macht Text sichtbar oder unsichtbar|Legt Pop-Out oder normalen Rahmen fest|Identisch mit `SetCheck`|Legt Bereichstext fest|
|Normale Taste in`CDialogBar`|Aktiviert oder deaktiviert|Kontrollkästchen oder Unchecks|Identisch mit `SetCheck`|Legt Denperatontext fest|
|Normale Steuerung in`CDialogBar`|Aktiviert oder deaktiviert|(Nicht vorhanden)|(Nicht vorhanden)|Legt Fenstertext fest|

Weitere Informationen zur Verwendung dieser Klasse finden Sie unter [So aktualisieren Sie Benutzeroberflächenobjekte](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CCmdUI`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::WeiterRouting

Rufen Sie diese Memberfunktion auf, um den Befehlsroutingmechanismus anzuweisen, die aktuelle Nachricht weiterhin über die Kette von Handlern weiterzuleiten.

```
void ContinueRouting();
```

### <a name="remarks"></a>Bemerkungen

Dies ist eine erweiterte Memberfunktion, die in Verbindung mit einem ON_COMMAND_EX-Handler verwendet werden sollte, der FALSE zurückgibt. Weitere Informationen finden Sie unter [Technischer Hinweis 6](../../mfc/tn006-message-maps.md).

## <a name="ccmduienable"></a><a name="enable"></a>CCmdUI::Aktivieren

Rufen Sie diese Memberfunktion auf, um das Benutzeroberflächenelement für diesen Befehl zu aktivieren oder zu deaktivieren.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
TRUE, um das Element zu aktivieren, FALSE, um es zu deaktivieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI::m_nID

Die ID des Menüelements, der Symbolleistenschaltfläche oder eines `CCmdUI` anderen Benutzeroberflächenobjekts, das durch das Objekt dargestellt wird.

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex

Der Index des Menüelements, der Symbolleistenschaltfläche oder eines `CCmdUI` anderen Benutzeroberflächenobjekts, das durch das Objekt dargestellt wird.

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu

Zeiger (vom `CMenu` Typ) auf das `CCmdUI` Menü, das durch das Objekt dargestellt wird.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn es sich bei dem Element nicht um ein Menü handelt.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CCmdUI::m_pSubMenu

Zeiger (vom `CMenu` Typ) auf das enthaltene `CCmdUI` Untermenü, das durch das Objekt dargestellt wird.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn es sich bei dem Element nicht um ein Menü handelt. Wenn es sich bei dem Untermenü um ein Pop-up handelt, *enthält m_nID* die ID des ersten Elements im Popupmenü. Weitere Informationen finden Sie unter [Technische Anmerkung 21](../../mfc/tn021-command-and-message-routing.md).

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CCmdUI::m_pOther

Zeiger (vom `CWnd`Typ ) auf das Fensterobjekt, z. B. ein Werkzeug oder eine Statusleiste, das die Benachrichtigung gesendet hat.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Bemerkungen

NULL, wenn es sich bei `CWnd` dem Element um ein Menü oder ein Nicht-Objekt handelt.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck

Rufen Sie diese Memberfunktion auf, um das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfzustand festzulegen.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parameter

*nCheck*<br/>
Gibt den festzulegenden Prüfzustand an. Wenn 0, wird die Überprüfung enk. wenn 1, kontrollen; und wenn 2, setzt unbestimmt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion funktioniert für Menüelemente und Symbolleistenschaltflächen. Der unbestimmte Status gilt nur für Symbolleistenschaltflächen.

## <a name="ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio

Rufen Sie diese Memberfunktion auf, um das Benutzeroberflächenelement für diesen Befehl auf den entsprechenden Prüfzustand festzulegen.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
TRUE, um das Element zu aktivieren; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion `SetCheck`funktioniert wie , außer dass sie auf Elementen der Benutzeroberfläche arbeitet, die als Teil einer Funkgruppe fungieren. Das Deaktivieren der anderen Elemente in der Gruppe erfolgt nicht automatisch, es sei denn, die Elemente selbst behalten das Radiogruppenverhalten bei.

## <a name="ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText

Rufen Sie diese Memberfunktion auf, um den Text des Benutzeroberflächenelements für diesen Befehl festzulegen.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Ein Zeiger auf eine Textzeichenfolge.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
