---
title: ATL-Steuerelement-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: c89fe17272399212e4436481abc2800c3ab6e660
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353141"
---
# <a name="atl-control-wizard"></a>ATL-Steuerelement-Assistent

Fügt ein ATL-Steuerelement in ein ATL-Projekt (oder ein MFC-Projekt mit ATL-Unterstützung) ein. Mit diesem Assistenten können Sie eine von drei Arten von Steuerelementen einfügen:

- Standard Steuerelement

- Composite-Steuerelement

- DHTML-Steuerelement

Darüber hinaus können Sie ein minimales Steuerelement angeben, indem Sie die Schnittstellen aus der [Schnittstellen](../../atl/reference/interfaces-atl-control-wizard.md) Liste entfernen, die als Standardwerte für Steuerelemente bereitgestellt werden, die in den meisten Containern geöffnet werden Sie können die Schnittstellen, die für das-Steuerelement unterstützt werden sollen, auf der Seite **Schnittstellen** des Assistenten festlegen.

## <a name="remarks"></a>Hinweise

Das Registrierungs Skript, das von diesem Assistenten erstellt wird, registriert seine com-Komponenten unter HKEY_CURRENT_USER anstatt HKEY_LOCAL_MACHINE. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme von **Kurznamen**können alle anderen Felder unabhängig voneinander geändert werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider. Wenn Sie den **coclass** -Namen im com-Abschnitt ändern, wird die Änderung im Feld **Typ** widergespiegelt, aber der **Schnittstellen** Name und die **ProgID** werden nicht geändert. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

> [!NOTE]
> Die **Co-Klasse** kann nur auf nicht attributierten Steuerelementen bearbeitet werden. Wenn Ihr Projekt Attribute enthält, können Sie **Co-Klasse** nicht bearbeiten.

### <a name="c"></a>C++

Stellt Informationen für die C++-Klasse bereit, die zum Implementieren des Objekts erstellt wurde.

- **Kurzname**

   Legt einen abgekürzten Namen für das Objekt fest. Der von Ihnen bereitgestellte Name bestimmt die Klassen-und **Co-Klassen** Namen, die Datei (. Cpp und. H), den Namen der Schnittstelle und die **Typnamen** , sofern Sie diese Felder nicht einzeln ändern.

- **Klasse**

   Legt den Namen der Klasse fest, die das Objekt implementiert. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.

- **H-Datei**

   Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, wird Sie vom Assistenten nicht am ausgewählten Speicherort gespeichert, bis Sie auf **Fertig**stellen geklickt haben.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **CPP-Datei**

   Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Attributiert**

   Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.

   Sie können ein attributiertes Objekt nur zu einem ATL-Projekt hinzufügen, das Attribute verwendet. Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.

   Standardmäßig werden alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.

   Weitere Informationen finden Sie [unter Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [grundlegende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält.

   > [!NOTE]
   > Wenn Sie Ihr Projekt mithilfe von Attributen erstellen oder wenn Sie auf dieser Assistenten Seite angeben, dass das Steuerelement Attribute verwendet, können Sie diese Option nicht ändern, da ATL das **Co-Klasse** -Attribut nicht enthält.

- **Interface**

   Legt den Namen der Schnittstelle für das-Objekt fest. Standardmäßig wird einem Schnittstellennamen "I" vorangestellt.

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung angezeigt wird.

- **ProgID**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können. Dieses Feld wird nicht automatisch aufgefüllt. Wenn Sie dieses Feld nicht manuell auffüllen, ist das Steuerelement möglicherweise nicht für andere Tools verfügbar. ActiveX-Steuerelemente, die ohne eine generiert werden, `ProgID` sind z. b. im Dialogfeld **ActiveX-Steuerelement einfügen** nicht verfügbar. Weitere Informationen zum Dialogfeld finden Sie unter [Einfügen von ActiveX](../../windows/adding-editing-or-deleting-controls.md#insert-activex-controls)-Steuerelementen.

## <a name="see-also"></a>Weitere Informationen

[ATL-Steuerelement](../../atl/reference/adding-an-atl-control.md)<br/>
[Hinzufügen von Funktionen zum zusammengesetzten Steuerelement](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Grundlagen von ATL-COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md)
