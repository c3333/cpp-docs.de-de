---
title: Klassen für einfache Datentypen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365400"
---
# <a name="simple-data-type-classes"></a>Klassen für einfache Datentypen

Die folgenden Klassen kapseln Zeichnungskoordinaten, Zeichenfolgen sowie Zeit- und Datumsinformationen, sodass Die C++-Syntax bequem verwendet werden kann. Diese Objekte werden häufig als Parameter für die Memberfunktionen von Windows-Klassen in der Klassenbibliothek verwendet. Da `CPoint` `CSize`, `CRect` und den **POINT**-, **SIZE-** und **RECT-Strukturen** im Windows SDK entsprechen, können Sie Objekte dieser C++-Klassen überall dort verwenden, wo Sie diese C-Sprache-Strukturen verwenden können. Die Klassen stellen über ihre Memberfunktionen nützliche Schnittstellen bereit. `CStringT`bietet sehr flexible dynamische Zeichenketten. `CTime`, `COleDateTime` `CTimeSpan`, `COleTimeSpan` und stellen Zeit- und Datumswerte dar. Weitere Informationen zu diesen Klassen finden Sie im Artikel [Datum und Uhrzeit](../atl-mfc-shared/date-and-time.md).

Die Klassen, die`COle`mit " beginnen, sind Kapseln von Datentypen, die von OLE bereitgestellt werden. Diese Datentypen können in Windows-Programmen verwendet werden, unabhängig davon, ob andere OLE-Features verwendet werden.

[CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Enthält Zeichenfolgen.

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Enthält absolute Zeit- und Datumswerte.

[Coledatetime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **DATE**. Stellt Datums- und Uhrzeitwerte dar.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Enthält relative Zeit- und Datumswerte.

[ColedateTimespan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Enthält `COleDateTime` relative Werte, z. `COleDateTime` B. die Differenz zwischen zwei Werten.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Hält Koordinatenpaare (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Hält Abstand, relative Positionen oder gekoppelte Werte.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Enthält Koordinaten von rechteckigen Bereichen.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Stellt die Funktionalität der Windows-Abbildliste bereit. Bildlisten werden mit Listensteuerelementen und Struktursteuerelementen verwendet. Sie können auch zum Speichern und Archivieren eines Satzes von Bitmaps gleicher Größe verwendet werden.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **VARIANT**. Daten in **VARIANT**s können in vielen Formaten gespeichert werden.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **CURRENCY**, ein Festkomma-Arithmetiktyp, mit 15 Ziffern vor dem Dezimaltrennzeichen und 4 Ziffern danach.

> [!NOTE]
> `CRect`, `CSize`und `CPoint` sind in ATL- oder MFC-Anwendungen einsetzbar. Darüber hinaus `CStringT` bietet eine MFC-unabhängige `CString`-like-Klasse. Weitere Informationen zu freigegebenen Dienstprogrammklassen finden Sie unter [Freigegebene Klassen](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../mfc/class-library-overview.md)
