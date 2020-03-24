---
title: AsyncStatusInternal-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 0eadd1e3a287feecd36b00b231b42c31218352c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214148"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal-Enumeration

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Bemerkungen

Gibt eine Zuordnung zwischen internen Enumerationen für den Zustand von asynchronen Vorgängen und die `Windows::Foundation::AsyncStatus` Enumeration an.

## <a name="members"></a>Members

`_Created`<br/>
Entspricht `::Windows::Foundation::AsyncStatus::Created`.

`_Started`<br/>
Entspricht `::Windows::Foundation::AsyncStatus::Started`.

`_Completed`<br/>
Entspricht `::Windows::Foundation::AsyncStatus::Completed`.

`_Cancelled`<br/>
Entspricht `::Windows::Foundation::AsyncStatus::Cancelled`.

`_Error`<br/>
Entspricht `::Windows::Foundation::AsyncStatus::Error`.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
