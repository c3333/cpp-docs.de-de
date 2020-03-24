---
title: local (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: d3710eee748a43a1daa5c07d8b3feb6beb8f64fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214746"
---
# <a name="local-c"></a>local (C++)

Wenn Sie im Schnittstellen Header verwendet wird, können Sie den Mittel l-Compiler als Header Generator verwenden. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.

## <a name="syntax"></a>Syntax

```cpp
[local]
```

## <a name="remarks"></a>Bemerkungen

Das **lokale** C++ Attribut verfügt über die gleiche Funktionalität wie das [lokale](/windows/win32/Midl/local) Attribut "Mittel l".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **local**finden Sie unter [Call_as](call-as.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Schnittstelle**, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`dispinterface`|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[call_as](call-as.md)
