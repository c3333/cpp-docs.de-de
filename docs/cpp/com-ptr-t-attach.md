---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180497"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft-spezifisch**

Kapselt einen unformatierten Schnittstellenzeiger vom Typ dieses intelligenten Zeigers.

## <a name="syntax"></a>Syntax

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parameter

*pinterface*<br/>
Ein unformatierter Schnittstellenzeiger.

*abadressf*<br/>
Wenn der Wert true ist, wird `AddRef` aufgerufen. Wenn der Wert false ist, übernimmt das `_com_ptr_t` Objekt den Besitz des unformatierten Schnittstellen Zeigers, ohne `AddRef`zu aufrufen.

## <a name="remarks"></a>Bemerkungen

- **Attach (**  *pinterface*  **)** -`AddRef` wird nicht aufgerufen. Der Besitz der Schnittstelle wird an dieses `_com_ptr_t`-Objekt übergeben. `Release` wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern.

- **Attach (**  *pinterface* **,**  *f*  **)** Wenn *fadressf* true ist, wird `AddRef` aufgerufen, um den Verweis Zähler für den gekapselten Schnittstellen Zeiger zu erhöhen. Wenn *fadressf* false ist, übernimmt dieses `_com_ptr_t` Objekt den Besitz des unformatierten Schnittstellen Zeigers, ohne dass `AddRef`aufgerufen wird. `Release` wird aufgerufen, um den Verweis Zähler für den zuvor gekapselten Zeiger zu verringern.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
