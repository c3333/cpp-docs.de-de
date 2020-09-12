---
title: high_resolution_clock Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341cae04742d72fdcc7483e74977bf413854df82
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039650"
---
# <a name="high_resolution_clock-struct"></a>high_resolution_clock-Struktur

Stellt eine *high_resolution* Uhr dar.

## <a name="syntax"></a>Syntax

```cpp
class high_resolution_clock
```

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`duration`|Ein Synonym für `nanoseconds` , das in definiert ist \<chrono> .|
|`period`|Ein Synonym für `nano` , das in definiert ist \<ratio> .|
|`rep`|Ein Synonym für **`long long`** , der Typ, der zum Darstellen der Anzahl von Takt Ticks in der enthaltenen Instanziierung von verwendet wird `duration` .|
|`time_point`|Ein Synonym für `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|-|-|
|`now`|Gibt die aktuelle Uhrzeit als- `time_point` Wert zurück.|

## <a name="constants"></a>Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|`is_steady`|Enthält **`true`** . Eine `high_resolution_clock` ist *gleichmäßig*.|
