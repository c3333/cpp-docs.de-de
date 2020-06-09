---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: 0008a2bc433401f3e048b6f5a92cded88114d08e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625554"
---
# <a name="mapi"></a>MAPI

Dieser Artikel beschreibt die Microsoft-Messaging Application Programming Interface (MAPI) für Entwickler von Client Nachrichten Anwendungen. MFC bietet Unterstützung für eine Teilmenge von MAPI in der Klasse, `CDocument` aber nicht die gesamte API. Weitere Informationen finden Sie [unter MAPI-Unterstützung in MFC](mapi-support-in-mfc.md).

MAPI ist eine Reihe von Funktionen, die e-Mail-aktivierte und e-Mail-fähige Anwendungen zum Erstellen, bearbeiten, übertragen und Speichern von e-Mail-Nachrichten verwenden Er bietet Anwendungsentwicklern die Tools zum Definieren des Zwecks und Inhalts von e-Mail-Nachrichten und bietet Ihnen Flexibilität bei der Verwaltung gespeicherter e-Mail-Nachrichten. MAPI bietet auch eine gemeinsame Schnittstelle, die Anwendungsentwickler zum Erstellen von e-Mail-aktivierten und e-Mail-fähigen Anwendungen verwenden können, unabhängig vom zugrunde liegenden Messaging System.

Messaging Clients stellen eine Benutzeroberfläche für die Interaktion mit dem Microsoft Windows-Messaging System (WMS) dar. Diese Interaktion umfasst in der Regel das Anfordern von Diensten von MAPI-kompatiblen Anbietern wie Nachrichten speichern und Adressbüchern.

Weitere Informationen zu MAPI finden Sie in den Artikeln unter Leitfaden in Win32 Messaging (MAPI) des Windows SDK.

## <a name="in-this-section"></a>In diesem Abschnitt

[MAPI-Unterstützung in MFC](mapi-support-in-mfc.md)

## <a name="see-also"></a>Siehe auch

[CDocument:: OnFileSendMail](reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument:: OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument:: OnFileSendMail](reference/coledocument-class.md#onfilesendmail)
