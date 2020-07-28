---
title: Threading (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: e08d25df07ad881c8843953d01d9074c815ddb85
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193067"
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

- `apartment`(Apartment Threading)

- `neutral`(.NET Framework Komponenten ohne Benutzeroberfläche)

- `single`(einfaches Threading)

- `free`(freies Threading)

- `both`(Apartment und freies Threading)

Der Standardwert ist `apartment`.

## <a name="remarks"></a>Hinweise

Das **Threading** C++-Attribut wird nicht in der generierten IDL-Datei angezeigt, wird jedoch in der Implementierung des COM-Objekts verwendet.

Wenn in ATL-Projekten auch das [Co-Klasse](coclass.md) -Attribut vorhanden ist, wird das von *Model* angegebene Threading Modell als Vorlagen Parameter an die [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) -Klasse übergeben, die durch das-Attribut eingefügt wird `coclass` .

Das **Threading** Attribut schützt auch den Zugriff auf eine [event_source](event-source.md).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Threading**finden Sie im [lizenzierten](licensed.md) Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Multithreading-Unterstützung für älteren Code (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutrale Apartments](/windows/win32/cossdk/neutral-apartments)
