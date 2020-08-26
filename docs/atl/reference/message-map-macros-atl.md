---
title: Meldungs Zuordnungs Makros (ATL)
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 9917f31dbb115552cf9dc9bde24f7b6921611750
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835297"
---
# <a name="message-map-macros-atl"></a>Meldungs Zuordnungs Makros (ATL)

Diese Makros definieren Meldungs Zuordnungen und Einträge.

|Name|Beschreibung|
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Markiert den Anfang einer alternativen Meldungs Zuordnung.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Markiert den Anfang der Standard Meldungs Zuordnung.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Verkettet eine Alternative Meldungs Zuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Verkettet eine Alternative Meldungs Zuordnung in einem Datenmember der-Klasse.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Verkettet mit der Standard Meldungs Zuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Verkettet zur Laufzeit eine Verkettung mit der Meldungs Zuordnung in einer anderen Klasse.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Verkettet mit der Standard Meldungs Zuordnung in einem Datenmember der-Klasse.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[COMMAND_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Bezeichner des Menü Elements, der Steuerung oder der Zugriffstaste.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Ordnet eine WM_COMMAND Meldung einer Handlerfunktion zu, die auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste basiert.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementiert eine leere Meldungs Zuordnung.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Stellt einen Standard Handler für reflektierte Meldungen bereit, die nicht anderweitig behandelt werden.|
|[END_MSG_MAP](#end_msg_map)|Markiert das Ende einer Meldungs Zuordnung.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Leitet Benachrichtigungs Meldungen an das übergeordnete Fenster weiter.|
|[MESSAGE_HANDLER](#message_handler)|Ordnet eine Windows-Meldung einer Handlerfunktion zu.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Ordnet einem Handlerfunktion einen zusammenhängenden Bereich von Windows-Meldungen zu.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[NOTIFY_HANDLER](#notify_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelement Bezeichner basiert.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Gibt Benachrichtigungs Meldungen zurück in das Fenster an, in dem Sie gesendet wurden.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Bezeichner des Menü Elements, der Steuerung oder der Zugriffstaste.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelement Bezeichner basiert.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a> ALT_MSG_MAP

Markiert den Anfang einer alternativen Meldungs Zuordnung.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parameter

*msgmapid*<br/>
in Der Bezeichner der Meldungs Zuordnung.

### <a name="remarks"></a>Bemerkungen

ATL identifiziert die einzelnen Nachrichten Zuordnungen nach einer Zahl. Die standardmäßige Meldungs Zuordnung (deklariert mit dem BEGIN_MSG_MAP-Makro) wird durch 0 identifiziert. Eine Alternative Meldungs Zuordnung wird durch *msgmapid*identifiziert.

Meldungs Zuordnungen werden verwendet, um an ein Fenster gesendete Nachrichten zu verarbeiten. Beispielsweise können Sie mit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) den Bezeichner einer Meldungs Zuordnung im enthaltenden Objekt angeben. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) verwendet diese Meldungs Zuordnung dann, um die Nachrichten des enthaltenen Fensters entweder an die entsprechende Handlerfunktion oder an eine andere Meldungs Zuordnung weiterzuleiten. Eine Liste der Makros, die Handlerfunktionen deklarieren, finden Sie unter [BEGIN_MSG_MAP](#begin_msg_map).

Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen deklarieren.

Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Beachten Sie, dass immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP vorhanden ist.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die standardmäßige Meldungs Zuordnung und eine Alternative Meldungs Zuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Meldungs Zuordnungen. Die Standard Meldungs Zuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a> BEGIN_MSG_MAP

Markiert den Anfang der Standard Meldungs Zuordnung.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
in Der Name der Klasse, die die Meldungs Zuordnung enthält.

### <a name="remarks"></a>Bemerkungen

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) verwendet die standardmäßige Meldungs Zuordnung, um Nachrichten zu verarbeiten, die an das Fenster gesendet werden. Die Meldungs Zuordnung leitet Nachrichten entweder an die entsprechende Handlerfunktion oder an eine andere Meldungs Zuordnung weiter.

Die folgenden Makros ordnen eine-Nachricht einer Handlerfunktion zu. Diese Funktion muss in " *TheClass*" definiert werden.

|Makro|Beschreibung|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Ordnet eine Windows-Meldung einer Handlerfunktion zu.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Ordnet einem Handlerfunktion einen zusammenhängenden Bereich von Windows-Meldungen zu.|
|[COMMAND_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Bezeichner des Menü Elements, der Steuerung oder der Zugriffstaste.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Ordnet eine WM_COMMAND Meldung einer Handlerfunktion zu, die auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste basiert.|
|[COMMAND_CODE_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Ordnet einen zusammenhängenden Bereich von WM_COMMAND Meldungen einer Handlerfunktion zu, basierend auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.|
|[NOTIFY_HANDLER](#notify_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelement Bezeichner basiert.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Ordnet einen zusammenhängenden Bereich von WM_NOTIFY Meldungen einer Handlerfunktion zu, basierend auf dem Steuerelement Bezeichner.|

Die folgenden Makros leiten Nachrichten an eine andere Meldungs Zuordnung weiter. Dieser Vorgang wird als "Verkettung" bezeichnet.

|Makro|Beschreibung|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Verkettet mit der Standard Meldungs Zuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Verkettet mit der Standard Meldungs Zuordnung in einem Datenmember der-Klasse.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Verkettet eine Alternative Meldungs Zuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Verkettet eine Alternative Meldungs Zuordnung in einem Datenmember der-Klasse.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Verkettet zur Laufzeit eine Verkettung mit der Standard Meldungs Zuordnung in einer anderen Klasse.|

Die folgenden Makros leiten "reflektierte" Nachrichten aus dem übergeordneten Fenster weiter. Ein Steuerelement sendet z. b. normalerweise Benachrichtigungs Meldungen zur Verarbeitung an das übergeordnete Fenster, aber das übergeordnete Fenster kann die Nachricht an das Steuerelement zurückgeben.

|Makro|Beschreibung|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Bezeichner des Menü Elements, der Steuerung oder der Zugriffstaste.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelement Bezeichner basiert.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion auf Grundlage des Benachrichtigungs Codes zu.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungs Code und einem zusammenhängenden Bereich von Steuerelement bezeichaten basiert.|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Wenn ein- `CMyExtWindow` Objekt eine WM_PAINT Nachricht empfängt, wird die Nachricht `CMyExtWindow::OnPaint` für die tatsächliche Verarbeitung an weitergeleitet. Wenn `OnPaint` anzeigt, dass die Nachricht weiterverarbeitet werden muss, wird die Nachricht an die Standard Meldungs Zuordnung in weitergeleitet `CMyBaseWindow` .

Zusätzlich zur Standard Meldungs Zuordnung können Sie eine Alternative Meldungs Zuordnung mit [ALT_MSG_MAP](#alt_msg_map)definieren. Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen deklarieren. Das folgende Beispiel zeigt die standardmäßige Meldungs Zuordnung und eine Alternative Meldungs Zuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Meldungs Zuordnungen. Die Standard Meldungs Zuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Beachten Sie, dass immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP vorhanden ist.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a> CHAIN_MSG_MAP_ALT

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parameter

*"-chainclass"*<br/>
in Der Name der Basisklasse, die die Meldungs Zuordnung enthält.

*msgmapid*<br/>
in Der Bezeichner der Meldungs Zuordnung.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_ALT leitet Nachrichten an eine Alternative Meldungs Zuordnung in einer Basisklasse weiter. Sie müssen diese Alternative Meldungs Zuordnung mit [ALT_MSG_MAP (msgmapid)](#alt_msg_map)deklarieren. Verwenden Sie CHAIN_MSG_MAP, um Nachrichten an die Standard Meldungs Zuordnung einer Basisklasse weiterzuleiten (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert). Ein Beispiel finden Sie unter [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a> CHAIN_MSG_MAP_ALT_MEMBER

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parameter

*der chainmember*<br/>
in Der Name des Datenmembers, der die Meldungs Zuordnung enthält.

*msgmapid*<br/>
in Der Bezeichner der Meldungs Zuordnung.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_ALT_MEMBER leitet Nachrichten an eine Alternative Nachrichten Zuordnung in einem Datenmember weiter. Sie müssen diese Alternative Meldungs Zuordnung mit [ALT_MSG_MAP (msgmapid)](#alt_msg_map)deklarieren. Verwenden Sie CHAIN_MSG_MAP_MEMBER, um Nachrichten an die Standard Meldungs Zuordnung eines Datenelements weiterzuleiten (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert). Ein Beispiel finden Sie unter [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a> CHAIN_MSG_MAP

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parameter

*"-chainclass"*<br/>
in Der Name der Basisklasse, die die Meldungs Zuordnung enthält.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP leitet Nachrichten an die Standard Meldungs Zuordnung einer Basisklasse (deklariert mit [BEGIN_MSG_MAP](#begin_msg_map)). Verwenden Sie [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt), um Nachrichten an die Alternative Meldungs Zuordnung einer Basisklasse weiterzuleiten (mit [ALT_MSG_MAP](#alt_msg_map)deklariert).

> [!NOTE]
> Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

In diesem Beispiel wird Folgendes veranschaulicht:

- Wenn eine Fenster Prozedur die Standard Meldungs Zuordnung verwendet `CMyClass` und `OnPaint` keine Nachricht verarbeitet, wird die Nachricht zur Verarbeitung an die standardmäßige Meldungs Zuordnung weitergeleitet `CMyBaseClass` .

- Wenn eine Fenster Prozedur die erste Alternative Meldungs Zuordnung in verwendet `CMyClass` , werden alle Nachrichten an die standardmäßige Meldungs Zuordnung weitergeleitet `CMyBaseClass` .

- Wenn eine Fenster Prozedur `CMyClass` die zweite Alternative Nachrichten Zuordnung verwendet und `OnChar` keine Nachricht verarbeitet, wird die Nachricht an die angegebene alternative Meldungs Zuordnung in umgeleitet `CMyBaseClass` . `CMyBaseClass` Diese Meldungs Zuordnung muss mit ALT_MSG_MAP (1) deklariert werden.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a> CHAIN_MSG_MAP_DYNAMIC

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parameter

*dynachainid*<br/>
in Der eindeutige Bezeichner für die Meldungs Zuordnung eines Objekts.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_DYNAMIC leitet Nachrichten zur Laufzeit an die Standard Meldungs Zuordnung in einem anderen Objekt weiter. Das-Objekt und seine Meldungs Zuordnung sind mit *dynachainid*verknüpft, das Sie durch [cdynamicchain:: setchainentry](cdynamicchain-class.md#setchainentry)definieren. Sie müssen die Klasse von ableiten `CDynamicChain` , um CHAIN_MSG_MAP_DYNAMIC zu verwenden. Ein Beispiel finden Sie in der Übersicht über [cdynamicchain](../../atl/reference/cdynamicchain-class.md) .

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a> CHAIN_MSG_MAP_MEMBER

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parameter

*der chainmember*<br/>
in Der Name des Datenmembers, der die Meldungs Zuordnung enthält.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_MEMBER leitet Nachrichten an die Standard Meldungs Zuordnung eines Daten Members (deklariert mit [BEGIN_MSG_MAP](#begin_msg_map)). Verwenden Sie [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member), um Nachrichten an die Alternative Meldungs Zuordnung eines Datenelements weiterzuleiten (mit [ALT_MSG_MAP](#alt_msg_map)deklariert).

> [!NOTE]
> Beginnen Sie immer mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

In diesem Beispiel wird Folgendes veranschaulicht:

- Wenn eine Fenster Prozedur die Standard Meldungs Zuordnung verwendet `CMyClass` und `OnPaint` keine Nachricht verarbeitet, wird die Nachricht zur Verarbeitung an die standardmäßige Meldungs Zuordnung weitergeleitet `m_obj` .

- Wenn eine Fenster Prozedur die erste Alternative Meldungs Zuordnung in verwendet `CMyClass` , werden alle Nachrichten an die standardmäßige Meldungs Zuordnung weitergeleitet `m_obj` .

- Wenn eine Fenster Prozedur `CMyClass` die zweite Alternative Nachrichten Zuordnung verwendet und `OnChar` keine Nachricht verarbeitet, wird die Nachricht an die angegebene alternative Meldungs Zuordnung von weitergeleitet `m_obj` . Die Klasse muss diese Meldungs Zuordnung `CMyContainedClass` mit ALT_MSG_MAP (1) deklarieren.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="command_code_handler"></a><a name="command_code_handler"></a> COMMAND_CODE_HANDLER

Ähnlich wie [COMMAND_HANDLER](#command_handler), ordnet aber eine [WM_COMMAND](/windows/win32/menurc/wm-command) Meldung nur auf Grundlage des Benachrichtigungs Codes zu.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parameter

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="command_handler"></a><a name="command_handler"></a> COMMAND_HANDLER

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

COMMAND_HANDLER ordnet der angegebenen Handlerfunktion eine [WM_COMMAND](/windows/win32/menurc/wm-command) Meldung basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner zu. Beispiel:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Jede in einem COMMAND_HANDLER-Makro angegebene Funktion muss wie folgt definiert werden:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Die Meldungs Zuordnung `bHandled` wird auf true festgelegt, bevor `CommandHandler` aufgerufen wird. Wenn `CommandHandler` die Nachricht nicht vollständig verarbeitet, sollte Sie auf false festgelegt werden, `bHandled` um anzugeben, dass die Nachricht weiterverarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu COMMAND_HANDLER können Sie [MESSAGE_HANDLER](#message_handler) verwenden, um eine WM_COMMAND Nachricht ohne Berücksichtigung eines Bezeichners oder Codes zuzuordnen. In diesem Fall `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` leitet alle WM_COMMAND-Nachrichten an weiter `OnHandlerFunction` .

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="command_id_handler"></a><a name="command_id_handler"></a> COMMAND_ID_HANDLER

Ähnelt [COMMAND_HANDLER](#command_handler), aber ordnet eine [WM_COMMAND](/windows/win32/menurc/wm-command) Meldung nur auf Grundlage des Bezeichners des Menü Elements, des Steuer Elements oder der Zugriffstaste zu.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, Steuer Elements oder Zugriffstasten, der die Nachricht sendet.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a> COMMAND_RANGE_CODE_HANDLER

Ähnelt [COMMAND_RANGE_HANDLER](#command_range_handler), aber ordnet [WM_COMMAND](/windows/win32/menurc/wm-command) Nachrichten mit einem bestimmten Benachrichtigungs Code aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste, die die Nachricht sendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="command_range_handler"></a><a name="command_range_handler"></a> COMMAND_RANGE_HANDLER

Ähnelt [COMMAND_HANDLER](#command_handler), aber ordnet [WM_COMMAND](/windows/win32/menurc/wm-command) Meldungen aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste, die die Nachricht sendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a> DECLARE_EMPTY_MSG_MAP

Deklariert eine leere Meldungs Zuordnung.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Bemerkungen

DECLARE_EMPTY_MSG_MAP ist ein praktisches Makro, das die Makros [BEGIN_MSG_MAP](#begin_msg_map) aufruft und [END_MSG_MAP](#end_msg_map) , eine leere Meldungs Zuordnung zu erstellen:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a> DEFAULT_REFLECTION_HANDLER

Stellt einen Standard Handler für das untergeordnete Fenster (-Steuerelement) bereit, das reflektierte Meldungen empfängt. der Handler übergibt nicht verarbeitete Nachrichten ordnungsgemäß an `DefWindowProc` .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="end_msg_map"></a><a name="end_msg_map"></a> END_MSG_MAP

Markiert das Ende einer Meldungs Zuordnung.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie immer das [BEGIN_MSG_MAP](#begin_msg_map) -Makro, um den Anfang einer Meldungs Zuordnung zu markieren. Verwenden Sie [ALT_MSG_MAP](#alt_msg_map) , um nachfolgende Alternative Nachrichten Zuordnungen zu deklarieren

Beachten Sie, dass immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP vorhanden ist.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die standardmäßige Meldungs Zuordnung und eine Alternative Meldungs Zuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Meldungs Zuordnungen. Die Standard Meldungs Zuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="forward_notifications"></a><a name="forward_notifications"></a> FORWARD_NOTIFICATIONS

Leitet Benachrichtigungs Meldungen an das übergeordnete Fenster weiter.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Bemerkungen

Geben Sie dieses Makro als Teil der Meldungs Zuordnung an.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="message_handler"></a><a name="message_handler"></a> MESSAGE_HANDLER

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parameter

*msg*<br/>
in Die Windows-Meldung.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

MESSAGE_HANDLER eine Windows-Meldung der angegebenen Handlerfunktion zuordnet.

Jede in einem MESSAGE_HANDLER-Makro angegebene Funktion muss wie folgt definiert werden:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Die Meldungs Zuordnung `bHandled` wird auf true festgelegt, bevor `MessageHandler` aufgerufen wird. Wenn `MessageHandler` die Nachricht nicht vollständig verarbeitet, sollte Sie auf false festgelegt werden, `bHandled` um anzugeben, dass die Nachricht weiterverarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu MESSAGE_HANDLER können Sie [COMMAND_HANDLER](#command_handler) und [NOTIFY_HANDLER](#notify_handler) verwenden, um [WM_COMMAND](/windows/win32/menurc/wm-command) -bzw. [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachrichten zuzuordnen.

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="message_range_handler"></a><a name="message_range_handler"></a> MESSAGE_RANGE_HANDLER

Ähnlich wie [MESSAGE_HANDLER](#message_handler), ordnet aber einen Bereich von Windows-Meldungen einer einzelnen Handlerfunktion zu.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parameter

*msgfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Meldungen.

*msglast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Meldungen.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a> NOTIFY_CODE_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), ordnet aber eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Meldung nur auf Grundlage des Benachrichtigungs Codes zu.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parameter

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="notify_handler"></a><a name="notify_handler"></a> NOTIFY_HANDLER

Definiert einen Eintrag in einer Meldungs Zuordnung.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Steuer Elements, das die Nachricht sendet.

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

NOTIFY_HANDLER ordnet der angegebenen Handlerfunktion eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Meldung basierend auf dem Benachrichtigungs Code und dem Steuerelement Bezeichner zu.

Jede in einem NOTIFY_HANDLER-Makro angegebene Funktion muss wie folgt definiert werden:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Die Meldungs Zuordnung `bHandled` wird auf true festgelegt, bevor `NotifyHandler` aufgerufen wird. Wenn `NotifyHandler` die Nachricht nicht vollständig verarbeitet, sollte Sie auf false festgelegt werden, `bHandled` um anzugeben, dass die Nachricht weiterverarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende Alternative Nachrichten Zuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP](#end_msg_map) -Makro markiert das Ende der Meldungs Zuordnung. Jede Nachrichten Zuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu NOTIFY_HANDLER können Sie [MESSAGE_HANDLER](#message_handler) verwenden, um eine WM_NOTIFY Nachricht ohne Berücksichtigung eines Bezeichners oder Codes zuzuordnen. In diesem Fall `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` leitet alle WM_NOTIFY-Nachrichten an weiter `OnHandlerFunction` .

Weitere Informationen zum Verwenden von Meldungs Zuordnungen in ATL finden Sie unter [Message Maps](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a> NOTIFY_ID_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), ordnet aber eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Meldung nur auf Grundlage des Steuerelement Bezeichners zu.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Steuer Elements, das die Nachricht sendet.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a> NOTIFY_RANGE_CODE_HANDLER

Ähnelt [NOTIFY_RANGE_HANDLER](#notify_range_handler), aber ordnet [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachrichten mit einem bestimmten Benachrichtigungs Code aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Steuer Elements, das die Nachricht sendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a> NOTIFY_RANGE_HANDLER

Ähnelt [NOTIFY_HANDLER](#notify_handler), aber ordnet [WM_NOTIFY](/windows/win32/controls/wm-notify) Meldungen aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Steuer Elements, das die Nachricht sendet.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a> REFLECT_NOTIFICATIONS

Gibt Benachrichtigungs Meldungen zurück an das untergeordnete Fenster (Steuerelement), das Sie gesendet hat.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Bemerkungen

Geben Sie dieses Makro als Teil der Meldungs Zuordnung des übergeordneten Fensters an.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a> REFLECTED_COMMAND_CODE_HANDLER

Ähnlich wie [COMMAND_CODE_HANDLER](#command_code_handler), ordnet jedoch Befehle zu, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parameter

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a> REFLECTED_COMMAND_HANDLER

Ähnlich wie [COMMAND_HANDLER](#command_handler), ordnet jedoch Befehle zu, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a> REFLECTED_COMMAND_ID_HANDLER

Ähnlich wie [COMMAND_ID_HANDLER](#command_id_handler), ordnet jedoch Befehle zu, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a> REFLECTED_COMMAND_RANGE_CODE_HANDLER

Ähnlich wie [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ordnet jedoch Befehle zu, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*code*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a> REFLECTED_COMMAND_RANGE_HANDLER

Ähnlich wie [COMMAND_RANGE_HANDLER](#command_range_handler), ordnet jedoch Befehle zu, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a> REFLECTED_NOTIFY_CODE_HANDLER

Ähnlich wie [NOTIFY_CODE_HANDLER](#notify_code_handler), ordnet aber die vom übergeordneten Fenster reflektierten Benachrichtigungen zu.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parameter

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a> REFLECTED_NOTIFY_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), ordnet aber die vom übergeordneten Fenster reflektierten Benachrichtigungen zu.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a> REFLECTED_NOTIFY_ID_HANDLER

Ähnlich wie [NOTIFY_ID_HANDLER](#notify_id_handler), ordnet aber die vom übergeordneten Fenster reflektierten Benachrichtigungen zu.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Der Bezeichner des Menü Elements, des Steuer Elements oder der Zugriffstaste.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a> REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Ähnlich wie [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ordnet aber die vom übergeordneten Fenster reflektierten Benachrichtigungen zu.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*cd*<br/>
in Der Benachrichtigungs Code.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a> REFLECTED_NOTIFY_RANGE_HANDLER

Ähnlich wie [NOTIFY_RANGE_HANDLER](#notify_range_handler), ordnet aber die vom übergeordneten Fenster reflektierten Benachrichtigungen zu.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idfirst*<br/>
in Markiert den Anfang eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*idlast*<br/>
in Markiert das Ende eines zusammenhängenden Bereichs von Steuerelement bezeichlern.

*func*<br/>
in Der Name der nachrichtenhandlerfunktion.

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
