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
ms.openlocfilehash: a79cb91a6b0e6ca633540fd37f7a0e1ece53b712
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845783"
---
# <a name="steady_clock-struct"></a>steady_clock-Struktur

Stellt eine *high_resolution* Uhr dar.

## <a name="syntax"></a>Syntax

```cpp
class high_resolution_clock
```

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|----------|-----------------|
|`duration`|Ein Synonym für `nanoseconds` , das in definiert ist \<chrono> .|
|`period`|Ein Synonym für `nano` , das in definiert ist \<ratio> .|
|`rep`|Ein Synonym für **`long long`** , der Typ, der zum Darstellen der Anzahl von Takt Ticks in der enthaltenen Instanziierung von verwendet wird `duration` .|
|`time_point`|Ein Synonym für `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|`now`|Gibt die aktuelle Uhrzeit als- `time_point` Wert zurück.|

## <a name="constants"></a>Konstanten

|Name|Beschreibung|
|----------|-----------------|
|`is_steady`|Enthält **`true`** . Eine `high_resolution_clock` ist *gleichmäßig*.|
