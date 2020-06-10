---
title: 'MFC-ActiveX-Steuerelemente: Methoden'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621238"
---
# <a name="mfc-activex-controls-methods"></a>MFC-ActiveX-Steuerelemente: Methoden

Ein ActiveX-Steuerelement löst Ereignisse für die Kommunikation zwischen sich selbst und dessen Steuerelement Container aus. Ein Container kann mithilfe von Methoden und Eigenschaften auch mit einem-Steuerelement kommunizieren. Methoden werden auch als Funktionen bezeichnet.

Methoden und Eigenschaften stellen eine exportierte Schnittstelle zur Verwendung durch andere Anwendungen bereit, wie z. b. Automatisierungs Clients und ActiveX-Steuerelement Container. Weitere Informationen zu den Eigenschaften des ActiveX-Steuer Elements finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md).

Methoden sind in Verwendung und Zweck den Element Funktionen einer C++-Klasse ähnlich. Es gibt zwei Arten von Methoden, die von Ihrem Steuerelement implementiert werden können: Stock und Custom. Ähnlich wie bei Aktien Ereignissen sind Aktien Methoden die Methoden, für die [COleControl](reference/colecontrol-class.md) eine Implementierung bereitstellt. Weitere Informationen zu Kurs Methoden finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Hinzufügen von Aktien Methoden](mfc-activex-controls-adding-stock-methods.md). Benutzerdefinierte Methoden, die vom Entwickler definiert werden, ermöglichen eine zusätzliche Anpassung des Steuer Elements. Weitere Informationen finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden](mfc-activex-controls-adding-custom-methods.md).

Der Microsoft Foundation Class-Bibliothek (MFC) implementiert einen Mechanismus, mit dem Ihr Steuerelement Aktien-und benutzerdefinierte Methoden unterstützen kann. Der erste Teil ist "Class" `COleControl` . Von abgeleitet `CWnd` Element `COleControl` Funktionen unterstützen Aktien Methoden, die allen ActiveX-Steuerelementen gemeinsam sind. Der zweite Teil dieses Mechanismus ist die Dispatchzuordnung. Eine dispatchmap ähnelt einer Meldungs Zuordnung. anstatt einer Windows-Meldungs-ID jedoch eine Funktion zuzuordnen, ordnet eine Dispatchzuordnung virtuellen Element Funktionen IDispatch-IDs zu.

Damit ein Steuerelement verschiedene Methoden ordnungsgemäß unterstützt, muss die Klasse eine dispatchmap deklarieren. Dies wird durch die folgende Codezeile im Header der Steuerelement Klasse () erreicht. H):

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

Der Hauptzweck der Dispatchzuordnung besteht darin, die Beziehung zwischen den Methodennamen, die von einem externen Aufrufer (z. b. dem Container) verwendet werden, und den Element Funktionen der-Klasse des Steuer Elements herzustellen, die die-Methoden implementieren. Nachdem die Dispatchzuordnung deklariert wurde, muss Sie in der-Implementierung des-Steuer Elements () definiert werden. Cpp-Datei. Die folgenden Codezeilen definieren die dispatchkarte:

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Wenn Sie den [MFC-ActiveX-Steuer](reference/mfc-activex-control-wizard.md) Element-Assistenten zum Erstellen des Projekts verwendet haben, wurden diese Zeilen automatisch hinzugefügt. Wenn der MFC-ActiveX-Steuerelement-Assistent nicht verwendet wurde, müssen Sie diese Zeilen manuell hinzufügen.

In den folgenden Artikeln werden Methoden ausführlich erläutert:

- [MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Methoden](mfc-activex-controls-adding-stock-methods.md)

- [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden](mfc-activex-controls-adding-custom-methods.md)

- [MFC-ActiveX-Steuerelemente: Zurückgeben von Fehlercodes aus einer Methode](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
