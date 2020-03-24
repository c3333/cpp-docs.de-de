---
title: event_receiver (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 9653a0b5c756857d92914496b9c5c6f8aee56ebb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167081"
---
# <a name="event_receiver"></a>event_receiver

Erstellt einen Ereignisempfänger (Senke).

## <a name="syntax"></a>Syntax

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parameter

*type*<br/>
Eine Enumeration von einem der folgenden Werte:

- `native` für nicht verwalteten C/C++ Code (Standard für Native Klassen).

- `com` für COM-Code. Dieser Wert erfordert, dass Sie folgende Headerdateien einschließen:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Geben Sie *layout_dependent* nur an, wenn `type`=**com**. *layout_dependent* ist ein boolescher Wert:

- " **true** " bedeutet, dass die Signatur der Delegaten im Ereignis Empfänger genau mit denen übereinstimmen muss, an die Sie in der Ereignis Quelle angeschlossen sind. Die Namen des ereignishandlerhandlers müssen mit den in der relevanten Ereignis Quellen Schnittstelle angegebenen Namen identisch sein. Sie müssen `coclass` verwenden, wenn *layout_dependent* den Wert " **true**" hat. Es ist etwas effizienter, " **true**" anzugeben.

- **false** (Standard) bedeutet, dass die Aufruf Konvention und die Speicher Klasse (virtuell, statisch und andere) nicht mit der Ereignismethode und den Handlern übereinstimmen müssen. Außerdem müssen die Handlernamen nicht mit den Methodennamen der Ereignis Quell Schnittstellen identisch sein.

## <a name="remarks"></a>Bemerkungen

Das **event_receiver** C++ -Attribut gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, mithilfe des visuellen C++ Unified-Ereignis Modells als Ereignis Empfänger festgelegt wird.

**event_receiver** wird mit dem [event_source](event-source.md) -Attribut und den Schlüsselwörtern [__hook](../../cpp/hook.md) und [__unhook](../../cpp/unhook.md) verwendet. Verwenden Sie `event_source` zum Erstellen von Ereignis Quellen. Verwenden Sie **__hook** in den Methoden eines Ereignis Empfängers, um Ereignis Empfänger Methoden ("Hook") den Ereignissen einer Ereignis Quelle zuzuordnen. Verwenden Sie **__unhook** , um Sie zu trennen.

*layout_dependent* wird nur für com-Ereignis Empfänger (`type`=**com**) angegeben. Der Standardwert für *layout_dependent* ist **false**.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|`coclass`, wenn *layout_dependent*=**true**|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Klassenattribute](class-attributes.md)
