---
title: Linkertoolfehler LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194498"
---
# <a name="linker-tools-error-lnk2039"></a>Linkertoolfehler LNK2039

Importieren der Verweis Klasse "\<Type >", die in einer anderen. obj; definiert ist Es muss entweder importiert oder definiert werden, aber nicht beides.

Die Verweis Klasse ' <`type`> ' wird in die angegebene obj-Datei importiert, aber auch in einer anderen. obj-Datei definiert. Diese Bedingung kann einen Laufzeitfehler oder ein anderes unerwartetes Verhalten verursachen.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Überprüfen Sie, ob '`type`' in der anderen. obj-Datei definiert sein muss, und überprüfen Sie, ob die Datei aus der winmd-Datei importiert werden muss.

1. Entfernen Sie entweder die Definition oder den Import.

## <a name="see-also"></a>Weitere Informationen

[Fehler und Warnungen der Linkertools](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Linkertoolfehler LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
