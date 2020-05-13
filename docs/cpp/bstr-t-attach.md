---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749700"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Microsoft Specific**

Verknüpft einen `_bstr_t`-Wrapper mit einem `BSTR`.

## <a name="syntax"></a>Syntax

```cpp
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parameter

*s*<br/>
Eine `BSTR`-Variable, die `_bstr_t` zugeordnet oder zugewiesen werden soll.

## <a name="remarks"></a>Bemerkungen

Wenn `_bstr_t` zuvor an einen anderen `BSTR` angefügt war, bereinigt `_bstr_t` die `BSTR`-Ressource, wenn keine anderen `_bstr_t`-Variablen den `BSTR` verwenden.

## <a name="example"></a>Beispiel

Siehe [_bstr_t::Zuweisen](../cpp/bstr-t-assign.md) für ein Beispiel mit **Anfügen**.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
