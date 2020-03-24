---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170591"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Microsoft-spezifisch**

Ruft die **releasemember** -Funktion von `IUnknown` für den gekapselten Schnittstellen Zeiger auf.

## <a name="syntax"></a>Syntax

```
void Release( );
```

## <a name="remarks"></a>Bemerkungen

Ruft `IUnknown::Release` für den gekapselten Schnittstellen Zeiger auf und gibt einen `E_POINTER` Fehler aus, wenn dieser Schnittstellen Zeiger NULL ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_ptr_t-Klasse](../cpp/com-ptr-t-class.md)
