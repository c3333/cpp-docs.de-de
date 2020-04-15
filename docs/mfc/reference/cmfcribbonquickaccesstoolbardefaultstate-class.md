---
title: CMFCRibbonQuickAccessToolBarDefaultState-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 56219e8ed1833f4b448ec6ffd3c16e9db3c66ada
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368872"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState-Klasse

Eine Hilfsklasse, die den Standardstatus für die Quick Access Toolbar verwaltet, die sich auf der Multifunktionsleistenleiste ( [CMFCRibbonBar-Klasse )](../../mfc/reference/cmfcribbonbar-class.md)befindet.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Erstellt ein `CMFCRibbonQuickAccessToolbarDefaultState`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Fügt dem Standardstatus für die Quick Access Toolbar einen Befehl hinzu. Dadurch wird die Symbolleiste selbst nicht geändert.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopiert die Eigenschaften einer Quick Access Toolbar in eine andere.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Entfernt alle Befehle aus der Quick Access Toolbar. Dadurch wird die Symbolleiste selbst nicht geändert.|

## <a name="remarks"></a>Bemerkungen

Nachdem Sie die Quick Access Toolbar in Ihrer Anwendung erstellt haben, wird empfohlen, den Standardstatus festzulegen, indem Sie [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)aufrufen. Dieser Standardzustand wird wiederhergestellt, wenn ein Benutzer auf der Seite **Anpassen** im Dialogfeld **Optionen** der Anwendung auf die Schaltfläche **Zurücksetzen** klickt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonQuickAccessToolbarDefaultState` wie ein Objekt der Klasse erstellt und wie dem Standardstatus für die Schnellzugriffssymbolleiste ein Befehl hinzugefügt wird.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribbonquickaccesstoolbar.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Fügt dem Standardstatus für die Quick Access Toolbar einen Befehl hinzu.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parameter

*[in] uiCmd*<br/>
Gibt die Befehls-ID an.

*[in] bIsVisible*<br/>
Legt die Sichtbarkeit des Befehls fest, wenn sich die Schnellzugriffssymbolleiste im Standardzustand befindet.

### <a name="remarks"></a>Bemerkungen

Das Hinzufügen eines Befehls zum CMFCRibbonQuickAccessToolBarDefaultState führt zu drei Ergebnissen. Zunächst wird jeder hinzugefügte Befehl in der Dropdownliste auf der rechten Seite der Schnellzugriffssymbolleiste aufgeführt. Auf diese Weise kann ein Benutzer diesen Befehl einfach hinzufügen oder aus der Schnellzugriffssymbolleiste entfernen. Zweitens wird die Schnellzugriffssymbolleiste zurückgesetzt, um nur die Befehle anzuzeigen, die im Standardzustand als sichtbar aufgeführt sind, wenn der Benutzer im Dialogfeld **Anpassen** auf die Schaltfläche **Zurücksetzen** klickt. Drittens: Wenn Sie [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)nicht aufgerufen haben, verwendet die Quick Access Toolbar die sichtbaren Befehle aus dieser Liste als standardmäßig sichtbare Befehle, wenn ein Benutzer Ihre Anwendung zum ersten Mal ausführt. Nachdem Sie alle gewünschten Befehle hinzugefügt haben, rufen Sie [CMFCRibbonBar::SetQuickAccessDefaultState auf,](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) um diese Instanz als Standardstatus für die Schnellzugriffssymbolleiste dieser Multifunktionsleistenleiste festzulegen.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Kopiert die Eigenschaften einer Quick Access Toolbar in eine andere.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
[in] Ein Verweis auf `CMFCRibbonQuickAccessToolBarDefaultState` das Quellobjekt, aus dem kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode kopiert jeden `CMFCRibbonQuickAccessToolBarDefaultState` Befehl aus dem Quellobjekt in dieses Objekt mithilfe der [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand-Methode.](#addcommand)

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Erstellt das Standardstatusobjekt der Schnellzugriffssymbolleiste.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist die Liste der Befehle, die die neue Instanz von [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) enthält, leer.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Löscht die Liste der Standardbefehle in der Schnellzugriffssymbolleiste.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion entfernt aus dieser Instanz alle Befehle, die die vorherigen Aufrufe von [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) hinzugefügt haben.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)
