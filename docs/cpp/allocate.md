---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0bf31423cd76c838cbeffa7458bbccb89592bf43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227620"
---
# <a name="allocate"></a>allocate

**Microsoft-spezifisch**

Der **`allocate`** deklarationsspezifizierer benennt ein Daten Segment, in dem das Datenelement zugeordnet wird.

## <a name="syntax"></a>Syntax

> **`__declspec(allocate("`***segname* **`))`** *Deklarator*

## <a name="remarks"></a>Bemerkungen

Der Name " *segname* " muss mit einem der folgenden Pragmas deklariert werden:

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [Sektions](../preprocessor/section.md)

## <a name="example"></a>Beispiel

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[`__declspec`](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
