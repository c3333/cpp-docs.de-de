---
title: Relationale Funktionsvorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- relational function templates
ms.assetid: 57893a51-9adb-41fc-941d-2ca97687db2a
ms.openlocfilehash: db5091ca8fd29235ea1a0f70410a05ffcb9d7a65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188180"
---
# <a name="relational-function-templates"></a>Relationale Funktionsvorlagen

**Microsoft-spezifisch**

## <a name="syntax"></a>Syntax

```
template<typename _InterfaceType> bool operator==(
   int NULL,
   _com_ptr_t<_InterfaceType>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator==(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
template<typename _Interface> bool operator!=(
   int NULL,
   _com_ptr_t<_Interface>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator!=(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
template<typename _Interface> bool operator<(
   int NULL,
   _com_ptr_t<_Interface>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator<(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
template<typename _Interface> bool operator>(
   int NULL,
   _com_ptr_t<_Interface>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator>(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
template<typename _Interface> bool operator<=(
   int NULL,
   _com_ptr_t<_Interface>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator<=(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
template<typename _Interface> bool operator>=(
   int NULL,
   _com_ptr_t<_Interface>& p
);
template<typename _Interface,
   typename _InterfacePtr> bool operator>=(
   _Interface* i,
   _com_ptr_t<_InterfacePtr>& p
);
```

### <a name="parameters"></a>Parameter

*i*<br/>
Ein unformatierter Schnittstellenzeiger.

*p*<br/>
Ein intelligenter Zeiger.

## <a name="remarks"></a>Bemerkungen

Diese Funktionsvorlagen ermöglichen den Vergleich mit einem intelligenten Zeiger auf der rechten Seite des Vergleichsoperators. Dies sind keine Memberfunktionen von `_com_ptr_t`.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
