---
title: unchecked_array_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 5344a108f32b694b9dafac78dbb8eb7064cdf4cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455006"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator-Klasse

Die `unchecked_array_iterator`-Klasse ermöglicht es Ihnen, ein Array oder einen Zeiger in einen deaktivierten Iterator zu umschließen. Verwenden Sie diese Klasse (mithilfe der [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)-Funktion) als Wrapper für unformatierte Zeiger oder Arrays als gezielte Methode zum Verwalten von Warnungen zu nicht aktivierten Zeigern, anstatt diese Warnungen allgemein zu deaktivieren. Verwenden Sie wenn möglich die aktivierte Version [checked_array_iterator](../standard-library/checked-array-iterator-class.md) dieser Klasse.

> [!NOTE]
> Bei dieser Klasse handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.

## <a name="syntax"></a>Syntax

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Hinweise

Diese Klasse wird im [stdext](../standard-library/stdext-namespace.md)-Namespace definiert.

Das ist die nicht aktivierte Version der [checked_array_iterator-Klasse](../standard-library/checked-array-iterator-class.md), die dieselben Überladungen und Member unterstützt. Weitere Informationen zur aktivierten Iteratorfunktion mit Codebeispielen finden Sie unter [Checked Iterators (Aktivierte Iteratoren)](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Anforderungen

**Header:** \<iterator>

**Namespace:** stdext

## <a name="see-also"></a>Siehe auch

[\<iterator>](../standard-library/iterator.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
