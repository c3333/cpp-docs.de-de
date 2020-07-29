---
title: ProgID (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 3092111236afe1e1360a2814c3091ab0de4ff6ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213852"
---
# <a name="progid"></a>progid

Gibt die ProgID für ein COM-Objekt an.

## <a name="syntax"></a>Syntax

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parameter

*name*<br/>
Die ProgID, die das-Objekt darstellt.

ProgIDs stellen eine lesbare Version des Klassen Bezeichners (CLSID) dar, mit der com-/ActiveX-Objekte identifiziert werden.

## <a name="remarks"></a>Bemerkungen

`progid`Mit dem C++-Attribut können Sie die ProgID für ein COM-Objekt angeben. Eine ProgID hat das Format *Name1. name2. Version*. Wenn Sie keine *Version* für eine ProgID angeben, ist die Standardversion 1. Wenn Sie *Name1. name2*nicht angeben, lautet der Standardname *ClassName. ClassName*. Wenn Sie nicht angeben `progid` und angeben `vi_progid` , werden *Name1. name2* von `vi_progid` und die (nächste sequenzielle Nummer)-Version angehängt.

Wenn von einem Attribut Block `progid` nicht auch verwendet `uuid` wird, prüft der Compiler die Registrierung, um festzustellen, ob eine `uuid` für den angegebenen vorhanden ist `progid` . Wenn `progid` nicht angegeben ist, wird die Version (und der Co-Klassenname beim Erstellen einer Co-Klasse) verwendet, um ein zu generieren `progid` .

`progid`impliziert das `coclass` -Attribut, d. h., wenn Sie angeben `progid` , entspricht es dem Angeben der `coclass` `progid` Attribute und.

Das- `progid` Attribut bewirkt, dass eine Klasse automatisch unter dem angegebenen Namen registriert wird. In der generierten IDL-Datei wird der Wert nicht angezeigt `progid` .

Wenn dieses Attribut in einem Projekt verwendet wird, das ATL verwendet, ändert sich das Verhalten des Attributs. Zusätzlich zum obigen Verhalten werden die mit diesem Attribut angegebenen Informationen in der Funktion verwendet, die `GetProgID` durch das Attribut eingefügt wird `coclass` . Weitere Informationen finden Sie unter dem [Co-Klasse](coclass.md) -Attribut.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie im Beispiel für die [Co-Klasse](coclass.md) `progid` .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|`class`, `struct`|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID-Schlüssel](/windows/win32/com/-progid--key)
