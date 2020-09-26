---
title: ATL-Assistent für einfache Objekte
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.overview
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
ms.openlocfilehash: 8bc611442e98e467a174ebd52ea3c540cf72975f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352686"
---
# <a name="atl-simple-object-wizard"></a>ATL-Assistent für einfache Objekte

Dieser Assistent fügt ein minimales COM-Objekt in das Projekt ein. Auf dieser Seite des Assistenten können Sie die Namen angeben, mit denen die C++-Klasse und die Dateien für das Objekt und seine com-Funktionalität identifiziert werden.

Verwenden Sie die Seite [Optionen](../../atl/reference/options-atl-simple-object-wizard.md) dieses Assistenten, um das Threading Modell des Objekts, seine Aggregations Unterstützung und die Unterstützung für duale Schnittstellen und Automatisierung anzugeben. Sie können auch die Unterstützung für die Schnittstelle für Fehlerinformationen, Verbindungspunkte, Internet Explorer-Unterstützung und Freethread-Marshalling angeben.

## <a name="remarks"></a>Hinweise

Ab Visual Studio 2008 werden mit dem von diesem Assistenten generierten Registrierungsskript die zugehörigen COM-Komponenten nicht unter **HKEY_LOCAL_MACHINE**, sondern unter **HKEY_CURRENT_USER** registriert. Um dieses Verhalten zu ändern, legen Sie die Option **Komponente für alle Benutzer registrieren** des ATL-Assistenten fest.

## <a name="names"></a>Namen

Geben Sie die Namen für das Objekt, die Schnittstelle und die Klassen an, das bzw. die Ihrem Projekt hinzugefügt werden sollen. Mit Ausnahme von **Kurzname** können alle Felder unabhängig voneinander bearbeitet werden. Wenn Sie den Text für **Kurzname** ändern, spiegelt sich die Änderung in den Namen aller anderen Felder auf dieser Seite wider. Wenn Sie im COM-Abschnitt den Namen der **Co-Klasse** ändern, spiegelt sich diese Änderung in den Feldern **Typ** und **ProgID** wider, der Name der **Schnittstelle** ändert sich jedoch nicht. Dieses Benennungsverhalten wurde so konzipiert, damit Sie beim Entwickeln der Steuerelemente alle Namen problemlos identifizieren können.

> [!NOTE]
> **Co-Klasse** kann nur in Projekten ohne Attribute bearbeitet werden. Wenn Ihr Projekt Attribute enthält, können Sie **Co-Klasse** nicht bearbeiten.

## <a name="c"></a>C++

Stellt Informationen für die C++-Klasse bereit, die für das Objekt erstellt wurde.

- **Kurzname**

   Legt einen abgekürzten Namen für das Objekt fest. Der Name, den Sie hier angeben, bestimmt die Namen der `Class` und der `Coclass`, die Namen der **.cpp-Datei** und der **.h-Datei**, den Namen der **Schnittstelle**, den Namen des **Typs** und die **ProgID**, sofern Sie diese Felder nicht individuell ändern.

- **H-Datei**

   Legt den Namen der Headerdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei auswählen, speichert der Assistent diese erst dann am ausgewählten Speicherort, wenn Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Klasse**

   Legt den Namen der zu erstellenden Klasse fest. Dieser Name basiert auf dem Namen, den Sie unter **Kurzname** angeben. Dem Namen ist „C“ vorangestellt, das typische Präfix für einen Klassennamen.

- **CPP-Datei**

   Legt den Namen der Implementierungsdatei für die neue Klasse des Objekts fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Kurzname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen am gewünschten Speicherort zu speichern. Die Datei wird nicht am ausgewählten Speicherort gespeichert, bis Sie im Assistenten auf **Fertig stellen** klicken.

   Der Assistent überschreibt Dateien nicht. Wenn Sie den Namen einer vorhandenen Datei auswählen, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassenimplementierung an die Inhalte der Datei angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Datei anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Attributiert**

   Gibt an, ob das Objekt Attribute verwendet. Wenn Sie ein Objekt zu einem attributierten ATL-Projekt hinzufügen, wird diese Option ausgewählt und kann nicht geändert werden. Das bedeutet, dass Sie einem Projekt, das mit Attributunterstützung erstellt wurde, nur attributierte Objekte hinzufügen können.

   Sie können ein attributiertes Objekt nur zu einem ATL-Projekt hinzufügen, das Attribute verwendet. Wenn Sie diese Option für ein ATL-Projekt ohne Attributunterstützung auswählen, werden Sie vom Assistenten aufgefordert, anzugeben, ob Sie dem Projekt Attributunterstützung hinzufügen möchten.

   Standardmäßig werden alle Objekte, die Sie nach dem Festlegen dieser Option hinzufügen, als attributiert festgelegt (das Kontrollkästchen ist aktiviert). Sie können das Kontrollkästchen deaktivieren, um ein Objekt hinzuzufügen, das keine Attribute verwendet.

   Weitere Informationen finden Sie [unter Anwendungseinstellungen, ATL-Projekt-Assistent](../../atl/reference/application-settings-atl-project-wizard.md) und [grundlegende Funktionsweise von Attributen](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

## <a name="com"></a>COM

Stellt Informationen über die COM-Funktionalität für das Objekt bereit.

- **Co-Klasse**

   Legt den Namen der Komponentenklasse fest, die eine Liste der vom Objekt unterstützten Schnittstellen enthält.

   > [!NOTE]
   > Wenn Sie Ihr Projekt mithilfe von Attributen erstellen oder wenn Sie auf dieser Assistenten Seite angeben, dass das Objekt Attribute verwendet, können Sie diese Option nicht ändern, da ATL das-Attribut nicht enthält `coclass` .

- **Typ**

   Legt die Objektbeschreibung fest, die in der Registrierung angezeigt wird.

- **Interface**

   Legt die Schnittstelle fest, die Sie für Ihr Objekt erstellen. Diese Schnittstelle enthält Ihre benutzerdefinierten Methoden.

- **ProgID**

   Legt den Namen fest, den Container anstelle der CLSID des Objekts verwenden können.

## <a name="see-also"></a>Weitere Informationen

[ATL Simple Object (Einfaches ATL-Objekt)](../../atl/reference/adding-an-atl-simple-object.md)
