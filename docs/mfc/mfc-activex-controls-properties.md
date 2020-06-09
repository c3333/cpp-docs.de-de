---
title: 'MFC-ActiveX-Steuerelemente: Eigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: c7ed0fddea660409f5089159b71d39a29b01d538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618183"
---
# <a name="mfc-activex-controls-properties"></a>MFC-ActiveX-Steuerelemente: Eigenschaften

Ein ActiveX-Steuerelement löst Ereignisse aus, um mit dem Steuerelement Container zu kommunizieren. Der Container verwendet in der Rückgabe Methoden und Eigenschaften, um mit dem Steuerelement zu kommunizieren. Methoden und Eigenschaften sind in der Verwendung bzw. dem Zweck der Element Funktionen und Element Variablen einer C++-Klasse ähnlich. Eigenschaften sind Datenmember des ActiveX-Steuer Elements, die für einen beliebigen Container verfügbar gemacht werden. Eigenschaften stellen eine Schnittstelle für Anwendungen bereit, die ActiveX-Steuerelemente wie Automatisierungs Clients und ActiveX-Steuerelement Container enthalten.

Eigenschaften werden auch als Attribute bezeichnet.

Weitere Informationen zu ActiveX-Steuerelement Methoden finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md).

ActiveX-Steuerelemente können sowohl Aktien-als auch benutzerdefinierte Methoden und Eigenschaften implementieren. Die-Klasse `COleControl` stellt eine Implementierung für Aktien Eigenschaften bereit. (Eine komplette Liste der vordefinierten Eigenschaften finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Hinzufügen](mfc-activex-controls-adding-stock-properties.md)von vordefinierten Eigenschaften.) Benutzerdefinierte Eigenschaften, die vom Entwickler definiert werden, fügen spezialisierte Funktionen zu einem ActiveX-Steuerelement hinzu. Weitere Informationen finden Sie unter [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften](mfc-activex-controls-adding-custom-properties.md).

Sowohl benutzerdefinierte Eigenschaften als auch Eigenschaften mit Eigenschaften, wie z. b. Methoden, werden von einem Mechanismus unterstützt, der aus einer dispatchmap besteht, die Eigenschaften und Methoden sowie vorhandene Element Funktionen der `COleControl` Klasse behandelt. Außerdem können diese Eigenschaften über Parameter verfügen, die der Entwickler verwendet, um zusätzliche Informationen an das Steuerelement zu übergeben.

In den folgenden Artikeln werden die ActiveX-Steuerelement Eigenschaften ausführlicher erläutert:

- [MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Eigenschaften](mfc-activex-controls-adding-stock-properties.md)

- [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften](mfc-activex-controls-adding-custom-properties.md)

- [MFC-ActiveX-Steuerelemente: Weiterführende Eigenschaftenimplementierung](mfc-activex-controls-advanced-property-implementation.md)

- [MFC-ActiveX-Steuerelemente: Zugreifen auf Umgebungseigenschaften](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
