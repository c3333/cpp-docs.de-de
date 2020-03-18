---
title: '&lt;codecvt&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bbef1fe28c3321f06c0cc586062cd017168f8e73
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427200"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt;-Enumerationen

## <a name="codecvt_mode"></a> codecvt_mode-Enumeration

Gibt Konfigurationsinformationen für [Gebietsschemafacets](../standard-library/locale-class.md) an.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Hinweise

Die Enumeration definiert drei Konstanten, die Konfigurationsinformationen für Gebietsschemafacets angeben, die in [\<codecvt>](../standard-library/codecvt.md) deklariert sind. Die unterschiedlichen Werte lauten:

- `consume_header`, um eine Sequenz des ursprünglichen Headers zu verwenden, wenn eine Multibytesequenz gelesen wird, und um die Bytereihenfolge der nachfolgenden zu lesenden Multibytesequenz zu bestimmen

- `generate_header`, um eine Sequenz des ursprünglichen Headers zu generieren, wenn eine Multibytesequenz geschrieben wird, um die Bytereihenfolge der nachfolgenden zu schreibenden Multibytesequenz anzukündigen

- `little_endian`, um eine Multibytesequenz in der Little-Endian-Reihenfolge zu generieren (und nicht in der standardmäßigen Big-Endian-Reihenfolge)

Diese Konstanten können mit OR beliebig kombiniert werden.

## <a name="see-also"></a>Siehe auch

[\<codecvt>](../standard-library/codecvt.md)
