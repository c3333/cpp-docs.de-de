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
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442035"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Zwei Möglichkeiten zur Erstellung eines CArchive-Objekts

Es gibt zwei Möglichkeiten, ein `CArchive` Objekt zu erstellen:

- [Implizites Erstellen eines CArchive-Objekts über das Framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Explizite Erstellung eines CArchive-Objekts](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Implizites Erstellen eines CArchive-Objekts über das Framework

Die häufigste und einfachste Methode besteht darin, dass das Framework im Auftrag der Befehle "Speichern", "Speichern unter" und "Öffnen" im Menü "Datei" ein `CArchive` Objekt für Ihr Dokument erstellt.

Das Framework führt Folgendes aus, wenn der Benutzer der Anwendung im Menü Datei den Befehl Speichern unter ausgibt:

1. Zeigt das Dialogfeld **Speichern** unter an und ruft den Dateinamen des Benutzers ab.

1. Öffnet die Datei, die vom Benutzer als `CFile` Objekt bezeichnet wird.

1. Erstellt ein `CArchive` Objekt, das auf dieses `CFile` Objekt zeigt. Beim Erstellen des `CArchive` Objekts legt das Framework den Modus auf "Store" (schreiben, serialisieren) fest, anstatt auf "Laden" (lesen, Deserialisieren).

1. Ruft die `Serialize` Funktion auf, die in der von `CDocument`abgeleiteten Klasse definiert ist, und übergibt ihr einen Verweis auf das `CArchive`-Objekt.

Die `Serialize` Funktion Ihres Dokuments schreibt dann Daten in das `CArchive` Objekt, wie in Kürze erläutert. Bei der Rückgabe von der `Serialize` Funktion zerstört das Framework das `CArchive`-Objekt und dann das `CFile`-Objekt.

Wenn Sie das Framework also das `CArchive` Objekt für das Dokument erstellen lassen, müssen Sie lediglich die `Serialize` Funktion des Dokuments implementieren, die Schreib-und Lesevorgänge aus dem Archiv durchführen soll. Sie müssen auch `Serialize` für alle `CObject`abgeleiteten Objekte implementieren, die die `Serialize` Funktion des Dokuments wiederum direkt oder indirekt serialisieren.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Explizite Erstellung eines CArchive-Objekts

Neben dem Serialisieren eines Dokuments über das Framework gibt es auch andere Situationen, in denen Sie möglicherweise ein `CArchive` Objekt benötigen. Beispielsweise können Sie Daten in und aus der Zwischenablage serialisieren, die durch ein `CSharedFile`-Objekt dargestellt wird. Oder Sie möchten eine Benutzeroberfläche verwenden, um eine andere Datei als die des Frameworks zu speichern. In diesem Fall können Sie explizit ein `CArchive` Objekt erstellen. Dies erfolgt auf die gleiche Weise wie das Framework, indem Sie das folgende Verfahren verwenden.

#### <a name="to-explicitly-create-a-carchive-object"></a>So erstellen Sie explizit ein CArchive-Objekt

1. Erstellen Sie ein `CFile` Objekt oder ein Objekt, das von `CFile`abgeleitet ist.

1. Übergeben Sie das `CFile`-Objekt an den Konstruktor für `CArchive`, wie im folgenden Beispiel gezeigt:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Das zweite Argument für den `CArchive`-Konstruktor ist ein Enumerationswert, der angibt, ob das Archiv zum Speichern oder Laden von Daten in die oder aus der Datei verwendet wird. Die `Serialize`-Funktion eines Objekts überprüft diesen Zustand durch Aufrufen der `IsStoring`-Funktion für das Archive-Objekt.

Wenn Sie mit dem Speichern oder Laden von Daten in das oder aus dem `CArchive` Objekt fertig sind, schließen Sie es. Obwohl die Objekte `CArchive` (und `CFile`) das Archiv (und die Datei) automatisch schließen, empfiehlt es sich, dies explizit zu tun, da dadurch die Wiederherstellung von Fehlern vereinfacht wird. Weitere Informationen zur Fehlerbehandlung finden Sie im Artikel [Ausnahmen: abfangen und Löschen von Ausnahmen](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>So schließen Sie das CArchive-Objekt

1. Im folgenden Beispiel wird veranschaulicht, wie das `CArchive` Objekt geschlossen wird:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
