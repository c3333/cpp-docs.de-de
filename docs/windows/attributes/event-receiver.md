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
ms.openlocfilehash: fb17eaa5d94636cedd650eb1bfb393d7c09e4fcc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217271"
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

- `native`für nicht verwalteten C/C++-Code (Standardeinstellung für Native Klassen).

- `com` für COM-Code. Dieser Wert erfordert, dass Sie folgende Headerdateien einschließen:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Geben Sie *layout_dependent* nur dann an, wenn `type` = **com**. *layout_dependent* ist ein boolescher Wert:

- **`true`** bedeutet, dass die Signatur der Delegaten im Ereignis Empfänger genau mit denen übereinstimmen muss, an die Sie in der Ereignis Quelle angeschlossen sind. Die Namen des ereignishandlerhandlers müssen mit den in der relevanten Ereignis Quellen Schnittstelle angegebenen Namen identisch sein. Sie müssen verwenden, `coclass` Wenn *layout_dependent* ist **`true`** . Es ist etwas effizienter, anzugeben **`true`** .

- **`false`**(Standard) bedeutet, dass die Aufruf Konvention und die Speicher Klasse (virtuell, statisch und andere) nicht mit der Ereignismethode und den Handlern übereinstimmen müssen. Außerdem müssen die Handlernamen nicht mit den Methodennamen der Ereignis Quell Schnittstellen identisch sein.

## <a name="remarks"></a>Bemerkungen

Das **event_receiver** C++-Attribut gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, ein Ereignis Empfänger ist, wobei das Visual C++ Unified-Ereignis Modell verwendet wird.

**event_receiver** wird mit dem [event_source](event-source.md) -Attribut und den Schlüsselwörtern [__hook](../../cpp/hook.md) und [__unhook](../../cpp/unhook.md) verwendet. Verwenden `event_source` Sie zum Erstellen von Ereignis Quellen. Verwenden **`__hook`** Sie in den Methoden eines Ereignis Empfängers, um Ereignis Empfänger Methoden ("Hook") den Ereignissen einer Ereignis Quelle zuzuordnen. Verwenden **`__unhook`** Sie, um Sie zu trennen.

*layout_dependent* wird nur für com-Ereignis Empfänger ( `type` = **com**) angegeben. Der Standardwert für *layout_dependent* ist **`false`** .

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|`coclass`Wenn *layout_dependent*=**`true`**|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Klassenattribute](class-attributes.md)
