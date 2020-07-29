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
ms.openlocfilehash: 850d5e3a5434aa44e23a7f74aeb9c306ab6c0a8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203207"
---
# <a name="steady_clock-struct"></a>steady_clock-Struktur

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

|||
|-|-|
|`now`|Gibt die aktuelle Uhrzeit als- `time_point` Wert zurück.|

## <a name="constants"></a>Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|`is_steady`|Enthält **`true`** . Eine `high_resolution_clock` ist *gleichmäßig*.|
