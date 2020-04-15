---
title: Message Map Makros (ATL)
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
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326229"
---
# <a name="message-map-macros-atl"></a>Message Map Makros (ATL)

Diese Makros definieren Meldungszuordnungen und Einträge.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Markiert den Anfang einer alternativen Nachrichtenzuordnung.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Markiert den Anfang der Standardnachrichtenzuordnung.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Ketten zu einer alternativen Nachrichtenzuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Ketten zu einer alternativen Nachrichtenzuordnung in einem Datenmember der Klasse.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Ketten sie sich mit der Standardnachrichtenzuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Ketten zur Meldungszuordnung in einer anderen Klasse zur Laufzeit.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Ketten sie sich mit der Standardnachrichtenzuordnung in einem Datenmember der Klasse.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[COMMAND_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementiert eine leere Meldungszuordnung.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Stellt einen Standardhandler für reflektierte Nachrichten bereit, die andernfalls nicht behandelt werden.|
|[END_MSG_MAP](#end_msg_map)|Markiert das Ende einer Nachrichtenzuordnung.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Leitet Benachrichtigungen an das übergeordnete Fenster weiter.|
|[MESSAGE_HANDLER](#message_handler)|Ordnet eine Windows-Nachricht einer Handlerfunktion zu.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Ordnet einer Handlerfunktion einen zusammenhängenden Bereich von Windows-Nachrichten zu.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[NOTIFY_HANDLER](#notify_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Steuerelementbezeichner.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelementbezeichner basiert.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Spiegelt Benachrichtigungen zurück an das Fenster, das sie gesendet hat.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerelementbezeichnern.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode und dem Steuerelementbezeichner basiert.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelementbezeichner basiert.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerelementbezeichnern.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

Markiert den Anfang einer alternativen Nachrichtenzuordnung.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parameter

*msgMapID*<br/>
[in] Der Nachrichtenzuordnungsbezeichner.

### <a name="remarks"></a>Bemerkungen

ATL identifiziert jede Meldungszuordnung durch eine Zahl. Die Standardmeldungszuordnung (mit dem BEGIN_MSG_MAP-Makro deklariert) wird durch 0 identifiziert. Eine alternative Meldungszuordnung wird durch *msgMapID*identifiziert.

Nachrichtenzuordnungen werden verwendet, um Nachrichten zu verarbeiten, die an ein Fenster gesendet werden. Mit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) können Sie z. B. den Bezeichner einer Nachrichtenzuordnung im enthaltenden Objekt angeben. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) verwendet dann diese Meldungszuordnung, um die Nachrichten des enthaltenen Fensters entweder an die entsprechende Handlerfunktion oder an eine andere Nachrichtenzuordnung weiterzuleiten. Eine Liste der Makros, die Handlerfunktionen deklarieren, finden Sie [unter BEGIN_MSG_MAP](#begin_msg_map).

Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen deklarieren.

Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Beachten Sie, dass es immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP gibt.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Standardmeldungszuordnung und eine alternative Meldungszuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Nachrichtenzuordnungen. Die Standardmeldungszuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

Markiert den Anfang der Standardnachrichtenzuordnung.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
[in] Der Name der Klasse, die die Nachrichtenzuordnung enthält.

### <a name="remarks"></a>Bemerkungen

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) verwendet die Standard-Meldungszuordnung, um an das Fenster gesendete Nachrichten zu verarbeiten. Die Nachrichtenzuordnung leitet Nachrichten entweder an die entsprechende Handlerfunktion oder an eine andere Meldungszuordnung weiter.

Die folgenden Makros ordnen eine Nachricht einer Handlerfunktion zu. Diese Funktion muss in *derKlasse*definiert werden.

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Ordnet eine Windows-Nachricht einer Handlerfunktion zu.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Ordnet einer Handlerfunktion einen zusammenhängenden Bereich von Windows-Nachrichten zu.|
|[COMMAND_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[COMMAND_CODE_HANDLER](#command_handler)|Ordnet eine WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Ordnet einer Handlerfunktion basierend auf dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers einen zusammenhängenden Bereich von WM_COMMAND Nachrichten zu.|
|[NOTIFY_HANDLER](#notify_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Steuerelementbezeichner.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelementbezeichner basiert.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Ordnet eine WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Ordnet einer Handlerfunktion basierend auf dem Steuerelementbezeichner einen zusammenhängenden Bereich von WM_NOTIFY Nachrichten zu.|

Die folgenden Makros leiten Nachrichten an eine andere Nachrichtenzuordnung weiter. Dieser Prozess wird als "Verkettung" bezeichnet.

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Ketten sie sich mit der Standardnachrichtenzuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Ketten sie sich mit der Standardnachrichtenzuordnung in einem Datenmember der Klasse.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Ketten zu einer alternativen Nachrichtenzuordnung in der Basisklasse.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Ketten zu einer alternativen Nachrichtenzuordnung in einem Datenmember der Klasse.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Ketten zur Standardnachrichtenzuordnung in einer anderen Klasse zur Laufzeit.|

Die folgenden Makros leiten "reflektierte" Nachrichten aus dem übergeordneten Fenster. Beispielsweise sendet ein Steuerelement normalerweise Benachrichtigungen zur Verarbeitung an das übergeordnete Fenster, aber das übergeordnete Fenster kann die Nachricht an das Steuerelement zurückgeben.

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Bezeichner des Menüelements, Steuerelements oder Beschleunigers.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerelementbezeichnern.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Ordnet eine reflektierte WM_COMMAND Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode und dem Steuerelementbezeichner basiert.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Steuerelementbezeichner basiert.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, die auf dem Benachrichtigungscode basiert.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf einem zusammenhängenden Bereich von Steuerelementbezeichnern.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Ordnet eine reflektierte WM_NOTIFY Nachricht einer Handlerfunktion zu, basierend auf dem Benachrichtigungscode und einem zusammenhängenden Bereich von Steuerbezeichnern.|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Wenn `CMyExtWindow` ein Objekt eine WM_PAINT Nachricht empfängt, wird die Nachricht `CMyExtWindow::OnPaint` zur eigentlichen Verarbeitung weitergeleitet. Wenn `OnPaint` die Nachricht weiter verarbeitet werden muss, wird die Nachricht `CMyBaseWindow`an die Standardmeldungszuordnung in weitergeleitet.

Zusätzlich zur Standardmeldungszuordnung können Sie eine alternative Meldungszuordnung mit [ALT_MSG_MAP](#alt_msg_map)definieren. Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen deklarieren. Das folgende Beispiel zeigt die Standardmeldungszuordnung und eine alternative Meldungszuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Nachrichtenzuordnungen. Die Standardmeldungszuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Beachten Sie, dass es immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP gibt.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parameter

*theChainClass*<br/>
[in] Der Name der Basisklasse, die die Nachrichtenzuordnung enthält.

*msgMapID*<br/>
[in] Der Nachrichtenzuordnungsbezeichner.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_ALT leitet Nachrichten an eine alternative Nachrichtenzuordnung in einer Basisklasse weiter. Sie müssen diese alternative Meldungszuordnung mit [ALT_MSG_MAP(msgMapID)](#alt_msg_map)deklariert haben. Um Nachrichten an die Standardnachrichtenzuordnung einer Basisklasse weiterzuleiten (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert), verwenden Sie CHAIN_MSG_MAP. Ein Beispiel finden Sie [unter CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parameter

*theChainMember*<br/>
[in] Der Name des Datenelements, das die Nachrichtenzuordnung enthält.

*msgMapID*<br/>
[in] Der Nachrichtenzuordnungsbezeichner.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_ALT_MEMBER leitet Nachrichten an eine alternative Nachrichtenzuordnung in einem Datenmember weiter. Sie müssen diese alternative Meldungszuordnung mit [ALT_MSG_MAP(msgMapID)](#alt_msg_map)deklariert haben. Um Nachrichten an die Standardmeldungszuordnung eines Datenmitglieds weiterzuleiten (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert), verwenden Sie CHAIN_MSG_MAP_MEMBER. Ein Beispiel finden Sie [unter CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parameter

*theChainClass*<br/>
[in] Der Name der Basisklasse, die die Nachrichtenzuordnung enthält.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP leitet Nachrichten an die Standardnachrichtenzuordnung einer Basisklasse (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert). Um Nachrichten an die alternative Nachrichtenzuordnung einer Basisklasse weiterzuleiten (mit [ALT_MSG_MAP](#alt_msg_map)deklariert), verwenden Sie [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

In diesem Beispiel wird Folgendes veranschaulicht:

- Wenn eine Fensterprozedur `CMyClass`die Standardnachrichtenzuordnung `OnPaint` von verwendet und keine Nachricht `CMyBaseClass`verarbeitet, wird die Nachricht zur Verarbeitung an die Standardmeldungszuordnung von weitergeleitet.

- Wenn eine Fensterprozedur die erste alternative `CMyClass`Nachrichtenzuordnung in `CMyBaseClass`verwendet, werden alle Nachrichten an die Standardmeldungszuordnung von 's weitergeleitet.

- Wenn eine Fensterprozedur `CMyClass`die zweite alternative `OnChar` Nachrichtenzuordnung von verwendet und keine Nachricht verarbeitet, wird `CMyBaseClass`die Nachricht an die angegebene alternative Meldungszuordnung in weitergeleitet. `CMyBaseClass`muss diese Meldungszuordnung mit ALT_MSG_MAP(1) deklariert haben.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parameter

*dynaChainID*<br/>
[in] Der eindeutige Bezeichner für die Nachrichtenzuordnung eines Objekts.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_DYNAMIC leitet Nachrichten zur Laufzeit an die Standardnachrichtenzuordnung in einem anderen Objekt weiter. Das Objekt und seine Meldungszuordnung sind *dynaChainID*zugeordnet, die Sie über [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry)definieren. Sie müssen Ihre Klasse `CDynamicChain` ableiten, um CHAIN_MSG_MAP_DYNAMIC verwenden zu können. Ein Beispiel finden Sie in der [CDynamicChain-Übersicht.](../../atl/reference/cdynamicchain-class.md)

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parameter

*theChainMember*<br/>
[in] Der Name des Datenelements, das die Nachrichtenzuordnung enthält.

### <a name="remarks"></a>Bemerkungen

CHAIN_MSG_MAP_MEMBER leitet Nachrichten an die Standardmeldungszuordnung eines Datenmitglieds (mit [BEGIN_MSG_MAP](#begin_msg_map)deklariert). Um Nachrichten an die alternative Nachrichtenzuordnung eines Datenmembers weiterzuleiten (mit [ALT_MSG_MAP](#alt_msg_map)deklariert), verwenden Sie [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Beginnen Sie immer mit einer Nachrichtenzuordnung mit BEGIN_MSG_MAP. Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit ALT_MSG_MAP deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

In diesem Beispiel wird Folgendes veranschaulicht:

- Wenn eine Fensterprozedur `CMyClass`die Standardnachrichtenzuordnung `OnPaint` von verwendet und keine Nachricht `m_obj`verarbeitet, wird die Nachricht zur Verarbeitung an die Standardmeldungszuordnung von weitergeleitet.

- Wenn eine Fensterprozedur die erste alternative `CMyClass`Nachrichtenzuordnung in `m_obj`verwendet, werden alle Nachrichten an die Standardmeldungszuordnung von 's weitergeleitet.

- Wenn eine Fensterprozedur `CMyClass`die zweite alternative `OnChar` Nachrichtenzuordnung von verwendet und keine Nachricht verarbeitet, wird `m_obj`die Nachricht an die angegebene alternative Nachrichtenzuordnung von weitergeleitet. Die `CMyContainedClass` Klasse muss diese Meldungszuordnung mit ALT_MSG_MAP(1) deklariert haben.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Ähnlich wie [COMMAND_HANDLER,](#command_handler)aber ordnet eine [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht nur auf der Grundlage des Benachrichtigungscodes.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parameter

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die Kennung des Menüelements, Steuerelements oder Beschleunigers.

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

COMMAND_HANDLER ordnet der angegebenen Handlerfunktion basierend auf dem Benachrichtigungscode und dem Steuerelementbezeichner eine [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht zu. Beispiel:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Jede Funktion, die in einem COMMAND_HANDLER Makro angegeben ist, muss wie folgt definiert werden:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Die Meldungszuordnung setzt auf TRUE, `bHandled` bevor sie `CommandHandler` aufgerufen wird. Wenn `CommandHandler` die Nachricht nicht vollständig verarbeitet `bHandled` wird, sollte sie auf FALSE gesetzt werden, um anzugeben, dass die Nachricht weiter verarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu COMMAND_HANDLER können Sie [MESSAGE_HANDLER](#message_handler) verwenden, um eine WM_COMMAND Nachricht ohne Rücksicht auf einen Bezeichner oder Code zuzuordnen. In diesem `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` Fall leiten Sie `OnHandlerFunction`alle WM_COMMAND Nachrichten an .

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

Ähnlich wie [COMMAND_HANDLER](#command_handler), aber ordnet eine [WM_COMMAND](/windows/win32/menurc/wm-command) Nachricht nur auf der Grundlage des Bezeichners des Menüelements, Steuerelements oder Beschleunigers zu.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Der Bezeichner des Menüelements, Steuerelements oder Beschleunigers, der die Nachricht sendet.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Ähnlich wie [COMMAND_RANGE_HANDLER](#command_range_handler), ordnet [WM_COMMAND](/windows/win32/menurc/wm-command) Nachrichten jedoch einen bestimmten Benachrichtigungscode aus einem Steuerelementbereich einer einzelnen Handlerfunktion zu.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf der Kennung des Menüelements, Steuerelements oder Beschleunigers, der die Nachricht sendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Ähnlich wie [COMMAND_HANDLER](#command_handler), [ordnet](/windows/win32/menurc/wm-command) WM_COMMAND Nachrichten aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf der Kennung des Menüelements, Steuerelements oder Beschleunigers, der die Nachricht sendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Deklariert eine leere Meldungszuordnung.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Bemerkungen

DECLARE_EMPTY_MSG_MAP ist ein Komfortmakro, das die Makros [BEGIN_MSG_MAP](#begin_msg_map) und [END_MSG_MAP](#end_msg_map) aufruft, um eine leere Meldungszuordnung zu erstellen:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Stellt einen Standardhandler für das untergeordnete Fenster (Steuerelement) bereit, das reflektierte Nachrichten empfängt. Der Handler übergibt ordnungsgemäß nicht `DefWindowProc`behandelte Nachrichten an .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

Markiert das Ende einer Nachrichtenzuordnung.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [BEGIN_MSG_MAP](#begin_msg_map) immer das BEGIN_MSG_MAP-Makro, um den Anfang einer Meldungszuordnung zu markieren. Verwenden Sie [ALT_MSG_MAP,](#alt_msg_map) um nachfolgende alternative Nachrichtenzuordnungen zu deklarieren.

Beachten Sie, dass es immer genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP gibt.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Standardmeldungszuordnung und eine alternative Meldungszuordnung, die jeweils eine Handlerfunktion enthält:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Das nächste Beispiel zeigt zwei alternative Nachrichtenzuordnungen. Die Standardmeldungszuordnung ist leer.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Leitet Benachrichtigungen an das übergeordnete Fenster weiter.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Bemerkungen

Geben Sie dieses Makro als Teil der Nachrichtenzuordnung an.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parameter

*Msg*<br/>
[in] Die Windows-Nachricht.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

MESSAGE_HANDLER ordnet der angegebenen Handlerfunktion eine Windows-Nachricht zu.

Jede Funktion, die in einem MESSAGE_HANDLER Makro angegeben ist, muss wie folgt definiert werden:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Die Meldungszuordnung setzt auf TRUE, `bHandled` bevor sie `MessageHandler` aufgerufen wird. Wenn `MessageHandler` die Nachricht nicht vollständig verarbeitet `bHandled` wird, sollte sie auf FALSE gesetzt werden, um anzugeben, dass die Nachricht weiter verarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu MESSAGE_HANDLER können Sie [COMMAND_HANDLER](#command_handler) bzw. [NOTIFY_HANDLER](#notify_handler) verwenden, um [WM_COMMAND](/windows/win32/menurc/wm-command) bzw. [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachrichten zuzuordnen.

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Ähnlich wie [MESSAGE_HANDLER](#message_handler), ordnet jedoch eine Reihe von Windows-Nachrichten einer einzelnen Handlerfunktion zu.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parameter

*msgFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Nachrichtenbereichs.

*msgLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Nachrichtenbereichs.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), aber ordnet eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachricht nur basierend auf dem Benachrichtigungscode.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parameter

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

Definiert einen Eintrag in einer Nachrichtenzuordnung.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Der Bezeichner des Steuerelements, das die Nachricht sendet.

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

NOTIFY_HANDLER ordnet der angegebenen Handlerfunktion basierend auf dem Benachrichtigungscode und dem Steuerelementbezeichner eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachricht zu.

Jede Funktion, die in einem NOTIFY_HANDLER Makro angegeben ist, muss wie folgt definiert werden:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Die Meldungszuordnung setzt auf TRUE, `bHandled` bevor sie `NotifyHandler` aufgerufen wird. Wenn `NotifyHandler` die Nachricht nicht vollständig verarbeitet `bHandled` wird, sollte sie auf FALSE gesetzt werden, um anzugeben, dass die Nachricht weiter verarbeitet werden muss.

> [!NOTE]
> Beginnen Sie immer mit [BEGIN_MSG_MAP](#begin_msg_map). Anschließend können Sie nachfolgende alternative Nachrichtenzuordnungen mit [ALT_MSG_MAP](#alt_msg_map)deklarieren. Das [END_MSG_MAP-Makro](#end_msg_map) markiert das Ende der Meldungszuordnung. Jede Nachrichtenzuordnung muss genau eine Instanz von BEGIN_MSG_MAP und END_MSG_MAP haben.

Zusätzlich zu NOTIFY_HANDLER können Sie [MESSAGE_HANDLER](#message_handler) verwenden, um eine WM_NOTIFY Nachricht ohne Rücksicht auf einen Bezeichner oder Code zuzuordnen. In diesem `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` Fall leiten Sie `OnHandlerFunction`alle WM_NOTIFY Nachrichten an .

Weitere Informationen zur Verwendung von Nachrichtenzuordnungen in ATL finden Sie unter [Nachrichtenzuordnungen](../../atl/message-maps-atl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), ordnet jedoch eine [WM_NOTIFY](/windows/win32/controls/wm-notify) Nachricht zu, die nur auf dem Steuerelementbezeichner basiert.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Der Bezeichner des Steuerelements, das die Nachricht sendet.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Ähnlich wie [NOTIFY_RANGE_HANDLER](#notify_range_handler), [ordnet](/windows/win32/controls/wm-notify) WM_NOTIFY Nachrichten jedoch einen bestimmten Benachrichtigungscode aus einem Steuerelementbereich einer einzelnen Handlerfunktion zu.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Steuerelements, das die Nachricht sendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), [ordnet](/windows/win32/controls/wm-notify) WM_NOTIFY Nachrichten aus einem Bereich von Steuerelementen einer einzelnen Handlerfunktion zu.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="remarks"></a>Bemerkungen

Dieser Bereich basiert auf dem Bezeichner des Steuerelements, das die Nachricht sendet.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Spiegelt Benachrichtigungen zurück an das untergeordnete Fenster (Steuerelement), das sie gesendet hat.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Bemerkungen

Geben Sie dieses Makro als Teil der Meldungszuordnung des übergeordneten Fensters an.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Ähnlich wie [COMMAND_CODE_HANDLER](#command_code_handler), aber ordnet Befehle, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parameter

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Ähnlich wie [COMMAND_HANDLER](#command_handler), aber ordnet Befehle, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die Kennung des Menüelements, Steuerelements oder Beschleunigers.

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Ähnlich wie [COMMAND_ID_HANDLER](#command_id_handler), aber ordnet Befehle, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die Kennung des Menüelements, Steuerelements oder Beschleunigers.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Ähnlich wie [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), aber ordnet Befehle, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Code*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Ähnlich wie [COMMAND_RANGE_HANDLER](#command_range_handler), aber ordnet Befehle, die vom übergeordneten Fenster reflektiert werden.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Ähnlich wie [NOTIFY_CODE_HANDLER](#notify_code_handler), aber ordnet Benachrichtigungen, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parameter

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Ähnlich wie [NOTIFY_HANDLER](#notify_handler), aber ordnet Benachrichtigungen, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die Kennung des Menüelements, Steuerelements oder Beschleunigers.

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Ähnlich wie [NOTIFY_ID_HANDLER](#notify_id_handler), aber ordnet Benachrichtigungen, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Die Kennung des Menüelements, Steuerelements oder Beschleunigers.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Ähnlich wie [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), aber ordnet Benachrichtigungen, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Cd*<br/>
[in] Der Benachrichtigungscode.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Ähnlich wie [NOTIFY_RANGE_HANDLER](#notify_range_handler), aber ordnet Benachrichtigungen, die aus dem übergeordneten Fenster reflektiert werden.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parameter

*idFirst*<br/>
[in] Markiert den Beginn eines zusammenhängenden Bereichs von Steuerbezeichnern.

*idLast*<br/>
[in] Markiert das Ende eines zusammenhängenden Bereichs von Steuerbezeichnern.

*Func*<br/>
[in] Der Name der Message-Handler-Funktion.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
