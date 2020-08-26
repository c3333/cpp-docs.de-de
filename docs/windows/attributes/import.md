---
title: Import (C++ com-Attribut)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: 6b146bdad7d870b534c371a4396993202cc83a4b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842311"
---
# <a name="import"></a>Import

Gibt eine andere IDL-, ODL-oder Header Datei an, die Definitionen enthält, auf die Sie von Ihrer Haupt-IDL verweisen möchten.

## <a name="syntax"></a>Syntax

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parameter

*idl_file*<br/>
Der Name einer IDL-Datei, die in die Typbibliothek des aktuellen Projekts importiert werden soll.

## <a name="remarks"></a>Bemerkungen

Das **Import** C++-Attribut bewirkt `#import` , dass eine-Anweisung unter der- `import "docobj.idl"` Anweisung in der generierten IDL-Datei platziert wird. Das **Import** -Attribut verfügt über die gleiche Funktionalität wie das [Import](/windows/win32/Midl/import) -Attribut von "Mittel l".

Mit dem **Import** -Attribut wird die angegebene Datei nur in die IDL-Datei eingefügt, die vom Projekt generiert wird. mit dem **Import** -Attribut können Sie Konstrukte in der angegebenen Datei nicht aus dem Quellcode in Ihrem Projekt abrufen.  Um Konstrukte in der angegebenen Datei aus dem Quellcode in Ihrem Projekt aufzurufen, verwenden Sie entweder [#Import](../../preprocessor/hash-import-directive-cpp.md) und das- `embedded_idl` Attribut, oder Sie können die h-Datei für die *idl_file*einschließen, wenn eine h-Datei vorhanden ist.

## <a name="example"></a>Beispiel

Der folgende Code

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

erzeugt den folgenden Code in der generierten IDL-Datei:

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[darunter](include-cpp.md)<br/>
[Includelib](includelib-cpp.md)
