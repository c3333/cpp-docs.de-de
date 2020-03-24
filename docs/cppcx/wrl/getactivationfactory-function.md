---
title: GetActivationFactory-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: 430b4ed3f6a02fd3db2bcab05fbb7f21f5367b5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213979"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory-Funktion

Ruft eine aktivierungfactory für den Typ ab, der vom Vorlagen Parameter angegeben wird.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Vorlagen Parameter, der den Typ der Aktivierungs Factory angibt.

*activatableclassid*<br/>
Der Name der Klasse, die von der Aktivierungs Factory erzeugt werden kann.

*schen*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Verweis auf die aktivierungsfactory für Typ *T*.

## <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehler HRESULT, der angibt, warum dieser Vorgang fehlgeschlagen ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Windows:: Foundation

## <a name="see-also"></a>Weitere Informationen

[Windows::Foundation-Namespace](windows-foundation-namespace.md)
