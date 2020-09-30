---
title: Erstellen eines einfachen Consumers
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 0b142a73f66a796f3e22bae0aeacb88dc018aea9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501869"
---
# <a name="creating-a-simple-consumer"></a>Erstellen eines einfachen Consumers

::: moniker range="vs-2019"

Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Consumers ohne Assistent](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Verwenden Sie den **ATL-Projekt-Assistenten** und den **ATL-OLE DB-Consumer-Assistenten**, um einen OLE DB-Vorlagenconsumer zu generieren.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>So erstellen Sie eine Konsolenanwendung für einen OLE DB-Consumer

1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Klicken Sie im Bereich **Projekttypen** auf den Ordner **Installiert** > **Visual C++** > **Windows Desktop**, und klicken Sie dann im Bereich **Templates** auf das Symbol **Windows Desktop-Assistent**. Geben Sie im Feld **Name** den Namen Ihres Projekts ein, z.B. *MyCons*.

1. Klicken Sie auf **OK**.

   Der **Windows-Desktopprojekt**-Assistent wird angezeigt.

1. Wählen Sie auf der Seite **Anwendungseinstellungen** die Option **Konsolenanwendung** und aus, und klicken Sie dann auf **Allgemeine Headerdateien hinzufügen für ATL**.

1. Klicken Sie auf **OK**, um den Assistenten zu schließen und das Projekt zu generieren.

Verwenden Sie als Nächstes den **ATL-OLE DB-Consumer-Assistenten**, um ein OLE DB-Consumerobjekt hinzuzufügen.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>So erstellen Sie einen Consumer mit dem ATL-OLE DB-Consumer-Assistenten

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das `MyCons` Projekt.

1. Klicken Sie im Kontextmenü auf **Hinzufügen**, und klicken Sie danach auf **Neues Element**.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Klicken Sie im Bereich **Kategorien** auf **Installiert** > **Visual C++** > **ATL**. Klicken Sie im Bereich **Vorlagen** auf das Symbol **ATL-OLE DB-Consumer**, und klicken Sie dann auf **Hinzufügen**.

   Der **ATL-OLE DB-Consumer-Assistent** wird angezeigt.

1. Klicken Sie auf die Schaltfläche **Datenquelle**.

   Das Dialogfeld **Datenverknüpfungseigenschaften** wird angezeigt.

1. Gehen Sie im Dialogfeld **Datenverknüpfungseigenschaften** folgendermaßen vor:

   1. Geben Sie auf der Registerkarte **Anbieter** einen OLE DB-Anbieter an.

   1. Geben Sie auf der Registerkarte **Verbindung** die erforderlichen Informationen an, wie z.B. den Servernamen, die Anmelde-ID und das Kennwort für Ihre Datenquelle und Datenbank auf dem Server.

      > [!NOTE]
      > Es besteht ein Sicherheitsproblem mit dem Feature **Kennwortspeicherung zulassen** im Dialogfeld **Datenverknüpfungseigenschaften**. In **Geben Sie Informationen**ein, um sich beim Server anzumelden, gibt es zwei Options Felder: Verwenden Sie die **integrierte Sicherheit von Windows NT** , und **verwenden Sie einen bestimmten Benutzernamen und ein Kennwort**.

      > [!NOTE]
      > Wenn Sie **Bestimmten Benutzernamen und ein Kennwort verwenden** aktivieren, erhalten Sie die Möglichkeit zur Speicherung des Kennworts (über das Kontrollkästchen **Kennwortspeicherung zulassen**). Diese Option ist jedoch nicht sicher. Es wird empfohlen, die Option **Integrierte Sicherheit von Windows NT verwenden** auszuwählen. Diese Option verwendet Windows NT, um Ihre Identität zu überprüfen.

      > [!NOTE]
      > Wenn Sie die integrierte Sicherheit von Windows nicht verwenden können, sollten Sie eine Middle-Tier-Anwendung verwenden, um den Benutzer zur Eingabe des Kennworts aufzufordern oder das Kennwort anstatt im Quellcode an einem Ort zu speichern, der mit Sicherheitsmechanismen geschützt ist.

   1. Nach dem Auswählen des Anbieters und weiteren Einstellungen klicken Sie auf **Verbindung testen**, um die Einstellungen, die Sie auf den vorherigen Dialogfeldseiten ausgewählt haben, zu überprüfen. Wenn im Feld **Ergebnisse** die Meldung `Test connection succeeded` angezeigt wird, klicken Sie auf **OK**, um die Datenverknüpfung zu erstellen.

   Das Dialogfeld **Datenbankobjekt auswählen** wird angezeigt.

1. Verwenden Sie das Struktursteuerelement, um eine Tabelle, eine Sicht oder eine gespeicherte Prozedur auszuwählen. Wählen Sie für dieses Beispiel die Tabelle `Products` aus der Datenbank `Northwind` aus.

1. Klicken Sie auf **OK**. Damit kehren Sie zum **ATL-OLE DB-Consumer-Assistenten** zurück.

1. Der Assistent vervollständigt die Namen für `Class` und die **.h-Datei** basierend auf dem Namen der Tabelle, Sicht oder gespeicherten Prozedur, die Sie ausgewählt haben. Sie können diese Namen bearbeiten, wenn Sie möchten.

1. Deaktivieren Sie das Kontrollkästchen **Attributiert**, sodass der Assistent den Consumercode mithilfe von [OLE DB-Vorlagenklassen](../../data/oledb/ole-db-consumer-templates-reference.md) anstatt mit den standardmäßigen [OLE DB-Consumerattributen](../../windows/attributes/ole-db-consumer-attributes.md) erstellt.

1. Wählen Sie unter **Typ** den Eintrag **Befehl** aus.

   Der Assistent erstellt einen [CCommand](../../data/oledb/ccommand-class.md)-basierten Consumer, wenn Sie **Befehl** auswählen, oder einen [CTable](../../data/oledb/ctable-class.md)-basierten Consumer, wenn Sie **Tabelle** auswählen. Die Tabellen- bzw. Befehlsklasse ist nach dem ausgewählten Objekt benannt, aber Sie können den Namen bearbeiten.

1. Lassen Sie im Bereich **Unterstützung** die Kontrollkästchen **Ändern**, **Einfügen** und **Löschen** deaktiviert.

   Aktivieren Sie die Kontrollkästchen **Ändern**, **Einfügen** und **Löschen**, um das Ändern, Einfügen und Löschen von Datensätzen im Rowset zu unterstützen. Weitere Informationen zum Schreiben von Daten in den Datenspeicher finden Sie unter [Aktualisieren von Rowsets](../../data/oledb/updating-rowsets.md).

1. Klicken Sie auf **Fertig stellen**, um den Consumer zu erstellen.

Der Assistent generiert eine Befehlsklasse und eine Benutzerdatensatzklasse, wie in [Vom Consumer-Assistenten generierte Klassen](../../data/oledb/consumer-wizard-generated-classes.md) gezeigt. Die Befehlsklasse weist den Namen auf, den Sie im Assistenten im Feld `Class` eingeben (in diesem Fall `CProducts`), und der Name der Benutzerdatensatzklasse weist die Form „*ClassName*-Accessor“ auf (in diesem Fall `CProductsAccessor`).

> [!NOTE]
> Der Assistent fügt die folgende Zeile in `Products.h` ein:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Diese Zeile verhindert, dass die Consumeranwendung kompiliert wird, und erinnert Sie daran, die Verbindungszeichenfolge für hartcodierte Kennwörter zu überprüfen. Nach dem Überprüfen der Verbindungszeichenfolge können Sie diese Codezeile entfernen.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines OLE DB Consumers mithilfe eines Assistenten](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
