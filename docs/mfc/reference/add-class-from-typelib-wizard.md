---
title: Assistent zum Hinzufügen von Klassen aus der Typbibliothek
ms.date: 05/09/2019
helpviewer_keywords:
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: 6fa1dd3985fd5b565bcc4b4727f41960d1f4f5d0
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405129"
---
# <a name="add-class-from-typelib-wizard"></a>Assistent zum Hinzufügen von Klassen aus der Typbibliothek

::: moniker range="vs-2019"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=vs-2017"

Mit diesem Assistenten können Sie eine MFC-Klasse aus einer verfügbaren Typbibliothek hinzufügen. Der Assistent erstellt eine Klasse für jede Schnittstelle, die Sie aus der ausgewählten Typbibliothek hinzufügen.

- **Klasse hinzufügen aus**

   Gibt den Speicherort der Typbibliothek an, aus der die Klasse erstellt wird.

   |Option|BESCHREIBUNG|
   |------------|-----------------|
   |**Registrierung**|Die Typbibliothek ist im System registriert. Registrierte Typbibliotheken werden unter **Verfügbare Typbibliotheken** aufgeführt.|
   |**Datei**|Die Typbibliothek ist nicht unbedingt im System registriert, sondern in einer Datei enthalten. Sie müssen den Dateispeicherort unter **Speicherort** angeben.|

- **Verfügbare Typbibliotheken**

   Listet die Typbibliotheken auf, die derzeit im System registriert sind. Wählen Sie eine Typbibliothek aus dieser Liste aus, um die zugehörigen Schnittstellen in der Liste der **Schnittstellen** anzuzeigen.

- **Location**

   Gibt den Speicherort der Typbibliothek an. Wenn Sie unter **Add Class From** (Klasse hinzufügen aus) auf **Datei** klicken, können Sie den Speicherort der Datei angeben, die die Typbibliothek enthält. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um nach dem Speicherort der Datei zu suchen.

- **Schnittstellen**

   Listet die Schnittstellen in der Typbibliothek auf, die derzeit in der Liste **Verfügbare Typbibliotheken** ausgewählt ist.

   |Schaltfläche „Übertragen“|BESCHREIBUNG|
   |---------------------|-----------------|
   |**>**|Fügt die Schnittstelle hinzu, die derzeit in der Liste **Schnittstellen** ausgewählt ist. Abgetrübt, wenn keine Schnittstelle ausgewählt ist.|
   |**>>**|Fügt alle Schnittstellen in der Typbibliothek hinzu, die derzeit in der Liste **Verfügbare Typbibliotheken** ausgewählt ist.|
   |**\<**|Entfernt die Klasse, die derzeit in der Liste **Generierte Klassen** ausgewählt ist. Abgetrübt, wenn derzeit keine Klasse in der Liste der **generierten Klassen** ausgewählt ist.|
   |**\<\<**|Entfernt alle Klassen in der Liste **Generierte Klassen**. Abgetrübt, wenn die Liste der **generierten Klassen** leer ist.|

- **Generierte Klassen**

   Gibt die Klassennamen an, die von den Schnittstellen generiert werden, die mithilfe der **>** Schaltfläche oder hinzugefügt wurden **>>** Sie können auf dieses Kontrollkästchen klicken, um eine Klasse auszuwählen. verwenden Sie dann die nach-oben-oder nach-unten-Taste, um in der Liste einen Bildlauf durchführen, und sehen Sie sich die einzelnen Klassennamen **Finish**im Feld **Klasse** und Dateiname im Feld **Datei** an, die der Assistent generiert Sie können nur eine Klasse in diesem Feld auswählen.

   Sie können eine Klasse entfernen, indem Sie Sie in dieser Liste auswählen und dann auf klicken **<** . Sie müssen keine Klasse im Feld Generierte Klassen auswählen, um alle Klassen zu entfernen. Sie können alle Klassen im Feld **Generierte Klassen** entfernen, indem Sie auf **<<** klicken.

- **Klasse**

   Gibt den Namen der Klasse an, die im Feld **Generierte Klassen** ausgewählt ist. Dieses wird vom Assistenten hinzugefügt, wenn Sie auf **Fertig stellen** klicken. Sie können den Namen im Feld **Klasse** bearbeiten.

- **Datei**

   Legt den Namen der Headerdatei für die neue Klasse fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Generierte Klassen** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent diese nicht am ausgewählten Speicherort, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[MFC-Klasse aus einer Typbibliothek](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Automatisierungsclients: Verwenden von Typbibliotheken](../../mfc/automation-clients-using-type-libraries.md)
