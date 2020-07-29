---
title: Stabilität
ms.date: 11/04/2016
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
ms.openlocfilehash: 9de2611e29f5f9bfd08839517e873c3dda225af0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211592"
---
# <a name="robustness"></a>Stabilität

Verwenden Sie die folgenden C-Laufzeitbibliotheksfunktionen, um die Stabilität des Programms zu verbessern.

## <a name="run-time-robustness-functions"></a>Funktionen für die Laufzeitstabilität

|Funktion|Zweck|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Überträgt die Steuerung an den Fehler Behandlungs Mechanismus, wenn der **`new`** Operator keinen Arbeitsspeicher zuordnen kann.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Behandelt Win32-Ausnahmen (C-strukturierte Ausnahmen) als C++-typisierte Ausnahmen.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Installiert Ihre eigene Beendigungsfunktion, die von [terminate](../c-runtime-library/reference/terminate-crt.md) aufgerufen werden soll.|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Installiert Ihre eigene Beendigungsfunktion, die von [unexpected](../c-runtime-library/reference/unexpected-crt.md) aufgerufen werden soll.|

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[SetUnhandledExceptionFilter](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)<br/>
