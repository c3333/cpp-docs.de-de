---
title: Steuerelementnamen, MFC-ActiveX-Steuerelement-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: eff7b537e7fe5c19d10cce8766557a3d1ff49342
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077502"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Steuerelementnamen, MFC-ActiveX-Steuerelement-Assistent

Geben Sie die Namen für die Steuerelement Klasse und Eigenschaften Seiten Klasse, die Typnamen und die Typbezeichner für das Steuerelement an. Mit Ausnahme von **Short Name**können alle anderen Felder unabhängig bearbeitet werden. Wenn Sie den Text für **Kurzname**ändern, wird die Änderung in den Namen aller anderen Felder auf dieser Seite angezeigt. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

- **Kurzname**

   Gibt einen abgekürzten Namen für das Steuerelement an. Standardmäßig basiert dieser Name auf dem Projektnamen, den Sie im Dialogfeld **Neues Projekt** angegeben haben. Der von Ihnen bereitgestellte Name bestimmt die Klassennamen, die Typnamen und die Typbezeichner, es sei denn, Sie ändern diese Felder einzeln.

- **Name der Steuerelement Klasse**

   Standardmäßig basiert der Name der Steuerelement Klasse auf dem Kurznamen, wobei `C` als Präfix und als Suffix `Ctrl`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Name der Steuerelement Klasse `CPriceCtrl`.

- **Control. h-Datei**

   Standardmäßig basiert der Name der Header Datei auf dem Kurznamen, wobei `Ctrl` als Suffix und als Dateierweiterung `.h`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Name der Header Datei `PriceCtrl.h`. Der Name in diesem Feld muss mit dem Namen der Steuerelement Klasse identisch sein.

- **Control. cpp-Datei**

   Standardmäßig basiert der Name der Header Datei auf dem Kurznamen, wobei `Ctrl` als Suffix und als Dateierweiterung `.cpp`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Name der Header Datei `PriceCtrl.cpp`. Der Name in diesem Feld muss mit dem Header Namen identisch sein.

- **Steuerelement-Typname**

   Standardmäßig basiert der Name des Steuerelement Typs auf dem Kurznamen, gefolgt von `Control`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Typname der Steuerelement Klasse `Price Control`. Wenn Sie den Wert in diesem Feld ändern, stellen Sie sicher, dass der Name eine Vererbung angibt.

- **Steuerelement-Typkennung**

   Legt die Steuerelement-ID der Steuerelement Klasse fest. Das-Steuerelement schreibt diese Zeichenfolge in die Registrierung, wenn Sie zu einem Projekt hinzugefügt wird. Container Anwendungen verwenden diese Zeichenfolge, um eine Instanz des Steuer Elements zu erstellen.

   Standardmäßig basiert die Steuerelement-ID auf dem Projektnamen, den Sie im Dialogfeld **Neues Projekt** angegeben haben, und auf dem Kurznamen. Dieser Name muss mit dem Typnamen identisch sein.

   Standardmäßig wird die Steuerelement-Typ-ID wie folgt angezeigt:

   *ProjectName. ShortName* STRG. 1

   Wenn Sie den Kurznamen in diesem Dialogfeld ändern, wird die Steuerelement-Typ-ID wie folgt angezeigt:

   *ProjectName. newshortname* STRG. 1

- **PropPage-Klassenname**

   Standardmäßig basiert der Name der Eigenschaften Seiten Klasse auf dem Kurznamen, wobei `C` als Präfix und als Suffix `PropPage`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Klassenname der Eigenschaften Seite `CPricePropPage`. Dieser Name muss mit dem Namen der Steuerelement Klasse, angefügt `PropPage`, identisch sein.

- **PropPage. h-Datei**

   Standardmäßig basiert der Name der Header Datei der Eigenschaften Seite auf dem Kurznamen, wobei als Suffix `PropPage` als Suffix und als Dateierweiterung `.h`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Name der Header Datei der Eigenschaften Seite `PricePropPage.h`. Dieser Name muss mit dem Klassennamen identisch sein.

- **PropPage. cpp-Datei**

   Standardmäßig basiert der Name der Implementierungs Datei für die Eigenschaften Seite auf dem Kurznamen, wobei als Suffix `PropPage` als Suffix und als Dateierweiterung `.cpp`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, wird der Name der Header Datei der Eigenschaften Seite `PricePropPage.cpp`. Dieser Name muss mit dem Namen der Header Datei identisch sein.

- **PropPage-Typname**

   Standardmäßig basiert der Typ Name der Eigenschaften Seite auf dem Kurznamen, gefolgt von `Property Page`. Wenn z. b. der Kurzname Ihres Steuer Elements `Price`ist, ist der Typname der Eigenschaften Seite `Price Property Page`. Wenn Sie den Wert in diesem Feld ändern, stellen Sie sicher, dass der Name die Steuerelement Klasse angibt.

- **PropPage-Typ-ID**

   Legt die ID der Eigenschaften Seiten Klasse fest. Das-Steuerelement schreibt diese Zeichenfolge in die Registrierung, wenn Sie auf ein Projekt angewendet wird. Eine Containeranwendung verwendet diese Zeichenfolge, um eine Instanz der Eigenschaften Seite des-Steuer Elements zu erstellen.

   Standardmäßig basiert die Typ-ID der Eigenschaften Seite auf dem Projektnamen, den Sie im Dialogfeld **Neues Projekt** angegeben haben, und auf dem Kurznamen. Dieser Name muss mit dem Typnamen identisch sein.

   Standardmäßig sieht die Typ-ID der Eigenschaften Seite wie folgt aus:

   *ProjectName. ShortName* PropPage. 1

   Wenn Sie den Kurznamen in diesem Dialogfeld ändern, wird die Typ-ID der Eigenschaften Seite wie folgt angezeigt:

   *ProjectName. newshortname* PropPage. 1

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Anwendungseinstellungen, MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Steuerelementeinstellungen, MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Für Visual Studio C++-Projekte erstellte Dateitypen](../../build/reference/file-types-created-for-visual-cpp-projects.md)
