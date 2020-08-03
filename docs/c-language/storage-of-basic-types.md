---
title: Speicherung von einfachen Typen
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: 973866a912b694510d587df765ac8dd54176638e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211670"
---
# <a name="storage-of-basic-types"></a>Speicherung von einfachen Typen

In der folgenden Tabelle wird der Speicher zusammengefasst, welcher jedem Basistyp zugeordnet ist.

## <a name="sizes-of-fundamental-types"></a>Größen von grundlegenden Typen

|Typ|Speicher|
|----------|-------------|
|**`char`** , **`unsigned char`** , **`signed char`**|1 Byte|
|**`short`** , **`unsigned short`**|2 Bytes|
|**`int`** , **`unsigned int`**|4 Bytes|
|**`long`** , **`unsigned long`**|4 Bytes|
|**`long long`** , **`unsigned long long`**|8 Bytes|
|**`float`**|4 Bytes|
|**`double`**|8 Bytes|
|**`long double`**|8 Bytes|

Die C-Datentypen fallen in allgemeine Kategorien. Zu den *integralen Typen* gehören **`int`** , **`char`** , **`short`** , **`long`** und **`long long`** . Diese Typen können mit **`signed`** oder **`unsigned`** qualifiziert werden, und **`unsigned`** alleine kann als Kurzform für **`unsigned int`** verwendet werden. Enumerationstypen ( **`enum`** ) werden für die meisten Zwecke ebenfalls als integrale Typen behandelt. Zu den *Gleitkommatypen* gehören **`float`** , **`double`** und **`long double`** . Die *arithmetischen Typen* umfassen alle Gleitkomma- und Ganzzahltypen.

## <a name="see-also"></a>Siehe auch

[Deklarationen und Typen](../c-language/declarations-and-types.md)
