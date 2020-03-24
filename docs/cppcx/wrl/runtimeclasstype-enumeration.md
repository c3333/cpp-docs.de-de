---
title: RuntimeClassType-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213576"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType-Enumeration

Gibt den Typ der unterstützten [runtimeclass](runtimeclass-class.md) -Instanz an.

## <a name="syntax"></a>Syntax

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Members

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ClassicCom`|Eine klassische com-Lauf Zeit Klasse.|
|`Delegate`|Entspricht `ClassicCom`.|
|`InhibitFtmBase`|Deaktiviert die `FtmBase` Unterstützung, während `__WRL_CONFIGURATION_LEGACY__` nicht definiert ist.|
|`InhibitWeakReference`|Deaktiviert die Unterstützung für schwache Verweise.|
|`WinRt`|Eine Windows-Runtime-Klasse.|
|`WinRtClassicComMix`|Die Kombination aus `WinRt` und `ClassicCom`.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
