---
title: CMessageMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326721"
---
# <a name="cmessagemap-class"></a>CMessageMap-Klasse

Diese Klasse ermöglicht den Zugriff auf die Nachrichtenzuordnungen eines Objekts durch ein anderes Objekt.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Greift auf eine Nachrichtenzuordnung in der `CMessageMap`-derived-Klasse zu.|

## <a name="remarks"></a>Bemerkungen

`CMessageMap`ist eine abstrakte Basisklasse, mit der auf die Nachrichtenzuordnungen eines Objekts von einem anderen Objekt zugegriffen werden kann. Damit ein Objekt seine Nachrichtenzuordnungen verfügbar macht, `CMessageMap`muss seine Klasse von ableiten.

ATL `CMessageMap` unterstützt enthaltene Fenster und dynamische Nachrichtenzuordnungsverkettungen. Beispielsweise muss jede Klasse, die ein [CContainedWindow-Objekt](../../atl/reference/ccontainedwindowt-class.md) enthält, von `CMessageMap`ableiten. Der folgende Code wird dem [SUBEDIT-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) entnommen. Über [CComControl](../../atl/reference/ccomcontrol-class.md) `CAtlEdit` leitet sich die `CMessageMap`Klasse automatisch von ab.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Da das enthaltene Fenster `m_EditCtrl`, eine Nachrichtenzuordnung `CAtlEdit` in der `CMessageMap`enthaltenden Klasse verwendet, leitet sich von ab.

Weitere Informationen zu Nachrichtenzuordnungen finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md) im Artikel "ATL Window Classes".

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage

Greift auf die Nachrichtenzuordnung zu, die `CMessageMap`von *dwMsgMapID* in einer -derived-Klasse identifiziert wurde.

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>Parameter

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

*dwMsgMapID*<br/>
[in] Der Bezeichner der Nachrichtenzuordnung, die die Nachricht verarbeitet. Die mit [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)deklarierte Standardmeldungszuordnung wird durch 0 identifiziert. Eine alternative Meldungszuordnung, die mit [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)deklariert wurde, wird durch `msgMapID`identifiziert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Nachricht vollständig verarbeitet wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wird durch die Fensterprozedur eines [CContainedWindow-Objekts](../../atl/reference/ccontainedwindowt-class.md) oder eines Objekts aufgerufen, das dynamisch mit der Nachrichtenzuordnung verkettet wird.

## <a name="see-also"></a>Siehe auch

[CDynamicChain-Klasse](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
