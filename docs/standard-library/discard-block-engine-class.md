---
title: discard_block_engine-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: 6f7b11c360f58e6a838b22fbf2c68366dce973a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846289"
---
# <a name="discard_block_engine-class"></a>discard_block_engine-Klasse

Generiert eine zufällige Sequenz, indem die von der Basis-Engine zurückgegebenen Werte verworfen werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parameter

*Ge*\
Der Typ der Basis-Engine.

*Cker*\
**Blockgröße**. Die Anzahl von Werten in jedem Block.

*R*\
**Verwendeter Block**. Die Anzahl von Werten in jedem Block, die verwendet werden. Der Rest wird verworfen ( `P`  -  `R` ). **Vorbedingung**: `0 < R ≤ P`

## <a name="members"></a>Member

`discard_block_engine::discard_block_engine`\
`discard_block_engine::base`\
`discard_block_engine::base_type`\
`discard_block_engine::discard`\
`discard_block_engine::operator()`\
`discard_block_engine::seed`

Weitere Informationen zu Engine-Membern finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage beschreibt einen Engine-Adapter, der Werte erzeugt, indem einige der von der Basis-Engine zurückgegebenen Werte verworfen werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
