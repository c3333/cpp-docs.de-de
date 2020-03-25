---
title: importidl (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166821"
---
# <a name="importidl"></a>importidl

Fügt die angegebene IDL-Datei in die generierte IDL-Datei ein.

## <a name="syntax"></a>Syntax

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parameter

*idl_file*<br/>
Identifiziert den Namen der IDL-Datei, die Sie mit der IDL-Datei zusammenführen möchten, die für die Anwendung generiert wird.

## <a name="remarks"></a>Bemerkungen

Das **importidl** C++ -Attribut platziert den Abschnitt außerhalb des Bibliotheks Blocks (in *idl_file*) in der generierten IDL-Datei des Programms und im Bibliotheks Abschnitt (in *idl_file*) in den Bibliotheks Abschnitt der generierten IDL-Datei des Programms.

Sie können beispielsweise **importidl**verwenden, wenn Sie eine Hand codierte IDL-Datei mit der generierten IDL-Datei verwenden möchten.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[Compilerattribute](compiler-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
