---
title: Concurrency-Namespace-Enumerationen (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376317"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency-Namespace-Enumerationen (AMP)

|||
|-|-|
|[access_type-Enumeration](#access_type)|[queuing_mode-Enumeration](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type-Enumeration

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

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode-Enumeration

Gibt die Modi für das Hinzufügen zur Warteschlange an, die auf dem Beschleuniger unterstützt werden.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`queuing_mode_immediate`|Ein Warteschlangenmodus, der angibt, dass alle Befehle, z. B. [parallel_for_each Function (C++ AMP),](concurrency-namespace-functions-amp.md#parallel_for_each)an das entsprechende Beschleunigergerät gesendet werden, sobald sie an den Aufrufer zurückkehren.|
|`queuing_mode_automatic`|Ein Warteschlangenmodus, der angibt, dass Befehle in einer Befehlswarteschlange in die Warteschlange eingereiht werden, die dem [accelerator_view-Objekts](accelerator-view-class.md) entspricht. Befehle werden an das Gerät gesendet, wenn [accelerator_view::flush](accelerator-view-class.md#flush) aufgerufen wird.|

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
