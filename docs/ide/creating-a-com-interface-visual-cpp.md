---
title: Erstellen einer COM-Schnittstelle
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 6ad8d50049d34a711937f3d1f73157ce26f69808
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509687"
---
# <a name="create-a-com-interface"></a>Erstellen einer COM-Schnittstelle

Visual Studio stellt Assistenten und Vorlagen zum Erstellen von Projekten bereit, die definierende COM-Schnittstellen und Disp-Schnittstellen für Ihre COM-Objekte und Automatisierungsklassen verwenden.

Sie können diese Assistenten zum Ausführen der folgenden häufig benötigten Aufgaben verwenden:

- [Hinzufügen von ATL-Unterstützung zu einem MFC-Projekt](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

  Fügen Sie ATL-Unterstützung zu einer MFC-Anwendung hinzu, wenn Sie ein MFC-Projekt mithilfe des [MFC-Anwendungs-Assistenten](../mfc/reference/mfc-application-wizard.md) erstellt haben, und führen Sie den Codeassistenten zum **Hinzufügen von ATL-Unterstützung zu MFC** aus. Diese Unterstützung gilt nur für einfache COM-Objekte, die einer MFC-Anwendung oder einem DLL-Projekt hinzugefügt werden. Diese ATL-Objekte können über mehrere Schnittstellen verfügen.

- [Erstellen eines MFC-ActiveX-Steuerelements](../mfc/reference/creating-an-mfc-activex-control.md)

  Öffnen Sie den [MFC-ActiveX-Steuerelement-Assistenten](../mfc/reference/mfc-activex-control-wizard.md), um ein ActiveX-Steuerelement mit einer Display-Schnittstelle und einer Ereigniszuordnung zu erstellen, die jeweils in der IDL-Datei und der Steuerelementklasse definiert werden.

- [Hinzufügen eines ATL-Steuerelements](../atl/reference/adding-an-atl-control.md)

  Verwenden Sie eine Kombination aus dem [ATL-Projekt-Assistenten](../atl/reference/atl-project-wizard.md) und dem [ATL-Steuerelement-Assistenten](../atl/reference/atl-control-wizard.md), um ein ATL-ActiveX-Steuerelement zu erstellen.

  Sie können auch einem MFC-Projekt, dem Sie wie oben beschrieben ATL-Unterstützung hinzugefügt haben, ein ATL-Steuerelement hinzufügen. Darüber hinaus zeigt Visual Studio ein Dialogfeld zur Bestätigung des Hinzufügens von ATL-Unterstützung zu dem MFC-Projekt an, wenn Sie **ATL-Steuerelement** im Dialogfeld **Klasse hinzufügen** ausgewählt und dem MFC-Projekt noch keine ATL-Unterstützung hinzugefügt haben.

  Dieser Assistent generiert die IDL-Quelle und eine COM-Zuordnung in den Projektklassen.

Sobald Sie ein ATL-Projekt geöffnet haben, erhalten Sie im Dialogfeld [Klasse hinzufügen](./adding-a-class-visual-cpp.md#add-class-dialog-box) eine Auswahl zusätzlicher Assistenten und Vorlagen zum Hinzufügen von COM-Schnittstellen zum Projekt. Mithilfe der folgenden Assistenten können Sie mehrere Schnittstellen für das Objekt erstellen:

- [ATL COM+ 1.0 component wizard (ATL COM+ 1.0 Komponenten-Assistent)](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL simple object wizard (ATL-Assistent für einfache Objekte)](../atl/reference/atl-simple-object-wizard.md)
- [ATL active server page component wizard (ATL-Assistent für Active Server Page-Komponenten)](../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL control wizard (ATL-Steuerelement-Assistent)](../atl/reference/atl-control-wizard.md)

Außerdem können Sie neue Schnittstellen für Ihre COM-Steuerelemente implementieren. Klicken Sie dafür erst mit der rechten Maustaste auf die Steuerelementklasse des Objekts in der Klassenansicht und anschließend mit der linken auf [Schnittstelle implementieren](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).

> [!NOTE]
> Visual Studio stellt keinen Assistenten dafür bereit, Schnittstellen zu einem Projekt hinzuzufügen. Sie können Schnittstellen zu einem ATL-Projekt oder zu einem [MFC-Projekt](../mfc/reference/adding-atl-support-to-your-mfc-project.md) hinzufügen, zu dem von ATL-Unterstützung hinzugefügt wurde, indem Sie mithilfe des [ATL-Assistenten für einfache Objekte](../atl/reference/atl-simple-object-wizard.md) ein einfaches Objekt hinzufügen. Öffnen Sie alternativ die IDL-Datei des Projekts, und erstellen Sie die Schnittstelle, indem Sie Folgendes eingeben:

```
interface IMyInterface {
};
```

Weitere Informationen finden Sie unter [Implementieren einer Schnittstelle](../ide/implementing-an-interface-visual-cpp.md) und [Hinzufügen von Objekten und Steuerelementen zu einem ATL-Projekt](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ bietet mehrere Möglichkeiten zum Anzeigen und [Bearbeiten der COM-Schnittstellen](#edit-a-com-interface), die für Ihre Projekte definiert sind. Die [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) zeigt Symbole für Schnittstellen oder Disp-Schnittstellen an, die in einer IDL-Datei in Ihrem Projekt definiert sind.

Bei ATL-basierten COM-Objektklassen liest die Klassenansicht die COM-Zuordnung in der ATL-Klasse zum Anzeigen der Beziehung zwischen der ATL-Klasse und allen Schnittstellen, die sie implementiert.

In der Klassenansicht und den zugehörigen Kontextmenüs können Sie wie folgt mit Schnittstellen arbeiten:

- Fügen Sie ATL-Objekte zu einer MFC-basierten Anwendung hinzu.
- Fügen Sie Methoden, Eigenschaften und Ereignisse hinzu.
- Navigieren Sie direkt zum Schnittstellencode eines Elements, indem Sie auf das Element doppelklicken.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Bearbeiten einer COM-Schnittstelle](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Bearbeiten einer COM-Schnittstelle

Mithilfe der Befehle des Kontextmenüs der Klassenansicht können Sie neue Methoden und Eigenschaften für die COM-Schnittstellen in Ihren C++-Projekten in Visual Studio definieren. Darüber hinaus können Sie mit der Toolbox Ereignisse für ActiveX-Steuerelemente definieren.

Bei ATL- und MFC-basierten COM-Objektklassen können Sie die Implementierung der Klasse und die Schnittstelle zur gleichen Zeit bearbeiten.

> [!NOTE]
> Für Schnittstellen, die Sie außerhalb des Dialogfelds **Klasse hinzufügen** definiert haben, fügt Visual C++ die Methoden oder Eigenschaften der IDL-Datei und Stubs den Klassen hinzu, die Methoden implementieren, auch wenn die Schnittstellen manuell hinzugefügt werden.

Die folgenden drei Assistenten unterstützen Sie beim Anpassen vorhandener Schnittstellen. Sie sind in der Klassenansicht verfügbar:

|Assistent|Projekttyp|
|------------|------------------|
|[Assistent zum Hinzufügen von Eigenschaften](./adding-a-property-visual-cpp.md#names-add-property-wizard)|ATL- oder MFC-Projekte, die ATL unterstützen. Klicken Sie mit der rechten Maustaste auf die Schnittstelle, der die Eigenschaft hinzugefügt werden soll.<br /><br />Visual C++ erkennt den Projekttyp und ändert die Optionen im Assistenten zum Hinzufügen von Eigenschaften nach Bedarf:<br /><br />– Für Disp-Schnittstellen in Projekten, die mit dem [MFC-Anwendungs-Assistenten](../mfc/reference/mfc-application-wizard.md) erstellt wurden, werden durch das Aufrufen des Assistenten zum Hinzufügen von Eigenschaften MFC-spezifische Optionen bereitgestellt.<br />– Für ActiveX-Steuerelementschnittstellen stellt der Assistent zum Hinzufügen von Eigenschaften eine Liste vordefinierter Methoden und Eigenschaften bereit, die Sie verwenden oder für Ihr Steuerelement anpassen können.<br />– Für alle anderen Schnittstellen stellt der Assistent zum Hinzufügen von Eigenschaften Optionen bereit, die in den meisten Situationen nützlich sind.|
|[Assistent zum Hinzufügen von Methoden](./adding-a-method-visual-cpp.md#add-method-wizard)|ATL- oder MFC-Projekte, die ATL unterstützen. Klicken Sie mit der rechten Maustaste auf die Schnittstelle, der die Methode hinzugefügt werden soll.<br /><br />Visual C++ erkennt den Projekttyp und ändert die Optionen im Assistenten zum Hinzufügen von Methoden nach Bedarf:<br /><br />– Für Disp-Schnittstellen in Projekten, die mit dem [MFC-Anwendungs-Assistenten](../mfc/reference/mfc-application-wizard.md) erstellt wurden, werden durch das Aufrufen des Assistenten zum Hinzufügen von Methoden MFC-spezifische Optionen bereitgestellt.<br />– Für ActiveX-Steuerelementschnittstellen stellt der Assistent zum Hinzufügen von Methoden eine Liste vordefinierter Methoden und Eigenschaften bereit, die Sie verwenden oder für Ihr Steuerelement anpassen können.<br />– Für alle anderen Schnittstellen stellt der **Assistent zum Hinzufügen von Methoden** Optionen bereit, die in den meisten Situationen nützlich sind.|

Außerdem können Sie neue Schnittstellen für Ihre COM-Steuerelemente implementieren. Klicken Sie dafür erst mit der rechten Maustaste auf die Steuerelementklasse des Objekts in der Klassenansicht und anschließend mit der linken auf [Schnittstelle implementieren](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).
