---
title: numeric (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 1939a6dd9b6d8186eb278623f3b0a5a3d851f4d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208480"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)

Definiert Container Vorlagen Funktionen, die für die numerische Verarbeitung bereitgestellte Algorithmen ausführen.

## <a name="syntax"></a>Syntax

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/numeric >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Berechnet die Summe aller Elemente in einem angegebenen Bereich, einschließlich einigen Anfangswerten, indem aufeinander folgende Teilsummen berechnet werden, oder berechnet das Ergebnis der aufeinander folgenden Teilergebnisse, die auf ähnliche Weise mithilfe eines angegebenen binären Vorgangs (außer Summe) abgerufen werden.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Berechnet die aufeinander folgenden Unterschiede zwischen einem Element und seinem Vorgänger in einem Eingabebereich und gibt die Ergebnisse in einem Zielbereich aus oder berechnet das Ergebnis einer allgemeinen Prozedur, in der der Vorgang zum Feststellen von Unterschieden durch einen anderen angegebenen binären Vorgang ersetzt wird.|
|[inner_product (STL/CLR)](#inner_product)|Berechnet die Summe des elementweisen Produkts von zwei Bereichen und fügt sie einem angegebenen Anfangswert hinzu oder berechnet das Ergebnis einer allgemeinen Prozedur, in der die Summen- und Produktvorgänge durch andere angegebene binäre Vorgänge ersetzt werden.|
|[partial_sum (STL/CLR)](#partial_sum)|Berechnet eine Reihe von Summen in einem Eingabebereich vom ersten Element bis zum `i`th-Element und speichert das Ergebnis jeder solchen Summe in `i`th-Element eines Zielbereichs oder berechnet das Ergebnis einer allgemeinen Prozedur, bei der der Sum-Vorgang durch einen anderen angegebenen binären Vorgang ersetzt wird.|

## <a name="members"></a>Members

## <a name="accumulate-stlclr"></a><a name="accumulate"></a>kumulieren (STL/CLR)

Berechnet die Summe aller Elemente in einem angegebenen Bereich, einschließlich einigen Anfangswerten, indem aufeinander folgende Teilsummen berechnet werden, oder berechnet das Ergebnis der aufeinander folgenden Teilergebnisse, die auf ähnliche Weise mithilfe eines angegebenen binären Vorgangs (außer Summe) abgerufen werden.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die numerische C++ Funktion der Standard Bibliothek `accumulate`. Weitere Informationen finden Sie unter [kumulieren](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference-stlclr"></a><a name="adjacent_difference"></a>adjacent_difference (STL/CLR)

Berechnet die aufeinander folgenden Unterschiede zwischen einem Element und seinem Vorgänger in einem Eingabebereich und gibt die Ergebnisse in einem Zielbereich aus oder berechnet das Ergebnis einer allgemeinen Prozedur, in der der Vorgang zum Feststellen von Unterschieden durch einen anderen angegebenen binären Vorgang ersetzt wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die numerische C++ Funktion der Standard Bibliothek `adjacent_difference`. Weitere Informationen finden Sie unter [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product-stlclr"></a><a name="inner_product"></a>inner_product (STL/CLR)

Berechnet die Summe des elementweisen Produkts von zwei Bereichen und fügt sie einem angegebenen Anfangswert hinzu oder berechnet das Ergebnis einer allgemeinen Prozedur, in der die Summen- und Produktvorgänge durch andere angegebene binäre Vorgänge ersetzt werden.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die numerische C++ Funktion der Standard Bibliothek `inner_product`. Weitere Informationen finden Sie unter [Inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum-stlclr"></a><a name="partial_sum"></a>Partial_sum (STL/CLR)

Berechnet eine Reihe von Summen in einem Eingabebereich vom ersten Element bis zum `i`th-Element und speichert das Ergebnis jeder solchen Summe in `i`th-Element eines Zielbereichs oder berechnet das Ergebnis einer allgemeinen Prozedur, bei der der Sum-Vorgang durch einen anderen angegebenen binären Vorgang ersetzt wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die numerische C++ Funktion der Standard Bibliothek `partial_sum`. Weitere Informationen finden Sie unter [partial_sum](../standard-library/numeric-functions.md#partial_sum).
