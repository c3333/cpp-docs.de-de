---
title: DATUM-Typ
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
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317920"
---
# <a name="date-type"></a>DATUM-Typ

Der DATE-Typ wird mit einer 8-Byte-Gleitkommanummer implementiert. Tage werden durch ganze Zahlenstufen dargestellt, beginnend mit dem 30. Dezember 1899, Mitternacht als Zeit Null. Stundenwerte werden als absolute Werte der Stellen hinter dem Dezimalpunkt dargestellt. Die folgende Tabelle veranschaulicht mehrere Datumsangaben zusammen mit ihrem numerischen Äquivalent vom DATUMstyp:

|Datum und Uhrzeit|Darstellung|
|-------------------|--------------------|
|30. Dezember 1899, Mitternacht|0.00|
|1. Januar 1900, Mitternacht|2.00|
|4. Januar 1900, Mitternacht|5.00|
|4. Januar 1900, 6 Uhr|5.25|
|4. Januar 1900, 12 Uhr|5.50|
|4. Januar 1900, 21.00 Uhr|5.875|

Der DATUMstyp DATE sowie `COleDateTime` die Klasse stellen Datums- und Uhrzeitangaben als klassische Zahlenzeile dar. Die `COleDateTime` Klasse enthält mehrere Methoden zum Bearbeiten von DATE-Werten, einschließlich der Konvertierung in und aus anderen gängigen Datumsformaten.

Bei der Arbeit mit diesen Datums- und Uhrzeitformaten in Automation sind folgende Punkte zu beachten:

- Datumsangaben werden in ortszeit angegeben. Die Synchronisierung muss manuell durchgeführt werden, wenn Sie mit Datumsangaben in verschiedenen Zeitzonen arbeiten.

- Die Datumstypen berücksichtigen nicht die Sommerzeit.

- Die Datumszeitachse wird für Datumswerte kleiner als 0 (vor dem 30. Dezember 1899) diskontinuierlich. Dies liegt daran, dass der gesamte Zahlenteil des Datumswerts als signiert behandelt wird, während der Bruchteil als nicht signiert behandelt wird. Mit anderen Worten, der Gesamtenummernteil des Datumswerts kann positiv oder negativ sein, während der Bruchteil des Datumswerts immer zum gesamten logischen Datum addiert wird. Die folgende Tabelle veranschaulicht einige Beispiele:

|Datum und Uhrzeit|Darstellung|
|-------------------|--------------------|
|27. Dezember 1899, Mitternacht|-3.00|
|28. Dezember 1899, 12.00 Uhr|-2.50|
|28. Dezember 1899, Mitternacht|-2.00|
|29. Dezember 1899, Mitternacht|-1.00|
|30. Dezember 1899, 18.00 Uhr|-0.75|
|30. Dezember 1899, 12.00 Uhr|-0.50|
|30. Dezember 1899, 6 Uhr|-0.25|
|30. Dezember 1899, Mitternacht|0.00|
|30. Dezember 1899, 6 Uhr|0,25|
|30. Dezember 1899, 12.00 Uhr|0,50|
|30. Dezember 1899, 18.00 Uhr|0.75|
|31. Dezember 1899, Mitternacht|1.00|
|1. Januar 1900, Mitternacht|2.00|
|1. Januar 1900, 12 Uhr|2.50|
|2. Januar 1900, Mitternacht|3.00|

> [!CAUTION]
> Da 6:00 Uhr immer durch einen Bruchwert 0,25 dargestellt wird, unabhängig davon, ob die ganze Zahl, die den Tag darstellt, positiv (nach dem 30. Dezember 1899) oder negativ (vor dem 30. Dezember 1899) ist, würde ein einfacher Gleitkommavergleich fälschlicherweise jedes DATUM sortieren, das 6:00 Uhr an einem Tag vor dem 30.12.1899 darstellt, als *ein* DATUM, das 7:00 Uhr am selben Tag darstellt.

Weitere Informationen zu Problemen im `COleDateTime` Zusammenhang mit dem DATUM und den Typen finden Sie unter [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) and [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Siehe auch

[Datum und Uhrzeit](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime-Klasse](../atl-mfc-shared/reference/coledatetime-class.md)
