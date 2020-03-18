---
title: Allgemeine Prinzipien für den Klassenentwurf
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441187"
---
# <a name="general-class-design-philosophy"></a>Allgemeine Prinzipien für den Klassenentwurf

Microsoft Windows wurde schon lange entwickelt, C++ bevor die Sprache populär wurde. Da tausende von Anwendungen die Programmierschnittstelle für die Windows-Anwendungsprogrammierung (API) von C verwenden, wird diese Schnittstelle für die spätere Zukunft beibehalten. Eine C++ beliebige Windows-Schnittstelle muss daher auf der prozeduralen C-Language-API erstellt werden. Dadurch wird sicher C++ gestellt, dass Anwendungen mit C-Anwendungen koexistieren können.

Der Microsoft Foundation Class-Bibliothek ist eine objektorientierte Schnittstelle zu Windows, die die folgenden Entwurfs Ziele erfüllt:

- Deutliche Reduzierung des Aufwands zum Schreiben einer Anwendung für Windows.

- Ausführungsgeschwindigkeit, vergleichbar mit der der C-Programmiersprache API.

- Minimaler Code Größen Aufwand.

- Die Möglichkeit, eine beliebige Windows C-Funktion direkt aufzurufen.

- Einfachere Konvertierung vorhandener C-Anwendungen C++in.

- Die Möglichkeit, von der vorhandenen Basis der Programmiersprache der Programmiersprache C zu nutzen.

- Einfachere Verwendung der Windows-API mit C++ als mit C.

- Es ist einfacher, noch leistungsstarke Abstraktionen komplexer Features wie ActiveX-Steuerelemente, Datenbankunterstützung, Druck, Symbolleisten und Status leisten zu verwenden.

- Echte Windows-API C++ für, die C++ tatsächlich Sprachfunktionen verwendet.

Weitere Informationen zum Entwerfen der MFC-Bibliothek finden Sie unter:

- [Das Anwendungs Framework](../mfc/application-framework.md)

- [Beziehung zum C-Sprachen-API](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
