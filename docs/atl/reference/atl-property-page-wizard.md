---
title: ATL-Eigenschaftenseiten-Assistent
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: 85de65dc1b18ee5c2e62388e57b0199ed64cee3f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921125"
---
# <a name="atl-property-page-wizard"></a>ATL-Eigenschaftenseiten-Assistent

::: moniker range="msvc-160"

Dieser Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Dieser Assistent [fügt eine Eigenschaftenseite zu einem ATL-Projekt](../../atl/reference/adding-an-atl-property-page.md) oder zu einem MFC-Projekt mit ATL-Unterstützung hinzu. Eine ATL-Eigenschaftenseite stellt eine Benutzeroberfläche zum Festlegen der Eigenschaften (oder Aufrufen der Methoden) von einem oder mehreren COM-Objekten bereit.

## <a name="remarks"></a>Hinweise

Ab Visual Studio 2008 werden mit dem von diesem Assistenten generierten Registrierungsskript die zugehörigen COM-Komponenten nicht unter **HKEY_LOCAL_MACHINE** , sondern unter **HKEY_CURRENT_USER** registriert. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme von **Kurzname** können alle Felder unabhängig voneinander bearbeitet werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider. Wenn Sie im COM-Abschnitt den Namen der **Co-Klasse** ändern, spiegelt sich diese Änderung in den Feldern **Typ** und **ProgID** wider. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Eigenschaftenseite alle Namen problemlos identifizieren können.

> [!NOTE]
> **Co-Klasse** kann nur in Projekten ohne Attribute bearbeitet werden. Wenn Ihr Projekt Attribute enthält, können Sie **Co-Klasse** nicht bearbeiten.

### <a name="c"></a>C++

Stellt Informationen für die C++-Klasse bereit, die zum Implementieren des Objekts erstellt wurde.

|Begriff|Definition|
|-|-|
|**Kurzname**|Legt einen abgekürzten Namen für das Objekt fest. Der Name, den Sie hier angeben, bestimmt die Namen der Klasse und der **Co-Klasse** , die Dateinamen ( **.cpp** und **.h** ), den Namen des **Typs** und die **ProgID** , sofern Sie diese Felder nicht individuell ändern.|
|**H-Datei**|Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent diese erst dann am ausgewählten Speicherort, wenn Sie im Assistenten auf **Fertig stellen** klicken.<br /><br /> Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.|
|**Klasse**|Legt den Namen der Klasse fest, die das Objekt implementiert. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.|
|**CPP-Datei**|Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.<br /><br /> Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja** , um die Datei anzufügen. Klicken Sie auf **Nein** , um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.|
|**Attributiert**|Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.<br /><br /> Sie können ein attributiertes Objekt nur zu einem ATL-Projekt hinzufügen, das Attribute verwendet. Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.<br /><br /> Standardmäßig werden alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.<br /><br /> Weitere Informationen finden Sie [unter Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [grundlegende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .|

### <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält.

   > [!NOTE]
   > Wenn Sie Ihr Projekt unter Verwendung von Attributen erstellen oder auf dieser Seite des Assistenten angeben, dass die Eigenschaftenseite Attribute verwendet, können Sie diese Option nicht ändern, da ATL das `coclass`-Attribut nicht enthält.

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung angezeigt wird.

- **ProgID**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Optionen, ATL-Eigenschaftenseiten-Assistent](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Zeichenfolgen, ATL-Eigenschaftenseiten-Assistent](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Beispiel: Implementieren einer Eigenschaften Seite](../../atl/example-implementing-a-property-page.md)
