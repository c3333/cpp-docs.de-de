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
ms.openlocfilehash: a7231b01cd341bbc04bcccd3c2198d1a76dd5e39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232767"
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
Wenn der *Typ* auf fest `native` gelegt ist, können Sie angeben `optimize=size` , um anzugeben, dass für alle Ereignisse in einer Klasse 4 Bytes Speicher (minimal) vorhanden sind, oder `optimize=speed` (der Standardwert), um anzugeben, dass 4 * (# der Ereignisse) Speicher Bytes vorhanden sind.

*decorate*<br/>
Wenn *type* der Typ `native` auf festgelegt ist, können Sie angeben `decorate=false` , um anzugeben, dass der erweiterte Name in der zusammengeführten Datei (. MRG) nicht den einschließenden Klassennamen enthalten soll. Mit[/Fx](../../build/reference/fx-merge-injected-code.md) können Sie MRG-Dateien generieren. `decorate=false`(die Standardeinstellung) führt zu voll qualifizierten Typnamen in der zusammengeführten Datei.

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut **event_source** gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, eine Ereignisquelle sein wird.

**event_source** wird in Verbindung mit dem Attribut [event_receiver](event-receiver.md) und dem Schlüsselwort [__event](../../cpp/event.md) verwendet. Verwenden `event_receiver` Sie, um Ereignis Empfänger zu erstellen. Verwenden **`__event`** Sie für Methoden in der Ereignis Quelle, um diese Methoden als Ereignisse anzugeben.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**Co-Klasse** , wenn`type`=`com`|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[Compilerattribute](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Klassenattribute](class-attributes.md)
