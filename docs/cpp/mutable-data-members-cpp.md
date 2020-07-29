---
title: Änderbare Datenmember (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 9370952f503850fbc296c3df912d4a0fafe163f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227347"
---
# <a name="mutable-data-members-c"></a>Änderbare Datenmember (C++)

Dieses Schlüsselwort kann nur auf nicht statische und nicht konstante Datenmember einer Klasse angewendet werden. Wenn ein Datenmember deklariert wird **`mutable`** , ist es zulässig, diesem Datenmember aus einer Element Funktion einen Wert zuzuweisen **`const`** .

## <a name="syntax"></a>Syntax

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Bemerkungen

Der folgende Code wird z. b. ohne Fehler kompiliert, weil als `m_accessCount` deklariert wurde **`mutable`** und daher durch geändert werden kann, `GetFlag` Obwohl `GetFlag` eine Konstante Member-Funktion ist.

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
