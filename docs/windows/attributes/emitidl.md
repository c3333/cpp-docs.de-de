---
title: Emitidl (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 32362f287320e69d1680cbe07ca050143b507514
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846328"
---
# <a name="emitidl"></a>emitidl

Gibt an, ob alle nachfolgenden IDL-Attribute verarbeitet und in der generierten IDL-Datei abgelegt werden.

## <a name="syntax"></a>Syntax

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parameter

*state*<br/>
Einer der folgenden möglichen Werte: **`true`** , **`false`** , `forced` , `restricted` , `push` oder `pop` .

- Wenn **`true`** der Wert ist, werden alle in einer Quell Code Datei gefundenen IDL-Kategorieattribute in der generierten IDL-Datei abgelegt. Dies ist die Standardeinstellung für **Emitidl**.

- Wenn **`false`** der Wert ist, werden alle in einer Quell Code Datei gefundenen IDL-Kategorieattribute nicht in der generierten IDL-Datei abgelegt.

- Gibt `restricted` an, dass IDL-Attribute ohne [Modul](module-cpp.md) Attribut in der Datei enthalten sein können. Der Compiler generiert keine IDL-Datei.

- Wenn `forced` , wird ein nachfolgendes `restricted` Attribut überschrieben, das erfordert, dass eine Datei über ein-Attribut verfügt, `module` Wenn in der Datei IDL-Attribute vorhanden sind.

- `push` ermöglicht das Speichern der aktuellen **Emitidl** -Einstellungen in einem internen **Emitidl** -Stapel und `pop` ermöglicht das Festlegen von **Emitidl** auf einen beliebigen Wert, der sich am Anfang des internen **Emitidl** -Stapels befindet.

`defaultimports=`*boolescher* \( Wert optionale

- Wenn *boolescher* Wert ist **`true`** , wird docobj. idl in die generierte IDL-Datei importiert. Wenn sich eine IDL-Datei mit dem gleichen Namen wie eine h-Datei befindet, die Sie in `#include` Ihrem Quellcode in demselben Verzeichnis wie die h-Datei finden, enthält die generierte IDL-Datei außerdem eine Import-Anweisung für diese IDL-Datei.

- Wenn *boolescher* Wert ist **`false`** , wird docobj. idl nicht in die generierte IDL-Datei importiert. IDL-Dateien müssen explizit mit [Import](import.md)importiert werden.

## <a name="remarks"></a>Bemerkungen

Nachdem das Attribut " **Emitidl** C++" in einer Quell Code Datei gefunden wurde, werden die IDL-Kategorieattribute in der generierten IDL-Datei abgelegt. Wenn kein **Emitidl** -Attribut vorhanden ist, werden IDL-Attribute in der Quell Code Datei an die generierte IDL-Datei ausgegeben.

Es ist möglich, mehrere **Emitidl** -Attribute in einer Quell Code Datei zu haben. Wenn `[emitidl(false)];` in einer Datei ohne nachfolgende gefunden wird `[emitidl(true)];` , werden keine Attribute in der generierten IDL-Datei verarbeitet.

Jedes Mal, wenn der Compiler auf eine neue Datei stößt, wird **Emitidl** implizit auf festgelegt **`true`** .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)
