---
title: AsWeak-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214174"
---
# <a name="asweak-function"></a>AsWeak-Funktion

Ruft einen schwachen Verweis zur angegebenen Instanz ab.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Zeiger auf den Typ des Parameters *p*.

*p*<br/>
Eine Instanz eines Typs.

*pweak*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Zeiger auf einen schwachen Verweis auf den Parameter " *p*".

## <a name="return-value"></a>Rückgabewert

S_OK, wenn dieser Vorgang erfolgreich ist. andernfalls ein Fehler HRESULT, der die Ursache des Fehlers angibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
