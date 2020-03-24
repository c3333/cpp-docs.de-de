---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 26dda2dff83ff0adbb7ef05c5e75f64b44138bd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170670"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft-spezifisch**

Ruft die **QueryInterface** -Member-Funktion von `IUnknown` für den gekapselten Schnittstellen Zeiger auf.

## <a name="syntax"></a>Syntax

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Parameter

*IID*<br/>
`IID` eines Schnittstellen Zeigers.

*p*<br/>
Nicht formatierter Schnittstellenzeiger.

## <a name="remarks"></a>Bemerkungen

Ruft `IUnknown::QueryInterface` für den gekapselten Schnittstellen Zeiger mit dem angegebenen `IID` auf und gibt den resultierenden rohschnittstellen Zeiger in *p*zurück. Diese Routine gibt das HRESULT zurück, um einen Erfolg oder Fehler anzugeben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
