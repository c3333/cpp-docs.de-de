---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: 3477f77b811d8bec09b63664a05a4e251214aefa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213124"
---
# <a name="virtual-c"></a>virtual (C++)

Das **`virtual`** Schlüsselwort deklariert eine virtuelle Funktion oder eine virtuelle Basisklasse.

## <a name="syntax"></a>Syntax

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parameter

*typspezifierer*<br/>
Gibt den Rückgabetyp der virtuellen Memberfunktion an.

*Member-Function-declarator*<br/>
Deklariert eine Memberfunktion.

*Zugriffsspezifizierer*<br/>
Definiert die Zugriffsebene für die Basisklasse, **`public`** **`protected`** oder **`private`** . Kann vor oder nach dem- **`virtual`** Schlüsselwort angezeigt werden.

*Basisklassen Name*<br/>
Identifiziert einen zuvor deklarierten Klassentyp.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [virtuelle Funktionen](../cpp/virtual-functions.md) .

Siehe auch die folgenden Schlüsselwörter: [Class](../cpp/class-cpp.md), [private](../cpp/private-cpp.md), [Public](../cpp/public-cpp.md)und [Protected](../cpp/protected-cpp.md).

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)
