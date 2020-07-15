---
title: /HIGHENTROPYVA (Unterstützung für 64-Bit ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 8f8601d89e8456461aac3d91f9fd2cfda216d7f5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373839"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Unterstützung für 64-Bit ASLR)

Gibt an, ob das ausführbare Image 64-bit-ASLR mit hoher Entropie unterstützt.

## <a name="syntax"></a>Syntax

> **/HIGHENTROPYVA**[**: No**]

## <a name="remarks"></a>Hinweise

**/HIGHENTROPYVA** ändert den Header eines *ausführbaren Images*, eine DLL-Datei oder eine exe-Datei, um anzugeben, ob ASLR den gesamten 64-Bit-Adressraum verwenden kann. Wenn diese Option auf einer ausführbaren Datei und allen Modulen festgelegt wird, von denen sie abhängt, kann ein 64-Bit-ASLR unterstützendes Betriebssystem für die Segmente des ausführbaren Images zur Ladezeit ein Rebase ausführen, indem zufällige Adressen in einem virtuellen 64-Bit-Adressbereich verwendet werden. Aufgrund dieses großen Adressbereichs ist es für einen Angreifer schwieriger, den Ort eines bestimmten Speicherbereichs zu schätzen.

Standardmäßig ist **/HIGHENTROPYVA** für ausführbare 64-Bit-Images aktiviert. Diese Option erfordert [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), das auch standardmäßig für 64-Bit-Images aktiviert ist. **/HIGHENTROPYVA** ist nicht auf ausführbare 32-Bit-Images anwendbar, bei denen der Linker die Option ignoriert. Um diese Option explizit zu deaktivieren, verwenden Sie **/HIGHENTROPYVA: No**.

Damit **/HIGHENTROPYVA** zur Ladezeit wirksam wird, muss auch [/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) aktiviert werden. **/DynamicBase** ist standardmäßig aktiviert und ist erforderlich, um ASLR in Windows Vista und höheren Betriebssystemen zu aktivieren. In früheren Versionen von Windows wurde dieses Flag ignoriert.

### <a name="to-set-this-linker-option-in-visual-studio"></a>So legen Sie diese Linkeroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für die  >  **Linker**  >  **Linkerbefehlszeile** der Configuration Properties

1. Geben Sie unter **zusätzliche Optionen** `/HIGHENTROPYVA` oder ein `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Weitere Informationen

- [MSVC-Linkerreferenz](linking.md)
- [MSVC-Linkeroptionen](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Schutzmaßnahmen für Windows ISV-Software](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
