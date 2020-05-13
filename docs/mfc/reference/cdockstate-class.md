---
title: CDockState-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 9850486407ee7550ee866a10e656d45ad18fc196
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753258"
---
# <a name="cdockstate-class"></a>CDockState-Klasse

Eine serialisierte `CObject` -Klasse, die den Zustand einer oder mehrerer andockbarer Steuerleisten in einem persistenten Speicher (eine Datei) lädt, entlädt oder löscht.

## <a name="syntax"></a>Syntax

```
class CDockState : public CObject
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDockState::Löschen](#clear)|Löscht die Dockstatusinformationen.|
|[CDockState::GetVersion](#getversion)|Ruft die Versionsnummer des gespeicherten Balkenstatus ab.|
|[CDockState::LoadState](#loadstate)|Ruft Statusinformationen aus der Registrierung oder ab. INI-Datei.|
|[CDockState::SaveState](#savestate)|Speichert Statusinformationen in der Registrierung oder INI-Datei.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Array von Zeigern auf die gespeicherten Dockstatusinformationen mit einem Eintrag für jede Steuerleiste.|

## <a name="remarks"></a>Bemerkungen

Der Dock-Status enthält die Größe und Position des Balkens und ob er angedockt ist. Überprüft beim Abrufen des `CDockState` gespeicherten Dockstatus die Position der Leiste, und skaliert die `CDockState` Position der Leiste, wenn sie mit den aktuellen Bildschirmeinstellungen nicht sichtbar ist, die Position der Leiste so, dass sie sichtbar ist. Der Hauptzweck `CDockState` von besteht darin, den gesamten Status einer Reihe von Kontrollleisten zu speichern und zuzulassen, dass dieser Status gespeichert und entweder in die Registrierung, die Anwendung , geladen wird. INI-Datei oder in binärer `CArchive` Form als Teil des Inhalts eines Objekts.

Die Leiste kann eine beliebige andockbare Steuerleiste sein, einschließlich einer Symbolleiste, Statusleiste oder Dialogleiste. `CDockState`Objekte über ein `CArchive` Objekt geschrieben und in eine Datei gelesen werden.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) ruft die Statusinformationen aller Objekte `CControlBar` des Rahmenfensters `CDockState` ab und fügt sie in das Objekt ein. Sie können dann den `CDockState` Inhalt des Objekts mit [Serialize](../../mfc/reference/cobject-class.md#serialize) oder [CDockState::SaveState](#savestate)in den Speicher schreiben. Wenn Sie später den Status der Steuerleisten im Rahmenfenster wiederherstellen möchten, können Sie den Status mit `Serialize` oder [CDockState::LoadState](#loadstate)laden und dann [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) verwenden, um den gespeicherten Status auf die Kontrollleisten des Rahmenfensters anzuwenden.

Weitere Informationen zu Docking-Steuerleisten finden Sie in den Artikeln [Control Bars](../../mfc/control-bars.md), [Toolbars: Docking and Floating und](../../mfc/docking-and-floating-toolbars.md)Frame [Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState::Löschen

Rufen Sie diese Funktion auf, um `CDockState` alle im Objekt gespeicherten Andockinformationen zu löschen.

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Dazu gehört nicht nur, ob die Leiste angedockt ist oder nicht, sondern auch die Größe und Position der Bar und ob sie sichtbar ist.

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState::GetVersion

Rufen Sie diese Funktion auf, um die Versionsnummer des gespeicherten Balkenstatus abzurufen.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Rückgabewert

1, wenn die gespeicherten Balkeninformationen älter als der aktuelle Balkenstatus sind; 2 wenn die gespeicherten Balkeninformationen mit dem aktuellen Balkenstatus identisch sind.

### <a name="remarks"></a>Bemerkungen

Die Versionsunterstützung ermöglicht es einem überarbeiteten Balken, neue persistente Eigenschaften hinzuzufügen und dennoch den persistenten Zustand zu erkennen und zu laden, der von einer früheren Version des Balkens erstellt wurde.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::LoadState

Rufen Sie diese Funktion auf, um Statusinformationen aus der Registrierung oder abzurufen. INI-Datei.

```cpp
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
Verweist auf eine Null-Teminat-Zeichenfolge, die den Namen eines Abschnitts in der Initialisierungsdatei oder einen Schlüssel in der Windows-Registrierung angibt, in dem Statusinformationen gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Der Profilname ist der Abschnitt der Anwendung . INI-Datei oder die Registrierung, die die Statusinformationen der Balken enthält. Sie können Steuerelementleistenstatusinformationen in der Registrierung oder speichern. INI-Datei `SaveState`mit .

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo

Ein `CPtrArray` Objekt, das ein Array von Zeigern auf die gespeicherten Steuerelementleisteninformationen `CDockState` für jede Steuerelementleiste ist, die Statusinformationen im Objekt gespeichert hat.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::SaveState

Rufen Sie diese Funktion auf, um die Statusinformationen in der Registrierung oder zu speichern. INI-Datei.

```cpp
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
Verweist auf eine Null-Teminat-Zeichenfolge, die den Namen eines Abschnitts in der Initialisierungsdatei oder einen Schlüssel in der Windows-Registrierung angibt, in dem Statusinformationen gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Der Profilname ist der Abschnitt der Anwendung . INI-Datei oder die Registrierung, die die Statusinformationen der Steuerleiste enthält. `SaveState`speichert auch die aktuelle Bildschirmgröße. Sie können Steuerelementleisteninformationen aus der Registrierung oder abrufen. INI-Datei `LoadState`mit .

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
