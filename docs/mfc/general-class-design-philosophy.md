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
ms.openlocfilehash: cfad635c2a826c6f57e2e1513d753a4083494dee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618781"
---
# <a name="general-class-design-philosophy"></a>Allgemeine Prinzipien für den Klassenentwurf

Microsoft Windows wurde so lange entwickelt, bevor die C++-Sprache beliebt wurde. Da tausende von Anwendungen die Programmierschnittstelle für die Windows-Anwendungsprogrammierung (API) von C verwenden, wird diese Schnittstelle für die spätere Zukunft beibehalten. Eine beliebige C++-Windows-Schnittstelle muss daher zusätzlich zu der prozeduralen Programmiersprache C-Sprache erstellt werden. Dadurch wird sichergestellt, dass C++-Anwendungen mit C-Anwendungen koexistieren können.

Der Microsoft Foundation Class-Bibliothek ist eine objektorientierte Schnittstelle zu Windows, die die folgenden Entwurfs Ziele erfüllt:

- Deutliche Reduzierung des Aufwands zum Schreiben einer Anwendung für Windows.

- Ausführungsgeschwindigkeit, vergleichbar mit der der C-Programmiersprache API.

- Minimaler Code Größen Aufwand.

- Die Möglichkeit, eine beliebige Windows C-Funktion direkt aufzurufen.

- Einfachere Konvertierung vorhandener C-Anwendungen in C++.

- Die Möglichkeit, von der vorhandenen Basis der Programmiersprache der Programmiersprache C zu nutzen.

- Einfachere Verwendung der Windows-API mit C++ als bei C.

- Es ist einfacher, noch leistungsstarke Abstraktionen komplexer Features wie ActiveX-Steuerelemente, Datenbankunterstützung, Druck, Symbolleisten und Status leisten zu verwenden.

- Echte Windows-API für C++, die effektiv C++-Sprachfunktionen verwendet.

Weitere Informationen zum Entwerfen der MFC-Bibliothek finden Sie unter:

- [Das Anwendungs Framework](application-framework.md)

- [Beziehung zum C-Sprachen-API](relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
