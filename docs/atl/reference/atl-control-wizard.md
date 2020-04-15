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
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321699"
---
# <a name="atl-control-wizard"></a>ATL-Steuerelement-Assistent

Fügt ein ATL-Steuerelement in ein ATL-Projekt (oder ein MFC-Projekt mit ATL-Unterstützung) ein. Mit diesem Assistenten können Sie eine von drei Arten von Steuerelementen einfügen:

- Standardsteuerung

- Composite-Steuerung

- DHTML-Steuerung

Darüber hinaus können Sie ein minimales Steuerelement angeben und die Schnittstellen aus der Liste [Schnittstellen](../../atl/reference/interfaces-atl-control-wizard.md) entfernen, die als Standardwerte für Steuerelemente bereitgestellt werden, die in den meisten Containern geöffnet werden sollen. Sie können die Schnittstellen, die für das Steuerelement unterstützt werden sollen, auf der Seite **Schnittstellen** des Assistenten festlegen.

## <a name="remarks"></a>Bemerkungen

Das von diesem Assistenten erstellte Registrierungsskript registriert seine COM-Komponenten unter HKEY_CURRENT_USER statt HKEY_LOCAL_MACHINE. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme **des Kurznamens**können alle anderen Felder unabhängig voneinander geändert werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider. Wenn Sie den **Coclass-Namen** im COM-Abschnitt ändern, wird die Änderung im Feld **Typ** widergespiegelt, der **Schnittstellenname** und **ProgID** ändern sich jedoch nicht. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

> [!NOTE]
> **Coclass** kann nur für nicht attributierte Steuerelemente bearbeitet werden. Wenn Ihr Projekt Attribute enthält, können Sie **Co-Klasse** nicht bearbeiten.

### <a name="c"></a>C++

Stellt Informationen für die C++-Klasse bereit, die zum Implementieren des Objekts erstellt wurde.

- **Kurzname**

   Legt einen abgekürzten Namen für das Objekt fest. Der von Ihnen angezeigte Name bestimmt die Klassen- und **Coclass-Namen,** die Datei (. CPP und . H) Namen, schnittstellennamen und **typi.**

- **Class**

   Legt den Namen der Klasse fest, die das Objekt implementiert. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.

- **H-Datei**

   Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent sie erst am ausgewählten Speicherort, wenn Sie auf **Fertig stellen**klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **CPP-Datei**

   Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Attributiert**

   Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.

   Sie können ein attributiertes Objekt nur zu einem ATL-Projekt hinzufügen, das Attribute verwendet. Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.

   Standardmäßig werden alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.

   Weitere Informationen finden Sie unter [Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [Grundlegende Funktionsweise von Attributen](../../windows/basic-mechanics-of-attributes.md).

### <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält.

   > [!NOTE]
   > Wenn Sie das Projekt mit Attributen erstellen oder auf dieser Assistentenseite angeben, dass das Steuerelement Attribute verwendet, können Sie diese Option nicht ändern, da ATL das **Attribut coclass** nicht enthält.

- **Schnittstelle**

   Legt den Namen der Schnittstelle für das Objekt fest. Standardmäßig wird einem Schnittstellennamen "I" vorangestellt.

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung angezeigt wird.

- **Progid**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können. Dieses Feld wird nicht automatisch aufgefüllt. Wenn Sie dieses Feld nicht manuell auffüllen, ist das Steuerelement möglicherweise nicht für andere Tools verfügbar. ActiveX-Steuerelemente, die ohne `ProgID` a generiert werden, sind beispielsweise im Dialogfeld **ActiveX-Steuerelement einfügen** nicht verfügbar. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Insert ActiveX Control Dialog Box („Dialogfeld ‚ActiveX-Steuerelement einfügen‘“)](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Siehe auch

[ATL-Steuerelement](../../atl/reference/adding-an-atl-control.md)<br/>
[Hinzufügen von Funktionen zum Composite-Steuerelement](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Grundlagen von ATL COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md)
