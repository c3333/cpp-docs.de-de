---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: cb5950e311711dd489b3cab223714b1840773f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220586"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft-spezifisch**

Kapselt einen unformatierten Schnittstellenzeiger vom Typ dieses intelligenten Zeigers.

## <a name="syntax"></a>Syntax

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parameter

*pinterface*<br/>
Ein unformatierter Schnittstellenzeiger.

*abadressf*<br/>
Wenn dies der Fall ist **`true`** , `AddRef` wird aufgerufen. Wenn dies der Fall ist **`false`** , übernimmt das Objekt den Besitz des unformatierten `_com_ptr_t` Schnittstellen Zeigers, ohne zu aufrufen `AddRef` .

## <a name="remarks"></a>Bemerkungen

- **Anfügen (**  *pinterface*  **)** `AddRef` wird nicht aufgerufen. Der Besitz der Schnittstelle wird an dieses `_com_ptr_t`-Objekt übergeben. `Release`wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern.

- **Attach (**  *pinterface* **,**  *f*  **)** Wenn *fadressf* **`true`** den Wert hat, `AddRef` wird aufgerufen, um den Verweis Zähler für den gekapselten Schnittstellen Zeiger zu erhöhen. Wenn *fadressf* ist **`false`** , `_com_ptr_t` übernimmt dieses Objekt den Besitz des unformatierten Schnittstellen Zeigers, ohne dass aufgerufen wird `AddRef` . `Release`wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
