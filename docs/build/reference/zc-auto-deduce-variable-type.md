---
title: /Zc:auto (Variablentyp ableiten)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 866cccb490136e951effb1f8da20877c8d5ec763
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217180"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto`(Typ der deduce-Variable)

Die **`/Zc:auto`** Compileroption weist den Compiler an, die Verwendung des [ `auto` Schlüssel Worts](../../cpp/auto-keyword.md) zum Deklarieren von Variablen zu verwenden. Wenn Sie die Standardoption, **`/Zc:auto`** , ableiten, leitet der Compiler den Typ der deklarierten Variable aus dem Initialisierungs Ausdruck ab. Wenn Sie angeben **`/Zc:auto-`** , ordnet der Compiler die Variable der automatischen Speicher Klasse zu.

## <a name="syntax"></a>Syntax

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

Der C++-Standard definiert eine ursprüngliche und eine überarbeitete Bedeutung für das **`auto`** Schlüsselwort. Vor Visual Studio 2010 deklariert das Schlüsselwort eine Variable in der automatischen Speicher Klasse. Das heißt, eine Variable, die über eine lokale Lebensdauer verfügt. Beginnend mit Visual Studio 2010 leitet das-Schlüsselwort den Typ einer Variablen aus dem Initialisierungs Ausdruck der Deklaration ab. Verwenden Sie die- **`/Zc:auto`** Compileroption, um den Compiler anzuweisen, die überarbeitete Bedeutung des **`auto`** Schlüssel Worts zu verwenden. Die **`/Zc:auto`** Option ist standardmäßig aktiviert. Mit der- [`/permissive-`](permissive-standards-conformance.md) Option wird die Standardeinstellung von nicht geändert **`/Zc:auto`** .

Der Compiler gibt eine geeignete Diagnose Meldung aus, wenn die Verwendung des- **`auto`** Schlüssel Worts der aktuellen **`/Zc:auto`** Compileroption widerspricht. Weitere Informationen finden Sie unter [ `auto` Schlüsselwort](../../cpp/auto-keyword.md). Weitere Informationen zu Konformitäts Problemen bei Visual C++ finden Sie unter [nicht dem Standard entsprechende Verhalten](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>So legen Sie diese Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie **`/Zc:auto`** oder **`/Zc:auto-`** dem Bereich **zusätzliche Optionen hinzu:** .

## <a name="see-also"></a>Weitere Informationen

[`/Zc`Konformitäts](zc-conformance.md)<br/>
[`auto`Schlüsselwort](../../cpp/auto-keyword.md)
