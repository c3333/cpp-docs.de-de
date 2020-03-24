---
title: Threading (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: b249eaf61266ed9964e44f6f0ad1c2f12a1b1067
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214499"
---
# <a name="threading-c"></a>threading (C++)

Gibt das Threading Modell für ein COM-Objekt an.

## <a name="syntax"></a>Syntax

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parameter

*model*<br/>
Optionale Eines der folgenden Threading Modelle:

- `apartment` (Apartment Threading)

- `neutral` (.NET Framework Komponenten ohne Benutzeroberfläche)

- `single` (einfaches Threading)

- `free` (freies Threading)

- `both` (Apartment und freies Threading)

Standardwert: `apartment`.

## <a name="remarks"></a>Bemerkungen

Das **Threading** C++ Attribut wird nicht in der generierten IDL-Datei angezeigt, wird jedoch in der Implementierung des COM-Objekts verwendet.

Wenn in ATL-Projekten auch das [Co-Klasse](coclass.md) -Attribut vorhanden ist, wird das von *Model* angegebene Threading Modell als Vorlagen Parameter an die [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) -Klasse übergeben, die durch das `coclass`-Attribut eingefügt wird.

Das **Threading** Attribut schützt auch den Zugriff auf eine [event_source](event-source.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Threading**finden Sie im [lizenzierten](licensed.md) Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Multithreadingunterstützung für älteren Code (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutrale Apartments](/windows/win32/cossdk/neutral-apartments)
