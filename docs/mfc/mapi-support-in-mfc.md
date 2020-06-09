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
ms.openlocfilehash: 7eff22b2a7b4c838f2967fb5217b9dec96903d0e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625569"
---
# <a name="mapi-support-in-mfc"></a>MAPI-Unterstützung in MFC

MFC bietet Unterstützung für eine Teilmenge der Microsoft Messaging Application Program Interface (MAPI) in der-Klasse `CDocument` . Insbesondere verfügt über Element `CDocument` Funktionen, die bestimmen, ob die e-Mail-Unterstützung auf dem Computer des Endbenutzers vorhanden ist. wenn dies der Fall ist, aktivieren Sie einen Send Mail-Befehl, dessen Standard Befehls-ID ID_FILE_SEND_MAIL. Die MFC-Handlerfunktion für diesen Befehl ermöglicht dem Benutzer das Senden eines Dokuments per elektronischer e-Mail.

> [!TIP]
> Obwohl MFC den gesamten MAPI-Funktions Satz nicht kapist, können Sie MAPI-Funktionen weiterhin direkt aufzurufen, genauso wie Sie Win32-API-Funktionen direkt aus MFC-Programmen abrufen können.

Das Bereitstellen des Befehls "Mail senden" in der Anwendung ist sehr einfach. MFC stellt die-Implementierung bereit, um ein Dokument (d. h. ein von `CDocument` abgeleitetes Objekt) als Anlage zu verpacken und als e-Mail zu senden. Diese Anlage entspricht einem File Save-Befehl, der den Inhalt des Dokuments in der e-Mail-Nachricht speichert (serialisiert). Diese Implementierung ruft den e-Mail-Client auf dem Computer des Benutzers auf, um dem Benutzer die Möglichkeit zu geben, die e-Mail zu adressieren und der e-Mail-Nachricht Betreff und Nachrichtentext hinzuzufügen. Benutzern wird die Benutzeroberfläche der vertrauten Mail Anwendung angezeigt. Diese Funktion wird von zwei Element `CDocument` Funktionen bereitgestellt: `OnFileSendMail` und `OnUpdateFileSendMail` .

MAPI muss die Datei lesen, um die Anlage zu senden. Wenn die Anwendung die Datendatei während eines `OnFileSendMail` Funktions Aufrufes geöffnet hält, muss die Datei mit einem Freigabe Modus geöffnet werden, der mehreren Prozessen den Zugriff auf die Datei ermöglicht.

> [!NOTE]
> Eine über schreibende Version von für die- `OnFileSendMail` Klasse `COleDocument` verarbeitet Verbund Dokumente ordnungsgemäß.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>So implementieren Sie einen Befehl "Mail senden" mit MFC

1. Verwenden Sie den Visual C++ Menü-Editor, um ein Menü Element hinzuzufügen, dessen Befehls-ID ID_FILE_SEND_MAIL ist.

   Diese Befehls-ID wird vom Framework in AFXRES bereitgestellt. Micha. Der Befehl kann einem beliebigen Menü hinzugefügt werden, wird aber normalerweise dem Menü **Datei** hinzugefügt.

1. Fügen Sie der Meldungs Zuordnung Ihres Dokuments manuell Folgendes hinzu:

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Diese Nachrichten Zuordnung funktioniert für ein Dokument, das entweder von `CDocument` oder abgeleitet `COleDocument` ist – die richtige Basisklasse wird in beiden Fällen übernommen, auch wenn sich die Meldungs Zuordnung in der abgeleiteten Dokument Klasse befindet.

1. Erstellen Sie Ihre Anwendung.

Wenn e-Mail-Unterstützung verfügbar ist, aktiviert MFC das Menü Element mit `OnUpdateFileSendMail` und verarbeitet anschließend den Befehl mit `OnFileSendMail` . Wenn die e-Mail-Unterstützung nicht verfügbar ist, wird das Menü Element von MFC automatisch entfernt, sodass es dem Benutzer nicht angezeigt wird.

> [!TIP]
> Anstatt Nachrichten Zuordnungs Einträge wie zuvor beschrieben manuell hinzuzufügen, können Sie den Klassen [Klassen-Assistenten](reference/mfc-class-wizard.md) verwenden, um Nachrichten zu Funktionen zuzuordnen. Weitere Informationen finden Sie unter [Mapping von Nachrichten zu Funktionen](reference/mapping-messages-to-functions.md).

Weitere Informationen finden Sie in der Übersicht über [MAPI](mapi.md) .

Weitere Informationen zu den `CDocument` Member-Funktionen, die MAPI aktivieren, finden Sie unter:

- [CDocument:: OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument:: OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Siehe auch

[MAPI](mapi.md)
