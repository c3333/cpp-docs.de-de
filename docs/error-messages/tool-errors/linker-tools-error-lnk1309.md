---
title: Linkertoolfehler LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: 88b05512fd45adb6dc96a6c130ceccb74f3ab14e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194901"
---
# <a name="linker-tools-error-lnk1309"></a>Linkertoolfehler LNK1309

> *Typ1* -Modul erkannt; ungültig mit Switch/CLRIMAGETYPE:*Typ2*

## <a name="remarks"></a>Bemerkungen

Ein CLR-Imagetyp wurde mit **/CLRIMAGETYPE** angefordert, aber der Linker konnte kein Image dieses Typs ausgeben, da mindestens ein Modul mit diesem Typ nicht kompatibel war.

Beispielsweise wird Linkertoolfehler LNK1309 angezeigt, wenn Sie **/CLRIMAGETYPE: Safe** angeben und ein Modul übergeben, das mit **/clr: pure**erstellt wurde.

Die **/clr: pure** -und **/clr: Safe** -Compileroptionen und-Unterstützungs Bibliotheken sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

Außerdem wird Linkertoolfehler LNK1309 angezeigt, wenn Sie versuchen, eine teilweise vertrauenswürdige CLR-reine Anwendung mithilfe von Ptrustu [d]. lib zu erstellen. Informationen zum Erstellen einer teilweise vertrauenswürdigen Anwendung finden Sie unter Gewusst [wie: Erstellen einer teilweise vertrauenswürdigen Anwendung durch Entfernen der Abhängigkeit von der CRT-Bibliotheks-DLL](../../dotnet/create-a-partially-trusted-application.md).

Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) und [/CLRIMAGETYPE (Typ des CLR-Bilds angeben)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).
