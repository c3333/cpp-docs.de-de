---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 3b52661097ca1feab4c8045be240e4138a0c0f21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190663"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Microsoft-spezifisch**

Verknüpft einen `_bstr_t`-Wrapper mit einem `BSTR`.

## <a name="syntax"></a>Syntax

```
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

Ein Beispiel für die Verwendung von **Attach**finden Sie unter [_bstr_t:: Assign](../cpp/bstr-t-assign.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_bstr_t-Klasse](../cpp/bstr-t-class.md)
