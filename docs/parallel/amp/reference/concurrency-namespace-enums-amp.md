---
title: Concurrency-Namespace-Enumerationen (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855728"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency-Namespace-Enumerationen (AMP)

|||
|-|-|
|[access_type-Enumeration](#access_type)|[queuing_mode-Enumeration](#queuing_mode)|

## <a name="access_type"></a>access_type-Enumeration

Enumerationstyp wurde verwendet, um die verschiedenen Datenzugriffstypen anzugeben.

```cpp
enum access_type;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`access_type_auto`|Wählen Sie automatisch das beste `access_type`-Objekt für die Zugriffstaste aus.|
|`access_type_none`|Dediziert. Auf die Speicherbelegung kann nur auf der Zugriffstaste und nicht auf der CPU zugegriffen werden.|
|`access_type_read`|Freigegeben. Auf die Speicherbelegung kann auf der Zugriffstaste zugegriffen werden und sie ist auf der CPU lesbar.|
|`access_type_read_write`|Freigegeben. Auf die Speicherbelegung kann auf der Zugriffstaste zugegriffen werden und sie ist auf der CPU schreibbar.|
|`access_type_write`|Freigegeben. Auf die Speicherbelegung kann auf der Zugriffstaste zugegriffen werden und sie ist auf der CPU les- und schreibbar.|

## <a name="queuing_mode"></a>queuing_mode-Enumeration

Gibt die Modi für das Hinzufügen zur Warteschlange an, die auf dem Beschleuniger unterstützt werden.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`queuing_mode_immediate`|Ein queuingmodus, der angibt, dass alle Befehle, z. b. [Parallel_for_each Funktion (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each), an das entsprechende Zugriffstasten Gerät gesendet werden, sobald Sie zum Aufrufer zurückkehren.|
|`queuing_mode_automatic`|Ein queuingmodus, der angibt, dass Befehle in einer Befehls Warteschlange in die Warteschlange eingereiht werden, die dem [accelerator_view](accelerator-view-class.md) Objekt entspricht. Befehle werden an das Gerät gesendet, wenn [accelerator_view:: Flush](accelerator-view-class.md#flush) aufgerufen wird.|

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
