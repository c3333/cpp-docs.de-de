---
title: Hinzufügen einer generischen C++-Klasse
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: d5c00a35e375d133fbd3a6ed7fe3591e4b0cd54b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503123"
---
# <a name="add-a-generic-c-class"></a>Hinzufügen einer generischen C++-Klasse

Sie können eine generische C++-Klasse mithilfe der **Klassenansicht** hinzufügen. Eine generische C++-Klasse ist eine Klasse, die Sie definieren oder die von einer Klasse abgeleitet wird, die Sie definieren.

**So fügen Sie einem Projekt eine generische C++-Klasse hinzu:**

1. Klicken Sie in der **Klassenansicht** mit der rechten Maustaste auf das Projekt, dem die neue Klasse hinzugefügt werden soll, und klicken Sie dann auf **Hinzufügen** > **Klasse**.

1. Klicken Sie im Dialogfeld [Klasse hinzufügen](./adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich „Vorlagen“ auf **C++-Klasse**. Klicken Sie zum Anzeigen des [generischen C++-Klassen-Assistenten](#generic-c-class-wizard) auf **Hinzufügen**.

1. Geben Sie im Assistenten einen Klassennamen an, und definieren Sie die Einstellungen, oder akzeptieren Sie die Standardwerte.

1. Klicken Sie zum Schließen des Assistenten und Anzeigen der neuen generischen C++-Klasse in dem Projekt auf **Fertig stellen**.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Generic C++ class wizard (Generischer C++-Klassen-Assistent)](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Generischer C++-Klassen-Assistent

Fügt einem Projekt eine generische C++-Klasse hinzu. Die Klasse erbt nicht von ATL oder MFC.

- **Klassenname**

  Legt den Namen der neuen Klasse fest.

- **H-Datei**

  Legt den Namen der Headerdatei für die neue Klasse fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Klassenname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ( **...** ), um die Headerdatei am gewünschten Speicherort zu speichern oder um die Klassendeklaration an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei angeben, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendeklaration an die Dateiinhalte angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Deklaration anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **CPP-Datei**

  Legt den Namen der Implementierungsdatei für die neue Klasse fest. Standardmäßig basiert dieser Name auf dem Namen, den Sie unter **Klassenname** angeben. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ( **...** ), um die Implementierungsdatei am gewünschten Speicherort zu speichern oder um die Klassendefinition an eine vorhandene Datei anzufügen. Wenn Sie eine vorhandene Datei angeben, fordert der Assistent Sie dazu auf, anzugeben, ob die Klassendefinition an die Dateiinhalte angefügt werden sollen, wenn Sie auf **Fertig stellen** klicken. Klicken Sie auf **Ja**, um die Definition anzufügen. Klicken Sie auf **Nein**, um zum Assistenten zurückzukehren und einen anderen Dateinamen anzugeben.

- **Basisklasse**

  Legt die Basisklasse für die neue Klasse fest.

- **Zugriff**

  Legt den Zugriff auf die Member der Basisklasse für die neue Klasse fest. Bei Zugriffsmodifizierern handelt es sich um Schlüsselwörter, die den Zugriff festlegen, den andere Klassen auf die Klassenmemberfunktionen haben. Weitere Informationen zum Angeben des Zugriffs finden Sie unter [Memberzugriffssteuerung](../cpp/member-access-control-cpp.md). Die Klassenzugriffsebene ist standardmäßig auf **`public`** festgelegt.

  - **`public`**
  - **`protected`**
  - **`private`**
  - **Standard** (kein Zugriffsmodifizierer wird generiert)

- **Virtueller Destruktor**

  Gibt an, ob der Klassendestruktor virtuell ist. Die Verwendung eines virtuellen Destruktors trägt dazu bei, sicherzustellen, dass der richtige Destruktor aufgerufen wird, wenn Instanzen abgeleiteter Klassen gelöscht werden.

- **Inline**

  Generiert sowohl den Klassenkonstruktor als auch die Klassendefinition als Inlinefunktionen in der Headerdatei.

- **Verwaltet**

  Wenn diese Option ausgewählt ist, werden eine verwaltete Klasse und Headerdatei hinzugefügt. Wenn diese Option nicht ausgewählt ist, werden eine native Klasse und Headerdatei hinzugefügt.
