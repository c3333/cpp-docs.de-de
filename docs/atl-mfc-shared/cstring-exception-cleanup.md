---
title: CString-Ausnahmebereinigung
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: 48c8f1c0040236a4f7bf27a2d5ad985ae343c03a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222055"
---
# <a name="cstring-exception-cleanup"></a>CString-Ausnahmebereinigung

In früheren Versionen von MFC war es wichtig, dass Sie [CString](../atl-mfc-shared/reference/cstringt-class.md) -Objekte nach der Verwendung bereinigen. Bei MFC-Version 3,0 und höher ist die explizite Bereinigung nicht mehr erforderlich.

Unter dem C++-Mechanismus zur Ausnahmebehandlung, der von MFC jetzt verwendet wird, müssen Sie sich nicht mehr um die Bereinigung kümmern, nachdem eine Ausnahme ausgelöst wurde. Eine Beschreibung der Art und Weise, wie C++ den Stapel nach dem Auffangen einer Ausnahme abwickelt, finden [Sie unter try-, catch-und Throw-Anweisungen](../cpp/try-throw-and-catch-statements-cpp.md). Auch wenn Sie die MFC- **try** / -**catch** -Makros anstelle der C++ **`try`** -Schlüsselwörter und verwenden **`catch`** , verwendet MFC den untergeordneten C++-Ausnahme Mechanismus, sodass Sie nicht explizit eine Bereinigung durchführen müssen.

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Ausnahmebehandlung](../mfc/exception-handling-in-mfc.md)
