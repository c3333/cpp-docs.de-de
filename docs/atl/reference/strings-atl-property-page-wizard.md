---
title: Zeichenfolgen, ATL-Eigenschaftenseiten-Assistent
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.strings
helpviewer_keywords:
- ATL Property Page Wizard, strings
ms.assetid: 00547db6-911f-49eb-92e1-2ba67079d4df
ms.openlocfilehash: 61378e0aa2cee94420849195a94203be078418ff
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921112"
---
# <a name="strings-atl-property-page-wizard"></a>Zeichenfolgen, ATL-Eigenschaftenseiten-Assistent

::: moniker range="msvc-160"

Der ATL-Eigenschaftenseiten-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Ruft den Text ab, der der Eigenschaftenseite zugeordnet ist.

- **Titel**

   Legt den Text fest, der auf der Registerkarte der Eigenschaftenseite angezeigt wird.

- **Dokumentzeichenfolge**

   Legt eine Textzeichenfolge zur Beschreibung der Seite fest. Diese Zeichenfolge kann im Dialogfeld des Eigenschaftenblatts angezeigt werden. Der Eigenschaftenframe kann die Beschreibung in einer Statuszeile oder QuickInfo verwenden. Der standardmäßige Eigenschaftenframe verwendet diese Zeichenfolge derzeit nicht.

- **Hilfedatei**

   Legt den Namen der Hilfedatei fest, die beschreibt, wie die Eigenschaftenseite zu verwenden ist. Dieser Name darf keinen Pfad enthalten. Wenn der Benutzer auf **Hilfe** drückt, öffnet der Frame die Hilfedatei in dem Verzeichnis, das im Wert des HelpDir-Schlüssels in den Registrierungseinträgen für die Eigenschaftenseite unter der CLSID angegeben ist.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[ATL-Eigenschaftenseiten-Assistent](../../atl/reference/atl-property-page-wizard.md)<br/>
[Optionen, ATL-Eigenschaftenseiten-Assistent](../../atl/reference/options-atl-property-page-wizard.md)
