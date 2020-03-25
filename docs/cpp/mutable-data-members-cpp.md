---
title: Änderbare Datenmember (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179340"
---
# <a name="mutable-data-members-c"></a>Änderbare Datenmember (C++)

Dieses Schlüsselwort kann nur auf nicht statische und nicht konstante Datenmember einer Klasse angewendet werden. Wenn ein Datenmember als **änderbar**deklariert ist, ist es zulässig, diesem Datenmember aus einer **Konstanten** Element Funktion einen Wert zuzuweisen.

## <a name="syntax"></a>Syntax

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Bemerkungen

Der folgende Code wird z. b. ohne Fehler kompiliert, weil `m_accessCount` als **änderbar**deklariert wurde und daher durch `GetFlag` geändert werden kann, auch wenn `GetFlag` eine Konstante Element Funktion ist.

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

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)
