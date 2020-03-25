---
title: uuid (C++-Attribute)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: c507a9ae42afc5081c290d38464aa7f24c277d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166119"
---
# <a name="uuid-c-attributes"></a>uuid (C++-Attribute)

Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.

## <a name="syntax"></a>Syntax

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Parameter

*uuid*<br/>
Ein eindeutiger 128-Bit-Bezeichner.

## <a name="remarks"></a>Bemerkungen

Wenn die Definition einer Schnittstelle oder Klasse das **UUID** C++ -Attribut nicht angibt, wird vom Microsoft C++ -Compiler eine bereitgestellt. Wenn Sie eine **UUID**angeben, müssen Sie die Anführungszeichen einschließen.

Wenn Sie **UUID**nicht angeben, generiert der Compiler dieselbe GUID für Schnittstellen oder Klassen mit demselben Namen in unterschiedlichen Attribut Projekten auf einem Computer.

Sie können "uuidgen. exe" oder "Guidgen. exe" verwenden, um eigene eindeutige IDs zu generieren. (Um eines dieser Tools auszuführen, klicken Sie auf **Start** , und klicken Sie im Menü auf **Ausführen** . Geben Sie dann den Namen des erforderlichen Tools ein.)

Bei Verwendung in einem Projekt, das nicht auch ATL verwendet, ist die Angabe des **UUID** -Attributs mit dem Angeben des [UUID](../../cpp/uuid-cpp.md) - **__declspec** Modifizierers identisch. Zum Abrufen der **UUID** einer Klasse können Sie [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **UUID**finden Sie im [bindbare](bindable.md) -Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**, **Schnittstelle**, Union **,** Enumeration **union**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
