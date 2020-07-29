---
title: /Zc:externConstexpr (Externe constexpr-Variablen aktivieren)
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: 7546ab6d81137a2abb053cd18f0d5d74913c3b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211904"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr`(Externe constexpr-Variablen aktivieren)

Die- **`/Zc:externConstexpr`** Compileroption weist den Compiler an, dem C++-Standard zu entsprechen und externe Verknüpfungen für **`constexpr`** Variablen zuzulassen. Standardmäßig gibt Visual Studio immer eine **`constexpr`** interne Variablen Verknüpfung aus, auch wenn Sie das- **`extern`** Schlüsselwort angeben.

## <a name="syntax"></a>Syntax

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

Die- **`/Zc:externConstexpr`** Compileroption bewirkt, dass der Compiler externe Verknüpfungen auf Variablen anwendet, die mit deklariert werden `extern constexpr` . In früheren Versionen von Visual Studio und standardmäßig oder wenn **`/Zc:externConstexpr-`** angegeben ist, wendet Visual Studio eine interne Verknüpfung auf **`constexpr`** Variablen an, auch wenn das- **`extern`** Schlüsselwort verwendet wird. Die **`/Zc:externConstexpr`** Option ist ab Visual Studio 2017 Update 15,6 verfügbar. und ist standardmäßig deaktiviert. Die [`/permissive-`](permissive-standards-conformance.md) Option aktiviert nicht **`/Zc:externConstexpr`** .

Wenn eine Header Datei eine deklarierte Variable enthält `extern constexpr` , muss Sie markiert werden, um [`__declspec(selectany)`](../../cpp/selectany.md) die doppelten Deklarationen in einer einzelnen Instanz in der verknüpften Binärdatei zusammenzuführen. Andernfalls werden möglicherweise Linker-Fehler, z. b. LNK2005, für Verstöße gegen die eindefinitions Regel angezeigt.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>So legen Sie diese Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie **`/Zc:externConstexpr`** oder **`/Zc:externConstexpr-`** dem Bereich **zusätzliche Optionen hinzu:** .

## <a name="see-also"></a>Weitere Informationen

[`/Zc`Konformitäts](zc-conformance.md)<br/>
[`auto`Schlüsselwort](../../cpp/auto-keyword.md)
