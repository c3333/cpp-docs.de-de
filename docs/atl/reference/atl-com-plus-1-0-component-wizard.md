---
title: ATL COM+ 1.0 Komponenten-Assistent
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: c4e77c7f3c17a90ddd09661b5fea5bad984d3245
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923806"
---
# <a name="atl-com-10-component-wizard"></a>ATL COM+ 1.0 Komponenten-Assistent

::: moniker range="msvc-160"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Verwenden Sie diesen Assistenten, um ein Objekt zu Ihrem Projekt hinzuzufügen, das COM+ 1.0-Dienste einschließlich Transaktionen unterstützt.

Sie können angeben, ob das Objekt duale Schnittstellen und Automatisierung unterstützt. Sie können auch Unterstützung für die Schnittstelle für Fehlerinformationen, für die erweiterte Objektsteuerung, für Transaktionen und für asynchrones Meldungsqueuing angeben.

## <a name="remarks"></a>Hinweise

Ab Visual Studio 2008 werden mit dem von diesem Assistenten generierten Registrierungsskript die zugehörigen COM-Komponenten nicht unter **HKEY_LOCAL_MACHINE** , sondern unter **HKEY_CURRENT_USER** registriert. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme von **Kurzname** können alle Felder unabhängig voneinander bearbeitet werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider. Wenn Sie im COM-Abschnitt den Namen der **Co-Klasse** ändern, spiegelt sich diese Änderung in den Feldern **Typ** und **ProgID** wider, der Name der **Schnittstelle** ändert sich jedoch nicht. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

- **Kurzname**

   Legt einen abgekürzten Namen für das Objekt fest. Der Name, den Sie hier angeben, bestimmt die Namen der `Class` und der `Coclass`, die Namen der **.cpp-Datei** und der **.h-Datei** , den Namen der **Schnittstelle** , den Namen des **Typs** und die **ProgID** , sofern Sie diese Felder nicht individuell ändern.

- **H-Datei**

   Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent diese nicht am ausgewählten Speicherort, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Klasse**

   Legt den Namen der zu erstellenden Klasse fest. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.

- **CPP-Datei**

   Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Attributiert**

   Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.

   Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.

   Standardmäßig werden alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.

   Weitere Informationen finden Sie [unter Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [grundlegende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält.

> [!NOTE]
> Wenn Sie Ihr Projekt unter Verwendung von Attributen erstellen oder auf dieser Seite des Assistenten angeben, dass die COM+ 1.0-Komponente Attribute verwendet, können Sie diese Option nicht ändern, da ATL das `coclass`-Attribut nicht enthält.

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung angezeigt wird.

- **Interface**

   Legt die Schnittstelle fest, die Sie für Ihr Objekt erstellen. Diese Schnittstelle enthält Ihre benutzerdefinierten Methoden.

- **ProgID**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[ATL COM+ 1.0-Komponente](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
