---
title: Zwei Möglichkeiten zur Erstellung eines CArchive-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370956"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Zwei Möglichkeiten zur Erstellung eines CArchive-Objekts

Es gibt zwei Möglichkeiten, ein `CArchive` Objekt zu erstellen:

- [Implizite Erstellung eines CArchive-Objekts über das Framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Explizite Erstellung eines CArchive-Objekts](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Implizite Erstellung eines CArchive-Objekts über das Framework

Die häufigste und einfachste Möglichkeit besteht darin, `CArchive` das Framework ein Objekt für Ihr Dokument im Namen der Befehle Speichern, Speichern unter und Öffnen im Menü Datei erstellen zu lassen.

Hier ist, was das Framework tut, wenn der Benutzer Ihrer Anwendung den Befehl Speichern unter aus dem Menü Datei ausgibt:

1. Stellt das Dialogfeld **Speichern unter** vor und ruft den Dateinamen vom Benutzer ab.

1. Öffnet die vom Benutzer benannte Datei als `CFile` Objekt.

1. Erstellt `CArchive` ein Objekt, `CFile` das auf dieses Objekt verweist. Beim Erstellen `CArchive` des Objekts legt das Framework den Modus auf "speichern" (schreiben, serialisieren) im Gegensatz zu "load" (lesen, deserialisieren).

1. Ruft `Serialize` die in `CDocument`der -derived-Klasse definierte Funktion `CArchive` auf und übergibt ihr einen Verweis auf das Objekt.

Die Funktion `Serialize` Ihres Dokuments schreibt `CArchive` dann Daten in das Objekt, wie in Kürze erläutert. Nach der `Serialize` Rückkehr von Ihrer Funktion `CArchive` zerstört das `CFile` Framework das Objekt und dann das Objekt.

Wenn Sie also zulassen, `CArchive` dass das Framework das Objekt für Ihr Dokument `Serialize` erstellt, müssen Sie nur die Funktion des Dokuments implementieren, die in und aus dem Archiv schreibt und liest. Sie müssen auch `Serialize` für `CObject`alle -abgeleiteten Objekte `Serialize` implementieren, die die Funktion des Dokuments wiederum direkt oder indirekt serialisiert.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>Explizite Erstellung eines CArchive-Objekts

Neben der Serialisierung eines Dokuments über das Framework `CArchive` gibt es auch andere Gelegenheiten, bei denen Sie ein Objekt benötigen. Sie können z. B. Daten in und aus der `CSharedFile` Zwischenablage serialisieren, die durch ein Objekt dargestellt wird. Sie können auch eine Benutzeroberfläche verwenden, um eine Datei zu speichern, die sich von der vom Framework angebotenen unterscheidet. In diesem Fall können Sie `CArchive` explizit ein Objekt erstellen. Sie tun dies auf die gleiche Weise wie das Framework, indem Sie das folgende Verfahren verwenden.

#### <a name="to-explicitly-create-a-carchive-object"></a>So erstellen Sie explizit ein CArchive-Objekt

1. Erstellen `CFile` Sie ein Objekt `CFile`oder ein Objekt, das von abgeleitet wurde.

1. Übergeben `CFile` Sie das Objekt `CArchive`an den Konstruktor für , wie im folgenden Beispiel gezeigt:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Das zweite Argument `CArchive` für den Konstruktor ist ein aufgezählter Wert, der angibt, ob das Archiv zum Speichern oder Laden von Daten in oder aus der Datei verwendet wird. Die `Serialize` Funktion eines Objekts überprüft `IsStoring` diesen Zustand, indem die Funktion für das Archivobjekt aufgerufen wird.

Wenn Sie mit dem Speichern oder `CArchive` Laden von Daten in oder aus dem Objekt fertig sind, schließen Sie sie. Obwohl `CArchive` die `CFile`(und ) Objekte das Archiv (und die Datei) automatisch schließen, ist es sinnvoll, dies explizit zu tun, da dies die Wiederherstellung nach Fehlern vereinfacht. Weitere Informationen zur Fehlerbehandlung finden Sie im Artikel [Ausnahmen: Abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>So schließen Sie das CArchive-Objekt

1. Das folgende Beispiel veranschaulicht, `CArchive` wie das Objekt geschlossen wird:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
