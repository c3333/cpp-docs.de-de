---
title: Hinzufügen einer Klasse aus einem ActiveX-Steuerelement
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: d63f73e17e47f2cabb8f1a55c71325ec7068a2c8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500373"
---
# <a name="add-a-class-from-an-activex-control"></a>Hinzufügen einer Klasse aus einem ActiveX-Steuerelement

Verwenden Sie diesen Assistenten, um eine MFC-Klasse aus einer Schnittstelle in einem verfügbaren ActiveX-Steuerelement zu erstellen. Sie können eine MFC-Klasse in eine [MFC-Anwendung](../mfc/reference/creating-an-mfc-application.md), eine [MFC-DLL](../mfc/reference/creating-an-mfc-dll-project.md) oder ein [MFC-ActiveX-Steuerelement](../mfc/reference/creating-an-mfc-activex-control.md) einfügen.

> [!WARNING]
> Ab Version 15.9 von Visual Studio 2017 ist dieser Code-Assistent veraltet, und Microsoft wird ihn in einer zukünftigen Version von Visual Studio entfernen. Dieser Assistent wird nur selten verwendet. Die Entfernung dieses Assistenten wirkt sich nicht auf die allgemeine Unterstützung für Active Template Library (ATL) und Microsoft Foundation Classes (MFC) aus. In [dieser Umfrage](https://www.surveymonkey.com/r/QDWKKCN) können Sie Ihr Feedback zur Einstellung dieses Assistenten mitteilen. Ihr Feedback ist uns wichtig.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> Sie müssen Ihr MFC-Projekt nicht mit aktiver Automatisierung erstellen, um eine Klasse aus einem ActiveX-Steuerelement hinzuzufügen.

Ein ActiveX-Steuerelement ist eine wiederverwendbare Softwarekomponente, die auf dem Component Object Model (COM) basiert. Dieses Modell unterstützt zahlreiche OLE-Funktionen. Es kann an die unterschiedlichsten Softwareanforderungen angepasst werden. Sie können ActiveX-Steuerelemente sowohl in herkömmlichen ActiveX-Steuerelementcontainern als auch in Webseiten verwenden.

**So fügen Sie eine MFC-Klasse aus einem ActiveX-Steuerelement hinzu**

1. Klicken Sie entweder im **Projektmappen-Explorer** oder in der [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) mit der rechten Maustaste auf den Namen des Projekts, dem Sie die ActiveX-Steuerelementklasse hinzufügen möchten.

1. Wählen Sie im Kontextmenü **Hinzufügen** und dann **Klasse hinzufügen** aus.

1. Wählen Sie im Dialogfeld [Klasse hinzufügen](./adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich **Vorlagen** die Option **MFC-Klasse aus ActiveX-Steuerelement** aus, und wählen Sie dann **Öffnen** aus, um den [Assistenten zum Hinzufügen einer ActiveX-Steuerelementklasse](#add-class-from-activex-control-wizard) anzuzeigen.

Im Assistenten können Sie mehrere Schnittstellen in einem ActiveX-Steuerelement hinzufügen. Zudem können Sie Klassen aus mehreren ActiveX-Steuerelementen in einer einzelnen Assistenten-Sitzung erstellen.

Sie können Klassen aus ActiveX-Steuerelementen hinzufügen, die im System registriert sind oder sich in Typbibliotheksdateien befinden (TLB-, OLB-, DLL-, OCX- oder EXE-Dateien), ohne diese zuerst im System registrieren zu müssen. Weitere Informationen zum Registrieren von ActiveX-Steuerelementen finden Sie unter [Registrieren des OLE-Steuerelements](../mfc/reference/registering-ole-controls.md).

Der Assistent erstellt für jede Schnittstelle, die Sie aus dem ausgewählten ActiveX-Steuerelement hinzufügen, eine MFC-Klasse, die von [CWnd](../mfc/reference/cwnd-class.md) oder [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) abgeleitet wird.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Add class from ActiveX control wizard (Hinzufügen einer Klasse mit dem ActiveX-Steuerelement-Assistenten)](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Hinzufügen einer Klasse mit dem ActiveX-Steuerelement-Assistenten

Verwenden Sie diesen Assistenten, um eine MFC-Klasse aus einem verfügbaren ActiveX-Steuerelement hinzuzufügen. Der Assistent erstellt eine Klasse für jede Schnittstelle, die Sie aus dem ausgewählten ActiveX-Steuerelement hinzufügen.

- **Add Class From** (Klasse hinzufügen aus)

  Gibt den Speicherort der Typbibliothek an, aus der die Klasse erstellt wird.

  |Option|BESCHREIBUNG|
  |------------|-----------------|
  |**Registrierung**|Die Typbibliothek ist im System registriert. Registrierte Typbibliotheken werden unter **Available ActiveX controls** (Verfügbare ActiveX-Steuerelemente) aufgeführt.|
  |**File**|Die Typbibliothek ist nicht unbedingt im System registriert, sondern in einer Datei gespeichert. Geben Sie den Dateispeicherort unter **Speicherort** an.|

- **Verfügbare ActiveX-Steuerelemente**

  Gibt die ActiveX-Steuerelemente an, die derzeit im System registriert sind. Wählen Sie ein ActiveX-Steuerelement aus dieser Liste aus, um dessen Schnittstellen in der Liste **Schnittstellen** anzuzeigen. Weitere Informationen zur Registrierung von ActiveX-Steuerelementen finden Sie unter [MFC-ActiveX-Steuerelemente: Weitergabe von ActiveX-Steuerelementen](../mfc/mfc-activex-controls-distributing-activex-controls.md).

  Wenn Sie unter **Add Class From** (Klasse hinzufügen aus) **Datei** auswählen, kann dieses Feld nicht geändert werden.

- **Standort**

  Gibt den Speicherort des ActiveX-Steuerelements an. Wenn Sie unter **Add Class From** (Klasse hinzufügen aus) **Datei** auswählen, können Sie den Speicherort der Datei angeben, die die Typbibliothek enthält. Wählen Sie die Schaltfläche mit den Auslassungspunkten aus, um nach dem Speicherort der Datei zu suchen.

  Wenn Sie unter **Add Class From** (Klasse hinzufügen aus) **Registrierung** auswählen, kann dieses Feld nicht geändert werden.

- **Schnittstellen**

  Gibt die Schnittstellen im ActiveX-Steuerelement an. Der Assistent verwendet die Schnittstellen aus der aktuellen Auswahl in **Verfügbare ActiveX-Steuerelemente** oder die Schnittstellen aus der unter **Speicherort** angegebenen Typbibliotheksdatei.

  |Schaltfläche „Übertragen“|BESCHREIBUNG|
  |---------------------|-----------------|
  |**>**|Fügt die Schnittstelle hinzu, die derzeit in der Liste **Schnittstellen** ausgewählt ist. Nicht verfügbar, wenn keine Schnittstelle ausgewählt ist.|
  |**>>**|Fügt alle Schnittstellen im ActiveX-Steuerelement hinzu. Der Assistent verwendet die Schnittstellen aus der aktuellen Auswahl in **Verfügbare ActiveX-Steuerelemente** oder die Schnittstellen aus der unter **Speicherort** angegebenen Typbibliotheksdatei.|
  |**\<**|Entfernt die Klasse, die derzeit in der Liste **Generierte Klassen** ausgewählt ist. Nicht verfügbar, wenn derzeit keine Klasse in der Liste **Generierte Klassen** ausgewählt ist.|
  |**\<\<**|Entfernt alle Klassen in der Liste **Generierte Klassen**. Nicht verfügbar, wenn die Liste **Generierte Klassen** leer ist.|

- **Generierte Klassen**

  Gibt die Klassennamen an, die aus den Schnittstellen generiert werden sollen, die mithilfe der Schaltfläche **>** oder **>>** hinzugefügt wurden. Sie können dieses Kontrollkästchen aktivieren, um eine Klasse auszuwählen, und dann mit den Tasten nach oben oder unten durch die Liste scrollen. Wenn Sie **Fertig stellen** auswählen, können Sie jeden generierten Klassennamen im Feld **Klasse** und jeden generierten Dateinamen im Feld **.h-Datei** anzeigen. Sie können nur eine Klasse in diesem Feld auswählen.

  Wenn Sie eine Klasse entfernen möchten, wählen Sie diese in der Liste aus und wählen dann **<** aus. Sie müssen keine Klasse im Feld **Generierte Klassen** auswählen, um alle Klassen zu entfernen. Durch Auswahl von **<<** werden alle Klassen im Feld **Generierte Klassen** entfernt.

- **Klasse**

   Gibt den Namen der Klasse an, die im Feld **Generierte Klassen** ausgewählt ist. Dieses wird vom Assistenten hinzugefügt, wenn Sie **Fertig stellen** auswählen. Sie können den Namen im Feld **Klasse** bearbeiten.

- **H-Datei**

  Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Generierte Klassen** angeben. Wählen Sie die Schaltfläche mit den Auslassungspunkten aus, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Bei Auswahl einer vorhandenen Datei speichert der Assistent diese erst am ausgewählten Speicherort, wenn Sie im Assistenten **Fertig stellen** auswählen.

  Vom Assistenten werden keine Dateien überschrieben. Wenn Sie den Namen einer vorhandenen Datei und dann **Fertig stellen** auswählen, fordert der Assistent Sie dazu auf, ob die Klassendeklaration an den Dateiinhalt angefügt werden soll. Wählen Sie **Ja** aus, um die Datei anzufügen. Wählen Sie **Nein** aus, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **CPP-Datei**

  Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Generierte Klassen** angeben. Wählen Sie die Schaltfläche mit den Auslassungspunkten aus, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird erst am ausgewählten Speicherort gespeichert, wenn Sie im Assistenten **Fertig stellen** auswählen.

  Vom Assistenten werden keine Dateien überschrieben. Wenn Sie den Namen einer vorhandenen Datei und dann **Fertig stellen** auswählen, fordert der Assistent Sie dazu auf, ob die Klassenimplementierung an den Dateiinhalt angefügt werden soll. Wählen Sie **Ja** aus, um die Datei anzufügen. Wählen Sie **Nein** aus, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.
