---
title: Vi_progid (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: e7da3463b142fbca83387e52394ee33f42636124
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213787"
---
# <a name="vi_progid"></a>vi_progid

Gibt eine Versions unabhängige Form der ProgID an.

## <a name="syntax"></a>Syntax

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>Parameter

*name*<br/>
Die Versions unabhängige ProgID, die das-Objekt darstellt.

ProgIDs stellen eine lesbare Version des Klassen Bezeichners (CLSID) dar, mit der com-/ActiveX-Objekte identifiziert werden.

## <a name="remarks"></a>Bemerkungen

Mit dem **Vi_progid** C++-Attribut können Sie eine Versions unabhängige ProgID für ein COM-Objekt angeben. Eine ProgID hat das Format *Name1. name2. Version*. Eine Versions unabhängige ProgID hat keine *Version*. Es ist möglich, sowohl die `progid` -als auch die- **Vi_progid** Attribute für einen anzugeben `coclass` . Wenn Sie **Vi_progid**nicht angeben, ist die Versions unabhängige ProgID der Wert, der durch das [ProgID](progid.md) -Attribut angegeben wird.

**Vi_progid** impliziert das `coclass` -Attribut, d. h., wenn Sie **Vi_progid**angeben, ist dies dasselbe wie das Angeben der `coclass` Attribute und **Vi_progid** .

Das **Vi_progid** -Attribut bewirkt, dass eine Klasse automatisch unter dem angegebenen Namen registriert wird. In der generierten IDL-Datei wird der ProgID-Wert nicht angezeigt.

Wenn in ATL-Projekten auch das [Co-Klasse](coclass.md) -Attribut vorhanden ist, wird die angegebene ProgID von der `GetVersionIndependentProgID` Funktion verwendet (eingefügt durch das- `coclass` Attribut).

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Vi_progid**finden Sie im [Co-Klasse](coclass.md) -Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[ProgID-Schlüssel](/windows/win32/com/-progid--key)
