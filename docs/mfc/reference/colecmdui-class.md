---
title: COleCmdUI-Klasse
ms.date: 07/24/2020
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: c21d9b504656e6bba5ca693e57958743bb1b8309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233209"
---
# <a name="colecmdui-class"></a>COleCmdUI-Klasse

Implementiert eine Methode, die es MFC ermöglicht, den Zustand von Benutzeroberflächenobjekten zu aktualisieren, die in Bezug zu den `IOleCommandTarget`-gesteuerten Funktionen der Anwendung stehen.

## <a name="syntax"></a>Syntax

```cpp
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COleCmdUI:: COleCmdUI](#colecmdui)|Erstellt ein `COleCmdUI`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[COleCmdUI:: enable](#enable)|Legt das Flag zum Aktivieren des Befehls fest oder löscht dieses.|
|[COleCmdUI:: setcheck](#setcheck)|Legt den Status eines ein/aus-UMSCHALT Befehls fest.|
|[COleCmdUI:: SetText](#settext)|Gibt einen Textnamen oder eine Status Zeichenfolge für einen Befehl zurück.|

## <a name="remarks"></a>Bemerkungen

In einer Anwendung, die nicht für docobjects aktiviert ist, verarbeitet MFC UPDATE_COMMAND_UI Benachrichtigungen, wenn der Benutzer ein Menü in der Anwendung anzeigt. Jede Benachrichtigung erhält ein [CCmdUI](../../mfc/reference/ccmdui-class.md) -Objekt, das bearbeitet werden kann, um den Zustand eines bestimmten Befehls widerzuspiegeln. Wenn Ihre Anwendung jedoch für docobjects aktiviert ist, verarbeitet MFC UPDATE_OLE_COMMAND_UI Benachrichtigungen und weist `COleCmdUI` Objekte zu.

`COleCmdUI`ermöglicht einem DocObject, Befehle zu empfangen, die in der Benutzeroberfläche des Containers (z. b. File. File, Open, Print usw.) stammen, und ermöglicht einem Container, Befehle zu empfangen, die von der Benutzeroberfläche von DocObject stammen. `IDispatch`Kann zwar verwendet werden, um dieselben Befehle zu senden, `IOleCommandTarget` bietet jedoch eine einfachere Möglichkeit, abzufragen und auszuführen, da Sie auf einem Standardsatz von Befehlen basiert, in der Regel ohne Argumente, und es sind keine Typinformationen beteiligt. `COleCmdUI`kann verwendet werden, um andere Eigenschaften von DocObject-Benutzeroberflächen Befehlen zu aktivieren, zu aktualisieren und festzulegen. Wenn Sie den Befehl aufrufen möchten, rufen Sie [COleServerDoc:: onexecolecmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)auf.

Weitere Informationen zu docobjects finden Sie unter [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) und [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdocob. h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI:: COleCmdUI

Erstellt ein-Objekt, das `COleCmdUI` einem bestimmten Benutzerschnittstellen Befehl zugeordnet ist.

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parameter

*rgcmds*<br/>
Eine Liste der unterstützten Befehle, die mit der angegebenen GUID verknüpft sind. Die `OLECMD` Struktur ordnet Befehle mit Befehlsflags zu.

*ccmds*<br/>
Die Anzahl der Befehle in *rgcmds*.

*pgroup*<br/>
Ein Zeiger auf eine GUID, die einen Satz von Befehlen identifiziert.

### <a name="remarks"></a>Bemerkungen

Das- `COleCmdUI` Objekt stellt eine programmgesteuerte Schnittstelle zum Aktualisieren von DocObject-Benutzeroberflächen Objekten bereit, z. b. Menü Elemente oder Steuer leisten Schaltflächen. Die Benutzeroberflächen Objekte können aktiviert, deaktiviert, aktiviert und/oder durch das-Objekt gelöscht werden `COleCmdUI` .

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI:: enable

Mit dieser Funktion wird das Befehlsflag des `COleCmdUI` Objekts auf OLECOMDF_ENABLED festgelegt, das die Schnittstelle anweist, dass der Befehl verfügbar und aktiviert ist, oder um das Befehlsflag zu löschen.

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parameter

*Böller*<br/>
Gibt an, ob der Befehl, der dem-Objekt zugeordnet ist, `COleCmdUI` aktiviert oder deaktiviert werden soll. Nicht NULL aktiviert den Befehl. 0 deaktiviert den Befehl.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI:: setcheck

Mit dieser Funktion wird der Status eines ein-/ausschalten-Befehls zum Umschalten festgelegt.

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parameter

*nPrüfen*<br/>
Ein-Wert, der den Zustand zur Festlegung eines ein-/ausschalten-Befehls angibt. Gültige Werte:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|**1**|Legt den-Befehl auf ON fest.|
|**2**|Legt fest, dass der Befehl unbestimmt ist. der Status kann nicht bestimmt werden, da sich das-Attribut dieses Befehls in der relevanten Auswahl in den Status "ein" und "aus" befindet.|
|beliebiger anderer Wert|Legt den-Befehl auf OFF fest.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI:: SetText

Mit dieser Funktion wird ein Textname oder eine Status Zeichenfolge für einen Befehl zurückgegeben.

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Ein Zeiger auf den Text, der mit dem Befehl verwendet werden soll.

## <a name="see-also"></a>Siehe auch

[CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)
