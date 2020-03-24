---
title: Includelib (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 4022a3f1f2d4ccaabe65c24065be8e1c846d604d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214843"
---
# <a name="includelib-c"></a>includelib (C++)

Bewirkt, dass eine IDL-oder h-Datei in der generierten IDL-Datei enthalten ist.

## <a name="syntax"></a>Syntax

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parameter

*Name. idl*<br/>
Der Name der IDL-Datei, die als Teil der generierten IDL-Datei enthalten sein soll.

## <a name="remarks"></a>Bemerkungen

Das **Includelib** C++ -Attribut bewirkt, dass eine IDL-oder h-Datei in der generierten IDL-Datei nach der `importlib`-Anweisung eingeschlossen wird.

## <a name="example"></a>Beispiel

Der folgende Code wird in einer CPP-Datei angezeigt:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Überall|
|**Wiederholbar**|Ja|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)
