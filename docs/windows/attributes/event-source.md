---
title: event_source (C++ com-Attribut)
description: Erfahren Sie, wie Sie das com-Attribut Microsoft C++-Erweiterung verwenden `event_source` .
ms.date: 11/20/2020
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.openlocfilehash: 3cdfaaa86f8fc36bf0dc90d7961077546362a662
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483268"
---
# <a name="event_source-attribute"></a>`event_source`-Attribut

Erstellt eine Ereignisquelle.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="syntax"></a>Syntax

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parameter

*`type`*\
Eine Enumeration von einem der folgenden Werte:

- `native` für nicht verwalteten C/C++-Code (Standard für nicht verwaltete Klassen).

- `com` für COM-Code. Verwenden Sie, `coclass` Wenn *`type`* = `com` . Dieser Wert erfordert, dass Sie folgende Headerdateien einschließen:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`optimize`*\
Wenn der *Typ* auf fest `native` gelegt ist, können Sie angeben `optimize=size` , um anzugeben, dass für alle Ereignisse in einer Klasse 4 Bytes Speicher (minimal) vorhanden sind, oder `optimize=speed` (der Standardwert), um anzugeben, dass 4 * (# der Ereignisse) Speicher Bytes vorhanden sind.

*`decorate`*\
Wenn *type* der Typ `native` auf festgelegt ist, können Sie angeben `decorate=false` , um anzugeben, dass der erweiterte Name in der zusammengeführten *`.mrg`* Datei () nicht den einschließenden Klassennamen enthalten sollte. [`/Fx`](../../build/reference/fx-merge-injected-code.md) ermöglicht das Generieren von *`.mrg`* Dateien. `decorate=false`(die Standardeinstellung) führt zu voll qualifizierten Typnamen in der zusammengeführten Datei.

## <a name="remarks"></a>Bemerkungen

Das **`event_source`** C++-Attribut gibt an, dass die Klasse oder Struktur, auf die es angewendet wird, eine Ereignis Quelle sein wird.

**`event_source`** wird in Verbindung mit dem [`event_receiver`](event-receiver.md) -Attribut und dem- [`__event`](../../cpp/event.md) Schlüsselwort verwendet. Verwenden `event_receiver` Sie, um Ereignis Empfänger zu erstellen. Verwenden **`__event`** Sie für Methoden in der Ereignis Quelle, um diese Methoden als Ereignisse anzugeben.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="requirements"></a>Anforderungen

| Attribut Kontext | Wert |
|--|--|
| **Zielgruppe** | **`class`**, **`struct`** |
| **REPEATABLE** | Nein |
| **Erforderliche Attribute** | **`coclass`** Wenn `type`=`com` |
| **Ungültige Attribute** | Keine |

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[Compilerattribute](compiler-attributes.md)\
[`event_receiver`](event-receiver.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[Klassenattribute](class-attributes.md)
