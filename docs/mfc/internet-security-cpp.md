---
title: Internetsicherheit (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: ce044014c5c2e13528cea8b982227b0ec8bc03fc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621535"
---
# <a name="internet-security-c"></a>Internetsicherheit (C++)

Die Code Sicherheit ist ein wichtiges Problem für Entwickler und Benutzer von Internet Anwendungen. Es bestehen Risiken: bösartiger Code, Code, der manipuliert wurde, und Code von unbekannten Standorten oder Autoren.

Es gibt zwei grundlegende Ansätze für die Sicherheit bei der Entwicklung für das Internet. Der erste wird als "Sandboxing" bezeichnet. Bei dieser Vorgehensweise ist eine Anwendung auf einen bestimmten Satz von APIs beschränkt und von potenziell gefährlichen, z. b. Datei-e/a-Vorgängen ausgeschlossen, bei denen ein Programm Daten auf dem Computer eines Benutzers zerstören könnte. Die zweite wird mithilfe digitaler Signaturen implementiert. Diese Vorgehensweise wird als "Shrinkwrap" für das Internet bezeichnet. Der Code wird mit der Technologie des privaten Schlüssels/öffentlichen Schlüssels überprüft und signiert. Bevor der Code ausgeführt wird, wird die digitale Signatur überprüft, um sicherzustellen, dass der Code aus einer bekannten authentifizierten Quelle besteht und dass der Code seit der Signierung nicht geändert wurde.

Im ersten Fall Vertrauen Sie darauf, dass die Anwendung keinen Schaden anrichten wird und Sie dem Ursprung der Anwendung vertrauen. Im zweiten werden digitale Signaturen zum Überprüfen der Echtheit verwendet. Digitale Signierung ist ein Industriestandard, der zum Identifizieren und Bereitstellen von Details zum Herausgeber des Codes verwendet wird. Die Technologie basiert auf Standards, einschließlich RSA und X. 509. Browser ermöglichen es Benutzern in der Regel, auszuwählen, ob Sie den Code mit einem unbekannten Ursprung herunterladen und ausführen möchten.

## <a name="see-also"></a>Siehe auch

[MFC-Internetprogrammierungsaufgaben](mfc-internet-programming-tasks.md)<br/>
[Grundlagen der MFC-Internetprogrammierung](mfc-internet-programming-basics.md)
