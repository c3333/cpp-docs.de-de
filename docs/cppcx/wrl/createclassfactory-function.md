---
title: CreateClassFactory-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214057"
---
# <a name="createclassfactory-function"></a>CreateClassFactory-Funktion

Erstellt eine Factory, die Instanzen der angegebenen Klasse erstellt.

## <a name="syntax"></a>Syntax

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>Parameter

*flags*<br/>
Eine Kombination aus einem oder mehreren [runtimeclasstype](runtimeclasstype-enumeration.md) -Enumerationswerten.

*entry*<br/>
Zeiger auf eine " [kreatormap](creatormap-structure.md) ", die Initialisierungs-und Registrierungsinformationen über den Parameter " *riid*" enthält.

*riid*<br/>
Verweis auf eine Schnittstellen-ID.

*ppfactory*<br/>
Wenn dieser Vorgang erfolgreich abgeschlossen wurde, ein Zeiger auf eine Klassenfactory.

## <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="remarks"></a>Bemerkungen

Ein Assert-Fehler wird ausgegeben, wenn die Vorlagen *parameterfactory* nicht von der Schnittstelle `IClassFactory`abgeleitet ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Wrappers::Details-Namespace](microsoft-wrl-wrappers-details-namespace.md)
