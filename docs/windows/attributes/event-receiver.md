---
title: event_receiver (C++ com-Attribut)
description: Erfahren Sie, wie Sie das com-Attribut Microsoft C++-Erweiterung verwenden `event_receiver` .
ms.date: 11/20/2020
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
ms.openlocfilehash: 8ed6ef6113d72a9565b275dff4e035dc56f11e82
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483281"
---
# <a name="event_receiver-attribute"></a>`event_receiver`-Attribut

Erstellt einen Ereignisempfänger (Senke).

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="syntax"></a>Syntax

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parameter

*`type`*\
Eine Enumeration von einem der folgenden Werte:

- `native` für nicht verwalteten C/C++-Code (Standardeinstellung für Native Klassen).

- `com` für COM-Code. Dieser Wert erfordert, dass Sie diese Header Dateien einschließen:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`layout_dependent`*\
Geben Sie nur an, *`layout_dependent`* Wenn `type` = **com**. *`layout_dependent`* ist ein boolescher Wert:

- **`true`** bedeutet, dass die Signatur der Delegaten im Ereignis Empfänger genau mit den Zeichen übereinstimmen muss, mit denen Sie in der Ereignis Quelle verknüpft sind. Die Namen des ereignishandlerhandlers müssen mit den in der relevanten Ereignis Quellen Schnittstelle angegebenen Namen identisch sein. Verwenden Sie, `coclass` Wenn *`layout_dependent`* ist **`true`** . Es ist etwas effizienter, das anzugeben **`true`** .

- **`false`** (Standard) bedeutet, dass die Aufruf Konvention und die Speicher Klasse ( `virtual` , `static` und andere) nicht mit der Ereignismethode und den Handlern übereinstimmen müssen. Die Handlernamen müssen auch nicht mit den Methodennamen der Ereignis Quell Schnittstelle identisch sein.

## <a name="remarks"></a>Bemerkungen

Das **`event_receiver`** C++-Attribut gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, ein Ereignis Empfänger ist, wobei das Microsoft C++ Unified Event-Modell verwendet wird.

**`event_receiver`** wird mit dem [`event_source`](event-source.md) -Attribut und den [`__hook`](../../cpp/hook.md) [`__unhook`](../../cpp/unhook.md) Schlüsselwörtern und verwendet. Verwenden `event_source` Sie zum Erstellen von Ereignis Quellen. Verwenden **`__hook`** Sie in den Methoden eines Ereignis Empfängers, um Ereignis Empfänger Methoden ("Hook") den Ereignissen einer Ereignis Quelle zuzuordnen. Verwenden **`__unhook`** Sie, um die Zuordnung aufzuheben.

*`layout_dependent`* wird nur für com-Ereignis Empfänger ( `type` = **`com`** ) angegeben. Der Standardwert für *`layout_dependent`* ist **`false`** .

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Anforderungen

| Attribut Kontext | Wert |
|--|--|
| **Zielgruppe** | **`class`**, **`struct`** |
| **REPEATABLE** | Nein |
| **Erforderliche Attribute** | `coclass` Wenn *`layout_dependent`*=**`true`** |
| **Ungültige Attribute** | Keine |

Weitere Informationen finden Sie unter [Attribut Kontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[Compilerattribute](compiler-attributes.md)\
[`event_source`](event-source.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[Klassenattribute](class-attributes.md)
