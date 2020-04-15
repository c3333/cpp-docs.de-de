---
title: DAO-Klassen
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373518"
---
# <a name="dao-classes"></a>DAO-Klassen

DAO wird mit Access-Datenbanken verwendet und wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

Diese Klassen arbeiten mit den anderen Anwendungsframeworkklassen, um einfachen Zugriff auf DAO-Datenbanken (Data Access Object) zu gewähren, die dasselbe Datenbankmodul wie Microsoft Visual Basic und Microsoft Access verwenden. Die DAO-Klassen können auch auf eine Vielzahl von Datenbanken zugreifen, für die ODBC-Treiber (Open Database Connectivity) verfügbar sind.

Programme, die DAO-Datenbanken verwenden, `CDaoDatabase` verfügen `CDaoRecordset` über mindestens ein Objekt und ein Objekt.

> [!NOTE]
> Die Visual C++-Umgebung und die Assistenten unterstützen DAO nicht mehr (obwohl die DAO-Klassen enthalten sind und Sie sie weiterhin verwenden können). Microsoft empfiehlt, ODBC für neue MFC-Projekte zu verwenden. Sie sollten DAO nur bei der Verwaltung vorhandener Anwendungen verwenden.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Verwaltet eine benannte, kennwortgeschützte Datenbanksitzung von der Anmeldung bis zur Abmeldung. Die meisten Programme verwenden den Standardarbeitsbereich.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Eine Verbindung zu einer Datenbank, über die Sie die Daten bedienen können.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Stellt eine Gruppe von Datensätzen dar, die aus einer Datenquelle ausgewählt wurden.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Eine Sicht, die Datenbankdatensätze in Steuerelementen anzeigt.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Stellt eine Abfragedefinition dar, die normalerweise in einer Datenbank gespeichert ist.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Stellt die gespeicherte Definition einer Basistabelle oder einer angefügten Tabelle dar.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Stellt eine Ausnahmebedingung dar, die sich aus den DAO-Klassen ergibt.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Unterstützt die Routinen für den DAO-Datensatzfeldaustausch (DAO record field exchange, DFX), die von den DAO-Datenbankklassen verwendet werden. Normalerweise verwenden Sie diese Klasse nicht direkt.

## <a name="related-classes"></a>Verwandte Klassen

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Kapselt ein Handle zum Speicher für ein binäres großes Objekt (BLOB), z. B. eine Bitmap. `CLongBinary`Objekte werden verwendet, um große Datenobjekte zu verwalten, die in Datenbanktabellen gespeichert sind.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **CURRENCY**, ein Festkomma-Arithmetiktyp, mit 15 Ziffern vor dem Dezimaltrennzeichen und 4 Ziffern danach.

[Coledatetime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **DATE**. Stellt Datums- und Uhrzeitwerte dar.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Wrapper für den OLE-Automatisierungstyp **VARIANT**. Daten in **VARIANT**s können in vielen Formaten gespeichert werden.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../mfc/class-library-overview.md)
