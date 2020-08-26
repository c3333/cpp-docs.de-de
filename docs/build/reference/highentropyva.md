---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: 80e34a3f57974e1af6afb65196697cce9aa344b1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834998"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Gibt an, ob das ausführbare Image 64-bit-ASLR mit hoher Entropie unterstützt.

## <a name="syntax"></a>Syntax

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Bemerkungen

Diese Option ändert den Header einer *ausführbaren Bilddatei* (z. b. eine- *`.dll`* oder- *`.exe`* Datei), um Unterstützung für 64-Bit-Address ASLR anzugeben. Um einen Effekt zu erzielen, legen Sie die-Option für die ausführbare Datei und alle Module fest, von denen Sie abhängt. Dann können Betriebssysteme, die 64-Bit-ASLR unterstützen, die Segmente des ausführbaren Images zur Ladezeit mithilfe von zufälligen virtuellen 64-Bit-Adressen neu anordnen. Aufgrund dieses großen Adressbereichs ist es für einen Angreifer schwieriger, den Ort eines bestimmten Speicherbereichs zu schätzen.

Standardmäßig aktiviert der Linker **`/HIGHENTROPYVA`** ausführbare 64-Bit-Images. Diese Option erfordert sowohl [`/DYNAMICBASE`](dynamicbase.md) als [`/LARGEADDRESSAWARE`](largeaddressaware.md) auch, die standardmäßig auch für 64-Bit-Images aktiviert sind. **`/HIGHENTROPYVA`** gilt nicht für ausführbare 32-Bit-Images, bei denen die Option ignoriert wird. Um diese Option explizit zu deaktivieren, verwenden Sie **`/HIGHENTROPYVA:NO`** .

## <a name="see-also"></a>Siehe auch

[EDITBIN-Optionen](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Schutzmaßnahmen für Windows ISV-Software](/previous-versions/bb430720(v=msdn.10))
