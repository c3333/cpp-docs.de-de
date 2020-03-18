---
title: '&lt;Ausführung&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 81e9aa63265c367412fda709aacd5ca3953e9fdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445031"
---
# <a name="ltexecutiongt"></a>&lt;Ausführung&gt;

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

|||
|-|-|
|[is_execution_policy-Struktur](is-execution-policy-struct.md)|Erkennt Ausführungsrichtlinien, um Funktions Signaturen von der ansonsten mehrdeutigen Überladungs Auflösungs Beteiligung auszuschließen.|
|[parallel_policy-Klasse](parallel-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen eindeutig zu machen und anzugeben, dass die Ausführung eines parallelen Algorithmus parallelisiert werden kann.|
|[parallel_unsequenced_policy-Klasse](parallel-unsequenced-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen eindeutig zu machen und anzugeben, dass die Ausführung eines parallelen Algorithmus parallelisiert und vektorisiert werden kann.|
|[sequenced_policy-Klasse](sequenced-policy-class.md)|Wird als eindeutiger Typ verwendet, um das überladen paralleler Algorithmen zu unterscheiden, und erfordert, dass die Ausführung eines parallelen Algorithmus möglicherweise nicht parallelisiert wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Ausführung >

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](cpp-standard-library-header-files.md)\
[Threadsicherheit in der C++-Standardbibliothek](thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](cpp-standard-library-reference.md)
