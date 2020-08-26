---
title: Export (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 4854789d9f977b3b747fd9b546cb92642942be88
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845275"
---
# <a name="export"></a>Export

Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.

## <a name="syntax"></a>Syntax

```cpp
[export]
```

## <a name="remarks"></a>Bemerkungen

Das **`[export]`** C++-Attribut bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird und in der Typbibliothek in einem Binär kompatiblen Format verfügbar ist, das Sie für die Verwendung in einer beliebigen Sprache verfügbar macht.

Das-Attribut kann nicht **`[export]`** auf eine Klasse angewendet werden, auch wenn die-Klasse nur öffentliche Member (die Entsprechung eines **`struct`** ) aufweist.

Wenn Sie ein unbenanntes **`enum`** oder exportieren **`struct`** , erhält es einen Namen, der mit **__unnamed**<em>x</em>beginnt, wobei *x* eine sequenzielle Zahl ist.

Die für den Export gültigen Typedefs sind Basis Typen, Strukturen, Unions, Enumerationstypen oder Typbezeichner.  Weitere Informationen finden Sie unter [`typedef`](/windows/win32/Midl/typedef) .

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das- **`[export]`** Attribut verwendet wird:

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`union`**, **`typedef`** , **`enum`** , **`struct`** oder **`interface`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
