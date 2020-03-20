---
title: Fragen zum OLE DB-Architekturdesign
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: b481d9948d3055247bd284ca794a0fa65905e21b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544549"
---
# <a name="ole-db-architectural-design-issues"></a>Fragen zum OLE DB-Architekturdesign

> [!NOTE]
> Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

Berücksichtigen Sie die folgenden Fragen, bevor Sie mit Ihrer OLE DB-Anwendung beginnen:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Welche Programmierimplementierung verwenden Sie zum Schreiben Ihrer OLE DB-Anwendung?

Microsoft stellt verschiedene Bibliotheken für diese Aufgabe bereit: eine OLE DB-Vorlagenbibliothek, OLE DB-Attribute und die unformatierten OLE DB-Schnittstellen im OLE DB SDK. Darüber hinaus sind Assistenten vorhanden, die Sie beim Schreiben Ihres Programms unterstützen. Diese Implementierungen werden in [OLE DB-Vorlagen, -Attribute und weitere Implementierungen](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md) beschrieben.

## <a name="do-you-need-to-write-your-own-provider"></a>Müssen Sie einen eigenen Anbieter schreiben?

Die meisten Entwickler müssen keinen eigenen Anbieter schreiben. Microsoft stellt verschiedene Anbieter bereit. Wenn Sie eine Datenverbindung erstellen (z.B. wenn Sie Ihrem Projekt mit dem **ATL-OLE DB-Consumer-Assistenten** einen Consumer hinzugefügt haben), werden im Dialogfeld **Datenverknüpfungseigenschaften** alle verfügbaren Anbieter aufgelistet, die für Ihr System registriert sind. Wenn einer der Anbieter für Ihren eigenen Datenspeicher und die Datenzugriffsanwendung geeignet ist, ist es am einfachsten, einen dieser Anbieter zu verwenden. Wenn Ihr Datenspeicher jedoch in keine dieser Kategorien passt, müssen Sie einen eigenen Anbieter erstellen. Informationen zum Erstellen von Anbietern finden Sie unter [OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Welche Unterstützungsebene wird für Ihren Consumer benötigt?

Einige Consumer sind eher einfach gehalten, andere sind komplex. Die Funktionalität von OLE DB-Objekten wird über Eigenschaften angegeben. Wenn Sie den **ATL-OLE DB-Consumer-Assistenten** zum Erstellen eines Consumers oder den **Assistenten für Datenbankanbieter** zum Erstellen eines Anbieters verwenden, werden die geeigneten Objekteigenschaften für Sie festgelegt, um einen Standardsatz an Funktionen bereitzustellen. Wenn die vom Assistenten generierten Consumer- oder Anbieterklassen aber nicht alle gewünschten Funktionen unterstützen, müssen Sie auf die Schnittstellen für diese Klassen in der [OLE DB-Vorlagenbibliothek](../../data/oledb/ole-db-templates.md) zurückgreifen. Diese Schnittstellen umschließen die unformatierten OLE DB-Schnittstellen und bieten zusätzliche Implementierungen für eine einfachere Verwendung.

Wenn Sie beispielsweise die Daten in einem Rowset aktualisieren möchten, dies aber beim Erstellen des Consumers mit dem Assistenten vergessen haben, können Sie die Funktionalität nachträglich angegeben, indem Sie die Eigenschaften `DBPROP_IRowsetChange` und `DBPROP_UPDATABILITY` für das Befehlsobjekt angeben. Wenn Sie anschließend das Rowset erstellen, verfügt es über die `IRowsetChange`-Schnittstelle.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Verfügen Sie über älteren Code, der eine andere Datenzugriffstechnologie verwendet (ADO, ODBC oder DAO)?

Angesichts der Kombinationsmöglichkeiten hinsichtlich der verwendeten Technologien (z.B. die Verwendung von ADO-Komponenten mit OLE DB-Komponenten und die Migration von ODBC-Code zu OLE DB) würde eine Erläuterung aller Situationen den Rahmen der Visual C++-Dokumentation sprengen. Auf den folgenden Microsoft-Websites sind jedoch viele Artikel zu verschiedenen Szenarien verfügbar:

- [Microsoft Hilfe- und Supportcenter](https://support.microsoft.com/)

- [Technische Artikel zum Microsoft-Datenzugriff – Übersicht](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>Siehe auch

[OLE DB-Programmierung](../../data/oledb/ole-db-programming.md)<br/>
[Übersicht über die OLE DB-Programmierung](../../data/oledb/ole-db-programming-overview.md)
