---
title: ODBC-Administrator
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213168"
---
# <a name="odbc-administrator"></a>ODBC-Administrator

Der ODBC-Administrator registriert und konfiguriert die für Sie verfügbaren [Datenquellen](../../data/odbc/data-source-odbc.md) entweder lokal oder über ein Netzwerk. Die Assistenten erstellen mithilfe der vom ODBC-Administrator bereitgestellten Informationen Code in Anwendungen, der Verbindungen zu Datenquellen für den Benutzer aufbaut.

Zur Einrichtung einer ODBC-Datenquelle zur Verwendung mit MFC-ODBC-Datenbankklassen oder DAO-Klassen muss die Datenquelle zunächst registriert und konfiguriert werden. Zum Hinzufügen und Entfernen von Datenquellen verwenden Sie den ODBC-Administrator. Je nach ODBC-Treiber können Sie auch neue Datenquellen erstellen.

Der ODBC-Administrator wird beim Setup installiert. Wenn Sie **benutzerdefinierte** Installation ausgewählt und im Dialogfeld **Daten Bankoptionen** keine ODBC-Treiber ausgewählt haben, müssen Sie Setup erneut ausführen, um die erforderlichen Dateien zu installieren.

Wählen Sie beim Setup die ODBC-Treiber aus, die Sie installieren möchten. Später können Sie mit Setup für Visual C++ zusätzliche Treiber installieren, die in Visual C++ mitgeliefert werden.

Wenn Sie ODBC-Treiber installieren möchten, die nicht in Visual C++ mitgeliefert werden, müssen Sie das Setup ausführen, das mit dem Treiber geliefert wurde.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>So installieren Sie ODBC-Treiber, die in Visual C++ mitgeliefert werden

1. Starten Sie von der Visual C++-CD das Programm Setup.

   Das Begrüßungsdialogfeld von Setup wird angezeigt.

1. Klicken Sie in jedem Dialogfeld so lange auf **weiter** , bis das Dialogfeld **Installationsoptionen** angezeigt wird. Wählen Sie **Benutzer**definiert aus, und klicken Sie auf **weiter**.

1. Deaktivieren Sie alle Kontrollkästchen im Dialogfeld **Microsoft C++ Visual Setup** mit Ausnahme des Kontrollkästchens **Daten Bankoptionen** , und klicken Sie dann auf **Details** , um das Dialogfeld **Daten Bankoptionen** anzuzeigen.

1. Deaktivieren Sie das Kontrollkästchen **Microsoft-Datenzugriffs Objekte** , aktivieren Sie das Kontrollkästchen **Microsoft ODBC-Treiber** , und klicken Sie dann auf **Details**.

   Das Dialogfeld **Microsoft ODBC-Treiber** wird angezeigt.

1. Wählen Sie die Treiber aus, die Sie installieren möchten, und klicken Sie dann zweimal auf **OK** .

1. Klicken Sie in den verbleibenden Dialogfeldern auf **weiter** , um mit der Installation zu beginnen. Setup benachrichtigt Sie, wenn die Installation beendet ist.

Wenn die Treiber installiert sind, können Sie mit dem ODBC-Administrator die Datenquelle konfigurieren. In der Systemsteuerung finden Sie das ODBC-Symbol.

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)
