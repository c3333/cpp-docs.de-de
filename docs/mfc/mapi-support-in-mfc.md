---
title: MAPI-Unterstützung in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357001"
---
# <a name="mapi-support-in-mfc"></a>MAPI-Unterstützung in MFC

MFC bietet Unterstützung für eine Teilmenge der Microsoft Messaging Application `CDocument`Program Interface (MAPI) in der Klasse . Insbesondere `CDocument` verfügt member funktionen, die bestimmen, ob E-Mail-Unterstützung auf dem Computer des Endbenutzers vorhanden ist, und, wenn ja, einen Befehl "E-Mail senden" aktivieren, dessen Standardbefehls-ID ID_FILE_SEND_MAIL ist. Die MFC-Handlerfunktion für diesen Befehl ermöglicht es dem Benutzer, ein Dokument per E-Mail zu senden.

> [!TIP]
> Obwohl MFC nicht den gesamten MAPI-Funktionssatz kapselt, können Sie MAPI-Funktionen weiterhin direkt aufrufen, ebenso wie Sie Win32-API-Funktionen direkt aus MFC-Programmen aufrufen können.

Die Bereitstellung des Befehls E-Mail senden in Ihrer Anwendung ist sehr einfach. MFC stellt die Implementierung bereit, um `CDocument`ein Dokument (d. h. ein -abgeleitetes Objekt) als Anlage zu verpacken und als E-Mail zu senden. Diese Anlage entspricht einem Dateispeicherbefehl, der den Inhalt des Dokuments in der E-Mail-Nachricht speichert (serialisiert). Diese Implementierung fordert den E-Mail-Client auf dem Computer des Benutzers auf, dem Benutzer die Möglichkeit zu geben, die E-Mail zu adressieren und der E-Mail-Nachricht Betreff- und Nachrichtentext hinzuzufügen. Benutzer sehen die Benutzeroberfläche ihrer vertrauten E-Mail-Anwendung. Diese Funktionalität wird `CDocument` von zwei `OnFileSendMail` `OnUpdateFileSendMail`Memberfunktionen bereitgestellt: und .

MAPI muss die Datei lesen, um die Anlage zu senden. Wenn die Anwendung ihre Datendatei `OnFileSendMail` während eines Funktionsaufrufs geöffnet hält, muss die Datei mit einem Freigabemodus geöffnet werden, der mehreren Prozessen den Zugriff auf die Datei ermöglicht.

> [!NOTE]
> Eine übergeordnete Version `OnFileSendMail` von `COleDocument` for class verarbeitet zusammengesetzte Dokumente korrekt.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>So implementieren Sie einen Befehl E-Mail senden mit MFC

1. Verwenden Sie den Visuellen C++-Menüeditor, um ein Menüelement hinzuzufügen, dessen Befehls-ID ID_FILE_SEND_MAIL ist.

   Diese Befehls-ID wird vom Framework in AFXRES bereitgestellt. H. Der Befehl kann jedem Menü hinzugefügt werden, wird aber normalerweise dem **Menü Datei** hinzugefügt.

1. Fügen Sie der Nachrichtenzuordnung Ihres Dokuments manuell Folgendes hinzu:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Diese Meldungszuordnung funktioniert für `CDocument` ein `COleDocument` Dokument, das von einem der beiden Oder- es nimmt die richtige Basisklasse in beiden Fällen, obwohl die Meldungszuordnung in der abgeleiteten Dokumentklasse ist.

1. Erstellen Sie Ihre Anwendung.

Wenn E-Mail-Unterstützung verfügbar ist, `OnUpdateFileSendMail` aktiviert MFC Ihren `OnFileSendMail`Menüpunkt mit und verarbeitet ihn anschließend mit . Wenn der E-Mail-Support nicht verfügbar ist, entfernt MFC ihr Menüelement automatisch, sodass es vom Benutzer nicht angezeigt wird.

> [!TIP]
> Anstatt Meldungszuordnungseinträge wie zuvor beschrieben manuell hinzuzufügen, können Sie den [Klassenklassen-Assistenten](reference/mfc-class-wizard.md) verwenden, um Nachrichten Funktionen zuzuordnen. Weitere Informationen finden Sie unter [Zuordnen von Nachrichten zu Funktionen](../mfc/reference/mapping-messages-to-functions.md).

Weitere Informationen finden Sie in der [MAPI-Übersicht.](../mfc/mapi.md)

Weitere Informationen zu `CDocument` den Memberfunktionen, die MAPI aktivieren, finden Sie unter:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Siehe auch

[MAPI](../mfc/mapi.md)
