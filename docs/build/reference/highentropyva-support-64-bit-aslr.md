---
title: /HIGHENTROPYVA (Unterstützung für 64-Bit ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 929d6aa71010c1f303bf7a1ce64109a01b8792e4
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404124"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Unterstützung für 64-Bit ASLR)

Gibt an, ob das ausführbare Image 64-bit-ASLR mit hoher Entropie unterstützt.

## <a name="syntax"></a>Syntax

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Bemerkungen

**`/HIGHENTROPYVA`** ändert den Header einer *ausführbaren Bilddatei* (z. b. eine- *`.dll`* oder- *`.exe`* Datei), um anzugeben, ob ASLR den gesamten 64-Bit-Adressraum verwenden kann.  Um einen Effekt zu erzielen, legen Sie die-Option für die ausführbare Datei und alle Module fest, von denen Sie abhängt. Dann kann ein Betriebssystem, das 64-Bit-ASLR unterstützt, die Segmente des ausführbaren Images zur Ladezeit mithilfe von zufälligen 64-Bit-Adressen neu anordnen. Aufgrund dieses großen Adressbereichs ist es für einen Angreifer schwieriger, den Ort eines bestimmten Speicherbereichs zu schätzen.

Standardmäßig **`/HIGHENTROPYVA`** ist für ausführbare 64-Bit-Images aktiviert. Diese Option erfordert [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md) , das auch standardmäßig für 64-Bit-Images aktiviert ist. **`/HIGHENTROPYVA`** gilt nicht für ausführbare 32-Bit-Images, bei denen der Linker die Option ignoriert. Um diese Option explizit zu deaktivieren, verwenden Sie **`/HIGHENTROPYVA:NO`** .

Damit **`/HIGHENTROPYVA`** zur Ladezeit wirksam werden kann, [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md) muss ebenfalls aktiviert sein. **`/DYNAMICBASE`** ist standardmäßig aktiviert und ist erforderlich, um ASLR in Windows Vista und höheren Betriebssystemen zu aktivieren. In früheren Versionen von Windows wurde dieses Flag ignoriert.

### <a name="to-set-this-linker-option-in-visual-studio"></a>So legen Sie diese Linkeroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für die  >  **Linker**  >  **Linkerbefehlszeile** der Configuration Properties

1. Geben Sie unter **zusätzliche Optionen** `/HIGHENTROPYVA` oder ein `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Weitere Informationen

- [MSVC-Linkerreferenz](linking.md)
- [Linkeroptionen](linker-options.md)
- [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md)
- [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md)
- [Schutzmaßnahmen für Windows ISV-Software](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
