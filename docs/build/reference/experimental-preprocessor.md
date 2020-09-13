---
title: '/experimental: Präprozessor (präprozessorübereinstimmungs Modus aktivieren)'
description: 'Verwenden Sie die/Experimental: präprocessor-Compileroption, um die experimentelle Compilerunterstützung für einen standardkonformen Präprozessor zu aktivieren'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 9a98289434e7154d2ec8b8753d990876a8218acf
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042094"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>`/experimental:preprocessor` (Präprozessorübereinstimmungs Modus aktivieren)

Diese Option ist veraltet, beginnend mit Visual Studio 2019, Version 16,5, ersetzt durch die- [`/Zc:preprocessor`](zc-preprocessor.md) Compileroption. **`/experimental:preprocessor`** ermöglicht einen experimentellen, tokenbasierten Präprozessor, der den Standards von c++ 11 genauer entspricht, einschließlich C99-präprozessorfunktionen. Weitere Informationen finden Sie unter [MSVC: Übersicht über den neuen Präprozessor](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntax

> **`/experimental:preprocessor`**\[**`-`**]

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die- **`/experimental:preprocessor`** Compileroption, um den experimentellen konformen Präprozessor zu aktivieren. Sie können **`/experimental:preprocessor-`** die Option verwenden, um den herkömmlichen Präprozessor explizit anzugeben.

Die **`/experimental:preprocessor`** Option ist ab Visual Studio 2017 Version 15,8 verfügbar. Ab Visual Studio 2019 Version 16,5 ist der neue Präprozessor vollständig und unter der- [`/Zc:preprocessor`](zc-preprocessor.md) Compileroption verfügbar.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** in include, *`/experimental:preprocessor`* und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)
