---
title: ATL-Assistent für Active Server Page-Komponenten
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: 191b739354827dc1b7f0fd22e5ba2fd57f7b14d0
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923759"
---
# <a name="atl-active-server-page-component-wizard"></a>ATL-Assistent für Active Server Page-Komponenten

::: moniker range="msvc-160"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Dieser Assistent fügt eine ASP-Komponente (Active Server Pages) in das Projekt ein. Die Microsoft-Internetinformationsdienste (Internet Information Services, IIS) verwenden ASP-Komponenten im Rahmen der erweiterten Architektur für die Webseitenentwicklung.

Mit diesem Assistenten können Sie das Threadingmodell und die Aggregationsunterstützung der Komponente angeben. Sie können auch Unterstützung für die Schnittstelle für Fehlerinformationen, Verbindungspunkte und das Marshalling mit freiem Threading angeben.

## <a name="remarks"></a>Hinweise

Ab Visual Studio 2008 werden mit dem von diesem Assistenten generierten Registrierungsskript die zugehörigen COM-Komponenten nicht unter **HKEY_LOCAL_MACHINE** , sondern unter **HKEY_CURRENT_USER** registriert. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme von **Kurzname** können alle Felder unabhängig voneinander bearbeitet werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider.

Wenn Sie im COM-Abschnitt den Namen der **Co-Klasse** ändern, spiegelt sich diese Änderung in den Feldern **Typ** und **ProgID** wider, der Name der **Schnittstelle** ändert sich jedoch nicht. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

### <a name="c"></a>C++

Stellt Informationen für die C++-Klasse bereit, die für das Objekt erstellt wurde.

- **Kurzname**

   Legt den Stammnamen für das Objekt fest. Der Name, den Sie hier angeben, bestimmt die Namen der `Class` und der **Co-Klasse** , die Namen der **.cpp-Datei** und der **.h-Datei** , den Namen der **Schnittstelle** , den Namen des **Typs** und die **ProgID** , sofern Sie diese Felder nicht individuell ändern.

- **H-Datei**

   Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent diese erst dann am ausgewählten Speicherort, wenn Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Klasse**

   Legt den Namen der zu erstellenden Klasse fest. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.

- **CPP-Datei**

   Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Attributiert**

   Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.

   Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.

   Standardmäßig werden bei nicht attributierten Projekten alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.

   Weitere Informationen finden Sie [unter Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [grundlegende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält. Wenn Ihr Projekt oder dieses Objekt Attribute verwendet, können Sie diese Option nicht ändern, weil ATL das Attribut **coclass** nicht enthält.

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung für die Co-Klasse angezeigt wird.

- **Interface**

   Legt die Schnittstelle fest, die Sie für Ihr Objekt erstellen. Diese Schnittstelle enthält Ihre benutzerdefinierten Methoden.

- **ProgID**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[ATL Active Server Page-Komponente](../../atl/reference/adding-an-atl-active-server-page-component.md)
