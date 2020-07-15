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
ms.openlocfilehash: b2ff9929de74d99fbc45e4f4ff38fd6b939697bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373826"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Gibt an, ob das ausführbare Image 64-bit-ASLR mit hoher Entropie unterstützt.

## <a name="syntax"></a>Syntax

> **/HIGHENTROPYVA**[**: No**]

## <a name="remarks"></a>Hinweise

Diese Option ändert den Header eines *ausführbaren Images*, eine DLL-Datei oder exe-Datei, um anzugeben, ob ASLR mit 64-Bit-Adressen unterstützt wird. Wenn diese Option auf einer ausführbaren Datei und allen Modulen festgelegt wird, von denen sie abhängt, kann ein 64-Bit-ASLR unterstützendes Betriebssystem für die Segmente des ausführbaren Images zur Ladezeit ein Rebase ausführen, indem zufällige Adressen in einem virtuellen 64-Bit-Adressbereich verwendet werden. Aufgrund dieses großen Adressbereichs ist es für einen Angreifer schwieriger, den Ort eines bestimmten Speicherbereichs zu schätzen.

Standardmäßig aktiviert der Linker **/HIGHENTROPYVA** für ausführbare 64-Bit-Images. Diese Option erfordert [/LARGEADDRESSAWARE](largeaddressaware.md), das auch standardmäßig für 64-Bit-Images aktiviert ist. **/HIGHENTROPYVA** ist nicht auf ausführbare 32-Bit-Images anwendbar, bei denen die Option ignoriert wird. Um diese Option explizit zu deaktivieren, verwenden Sie **/HIGHENTROPYVA: No**. Damit diese Option wirksam wird, muss auch die [/DynamicBase](dynamicbase.md) -Option festgelegt werden.

## <a name="see-also"></a>Siehe auch

- [EDITBIN-Optionen](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Schutzmaßnahmen für Windows ISV-Software](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
