---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 6d9429aa7c079f0f99a936019e5945092dc1f006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181524"
---
# <a name="allocate"></a>allocate

**Microsoft-spezifisch**

Der Bezeichner der Zuordnungs **Deklaration** benennt ein Daten Segment, in dem das Datenelement zugeordnet wird.

## <a name="syntax"></a>Syntax

```
   __declspec(allocate("segname")) declarator
```

## <a name="remarks"></a>Bemerkungen

Der Name " *segname* " muss mit einem der folgenden Pragmas deklariert werden:

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [section](../preprocessor/section.md)

## <a name="example"></a>Beispiel

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
