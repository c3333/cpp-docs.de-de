---
title: CSnapInItemImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 04eeba0239789b9f3220b7bfece3eb41dc7f2826
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746428"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl-Klasse

Diese Klasse stellt Methoden zum Implementieren eines Snap-In-Knotenobjekts bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `CSnapInItemImpl`abgeleitet von .

*bIsExtension*<br/>
TRUE, wenn es sich bei dem Objekt um eine Snap-In-Erweiterung handelt; andernfalls FALSE.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Fügt Menüelemente zu einem Kontextmenü hinzu.|
|[CSnapInItemImpl::Befehl](#command)|Wird von der Konsole aufgerufen, wenn ein benutzerdefiniertes Menüelement ausgewählt ist.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Fügt dem Eigenschaftenblatt des Snap-Ins Seiten hinzu.|
|[CSnapInItemImpl::FillData](#filldata)|Kopiert Informationen über das Snap-In-Objekt in einen angegebenen Stream.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Ruft die `RESULTDATAITEM` Struktur des Snap-Ins ab.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Bestimmt den Ansichtstyp, der vom Ergebnisbereich verwendet wird.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Ruft die `SCOPEDATAITEM` Struktur des Snap-Ins ab.|
|[CSnapInItemImpl::Notify](#notify)|Wird von der Konsole aufgerufen, um das Snap-In der vom Benutzer ausgeführten Aktionen zu benachrichtigen.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Wird aufgerufen, um zu sehen, ob der Snap-In-Knoten Eigenschaftenseiten unterstützt.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Ändert die Menüeinfügeflags für ein Snap-In-Objekt.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Legt die Informationen der angegebenen Symbolleistenschaltfläche fest.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualisiert den Status eines Kontextmenüelements.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualisiert den Status der angegebenen Symbolleistenschaltfläche.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Der Name des Snap-In-Objekts.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Die `RESULTDATAITEM` vom `CSnapInItemImpl` Objekt verwendete Windows-Struktur.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Die `SCOPEDATAITEM` vom `CSnapInItemImpl` Objekt verwendete Windows-Struktur.|

## <a name="remarks"></a>Bemerkungen

`CSnapInItemImpl`stellt eine grundlegende Implementierung für ein Snap-In-Knotenobjekt bereit, z. B. das Hinzufügen von Menüelementen und Symbolleisten sowie das Weiterleiten von Befehlen für den Snap-In-Knoten an die entsprechende Handlerfunktion. Diese Features werden mit verschiedenen Schnittstellen und Kartentypen implementiert. Die Standardimplementierung verarbeitet Benachrichtigungen, die an das Knotenobjekt gesendet werden, indem die richtige Instanz der abgeleiteten Klasse bestimmt und die Nachricht dann an die richtige Instanz weitergeleitet wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems

Diese Methode implementiert die Win32-Funktion [IExtendContextMenu::AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parameter

*piCallback*<br/>
[in] Zeiger auf `IContextMenuCallback` die, die Elemente zum Kontextmenü hinzufügen kann.

*pInsertionAllowed*<br/>
[in, out] Identifiziert Microsoft Management Console (MMC)-definierte Einfügepunkte für Menüelemente, die verwendet werden können. Dies kann eine Kombination der folgenden Flags sein:

- CCM_INSERTIONALLOWED_TOP Elemente können oben in einem Kontextmenü eingefügt werden.

- CCM_INSERTIONALLOWED_NEW Elemente können in das Untermenü Neu erstellen eingefügt werden.

- CCM_INSERTIONALLOWED_TASK Elemente können in das Untermenü "Aufgaben" eingefügt werden.

- CCM_INSERTIONALLOWED_VIEW Elemente können in das Menü der Symbolleistenansicht oder in das Untermenü Ansicht des Kontextmenüs des Ergebnisbereichs eingefügt werden.

*type*<br/>
[in] Gibt den Objekttyp an. Die Variable muss einen der folgenden Werte aufweisen:

- CCT_SCOPE Data-Objekt für den Bereichskontext.

- CCT_RESULT Data-Objekt für den Kontext des Ergebnisbereichs.

- CCT_SNAPIN_MANAGER Data-Objekt für den Snap-In-Manager-Kontext.

- CCT_UNINITIALIZED Data-Objekt hat einen ungültigen Typ.

## <a name="csnapinitemimplcommand"></a><a name="command"></a>CSnapInItemImpl::Befehl

Diese Methode implementiert die Win32-Funktion [IExtendContextMenu::Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parameter

*lCommandID*<br/>
[in] Gibt den Befehlsbezeichner des Menüelements an.

*type*<br/>
[in] Gibt den Objekttyp an. Die Variable muss einen der folgenden Werte aufweisen:

- CCT_SCOPE Data-Objekt für den Bereichskontext.

- CCT_RESULT Data-Objekt für den Kontext des Ergebnisbereichs.

- CCT_SNAPIN_MANAGER Data-Objekt für den Snap-In-Manager-Kontext.

- CCT_UNINITIALIZED Data-Objekt hat einen ungültigen Typ.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

Diese Methode implementiert die Win32-Funktion [IExtendPropertySheet::CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parameter

*lpProvider*<br/>
[in] Zeiger auf die `IPropertySheetCallback`-Schnittstelle.

*Behandeln*<br/>
[in] Gibt das Handle an, das zum Weiterleiten der MMCN_PROPERTY_CHANGE Benachrichtigung an die entsprechende Datenklasse verwendet wird.

*Punk*<br/>
[in] Zeiger auf `IExtendPropertySheet` die Schnittstelle für das Objekt, die Kontextinformationen über den Knoten enthält.

*type*<br/>
[in] Gibt den Objekttyp an. Die Variable muss einen der folgenden Werte aufweisen:

- CCT_SCOPE Data-Objekt für den Bereichskontext.

- CCT_RESULT Data-Objekt für den Kontext des Ergebnisbereichs.

- CCT_SNAPIN_MANAGER Data-Objekt für den Snap-In-Manager-Kontext.

- CCT_UNINITIALIZED Data-Objekt hat einen ungültigen Typ.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

Erstellt ein `CSnapInItemImpl`-Objekt.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>CSnapInItemImpl::FillData

Diese Funktion wird aufgerufen, um Informationen über das Element abzurufen.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
[in] Das Format (Text, Rich-Text oder Rich-Text mit OLE-Elementen) der Zwischenablage.

*pStream*<br/>
[in] Ein Zeiger auf den Stream, der die Objektdaten enthält.

### <a name="remarks"></a>Bemerkungen

Um diese Funktion ordnungsgemäß zu implementieren, kopieren Sie die richtigen Informationen in den Stream (*pStream*), abhängig vom Zwischenablageformat, das durch *cf*angegeben ist.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

Rufen Sie diese Funktion auf, um den Ansichtstyp für den Ergebnisbereich des Snap-In-Objekts abzurufen.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parameter

*ppViewType*<br/>
[out] Zeiger auf die Adresse des zurückgegebenen Ansichtstyps.

*pViewOptions*<br/>
[out] Zeigen Sie auf die MMC_VIEW_OPTIONS-Enumeration, die der Konsole Optionen bereitstellt, die durch das besitzende Snap-In angegeben werden. Die folgenden Werte sind möglich:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x0000001 Weist die Konsole an, keine Standardlistenansichtsoptionen im **Menü Ansicht** anzuzeigen. Ermöglicht dem Snap-In, seine eigenen benutzerdefinierten Ansichten nur im Ergebnisansichtsbereich anzuzeigen. Dies ist das einzige Optionsflag, das derzeit definiert ist.

- MMC_VIEW_OPTIONS_NONE = 0 Erlaubt die Standardansichtsoptionen.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Rufen Sie diese `SCOPEDATAITEM` Funktion auf, um die Struktur des Snap-Ins abzurufen.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parameter

*pScopeDataItem*<br/>
[out] Ein Zeiger auf `SCOPEDATAITEM` die `CSnapInItemImpl` Struktur des Objekts.

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Rufen Sie diese `RESULTDATAITEM` Funktion auf, um die Struktur des Snap-Ins abzurufen.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parameter

*pResultDataItem*<br/>
[out] Ein Zeiger auf `RESULTDATAITEM` die `CSnapInItemImpl` Struktur des Objekts.

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Enthält die Zeichenfolge, die für das Knotenelement angezeigt wird.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

Die `SCOPEDATAITEM` Struktur des Snap-In-Datenobjekts.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

Die [RESULTDATAITEM-Struktur](/windows/win32/api/mmc/ns-mmc-resultdataitem) des Snap-In-Datenobjekts.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>CSnapInItemImpl::Notify

Wird aufgerufen, wenn das Snap-In-Objekt vom Benutzer betätigt wird.

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>Parameter

*event*<br/>
[in] Identifiziert eine Aktion, die von einem Benutzer ausgeführt wird. Folgende Benachrichtigungen sind möglich:

- MMCN_ACTIVATE Gesendet, wenn ein Fenster aktiviert und deaktiviert wird.

- MMCN_ADD_IMAGES Gesendet, um dem Ergebnisbereich Bilder hinzuzufügen.

- MMCN_BTN_CLICK Gesendet, wenn der Benutzer auf eine der Symbolleistenschaltflächen klickt.

- MMCN_CLICK Gesendet, wenn ein Benutzer auf eine Maustaste auf ein Listenansichtselement klickt.

- MMCN_DBLCLICK Gesendet, wenn ein Benutzer auf eine Maustaste auf ein Listenansichtselement doppelklickt.

- MMCN_DELETE gesendet, um das Snap-In zu informieren, dass das Objekt gelöscht werden soll.

- MMCN_EXPAND Gesendet, wenn ein Ordner erweitert oder vertraglich gebunden werden muss.

- MMCN_MINIMIZED Gesendet, wenn ein Fenster minimiert oder maximiert wird.

- MMCN_PROPERTY_CHANGE Gesendet, um ein Snap-In-Objekt zu benachrichtigen, dass sich die Ansicht des Snap-In-Objekts ändern wird.

- MMCN_REMOVE_CHILDREN Gesendet, wenn das Snap-In die gesamte Unterstruktur löschen muss, die es unterhalb des angegebenen Knotens hinzugefügt hat.

- MMCN_RENAME Das erste Mal gesendet, um eine Umbenennung abzufragen, und zum zweiten Mal, um die Umbenennung zu tun.

- MMCN_SELECT Gesendet, wenn ein Element im Bereichs- oder Ergebnisansichtsbereich ausgewählt ist.

- MMCN_SHOW Gesendet, wenn ein Bereichselement zum ersten Mal ausgewählt oder deaktiviert wird.

- MMCN_VIEW_CHANGE Gesendet, wenn das Snap-In alle Ansichten aktualisieren kann, wenn eine Änderung auftritt.

*arg*<br/>
[in] Abhängig vom Benachrichtigungstyp.

*Param*<br/>
[in] Abhängig vom Benachrichtigungstyp.

*pComponentData*<br/>
[out] Ein Zeiger auf das `IComponentData`Objekt, das implementiert. Dieser Parameter ist NULL, wenn die `IComponentData::Notify`Benachrichtigung nicht von weitergeleitet wird.

*pComponent*<br/>
[out] Ein Zeiger auf das Objekt, das `IComponent`implementiert. Dieser Parameter ist NULL, wenn die `IComponent::Notify`Benachrichtigung nicht von weitergeleitet wird.

*type*<br/>
[in] Gibt den Objekttyp an. Die Variable muss einen der folgenden Werte aufweisen:

- CCT_SCOPE Data-Objekt für den Bereichskontext.

- CCT_RESULT Data-Objekt für den Kontext des Ergebnisbereichs.

- CCT_SNAPIN_MANAGER Data-Objekt für den Snap-In-Manager-Kontext.

- CCT_UNINITIALIZED Data-Objekt hat einen ungültigen Typ.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

Wird aufgerufen, um zu sehen, ob der Snap-In-Knoten Eigenschaftenseiten unterstützt.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

Rufen Sie diese Funktion auf, um die Menüeinfügeflags zu ändern, die durch *pInsertionAllowed*für das Snap-In-Objekt angegeben werden.

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parameter

*bBeforeInsertion*<br/>
[in] Ein Wert ungleich Null, wenn die Funktion aufgerufen werden soll, bevor Elemente zum Kontextmenü hinzugefügt werden. andernfalls 0.

*pInsertionAllowed*<br/>
[in, out] Identifiziert Microsoft Management Console (MMC)-definierte Einfügepunkte für Menüelemente, die verwendet werden können. Dies kann eine Kombination der folgenden Flags sein:

- CCM_INSERTIONALLOWED_TOP Elemente können oben in einem Kontextmenü eingefügt werden.

- CCM_INSERTIONALLOWED_NEW Elemente können in das Untermenü Neu erstellen eingefügt werden.

- CCM_INSERTIONALLOWED_TASK Elemente können in das Untermenü "Aufgaben" eingefügt werden.

- CCM_INSERTIONALLOWED_VIEW Elemente können in das Menü der Symbolleistenansicht oder in das Untermenü Ansicht des Kontextmenüs des Ergebnisbereichs eingefügt werden.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein primäres Snap-In entwickeln, können Sie alle Einfügeflags zurücksetzen, um die Art von Menüelementen einzuschränken, die eine Drittanbietererweiterung hinzufügen kann. Das primäre Snap-In kann z. B. das CCM_INSERTIONALLOWED_NEW-Flag löschen, um zu verhindern, dass Erweiterungen ihre eigenen Menüelemente "Neue erstellen" hinzufügen.

Sie sollten nicht versuchen, Bits in *pInsertionAllowed* festzulegen, die ursprünglich gelöscht wurden. Zukünftige Versionen von MMC können Bits verwenden, die derzeit nicht definiert sind, daher sollten Sie keine Bits ändern, die derzeit nicht definiert sind.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Rufen Sie diese Funktion auf, um alle Symbolleisten-Schaltflächenstile des Snap-In-Objekts zu ändern, bevor die Symbolleiste erstellt wird.

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die ID der symbolleistenschaltfläche, die eingestellt werden soll.

*fsState*<br/>
[in] Die Statusflags der Schaltfläche. Kann einer oder mehrere der folgenden sein:

- TBSTATE_CHECKED Die Taste hat den TBSTYLE_CHECKED Stil und wird gedrückt.

- TBSTATE_ENABLED Die Schaltfläche akzeptiert Benutzereingaben. Eine Schaltfläche, die diesen Status nicht hat, akzeptiert keine Benutzereingaben und ist grau.

- TBSTATE_HIDDEN Die Schaltfläche ist nicht sichtbar und kann keine Benutzereingaben empfangen.

- TBSTATE_INDETERMINATE Die Schaltfläche ist grau.

- TBSTATE_PRESSED Die Taste wird gedrückt.

- TBSTATE_WRAP Ein Zeilenumbruch folgt der Schaltfläche. Die Schaltfläche muss auch die TBSTATE_ENABLED haben.

*fsType*<br/>
[in] Die Statusflags der Schaltfläche. Kann einer oder mehrere der folgenden sein:

- TBSTYLE_BUTTON Erstellt einen Standard-Druckknopf.

- TBSTYLE_CHECK Erstellt eine Schaltfläche, die jedes Mal zwischen den gedrückten und nicht gedrückten Zuständen umschaltet, wenn der Benutzer darauf klickt. Die Schaltfläche hat eine andere Hintergrundfarbe, wenn sie sich im gedrückten Zustand befindet.

- TBSTYLE_CHECKGROUP Erstellt eine Prüftaste, die gedrückt bleibt, bis eine andere Taste in der Gruppe gedrückt wird.

- TBSTYLE_GROUP Erstellt eine Taste, die gedrückt bleibt, bis eine andere Taste in der Gruppe gedrückt wird.

- TBSTYLE_SEP Erstellt ein Trennzeichen, das eine kleine Lücke zwischen Schaltflächengruppen bereitstellt. Eine Schaltfläche mit diesem Stil empfängt keine Benutzereingaben.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Rufen Sie diese Funktion auf, um ein Menüelement zu ändern, bevor es in das Kontextmenü des Snap-In-Objekts eingefügt wird.

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die ID des festzulegenden Menüelements.

*pBuf*<br/>
[in] Ein Zeiger auf die Zeichenfolge für das zu aktualisierende Menüelement.

*Flaggen*<br/>
[in] Gibt die neuen Statusflags an. Dies kann eine Kombination der folgenden Flags sein:

- MF_POPUP Gibt an, dass es sich um ein Untermenü im Kontextmenü handelt. Menüelemente, Einfügepunkte und weitere Untermenüs können `lCommandID` diesem `IInsertionPointID`Untermenü unter Verwendung seiner hinzugefügt werden.

- MF_BITMAP und MF_OWNERDRAW Diese Flags sind nicht zulässig und führen zu einem Rückgabewert von E_INVALIDARG.

- MF_SEPARATOR Zeichnet eine horizontale Trennlinie. Nur `IContextMenuProvider` ist das Hinzufügen von Menüelementen mit MF_SEPARATOR-Satz zulässig.

- MF_CHECKED Platziert ein Häkchen neben dem Menüpunkt.

- MF_DISABLED Deaktiviert das Menüelement, sodass es nicht ausgewählt werden kann, aber das Flag graut es nicht.

- MF_ENABLED Aktiviert das Menüelement, damit es ausgewählt werden kann, und stellt es aus seinem grauen Zustand wieder her.

- MF_GRAYED Deaktiviert das Menüelement und graut es, sodass es nicht ausgewählt werden kann.

- MF_MENUBARBREAK Funktioniert wie das MF_MENUBREAK-Flag für eine Menüleiste. Bei einem Dropdown-Menü, Untermenü oder Kontextmenü wird die neue Spalte durch eine vertikale Linie von der alten Spalte getrennt.

- MF_MENUBREAK Platziert das Element in einer neuen Zeile (für eine Menüleiste) oder in einer neuen Spalte (für ein Dropdown-Menü, Untermenü oder Verknüpfungsmenü), ohne Spalten zu trennen.

- MF_UNCHECKED Setzt kein Häkchen neben das Element (Standard).

Die folgenden Flags können nicht zusammen verwendet werden:

- MF_DISABLED, MF_ENABLED und MF_GRAYED.

- MF_MENUBARBREAK und MF_MENUBREAK.

- MF_CHECKED und MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Rufen Sie diese Funktion auf, um eine Symbolleistenschaltfläche des Snap-In-Objekts zu ändern, bevor sie angezeigt wird.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parameter

*id*<br/>
Gibt die Schaltflächen-ID der symbolleisten Schaltfläche an, die aktualisiert werden soll.

*fsState*<br/>
Gibt einen Symbolleisten-Schaltflächenstatus an. Wenn dieser Zustand festgelegt werden soll, geben Sie TRUE zurück. Dies kann eine Kombination der folgenden Flags sein:

- ENABLED Die Schaltfläche akzeptiert Benutzereingaben. Eine Schaltfläche, die diesen Status nicht hat, akzeptiert keine Benutzereingaben und ist grau.

- CHECKED Die Taste hat den CHECKED-Stil und wird gedrückt.

- HIDDEN Die Schaltfläche ist nicht sichtbar und kann keine Benutzereingaben empfangen.

- INDETERMINATE Die Schaltfläche ist grau.

- BUTTONPRESSED Die Taste wird gedrückt.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
