---
title: ActivationFactoryCallback-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214213"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback-Funktion

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parameter

*activationId*<br/>
Handle für eine Zeichenfolge, die einen Lauf Zeit Klassennamen angibt.

*ppfactory*<br/>
Wenn dieser Vorgang abgeschlossen ist, eine aktivierungfactory, die dem Parameter *ActivationID*entspricht.

## <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt. Wahrscheinliche Fehler-HRESULTs sind CLASS_E_CLASSNOTAVAILABLE und E_INVALIDARG.

## <a name="remarks"></a>Bemerkungen

Ruft die aktivierungsfactory für die angegebene Aktivierungs-ID ab.

Der Windows-Runtime ruft diese Rückruffunktion auf, um ein Objekt anzufordern, das durch den Namen der Lauf Zeit Klasse angegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
