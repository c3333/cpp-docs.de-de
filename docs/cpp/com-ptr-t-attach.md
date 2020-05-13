---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745069"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft Specific**

Kapselt einen unformatierten Schnittstellenzeiger vom Typ dieses intelligenten Zeigers.

## <a name="syntax"></a>Syntax

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parameter

*pInterface*<br/>
Ein unformatierter Schnittstellenzeiger.

*fAddRef*<br/>
Wenn es TRUE `AddRef` ist, dann wird aufgerufen. Wenn es FALSE `_com_ptr_t` ist, übernimmt das Objekt den `AddRef`Besitz des unformatierten Schnittstellenzeigers, ohne aufzurufen.

## <a name="remarks"></a>Bemerkungen

- **Attach(**  *pInterface*  **)** `AddRef` wird nicht aufgerufen. Der Besitz der Schnittstelle wird an dieses `_com_ptr_t`-Objekt übergeben. `Release`wird aufgerufen, um die Referenzanzahl für den zuvor gekapselten Zeiger zu dekrementotern.

- **Attach(**  *pInterface* **,**  *fAddRef*  **)** Wenn *fAddRef* TRUE `AddRef` ist, wird aufgerufen, um die Referenzanzahl für den gekapselten Schnittstellenzeiger zu erhöhen. Wenn *fAddRef* FALSE `_com_ptr_t` ist, übernimmt dieses Objekt den `AddRef`Besitz des unformatierten Schnittstellenzeigers, ohne aufzurufen. `Release`wird aufgerufen, um die Referenzanzahl für den zuvor gekapselten Zeiger zu dekrementotern.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
