---
title: Idl_quote (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168028"
---
# <a name="idl_quote"></a>idl_quote

Ermöglicht die Verwendung von IDL-Konstrukten, die in der aktuellen Version von Visual C++ nicht unterstützt werden und die Sie an die generierte IDL-Datei weiterleiten.

## <a name="syntax"></a>Syntax

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parameter

*text*<br/>
Der Attribut Name, den der Microsoft C++ -Compiler an die generierte IDL-Datei weitergeben soll, ohne einen Compilerfehler zurückzugeben.

## <a name="remarks"></a>Bemerkungen

Wenn das **Idl_quote** C++ -Attribut als eigenständiges Attribut verwendet wird (mit einem Semikolon nach der schließenden Klammer), wird der *Text* in die zusammengeführte IDL-Datei eingefügt, unverändert. Wenn **Idl_quote** für ein Symbol verwendet wird, wird der *Text* im Attribut Block für das Symbol platziert.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie Sie ein nicht unterstütztes Attribut angeben können (unter Verwendung von **in**, das unterstützt wird) und wie Sie ein nicht definiertes IDL-Konstrukt definieren und verwenden:

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

Dieser Code bewirkt, dass `MYFLOT` und `MYDUB` und der *Text* Eintrag in der generierten IDL-Datei platziert werden. Der *Name* -Parameter erzwingt das Platzieren von *Text* vor dem Verweis auf den *Namen* in der generierten IDL-Datei. Der *Abhängigkeiten* -Parameter erzwingt, dass die Abhängigkeits Listen Definitionen vor *Text* in der generierten IDL-Datei platziert werden.

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
[Eigenständige Attribute](stand-alone-attributes.md)
