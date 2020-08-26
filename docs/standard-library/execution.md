---
title: '&lt;Niederlage&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: f37458fdc0b58968e095a7c59de797eac295bde7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835935"
---
# <a name="ltexecutiongt"></a>&lt;Niederlage&gt;

Beschreibt die Ausführungsrichtlinien für parallele Algorithmen.

## <a name="syntax"></a>Syntax

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```

### <a name="classes-and-structs"></a>Klassen und Strukturen

|Name|Beschreibung|
|-|-|
|[is_execution_policy-Struktur](is-execution-policy-struct.md)|Erkennt Ausführungsrichtlinien, um Funktions Signaturen von der ansonsten mehrdeutigen Überladungs Auflösungs Beteiligung auszuschließen.|
|[parallel_policy-Klasse](parallel-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen eindeutig zu machen und anzugeben, dass die Ausführung eines parallelen Algorithmus parallelisiert werden kann.|
|[parallel_unsequenced_policy-Klasse](parallel-unsequenced-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen eindeutig zu machen und anzugeben, dass die Ausführung eines parallelen Algorithmus parallelisiert und vektorisiert werden kann.|
|[sequenced_policy-Klasse](sequenced-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen zu unterscheiden, und erfordert, dass die Ausführung eines parallelen Algorithmus möglicherweise nicht parallelisiert wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<execution>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](cpp-standard-library-reference.md)
