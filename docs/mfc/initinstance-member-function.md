---
title: InitInstance-Memberfunktion
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377199"
---
# <a name="initinstance-member-function"></a>InitInstance-Memberfunktion

Mit dem Windows-Betriebssystem können Sie mehr als eine Kopie oder "Instanz" derselben Anwendung ausführen. `WinMain`ruft [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) jedes Mal auf, wenn eine neue Instanz der Anwendung gestartet wird.

Die `InitInstance` vom MFC-Anwendungs-Assistenten erstellte Standardimplementierung führt die folgenden Aufgaben aus:

- Erstellt als zentrale Aktion die Dokumentvorlagen, die wiederum Dokumente, Ansichten und Rahmenfenster erstellen. Eine Beschreibung dieses Prozesses finden Sie unter Erstellen von [Dokumentvorlagen](../mfc/document-template-creation.md).

- Lädt Standarddateioptionen aus einer .ini-Datei oder der Windows-Registrierung, einschließlich der Namen der zuletzt verwendeten Dateien.

- Registriert eine oder mehrere Dokumentvorlagen.

- Erstellt für eine MDI-Anwendung ein Hauptrahmenfenster.

- Verarbeitet die Befehlszeile, um ein in der Befehlszeile angegebenes Dokument zu öffnen oder ein neues, leeres Dokument zu öffnen.

Sie können Ihren eigenen Initialisierungscode hinzufügen oder den vom Assistenten geschriebenen Code ändern.

> [!NOTE]
> MFC-Anwendungen müssen als Singlethread-Apartment (STA) initialisiert werden. Wenn Sie [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) `InitInstance` in Ihrer Außerkraftsetzung aufrufen, geben Sie COINIT_APARTMENTTHREADED (anstelle COINIT_MULTITHREADED) an.

## <a name="see-also"></a>Siehe auch

[CWinApp: Die Anwendungsklasse](../mfc/cwinapp-the-application-class.md)
