---
title: '/Zc: Präprozessor (präprozessorübereinstimmungs Modus aktivieren)'
description: 'Verwenden Sie die/Zc: präprocessor-Compileroption, um die Compilerunterstützung für einen standardkonformen Präprozessor zu aktivieren.'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /Zc:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /Zc:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 356434e4892966b9a9304021dd5d8770dcc2f8b1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90043174"
---
# <a name="zcpreprocessor-enable-preprocessor-conformance-mode"></a>`/Zc:preprocessor` (Präprozessorübereinstimmungs Modus aktivieren)

Diese Option aktiviert einen tokenbasierten Präprozessor, der den Standards C99 und c++ 11 und höher entspricht. Weitere Informationen finden Sie unter [MSVC: Übersicht über den neuen Präprozessor](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntax

> **`/Zc:preprocessor`**[**-**]

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die- **`/Zc:preprocessor`** Compileroption, um den entsprechenden Präprozessor zu aktivieren. Sie können **`/Zc:preprocessor-`** die Option verwenden, um den herkömmlichen (nicht konformen) Präprozessor explizit anzugeben.

Die **`/Zc:preprocessor`** Option ist ab Visual Studio 2019 Version 16,5 verfügbar. Eine frühere, unvollständige Version der neuen Präprozessoroption steht in Versionen von Visual Studio ab Visual Studio 2017, Version 15,8, zur Verfügung. Weitere Informationen finden Sie unter [`/experimental:preprocessor`](experimental-preprocessor.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** in include, *`/Zc:preprocessor`* und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)
