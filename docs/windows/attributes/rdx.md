---
title: RDX (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: b5f0981f249653b1068e2fbec3d02d3209d5f935
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232754"
---
# <a name="rdx"></a>rdx

Erstellt einen Registrierungsschlüssel oder ändert einen vorhandenen Registrierungsschlüssel.

## <a name="syntax"></a>Syntax

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Name des zu erstellenden oder zu öffnenden Schlüssels.

*valueName*<br/>
Optionale Gibt das Wertfeld an, das festgelegt werden soll. Wenn ein Wertfeld mit diesem Namen nicht bereits im Schlüssel vorhanden ist, wird es hinzugefügt.

*regyp*<br/>
Der Typ des Registrierungsschlüssels, der hinzugefügt wird. Kann eines der folgenden sein: `text` , `dword` , `binary` oder `CString` .

## <a name="remarks"></a>Bemerkungen

Das **RDX** C++-Attribut erstellt oder ändert einen vorhandenen Registrierungsschlüssel für eine COM-Komponente. Das-Attribut fügt dem-Objekt, das den Zielmember implementiert, ein BEGIN_RDX_MAP-Makro hinzu. `RegistryDataExchange`, eine Funktion, die als Ergebnis des BEGIN_RDX_MAP-Makros eingefügt wurde, kann zum Übertragen von Daten zwischen der Registrierung und den Datenmembern verwendet werden.

Dieses Attribut kann in Verbindung mit den Attributen [Co-Klasse](coclass.md), [ProgID](progid.md)oder [Vi_progid](vi-progid.md) oder anderen Attributen verwendet werden, die eines dieser Attribute impliziert.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`** oder- **`struct`** Member|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Beispiel

Der folgende Code fügt dem System einen Registrierungsschlüssel namens "myValue" hinzu, der die COM-Komponente "CMyClass" beschreibt.

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Siehe auch

[COM-Attribute](com-attributes.md)<br/>
[registration_script](registration-script.md)
