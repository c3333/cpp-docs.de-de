---
title: Memberzugriff
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179418"
---
# <a name="member-access"></a>Memberzugriff

Der Zugriff auf Klassenmember kann gesteuert werden, indem der Member Access Operator ( **->** ) überladen wird. Dieser Operator wird bei dieser Verwendung als unärer Operator betrachtet, und die überladene Operatorfunktion muss eine Klassenmemberfunktion sein. Daher ist die Deklaration für eine solche Funktion:

## <a name="syntax"></a>Syntax

```
class-type *operator->()
```

## <a name="remarks"></a>Hinweise

Where *Class-Type* ist der Name der Klasse, zu der dieser Operator gehört. Die Operatorfunktion für den Memberzugriff muss eine nicht statische Memberfunktion sein.

Dieser Operator wird (oft in Verbindung mit dem Zeiger-Dereferenzierungsoperator) verwendet, um "intelligente Zeiger" zu implementieren, die vor einer Dereferenzierung oder Zählung validiert werden.

Das Sprachelement **.** der Member Access-Operator kann nicht überladen werden.

## <a name="see-also"></a>Siehe auch

[Operatorüberladung](../cpp/operator-overloading.md)
