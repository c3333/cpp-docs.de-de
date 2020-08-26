---
title: include (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 6b75df74ee69ee4f89eb7bf18fb6bcd77d8a6284
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842194"
---
# <a name="include-c"></a>include (C++)

Gibt eine oder mehrere Header Dateien an, die in die generierte IDL-Datei eingeschlossen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parameter

*header_file*<br/>
Der Name einer Datei, die in die generierte IDL-Datei eingefügt werden soll.

## <a name="remarks"></a>Bemerkungen

Das **include** C++-Attribut bewirkt `#include` , dass eine-Anweisung unter der- `import "docobj.idl"` Anweisung in der generierten IDL-Datei platziert wird.

Das **include** C++-Attribut verfügt über die gleiche Funktionalität wie das [include](/windows/win32/Midl/include) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

Der folgende Code zeigt ein Beispiel für die Verwendung von **include**. In diesem Beispiel enthält die Datei include. h nur eine- `#include` Anweisung.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[Includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
