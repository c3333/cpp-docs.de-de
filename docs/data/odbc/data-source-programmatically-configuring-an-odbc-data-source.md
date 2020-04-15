---
title: 'Datenquelle: Programmgesteuertes Konfigurieren einer ODBC-Datenquelle'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358863"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Datenquelle: Programmgesteuertes Konfigurieren einer ODBC-Datenquelle

In diesem Thema wird erläutert, wie ODBC-Datenquellennamen programmgesteuert konfiguriert werden können. Dies ermöglicht es, auf Daten zuzugreifen, ohne den Benutzer dazu zu zwingen, die Namen der Datenquellen explizit mit ODBC-Administrator oder einem anderen Programm anzugeben.

Normalerweise führt ein Benutzer den ODBC-Administrator aus, um eine Datenquelle zu erstellen, wenn das betreffende Datenbankmanagementsystem (DBMS) diese Operation unterstützt.

Beim Anlegen einer Microsoft Access-ODBC-Datenquelle mit ODBC-Administrator haben Sie zwei Möglichkeiten: Sie können entweder eine vorhandene MDB-Datei auswählen oder eine neue MDB-Datei erstellen. Es gibt keine Möglichkeit, eine MDB-Datei von einer MFC-ODBC-Anwendung aus programmgesteuert anzulegen. Wenn es daher für die Anwendung erforderlich ist, Daten in einer Microsoft Access-Datenquelle (.mdb-Datei) zu speichern, benötigen Sie wahrscheinlich eine leere MDB-Datei, auf die Sie bei Bedarf zugreifen oder die Sie kopieren können.

Viele Datenbankmanagementsysteme ermöglichen jedoch das programmgesteuerte Erstellen einer Datenquelle. Einige Datenquellen verwenden eine Verzeichnisangabe für Datenbanken. Als Datenquelle wird also ein Verzeichnis verwendet. Jede Tabelle dieser Datenquelle ist in einer eigenen Datei gespeichert. Im Fall von dBASE ist jede Tabelle in einer eigenen DBF-Datei enthalten. Treiber für andere ODBC-Datenbanken, z. B. Microsoft Access und SQL Server, setzen voraus, dass bestimmte Kriterien erfüllt sind, bevor eine Datenquelle eingerichtet werden kann. Wenn z. B. der SQL Server-ODBC-Treiber verwendet wird, muss ein Computer mit SQL Server eingerichtet sein.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>SQLConfigDataSource-Beispiel

Im folgenden Beispiel `::SQLConfigDataSource` wird die ODBC-API-Funktion verwendet, um eine neue Excel-Datenquelle mit dem Namen New Excel Data Source zu erstellen:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Beachten Sie, dass es sich bei der Datenquelle um ein Verzeichnis handelt (C:\EXCELDIR), dessen Vorhandensein sichergestellt sein muss. Der Excel-Treiber verwendet Verzeichnisse als Datenquellen und Dateien als einzelne Tabellen, und zwar eine Tabelle pro XLS-Datei.

Weitere Informationen zum Erstellen von Tabellen finden Sie unter [Datenquelle: Programmgesteuertes Erstellen einer Tabelle in einer ODBC-Datenquelle](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

In den folgenden Informationen werden die Parameter `::SQLConfigDataSource` erläutert, die an die ODBC-API-Funktion übergeben werden müssen. Um `::SQLConfigDataSource`zu verwenden, müssen Sie die Odbcinst.h-Headerdatei einschließen und die Odbcinst.lib-Importbibliothek verwenden. Außerdem muss die Datei Odbccp32.dll zur Laufzeit im Ausführungspfad gespeichert sein, bzw. für 16 Bits die Datei Odbcinst.dll.

Sie können einen ODBC-Datenquellennamen mit ODBC-Administrator oder einem ähnlichen Dienstprogramm erstellen. Manchmal ist es jedoch besser, einen Datenquellennamen direkt aus einer Anwendung heraus anzulegen. So wird der Zugriff ermöglicht, ohne dass der Benutzer ein separates Hilfsprogramm ausführen muss.

ODBC-Administrator, der normalerweise in der Windows-Systemsteuerung installiert ist, erstellt eine neue Datenquelle, indem er Einträge in die Windows-Registrierung schreibt, bzw. bei 16 Bits in die Datei Odbc.ini. Der ODBC-Treiber-Manager verwendet diese Datei, um die benötigten Informationen über die Datenquelle zu ermitteln. Es ist wichtig zu wissen, welche Informationen in der Registrierung platziert werden `::SQLConfigDataSource`müssen, da Sie sie mit dem Aufruf von versorgen müssen.

Obwohl diese Informationen direkt in die `::SQLConfigDataSource`Registrierung geschrieben werden können, ohne zu verwenden, stützt sich jede Anwendung, die dies tut, auf die aktuelle Technik, die der Treiber-Manager verwendet, um seine Daten zu verwalten. Sollte eine spätere Version von ODBC-Treiber-Manager die Datensatzverwaltung für Datenquellen in einer anderen Weise implementieren, wäre eine solche Anwendung nicht mehr funktionsfähig. Soweit möglich, sollte immer eine API-Funktion verwendet werden. Beispielsweise ist Ihr Code von 16 Bit bis 32 `::SQLConfigDataSource` Bit portierbar, wenn Sie die Funktion verwenden, da die Funktion korrekt in die Datei Odbc.ini oder in die Registrierung schreibt.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigDataSource-Parameter

Im Folgenden werden die `::SQLConfigDataSource` Parameter der Funktion erläutert. Ein Großteil der Informationen stammt aus der ODBC API *Programmer-Referenz,* die mit Visual C++-Version 1.5 und höher geliefert wird.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>Funktionsprototyp

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Bemerkungen

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Parameter und Verwendung

*hwndParent*<br/>
Das Besitzerfenster für alle Dialogfelder, das der ODBC-Treiber-Manager oder der spezifische ODBC-Treiber erstellt, um vom Benutzer zusätzliche Informationen über die neue Datenquelle anzufordern. Wenn der Parameter *lpszAttributes* nicht genügend Informationen liefert, wird ein Dialogfeld angezeigt. Der *Parameter hwndParent* ist möglicherweise NULL.

*lpszDriver*<br/>
Hierbei handelt es sich um die Treiberbeschreibung. Dies ist der Name, der dem Benutzer an Stelle des physischen Treibernamens, also der DLL, angezeigt wird.

*lpszAttributes*<br/>
Die Liste der Attribute in der Form "Schlüsselname=Wert". Diese Zeichenfolgen werden durch NULL-Zeichen getrennt. Zwei aufeinander folgende NULL-Zeichen kennzeichnen das Ende der Liste. Diese Attribute sind in erster Linie treiberspezifische Standardeinträge, die für die neue Datenquelle in die Registrierung geschrieben werden. Ein wichtiger Schlüssel, der in der ODBC-API-Referenz zu dieser Funktion nicht erwähnt wird, ist "DSN" (Data Source Name, Datenquellenname). Hierdurch wird der Name der neuen Datenquelle angegeben. Die übrigen Einträge betreffen den Treiber für die neue Datenquelle. Meist ist es nicht erforderlich, alle Einträge zur Verfügung zu stellen, da der Benutzer durch den Treiber in Dialogfeldern zur Eingabe der neuen Werte aufgefordert werden kann. (Setzen Sie *hwndParent* auf NULL, um dies zu verursachen.) Sie können explizit Standardwerte angeben, damit der Benutzer nicht dazu aufgefordert wird.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>So ermitteln Sie mit ODBC-Administrator die Beschreibung eines Treibers für den lpszDriver-Parameter

1. Starten Sie den ODBC-Administrator.

1. Klicken Sie auf **Hinzufügen**.

Hierdurch wird eine Liste der installierten Treiber mit der entsprechenden Beschreibung angezeigt. Verwenden Sie diese Beschreibung als *lpszDriver-Parameter.* Verwenden Sie hierbei die vollständige Beschreibung, z. B. "Excel-Dateien (*.xls)", einschließlich der Dateinamenerweiterung und der Klammern, sofern diese in der Beschreibung vorhanden sind.

Wahlweise kann auch die Registrierung oder, bei 16 Bit-Systemen, die Datei Odbcinst.ini durchsucht werden, die eine Liste aller Treibereinträge und Beschreibungen unter dem Registrierungsschlüssel "ODBC Drivers" enthält bzw. der Abschnitt [ODBC Drivers] in der Datei Odbcinst.ini.

Eine Möglichkeit, die Schlüsselnamen und Werte für den Parameter *lpszAttributes* zu finden, besteht darin, die Datei Odbc.ini auf eine bereits konfigurierte Datenquelle zu untersuchen (möglicherweise eine, die vom ODBC-Administrator konfiguriert wurde).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>So suchen Sie Schlüsselnamen und Werte für den Parameter lpszAttributes

1. Führen Sie den Registrierungs-Editor von Windows aus, oder öffnen Sie bei einem 16-Bit-System die Datei Odbc.ini.

1. Suchen Sie nach den Informationen zu ODBC-Datenquellen mit einer der folgenden Methoden:

   - Suchen Sie für 32 Bit den Schlüssel **HKEY_CURRENT_USER.Software-ODBC-ODBC. INI-ODBC-Datenquellen** im linken Bereich.

      Im rechten Bereich sind Einträge des Formulars aufgeführt: "pub: REG_SZ:*\<Datenquellenname>*", wobei * \<der Datenquellenname>* eine Datenquelle ist, die bereits mit den gewünschten Einstellungen für den Treiber konfiguriert wurde, den Sie verwenden möchten. Wählen Sie die gewünschte Datenquelle aus, also z. B. SQL Server. Die Elemente, die der Zeichenfolge "pub:" folgen, sind in der Reihenfolge der Schlüsselname und der Wert, der in Ihrem *lpszAttributes-Parameter* verwendet werden soll.

   - Suchen Sie für 16 Bit den Abschnitt in der Datei Odbc.ini, die durch [*\<Datenquellenname>*] gekennzeichnet ist.

      Die Zeilen im Anschluss an diese Zeile haben die Form "Schlüsselname=Wert". Dies sind genau die Einträge, die in Ihrem *lpszAttributes-Parameter* verwendet werden sollen.

Sie können auch die Dokumentation des Treibers durchsuchen, den Sie verwenden möchten. Sie finden nützliche Informationen in der Onlinehilfe zu diesem Treiber, auf die Sie mit ODBC-Administrator zugreifen können. Diese Hilfedateien sind normalerweise im Verzeichnis WINDOWS\SYSTEM von Windows NT, Windows 3.1 oder Windows 95 gespeichert.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>So greifen Sie auf die Onlinehilfe des ODBC-Treibers zu

1. Starten Sie den ODBC-Administrator.

1. Klicken Sie auf **Hinzufügen**.

1. Wählen Sie den Namen des Treibers aus.

1. Klicken Sie auf **OK**.

Wenn DER ODBC-Administrator die Informationen zum Erstellen einer neuen Datenquelle für diesen bestimmten Treiber anzeigt, klicken Sie auf **Hilfe**. Hierdurch wird die Hilfedatei für diesen Treiber geöffnet, die in der Regel wichtige Informationen zu dessen Verwendung enthält.

## <a name="see-also"></a>Siehe auch

[Datenquelle (ODBC)](../../data/odbc/data-source-odbc.md)
