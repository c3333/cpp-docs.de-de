---
title: IID_PPV_ARGS_Helper-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 68dbd0b5b2e9d4fc04821a7e7e0193840b55e312
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077129"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper-Funktion

Überprüft, ob der Typ des angegebenen Arguments von der `IUnknown`-Schnittstelle abgeleitet ist.

> [!IMPORTANT]
> Diese Vorlagen Spezialisierung unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen. Verwenden Sie stattdessen [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Arguments *PP*.

*Trupp*<br/>
Ein doppelt indirekter Zeiger.

## <a name="return-value"></a>Rückgabewert

Argument- *PP* -Umwandlung in einen Zeiger auf einen Zeiger auf " **void**".

## <a name="remarks"></a>Bemerkungen

Ein Kompilierzeitfehler wird generiert, wenn der Vorlagen Parameter *T* nicht von `IUnknown`abgeleitet ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h
