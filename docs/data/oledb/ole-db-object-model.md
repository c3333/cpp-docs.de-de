---
title: OLE DB-Objektmodell
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369800"
---
# <a name="ole-db-object-model"></a>OLE DB-Objektmodell

Das OLE DB-Objektmodell besteht aus den folgenden Objekten oder Komponenten. Mit den ersten vier aufgelisteten Objekten oder Komponenten (Datenquellen, Sitzungen, Befehle und Rowsets) können Sie eine Verbindung zu einer Datenquelle herstellen und diese anzeigen. Der Rest, beginnend mit Accessoren, bezieht sich auf die Arbeit mit den Daten, wenn sie angezeigt werden.

## <a name="data-sources"></a>Projektmappen-Explorer

Mit Datenquellenobjekten können Sie eine Verbindung zu einer Datenquelle herstellen, z. B. einer Datei oder einem DBMS. Ein Datenquellenobjekt erstellt und verwaltet die Verbindung und enthält Berechtigungen und Authentifizierungsinformationen (z. B. Anmeldename und Kennwort). Ein Datenquellenobjekt kann eine oder mehrere Sitzungen erstellen.

## <a name="sessions"></a>Sitzungen

Eine Sitzung verwaltet eine bestimmte Interaktion mit der Datenquelle, um Daten abzufragen und abzurufen. Jede Sitzung ist eine einzelne Transaktion. Eine Transaktion ist eine unteilbare Arbeitseinheit, die durch den ACID-Test definiert wird. Eine Definition von ACID finden Sie unter [Transaktionen](#vcconoledbcomponents_transactions).

Sitzungen erledigen wichtige Aufgaben, z. B. das Öffnen von Rowsets und das Zurückgeben des Datenquellenobjekts, das es erstellt hat. Sitzungen können auch Metadaten oder Informationen über die Datenquelle selbst zurückgeben (z. B. Tabelleninformationen).

Eine Sitzung kann einen oder mehrere Befehle erstellen.

## <a name="commands"></a>Befehle

Befehle führen einen Textbefehl aus, z. B. eine SQL-Anweisung. Wenn der Textbefehl ein Rowset angibt, z. B. eine SQL **SELECT-Anweisung,** erstellt der Befehl das Rowset.

Ein Befehl ist einfach ein Container für einen Textbefehl, bei dem es sich um eine Zeichenfolge (z. B. eine SQL-Anweisung) handelt, die von einem Consumer an ein Datenquellenobjekt zur Ausführung durch den zugrunde liegenden Datenspeicher des Anbieters übergeben wird. In der Regel ist der Textbefehl eine SQL **SELECT-Anweisung** (in diesem Fall erstellt der Befehl automatisch ein Rowset, da SQL **SELECT** ein Rowset angibt).

## <a name="rowsets"></a>Rowsets

Rowsets zeigen Daten im tabellarischen Format an. Ein Index ist ein Sonderfall für ein Rowset. Sie können Rowsets aus der Sitzung oder dem Befehl erstellen.

### <a name="schema-rowsets"></a>Schemarowsets

Schemas verfügen über Metadaten (Strukturinformationen) zu einer Datenbank. Schemarowsets sind Rowsets mit Schemainformationen. Einige OLE DB-Anbieter für DBMS unterstützen Schemarowset-Objekte. Weitere Informationen zu Schemarowsets finden Sie unter [Abrufen von Metadaten mit Schemarowsets](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) und Schema [Rowset-Klassen und Typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Objekte anzeigen

Ein Ansichtsobjekt definiert eine Teilmenge der Zeilen und Spalten aus einem Rowset. Es hat keine eigenen Daten. Ansichtsobjekte können keine Daten aus mehreren Rowsets kombinieren.

## <a name="accessors"></a>Accessoren

Nur OLE DB verwendet das Konzept der Accessoren. Ein Accessor beschreibt, wie Daten in einem Consumer gespeichert werden. Es verfügt über eine Reihe von Bindungen (eine so genannte Spaltenzuordnung) zwischen Rowsetfeldern (Spalten) und Datenmembern, die Sie im Consumer deklarieren.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Transaktionen

Transaktionsobjekte werden verwendet, wenn geschachtelte Transaktionen auf einer anderen Ebene als der niedrigsten Ebene übertragen oder abgebrochen werden. Eine Transaktion ist eine unteilbare Arbeitseinheit, die durch den ACID-Test definiert wird. ACID steht für:

- Atomizität, kann nicht in kleinere Arbeitseinheiten unterteilt werden

- Parallelität kann mehrere Transaktionen gleichzeitig auftreten

- Isolation hat eine Transaktion nur begrenzte Kenntnisse über Änderungen, die von einer anderen

- Haltbarkeit, die Transaktion nimmt permanente Änderungen vor

## <a name="enumerators"></a>Enumeratoren

Enumeratoren suchen nach verfügbaren Datenquellen und anderen Enumeratoren. Benutzer, die nicht für eine bestimmte Datenquelle angepasst sind, verwenden Enumeratoren, um nach einer Datenquelle zu suchen.

Ein Stammenumerator, der im Microsoft Data Access SDK ausgeliefert wird, durchläuft die Registrierung auf der Suche nach Datenquellen und anderen Enumeratoren. Andere Enumeratoren durchlaufen die Registrierung oder suchen auf anbieterspezifische Weise.

## <a name="errors"></a>Errors

Jede Schnittstelle auf einem OLE DB-Objekt kann Fehler generieren. Fehler enthalten zusätzliche Informationen zu einem Fehler, einschließlich eines optionalen benutzerdefinierten Fehlerobjekts. Diese Informationen werden in einem HRESULT gespeichert.

## <a name="notifications"></a>Benachrichtigungen

Benachrichtigungen werden von Gruppen kooperierender Verbraucher verwendet, die ein Rowset gemeinsam nutzen (wobei Freigabe bedeutet, dass davon ausgegangen wird, dass die Verbraucher innerhalb derselben Transaktion arbeiten). Benachrichtigungen ermöglichen es kooperierenden Verbrauchern, die ein Rowset gemeinsam nutzen, über Aktionen im Rowset informiert zu werden, die von ihren Kollegen ausgeführt werden.

## <a name="see-also"></a>Siehe auch

[OLE DB Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB Programming Übersicht](../../data/oledb/ole-db-programming-overview.md)
