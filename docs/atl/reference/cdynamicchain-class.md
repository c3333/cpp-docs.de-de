---
title: CDynamicChain-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327035"
---
# <a name="cdynamicchain-class"></a>CDynamicChain-Klasse

Diese Klasse stellt Methoden bereit, die die dynamische Verkettung von Nachrichtenzuordnungen unterstützen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CDynamicChain
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Der Konstruktor.|
|[CDynamicChain::-CDynamicChain](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Leitet eine Windows-Nachricht an die Nachrichtenzuordnung eines anderen Objekts weiter.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Entfernt einen Meldungszuordnungseintrag aus der Auflistung.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Fügt der Auflistung einen Meldungszuordnungseintrag hinzu oder ändert einen vorhandenen Eintrag.|

## <a name="remarks"></a>Bemerkungen

`CDynamicChain`verwaltet eine Sammlung von Nachrichtenzuordnungen, sodass eine Windows-Nachricht zur Laufzeit an die Nachrichtenzuordnung eines anderen Objekts weitergeleitet werden kann.

Gehen Sie wie folgt vor, um Unterstützung für die dynamische Verkettung von Nachrichtenzuordnungen hinzuzufügen:

- Leiten Sie Ihre `CDynamicChain`Klasse von ab. Geben Sie in der Meldungszuordnung die [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) Makros an, das mit der Standardnachrichtenzuordnung eines anderen Objekts verkettet werden soll.

- Leiten Sie jede Klasse ab, an die Sie eine Kette von [CMessageMap](../../atl/reference/cmessagemap-class.md)verketten möchten. `CMessageMap`ermöglicht es einem Objekt, seine Nachrichtenzuordnungen für andere Objekte verfügbar zu machen.

- Rufen `CDynamicChain::SetChainEntry` Sie auf, um zu identifizieren, welches Objekt und an welche Nachrichtenzuordnung Sie verketten möchten.

Angenommen, Ihre Klasse ist wie folgt definiert:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Der Client `CMyWindow::SetChainEntry`ruft dann auf:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

wobei `chainedObj` das verkettete Objekt und eine Instanz `CMessageMap`einer von abgeleiteten Klasse ist. Wenn nun `myCtl` eine Nachricht empfängt wird, `OnPaint` `OnSetFocus`die nicht von oder behandelt `chainedObj`wird, leitet die Fensterprozedur die Nachricht an die Standardmeldungszuordnung von 's weiter.

Weitere Informationen zur Verkettung von Nachrichtenkarten finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md) im Artikel "ATL Window Classes".

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain

Leitet die Windows-Nachricht an die Nachrichtenzuordnung eines anderen Objekts weiter.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>Parameter

*dwChainID*<br/>
[in] Der eindeutige Bezeichner, der dem verketteten Objekt und seiner Meldungszuordnung zugeordnet ist.

*hWnd*<br/>
[in] Das Handle für das Fenster, das die Nachricht empfängt.

*uMsg*<br/>
[in] Die an das Fenster gesendete Nachricht.

*wParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lParam*<br/>
[in] Zusätzliche nachrichtenspezifische Informationen.

*lResult*<br/>
[out] Das Ergebnis der Nachrichtenverarbeitung.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Nachricht vollständig verarbeitet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Damit die Fensterprozedur `CallChain`aufgerufen werden kann, müssen Sie das [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) Makros in der Nachrichtenzuordnung angeben. Ein Beispiel finden Sie in der [CDynamicChain-Übersicht.](../../atl/reference/cdynamicchain-class.md)

`CallChain`erfordert einen vorherigen Aufruf von [SetChainEntry,](#setchainentry) um den *dwChainID-Wert* einem Objekt und seiner Nachrichtenzuordnung zuzuordnen.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain

Der Konstruktor.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain::-CDynamicChain

Der Destruktor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry

Entfernt die angegebene Meldungszuordnung aus der Auflistung.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parameter

*dwChainID*<br/>
[in] Der eindeutige Bezeichner, der dem verketteten Objekt und seiner Meldungszuordnung zugeordnet ist. Sie definieren diesen Wert ursprünglich über einen Aufruf von [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Nachrichtenzuordnung erfolgreich aus der Auflistung entfernt wurde. Andernfalls lautet der Wert FALSE.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain::SetChainEntry

Fügt der Auflistung die angegebene Nachrichtenzuordnung hinzu.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parameter

*dwChainID*<br/>
[in] Der eindeutige Bezeichner, der dem verketteten Objekt und seiner Meldungszuordnung zugeordnet ist.

*pObject*<br/>
[in] Ein Zeiger auf das verkettete Objekt, das die Nachrichtenzuordnung deklariert. Dieses Objekt muss von [CMessageMap](../../atl/reference/cmessagemap-class.md)abstammen.

*dwMsgMapID*<br/>
[in] Der Bezeichner der Nachrichtenzuordnung im verketteten Objekt. Der Standardwert ist 0, der die mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung identifiziert. Um eine alternative Meldungszuordnung anzugeben, die mit `msgMapID` [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, übergeben Sie .

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Nachrichtenzuordnung erfolgreich zur Auflistung hinzugefügt wurde. Andernfalls lautet der Wert FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn der *dwChainID-Wert* bereits in der Auflistung vorhanden ist, werden das zugehörige Objekt und die zugehörige Nachrichtenzuordnung durch *pObject* bzw. *dwMsgMapID*ersetzt. Andernfalls wird ein neuer Eintrag hinzugefügt.

## <a name="see-also"></a>Siehe auch

[CWindowImpl-Klasse](../../atl/reference/cwindowimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
