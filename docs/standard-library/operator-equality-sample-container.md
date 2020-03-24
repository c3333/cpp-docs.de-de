---
title: operator== (&lt;Sample Container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 08adfcc770551d3050daa46c870b950e468c95b3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150641"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;Sample Container&gt;)

> [!NOTE]
> Dieses Thema ist in der Microsoft C++ -Dokumentation als nicht funktionales Beispiel für Container, die C++ in der Standard Bibliothek verwendet werden. Weitere Informationen finden Sie unter [C++ Standard Library Containers (C++-Standardbibliothekcontainer)](../standard-library/stl-containers.md).

Über lädt `operator==`, um zwei Objekte des Klassen Vorlagen [Containers](../standard-library/sample-container-class.md)zu vergleichen.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Rückgabewert

Gibt `left.`[Größe](../standard-library/container-class-size.md) zurück, `== right.size && equal(left.``, left.`[Ende](../standard-library/container-class-end.md)`, right.begin)`[beginnen](../standard-library/container-class-begin.md) .

## <a name="see-also"></a>Weitere Informationen

[\<sample container>](../standard-library/sample-container.md)
