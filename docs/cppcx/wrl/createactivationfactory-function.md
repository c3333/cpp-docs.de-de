---
title: CreateActivationFactory-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ab03b15a968c6aba3fa6df8c975fb98e873f8e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214070"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory-Funktion

Erstellt eine Instanzen der angegebenen Klasse erstellende Factory, die durch die Windows-Runtime aktiviert werden kann.

## <a name="syntax"></a>Syntax

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Parameter

*flags*<br/>
Eine Kombination aus einem oder mehreren [runtimeclasstype](runtimeclasstype-enumeration.md) -Enumerationswerten.

*entry*<br/>
Zeiger auf eine " [kreatormap](creatormap-structure.md) ", die Initialisierungs-und Registrierungsinformationen über den Parameter " *riid*" enthält.

*riid*<br/>
Verweis auf eine Schnittstellen-ID.

*ppfactory*<br/>
Wenn dieser Vorgang erfolgreich abgeschlossen wurde, ein Zeiger auf eine aktivierungfactory.

## <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="remarks"></a>Bemerkungen

Ein Assert-Fehler wird ausgegeben, wenn die Vorlagen *parameterfactory* nicht von der Schnittstelle `IActivationFactory`abgeleitet ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Wrappers::Details-Namespace](microsoft-wrl-wrappers-details-namespace.md)
