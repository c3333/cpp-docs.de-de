---
title: ActivatableClass-Makros
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214270"
---
# <a name="activatableclass-macros"></a>ActivatableClass-Makros

Füllt einen internen Cache mit einer Factory auf, mit der eine Instanz der angegebenen Klasse erstellt werden kann.

## <a name="syntax"></a>Syntax

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der zu erstellenden Klasse.

*schen*<br/>
Factory, mit der eine Instanz der angegebenen Klasse erstellt wird.

*serverName*<br/>
Ein Name, der eine Teilmenge der Factorys im Modul angibt.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Makros nicht mit klassischem com, es sei denn, Sie verwenden die `#undef`-Direktive, um sicherzustellen, dass die `__WRL_WINRT_STRICT__` Makro Definition entfernt wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Module-Klasse](module-class.md)
