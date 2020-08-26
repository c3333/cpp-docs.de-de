---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 5451e3d16883eef225aebc3c420e6c0700947ad6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842583"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Gibt an, ob ein ausführbares Image generiert werden soll, das zur Ladezeit nach dem Zufallsprinzip zur Ladezeit neu erstellt werden kann, indem das ASLR (Address Space Layout Anordnung)-Feature von Windows verwendet wird, das erstmals in Windows Vista

## <a name="syntax"></a>Syntax

> **/DynamicBase**[**: No**]

## <a name="remarks"></a>Bemerkungen

Die Option **/DynamicBase** ändert den Header eines *ausführbaren Images*, eine DLL-oder exe-Datei, um anzugeben, ob die Anwendung zur Ladezeit nach dem Zufallsprinzip neu erstellt werden soll, und ermöglicht die zufällige Zuordnung von virtuellen Adressen, die sich auf den Speicherort des virtuellen Speichers von Heaps, Stapeln und anderen Betriebssystem Zuordnungen auswirkt. Die **/DynamicBase** -Option gilt sowohl für 32-Bit-als auch für 64-Bit-Images. ASLR wird unter Windows Vista und höheren Betriebssystemen unterstützt. Die Option wird von älteren Betriebssystemen ignoriert.

Standardmäßig ist **/DynamicBase** aktiviert. Verwenden Sie **/DynamicBase: No**, um diese Option zu deaktivieren. Die **/DynamicBase** -Option ist erforderlich, damit die [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) -Option wirksam wird.

## <a name="see-also"></a>Weitere Informationen

- [EDITBIN-Optionen](editbin-options.md)
- [Schutzmaßnahmen für Windows ISV-Software](/previous-versions/bb430720(v=msdn.10))
