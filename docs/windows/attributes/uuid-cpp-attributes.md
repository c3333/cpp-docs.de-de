---
title: uuid (C++-Attribute)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: 9ff8888c26945d7f118e71002e3b3290217b463c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843039"
---
# <a name="uuid-c-attributes"></a>uuid (C++-Attribute)

Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.

## <a name="syntax"></a>Syntax

```cpp
[ uuid( "uuid" ) ]
```

### <a name="parameters"></a>Parameter

*uuid*<br/>
Ein eindeutiger 128-Bit-Bezeichner.

## <a name="remarks"></a>Bemerkungen

Wenn die Definition einer Schnittstelle oder Klasse das C++-Attribut nicht angibt `uuid` , wird vom Microsoft C++-Compiler eine bereitgestellt. Wenn Sie angeben `uuid` , müssen Sie die Anführungszeichen einschließen.

Wenn Sie nicht angeben `uuid` , generiert der Compiler dieselbe GUID für Schnittstellen oder Klassen mit demselben Namen in unterschiedlichen Attribut Projekten auf einem Computer.

Sie können Uuidgen.exe oder Guidgen.exe verwenden, um eigene eindeutige IDs zu generieren. (Um eines dieser Tools auszuführen, klicken Sie auf **Start** , und klicken Sie im Menü auf **Ausführen** . Geben Sie dann den Namen des erforderlichen Tools ein.)

Wenn Sie in einem Projekt verwendet wird, das nicht auch ATL verwendet, ist die Angabe des `uuid` Attributs mit dem Angeben des [UUID](../../cpp/uuid-cpp.md) - **`__declspec`** Modifizierers identisch. Zum Abrufen des einer `uuid` Klasse können Sie [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie im [bindbare](bindable.md) -Beispiel `uuid` .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|`class`, `struct`, `interface`, `union`, `enum`|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
