---
title: COleCmdUI-Klasse
ms.date: 09/12/2018
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
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376271"
---
# <a name="colecmdui-class"></a>COleCmdUI-Klasse

Implementiert eine Methode, die es MFC ermöglicht, den Zustand von Benutzeroberflächenobjekten zu aktualisieren, die in Bezug zu den `IOleCommandTarget`-gesteuerten Funktionen der Anwendung stehen.

## <a name="syntax"></a>Syntax

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Erstellt ein `COleCmdUI`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleCmdUI::Aktivieren](#enable)|Legt das Befehlsflag "Enable" fest oder löscht es.|
|[COleCmdUI::SetCheck](#setcheck)|Legt den Status eines Ein-/Aus-Toggle-Befehls fest.|
|[COleCmdUI::SetText](#settext)|Gibt einen Textnamen oder eine Statuszeichenfolge für einen Befehl zurück.|

## <a name="remarks"></a>Bemerkungen

In einer Anwendung, die für DocObjects nicht aktiviert ist, verarbeitet MFC, wenn der Benutzer ein Menü in der Anwendung anzeigt, UPDATE_COMMAND_UI Notifationen. Jede Benachrichtigung erhält ein [CCmdUI-Objekt,](../../mfc/reference/ccmdui-class.md) das so bearbeitet werden kann, dass es den Status eines bestimmten Befehls widerspiegelt. Wenn Ihre Anwendung jedoch für DocObjects aktiviert ist, verarbeitet `COleCmdUI` MFC UPDATE_OLE_COMMAND_UI Benachrichtigungen und weist Objekte zu.

`COleCmdUI`ermöglicht einem DocObject das Empfangen von Befehlen, die von der Benutzeroberfläche des Containers stammen (z. B. FileNew, Open, Print usw.), und ermöglicht einem Container das Empfangen von Befehlen, die von der Benutzeroberfläche des DocObject stammen. Obwohl `IDispatch` zum Senden derselben Befehle `IOleCommandTarget` verwendet werden könnte, bietet dies eine einfachere Möglichkeit zum Abfragen und Ausführen, da sie auf einem Standardsatz von Befehlen basiert, in der Regel ohne Argumente, und es sind keine Typinformationen beteiligt. `COleCmdUI`kann zum Aktivieren, Aktualisieren und Festlegen anderer Eigenschaften von DocObject-Benutzeroberflächenbefehlen verwendet werden. Wenn Sie den Befehl aufrufen möchten, rufen Sie [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)auf.

Weitere Informationen zu DocObjects finden Sie unter [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) und [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Erstellt ein `COleCmdUI` Objekt, das einem bestimmten Benutzeroberflächenbefehl zugeordnet ist.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parameter

*rgCmds*<br/>
Eine Liste der unterstützten Befehle, die der angegebenen GUID zugeordnet sind. Die `OLECMD` Struktur ordnet Befehlen Befehlen mit Befehlsflags zu.

*cCmds*<br/>
Die Anzahl der Befehle in *rgCmds*.

*pGruppe*<br/>
Ein Zeiger auf eine GUID, der eine Reihe von Befehlen identifiziert.

### <a name="remarks"></a>Bemerkungen

Das `COleCmdUI` Objekt stellt eine programmgesteuerte Schnittstelle zum Aktualisieren von DocObject-Benutzeroberflächenobjekten wie Menüelementen oder Steuerelementleistenschaltflächen bereit. Die Benutzeroberflächenobjekte können aktiviert, deaktiviert, überprüft und/oder `COleCmdUI` über das Objekt gelöscht werden.

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI::Aktivieren

Rufen Sie diese Funktion auf, `COleCmdUI` um das Befehlsflag des Objekts auf OLECOMDF_ENABLED festzulegen, das der Schnittstelle mitteilt, dass der Befehl verfügbar und aktiviert ist, oder um das Befehlsflag zu löschen.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
Gibt an, ob `COleCmdUI` der dem Objekt zugeordnete Befehl aktiviert oder deaktiviert werden soll. Ein Wert ungleich Null aktiviert den Befehl. 0 deaktiviert den Befehl.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

Rufen Sie diese Funktion auf, um den Status eines Ein/Aus-Toggle-Befehls festzulegen.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parameter

*nCheck*<br/>
Ein Wert, der den Zustand bestimmt, um einen Ein-/Aus-Toggle-Befehl festzulegen. Werte:

|Wert|Beschreibung|
|-----------|-----------------|
|**1**|Legt den Befehl auf ein.|
|**2**|Legt den Befehl auf unbestimmt fest. Der Status kann nicht bestimmt werden, da sich das Attribut dieses Befehls sowohl in ein- als auch nach außerhalb in der entsprechenden Auswahl befindet.|
|jeder andere Wert|Legt den Befehl auf "Off" fest.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Rufen Sie diese Funktion auf, um einen Textnamen oder eine Statuszeichenfolge für einen Befehl zurückzugeben.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Ein Zeiger auf den Text, der mit dem Befehl verwendet werden soll.

## <a name="see-also"></a>Siehe auch

[CCmdUI-Klasse](../../mfc/reference/ccmdui-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
