---
title: event_source (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167068"
---
# <a name="event_source"></a>event_source

Erstellt eine Ereignisquelle.

## <a name="syntax"></a>Syntax

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parameter

*type*<br/>
Eine Enumeration von einem der folgenden Werte:

- `native` für nicht verwalteten C/C++-Code (Standard für nicht verwaltete Klassen).

- `com` für COM-Code. Sie müssen `coclass` verwenden, wenn `type`=`com`. Dieser Wert erfordert, dass Sie folgende Headerdateien einschließen:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Wenn der *Typ* `native`ist, können Sie `optimize=size`angeben, um anzugeben, dass für alle Ereignisse in einer Klasse oder `optimize=speed` (Standardwert) 4 Bytes Speicher (minimal) vorhanden sind, um anzugeben, dass es 4 * (# der Ereignisse) Speicher Bytes gibt.

*decorate*<br/>
Wenn *Type* `native`ist, können Sie `decorate=false`angeben, um anzugeben, dass der erweiterte Name in der zusammengeführten Datei (. MRG) nicht den einschließenden Klassennamen enthalten soll. Mit[/Fx](../../build/reference/fx-merge-injected-code.md) können Sie MRG-Dateien generieren. `decorate=false`ist die Standardeinstellung und führt zu voll qualifizierten Typnamen in der zusammengeführten Datei.

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut **event_source** gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, eine Ereignisquelle sein wird.

**event_source** wird in Verbindung mit dem Attribut [event_receiver](event-receiver.md) und dem Schlüsselwort [__event](../../cpp/event.md) verwendet. Verwenden Sie `event_receiver`, um Ereignis Empfänger zu erstellen. Verwenden Sie **__event** für Methoden innerhalb der Ereignis Quelle, um diese Methoden als Ereignisse anzugeben.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|**Co-Klasse** , wenn `type`=`com`|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Klassenattribute](class-attributes.md)
