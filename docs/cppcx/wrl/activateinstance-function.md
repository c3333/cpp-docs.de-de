---
title: ActivateInstance-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214226"
---
# <a name="activateinstance-function"></a>ActivateInstance-Funktion

Registriert eine Instanz eines angegebenen Typs, die in einer angegebenen Klassen-ID definiert ist, und ruft Sie ab.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ, der aktiviert werden soll.

*activatableclassid*<br/>
Der Name der Klassen-ID, die den Parameter *T*definiert.

*Instanz*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Verweis auf eine Instanz von *T*.

## <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehler HRESULT, der die Ursache des Fehlers angibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Windows:: Foundation

## <a name="see-also"></a>Weitere Informationen

[Windows::Foundation-Namespace](windows-foundation-namespace.md)
