---
title: include (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 39f991bb036dce1c50a9d2ee800d3fec65af7c55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166782"
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

Das **include** C++ -Attribut bewirkt, dass eine `#include` Anweisung unterhalb der `import "docobj.idl"`-Anweisung in der generierten IDL-Datei platziert wird.

Das **include** C++ -Attribut verfügt über die gleiche Funktionalität wie das [include](/windows/win32/Midl/include) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

Der folgende Code zeigt ein Beispiel für die Verwendung von **include**. In diesem Beispiel enthält die Datei include. h nur eine `#include`-Anweisung.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Überall|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)
