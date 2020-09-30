---
title: Date-Typ
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 5a6c1e1cca5b2cb978d6af4208377db1a2926357
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502174"
---
# <a name="date-type"></a>Date-Typ

Der Date-Typ wird mit einer 8-Byte-Gleit Komma Zahl implementiert. Tage werden durch ganze Zahlen dargestellt, beginnend mit dem 30. Dezember 1899, Mitternacht als zeitgleich 0 (null). Stundenwerte werden als absolute Werte der Stellen hinter dem Dezimalpunkt dargestellt. In der folgenden Tabelle werden mehrere Datumsangaben zusammen mit der numerischen Date Type-Entsprechung veranschaulicht:

|Datum und Uhrzeit|Darstellung|
|-------------------|--------------------|
|30. Dezember 1899, Mitternacht|0.00|
|1. Januar 1900, Mitternacht|2.00|
|4. Januar 1900, Mitternacht|5.00|
|4. Januar 1900, 6 Uhr|5.25|
|4. Januar 1900 Uhr Mittag|5.50|
|4. Januar 1900, 9 Uhr|5.875|

Der Date-Date-Typ sowie die- `COleDateTime` Klasse stellt Datumsangaben und Uhrzeiten als klassische Zahlen Linie dar. Die `COleDateTime` -Klasse enthält mehrere Methoden zum Bearbeiten von Datums Werten, einschließlich der Konvertierung in und aus anderen gängigen Datumsformaten.

Beachten Sie die folgenden Punkte, wenn Sie mit diesen Datums-und Uhrzeit Formaten in Automation arbeiten:

- Datumsangaben werden in Ortszeit angegeben. die Synchronisierung muss bei der Arbeit mit Datumsangaben in verschiedenen Zeitzonen manuell durchgeführt werden.

- Die Datums Typen berücksichtigen nicht die Sommerzeit.

- Die Datums Zeitachse wird für Datumswerte kleiner als 0 (vor 30. Dezember 1899) diskontinuierlich. Dies liegt daran, dass der ganzzahlige Teil des Datums Werts als signiert behandelt wird, während der Bruch Teil als nicht signiert behandelt wird. Anders ausgedrückt: der ganzzahlige Teil des Datums Werts kann positiv oder negativ sein, während der Bruchteile des Datums Werts immer dem logischen Gesamt Datum hinzugefügt wird. In der folgenden Tabelle werden einige Beispiele veranschaulicht:

|Datum und Uhrzeit|Darstellung|
|-------------------|--------------------|
|27. Dezember 1899, Mitternacht|-3.00|
|28. Dezember 1899 Uhr|-2.50|
|28. Dezember 1899, Mitternacht|-2.00|
|29. Dezember 1899, Mitternacht|-1.00|
|30. Dezember 1899, 6 Uhr|-0.75|
|30. Dezember 1899 Uhr Uhr|-0.50|
|30. Dezember 1899, 6 Uhr|-0.25|
|30. Dezember 1899, Mitternacht|0.00|
|30. Dezember 1899, 6 Uhr|0,25|
|30. Dezember 1899 Uhr Uhr|0.50|
|30. Dezember 1899, 6 Uhr|0,75|
|31. Dezember 1899, Mitternacht|1.00|
|1. Januar 1900, Mitternacht|2.00|
|1. Januar 1900 Uhr Mittag|2,50|
|2. Januar 1900, Mitternacht|3.00|

> [!CAUTION]
> Beachten Sie Folgendes *: da 6:00* am immer durch einen Bruch Wert von 0,25 dargestellt wird, unabhängig davon, ob die ganze Zahl, die den Tag darstellt, positiv ist (nach dem 30. Dezember 1899) oder negativ (vor dem 30. Dezember 1899), würde ein einfacher Gleit Komma Vergleich fälschlicherweise ein beliebiges Datum sortieren, das 6:00 Uhr an einem Tag vor 12/30/1899 darstellt.

Weitere Informationen zu Problemen, die sich auf das Datum und die Typen beziehen, finden Sie `COleDateTime` unter [COleDateTime-Klasse](../atl-mfc-shared/reference/coledatetime-class.md) und [Datum und Uhrzeit: Automatisierungsunterstützung](./date-and-time.md).

## <a name="see-also"></a>Weitere Informationen

[Datum und Uhrzeit](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime-Klasse](../atl-mfc-shared/reference/coledatetime-class.md)
