---
title: Ausnahmeverarbeitung
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d33da7a9bc81f9733df840a87fbbbeca1e02cc04
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855303"
---
# <a name="exception-processing"></a>Ausnahmeverarbeitung

Wenn ein Programm ausgeführt wird, kann es vorkommen, dass eine Reihe von ungewöhnlichen Bedingungen und Fehler als "Ausnahmen" bezeichnet wird. Dazu zählen möglicherweise nicht genügend Arbeitsspeicher, Ressourcen Zuordnungs Fehler und Fehler beim finden von Dateien.

Der-Microsoft Foundation Class-Bibliothek verwendet ein Ausnahme Behandlungsschema, das nach dem vom ANSI-Standards-Ausschuss für C++eingehalten modelliert wird. Ein Ausnahmehandler muss eingerichtet werden, bevor eine Funktion aufgerufen wird, die möglicherweise eine ungewöhnliche Situation auslöst. Wenn die Funktion auf eine ungewöhnliche Bedingung stößt, wird eine Ausnahme ausgelöst, und die Steuerung wird an den Ausnahmehandler übermittelt.

Mehrere in der Microsoft Foundation Class-Bibliothek enthaltene Makros richten Ausnahmehandler ein. Eine Reihe von anderen globalen Funktionen unterstützen Sie bei Bedarf beim Auslösen spezieller Ausnahmen und beim Beenden von Programmen. Diese Makros und globalen Funktionen fallen in die folgenden Kategorien:

- Ausnahme Makros, die den Ausnahmehandler strukturieren.

- Ausnahme auslösende Funktionen), die Ausnahmen bestimmter Typen generieren.

- Beendigungs Funktionen, die die Beendigung des Programms bewirken.

Beispiele und weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Ausnahme Makros

|||
|-|-|
|[Versu](#try)|Legt einen Codeblock für die Ausnahme Verarbeitung fest.|
|[Quote](#catch)|Legt einen Codeblock für das Abfangen einer Ausnahme aus dem vorangehenden **try** -Block fest.|
|[CATCH_ALL](#catch_all)|Legt einen Codeblock zum Abfangen aller Ausnahmen aus dem vorangehenden **try** -Block fest.|
|[AND_CATCH](#and_catch)|Legt einen Codeblock für das Abfangen zusätzlicher Ausnahme Typen aus dem vorangehenden **try** -Block fest.|
|[AND_CATCH_ALL](#and_catch_all)|Legt einen Codeblock für das Abfangen aller anderen zusätzlichen Ausnahme Typen fest, die in einem vorangehenden **try** -Block ausgelöst werden.|
|[END_CATCH](#end_catch)|Beendet den letzten **catch** -oder **AND_CATCH** -Codeblock.|
|[END_CATCH_ALL](#end_catch_all)|Beendet den letzten **CATCH_ALL** Codeblock.|
|[THROW](#throw)|Löst eine angegebene Ausnahme aus.|
|[THROW_LAST](#throw_last)|Löst die aktuell behandelte Ausnahme für den nächsten äußeren Handler aus.|

### <a name="exception-throwing-functions"></a>Ausnahme-auslösende Funktionen

|||
|-|-|
|[Afxthrowarchiveexception](#afxthrowarchiveexception)|Löst eine Archivierungs Ausnahme aus.|
|[Afxthrowfileexception](#afxthrowfileexception)|Löst eine Datei Ausnahme aus.|
|[Afxthrowinvalidargexception](#afxthrowinvalidargexception)|Löst eine Ausnahme für ein ungültiges Argument aus.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Löst eine Speicher Ausnahme aus.|
|[Afxthrownotsupportedexception](#afxthrownotsupportedexception)|Löst eine Ausnahme aus, die nicht unterstützt wird.|
|[Afxthrowresourceexception](#afxthrowresourceexception)|Löst eine Ausnahme vom Typ "Windows-Ressource nicht gefunden" aus.|
|[Afxthrowuserexception](#afxthrowuserexception)|Löst eine Ausnahme in einer vom Benutzer initiierten Programm Aktion aus.|

MFC bietet zwei Funktionen zum Auslösen von Ausnahmen, die speziell für OLE-Ausnahmen gelten:

### <a name="ole-exception-functions"></a>OLE-Ausnahme Funktionen

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Löst eine Ausnahme in einer OLE-Automatisierungsfunktion aus.|
|[AfxThrowOleException](#afxthrowoleexception)|Löst eine OLE-Ausnahme aus.|

Zur Unterstützung von Daten Bank Ausnahmen bieten die Datenbankklassen zwei Ausnahme Klassen, `CDBException` und `CDaoException`sowie globale Funktionen zur Unterstützung der Ausnahme Typen:

### <a name="dao-exception-functions"></a>DAO-Ausnahme Funktionen

|||
|-|-|
|[Afxthrowdaoexception](#afxthrowdaoexception)|Löst eine [CDaoException](../../mfc/reference/cdaoexception-class.md) aus Ihrem eigenen Code aus.|
|[Afxthrowdbexception](#afxthrowdbexception)|Löst eine [CDBException](../../mfc/reference/cdbexception-class.md) aus Ihrem eigenen Code aus.|

MFC stellt die folgende Beendigungs Funktion bereit:

### <a name="termination-functions"></a>Beendigungs Funktionen

|||
|-|-|
|[Afxabort](#afxabort)|Wird aufgerufen, um eine Anwendung beim Auftreten eines schwerwiegenden Fehlers zu beenden.|

##  <a name="try"></a>Versu

Richtet einen **try** -Block ein.

```
TRY
```

### <a name="remarks"></a>Bemerkungen

Ein **try** -Block identifiziert einen Codeblock, der möglicherweise Ausnahmen auslöst. Diese Ausnahmen werden in den folgenden **catch** -und **AND_CATCH** -Blöcken behandelt. Rekursion ist zulässig: Ausnahmen können an einen äußeren **try** -Block übertragen werden, indem Sie entweder ignoriert werden oder indem Sie das THROW_LAST-Makro verwenden. Beenden **Sie den try** -Block mit einem END_CATCH-oder END_CATCH_ALL-Makro.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [catch](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

Header: afx.h

##  <a name="catch"></a>Quote

Definiert einen Codeblock, der den ersten Ausnahmetyp abfängt, der im vorangehenden **try** -Block ausgelöst wird.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_class*<br/>
Gibt den Ausnahmetyp an, der getestet werden soll. Eine Liste der Standard Ausnahme Klassen finden Sie unter Class [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Gibt einen Namen für einen Ausnahme Objekt Zeiger an, der vom-Makro erstellt wird. Sie können den Zeiger Namen verwenden, um auf das Ausnahme Objekt innerhalb des **catch** -Blocks zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Der Code für die Ausnahme Verarbeitung kann ggf. das Ausnahme Objekt Abfragen, um weitere Informationen über die genaue Ursache der Ausnahme zu erhalten. Rufen Sie das THROW_LAST-Makro auf, um die Verarbeitung auf den nächsten äußeren Ausnahme Rahmen zu verschieben. Beenden **Sie den try** -Block mit einem END_CATCH-Makro.

Wenn *exception_class* die Klasse `CException`ist, werden alle Ausnahme Typen abgefangen. Sie können die Member-Funktion [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) verwenden, um zu bestimmen, welche spezifische Ausnahme ausgelöst wurde. Eine bessere Möglichkeit, mehrere Arten von Ausnahmen abzufangen, ist die Verwendung von sequenziellen **AND_CATCH** -Anweisungen, die jeweils einen anderen Ausnahmetyp haben.

Der Ausnahme Objekt Zeiger wird vom-Makro erstellt. Sie müssen Sie nicht selbst deklarieren.

> [!NOTE]
>  Der **catch** -Block wird als durch C++ geschweifte Klammern umschlossen Bereich definiert. Wenn Sie Variablen in diesem Bereich deklarieren, ist nur innerhalb dieses Bereichs zugänglich. Dies gilt auch für *exception_object_pointer_name*.

Weitere Informationen zu Ausnahmen und zum Catch-Makro finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>CATCH_ALL

Definiert einen Codeblock, der alle Ausnahme Typen abfängt, die im vorherigen **try** -Block ausgelöst werden.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer_name*<br/>
Gibt einen Namen für einen Ausnahme Objekt Zeiger an, der vom-Makro erstellt wird. Sie können den Zeiger Namen verwenden, um auf das Ausnahme Objekt innerhalb des `CATCH_ALL` Blocks zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Der Code für die Ausnahme Verarbeitung kann ggf. das Ausnahme Objekt Abfragen, um weitere Informationen über die genaue Ursache der Ausnahme zu erhalten. Rufen Sie das `THROW_LAST`-Makro auf, um die Verarbeitung auf den nächsten äußeren Ausnahme Rahmen zu verschieben. Wenn Sie **CATCH_ALL**verwenden, beenden Sie den **try** -Block mit einem END_CATCH_ALL-Makro.

> [!NOTE]
>  Der **CATCH_ALL** -Block wird als durch C++ geschweifte Klammern umschlossen Bereich definiert. Wenn Sie Variablen in diesem Bereich deklarieren, ist nur innerhalb dieses Bereichs zugänglich.

Weitere Informationen zu Ausnahmen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CFile:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="and_catch"></a>AND_CATCH

Definiert einen Codeblock zum Abfangen zusätzlicher Ausnahme Typen, die in einem vorangehenden **try** -Block ausgelöst werden.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_class*<br/>
Gibt den Ausnahmetyp an, der getestet werden soll. Eine Liste der Standard Ausnahme Klassen finden Sie unter Class [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Ein Name für einen Ausnahme Objekt Zeiger, der vom-Makro erstellt wird. Sie können den Zeiger Namen verwenden, um auf das Ausnahme Objekt innerhalb des **AND_CATCH** Blocks zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das CATCH-Makro, um einen Ausnahmetyp abzufangen, und dann das AND_CATCH Makro, um jeden nachfolgenden Typ abzufangen Beenden **Sie den try** -Block mit einem END_CATCH-Makro.

Der Code für die Ausnahme Verarbeitung kann ggf. das Ausnahme Objekt Abfragen, um weitere Informationen über die genaue Ursache der Ausnahme zu erhalten. Ruft das THROW_LAST-Makro innerhalb des **AND_CATCH** -Blocks auf, um die Verarbeitung auf den nächsten äußeren Ausnahme Rahmen zu verschieben. **AND_CATCH** markiert das Ende des vorangehenden **catch** -oder **AND_CATCH** -Blocks.

> [!NOTE]
>  Der **AND_CATCH** -Block wird als Gültigkeits C++ Bereich definiert (durch geschweifte Klammern getrennt). Wenn Sie Variablen in diesem Bereich deklarieren, denken Sie daran, dass nur innerhalb dieses Bereichs darauf zugegriffen werden kann. Dies gilt auch für die *exception_object_pointer_name* Variable.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [catch](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"
##  <a name="and_catch_all"></a>AND_CATCH_ALL

Definiert einen Codeblock zum Abfangen zusätzlicher Ausnahme Typen, die in einem vorangehenden **try** -Block ausgelöst werden.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer_name*<br/>
Ein Name für einen Ausnahme Objekt Zeiger, der vom-Makro erstellt wird. Sie können den Zeiger Namen verwenden, um auf das Ausnahme Objekt innerhalb des **AND_CATCH_ALL** Blocks zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das **catch** -Makro, um einen Ausnahmetyp abzufangen, dann das AND_CATCH_ALL Makro, um alle anderen nachfolgenden Typen abzufangen. Wenn Sie AND_CATCH_ALL verwenden, beenden Sie den **try** -Block mit einem END_CATCH_ALL-Makro.

Der Code für die Ausnahme Verarbeitung kann ggf. das Ausnahme Objekt Abfragen, um weitere Informationen über die genaue Ursache der Ausnahme zu erhalten. Ruft das THROW_LAST-Makro innerhalb des **AND_CATCH_ALL** -Blocks auf, um die Verarbeitung auf den nächsten äußeren Ausnahme Rahmen zu verschieben. **AND_CATCH_ALL** markiert das Ende des vorangehenden **catch** -oder **AND_CATCH_ALL** -Blocks.

> [!NOTE]
>  Der **AND_CATCH_ALL** -Block wird als C++ Bereich definiert (durch geschweifte Klammern getrennt). Wenn Sie Variablen in diesem Bereich deklarieren, denken Sie daran, dass nur innerhalb dieses Bereichs darauf zugegriffen werden kann.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="end_catch"></a>END_CATCH

Markiert das Ende des letzten **catch** -oder **AND_CATCH** Blocks.

```
END_CATCH
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum END_CATCH-Makro finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="end_catch_all"></a>END_CATCH_ALL

Markiert das Ende des letzten **CATCH_ALL88** oder **AND_CATCH_ALL** Blocks.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="throw"></a>Throw (MFC)

Löst die angegebene Ausnahme aus.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer*<br/>
Verweist auf ein Ausnahme Objekt, das von `CException`abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Löst **eine Interrupts** -Programmausführung aus und übergibt die Steuerung an den zugeordneten **catch** -Block im Programm. Wenn Sie den **catch** -Block nicht angegeben haben, wird die Steuerung an ein Microsoft Foundation Class-Bibliothek Modul weitergeleitet, das eine Fehlermeldung ausgibt und beendet.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="throw_last"></a>THROW_LAST

Löst die Ausnahme zurück zum nächsten äußeren **catch** -Block aus.

```
THROW_LAST()
```

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie eine lokal erstellte Ausnahme auslösen. Wenn Sie versuchen, eine Ausnahme auszulösen, die Sie gerade abgefangen haben, wird der Gültigkeitsbereich normalerweise verlassen und gelöscht. Bei **THROW_LAST**wird die Ausnahme ordnungsgemäß an den nächsten **catch** -Handler weitergegeben.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CFile:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowarchiveexception"></a>Afxthrowarchiveexception

Löst eine Archivierungs Ausnahme aus.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parameter

*cause*<br/>
Gibt eine ganze Zahl an, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [carchiveexception:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszarchivename*<br/>
Verweist auf eine Zeichenfolge, die den Namen des `CArchive` Objekts enthält, das die Ausnahme verursacht hat (falls verfügbar).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowfileexception"></a>Afxthrowfileexception

Löst eine Datei Ausnahme aus.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*cause*<br/>
Gibt eine ganze Zahl an, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*loserror*<br/>
Enthält die Betriebssystem-Fehlernummer (sofern vorhanden), die den Grund für die Ausnahme angibt. Eine Liste der Fehlercodes finden Sie in Ihrem Betriebssystem Handbuch.

*lpszfilename*<br/>
Verweist auf eine Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat (falls verfügbar).

### <a name="remarks"></a>Bemerkungen

Sie sind dafür verantwortlich, die Ursache basierend auf dem Fehlercode des Betriebssystems zu ermitteln.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

## <a name="afxthrowinvalidargexception"></a>Afxthrowinvalidargexception

Löst eine Ausnahme für ein ungültiges Argument aus.

### <a name="syntax"></a>Syntax

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, wenn ungültige Argumente verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afx.h

##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Löst eine Speicher Ausnahme aus.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, wenn Aufrufe von zugrunde liegenden Systemspeicher Zuweisungen (z. b. **malloc** und die [globalbelegc](/windows/win32/api/winbase/nf-winbase-globalalloc) -Windows-Funktion) fehlschlagen. Sie müssen Sie nicht für einen **neuen** Befehl abrufen, da **New** automatisch eine Speicher Ausnahme auslöst, wenn die Speicher Belegung fehlschlägt.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrownotsupportedexception"></a>Afxthrownotsupportedexception

Löst eine Ausnahme aus, die das Ergebnis einer Anforderung für ein nicht unterstütztes Feature ist.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowresourceexception"></a>Afxthrowresourceexception

Löst eine Ressourcen Ausnahme aus.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise aufgerufen, wenn eine Windows-Ressource nicht geladen werden kann.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowuserexception"></a>Afxthrowuserexception

Löst eine Ausnahme aus, um einen Endbenutzer Vorgang zu beenden.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise sofort aufgerufen, nachdem `AfxMessageBox` einen Fehler an den Benutzer gemeldet hat.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Verwenden Sie diese Funktion, um eine Ausnahme in einer OLE-Automatisierungsfunktion auszulösen.

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Parameter

*wCode*<br/>
Ein spezifischer Fehlercode für Ihre Anwendung.

*lpszdescription*<br/>
Die verbale Beschreibung des Fehlers.

*ndeskriptionid*<br/>
Die Ressourcen-ID für die Beschreibung des verbalen Fehlers.

*nhelpid*<br/>
Ein Hilfe Kontext für die Hilfe Ihrer Anwendung (. HLP-Datei).

### <a name="remarks"></a>Bemerkungen

Die Informationen, die für diese Funktion bereitgestellt werden, können von der Driving-Anwendung (Microsoft Visual Basic oder einer anderen OLE-Automatisierungs Client Anwendung) angezeigt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxthrowoleexception"></a>AfxThrowOleException

Erstellt ein Objekt vom Typ `COleException` und löst eine Ausnahme aus.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parameter

*SC*<br/>
Ein OLE-Statuscode, der den Grund für die Ausnahme angibt.

*HR*<br/>
Handle für einen Ergebniscode, der den Grund für die Ausnahme angibt.

### <a name="remarks"></a>Bemerkungen

Die Version, die ein HRESULT als Argument annimmt, konvertiert diesen Ergebniscode in den entsprechenden SCODE. Weitere Informationen zu HRESULT und SCODE finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdao. h

##  <a name="afxthrowdaoexception"></a>Afxthrowdaoexception

Mit dieser Funktion wird eine Ausnahme vom Typ " [CDaoException](../../mfc/reference/cdaoexception-class.md) " aus dem eigenen Code ausgelöst.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parameter

*nafxdaoerror*<br/>
Ein ganzzahliger Wert, der einen erweiterten DAO-Fehlercode darstellt, bei dem es sich um einen der unter [CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)aufgeführten Werte handeln kann.

*SCODE*<br/>
Ein OLE-Fehlercode aus DAO, vom Typ SCODE. Weitere Informationen finden Sie unter [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Bemerkungen

Das Framework ruft auch `AfxThrowDaoException`auf. In Ihrem-Befehl können Sie einen oder beide Parameter übergeben. Wenn Sie z. b. einen der in **CDaoException:: nafxdaoerror** definierten Fehler, aber keinen Bezug zum *SCODE* -Parameter machen möchten, übergeben Sie einen gültigen Code im Parameter *nafxdaoerror* , und übernehmen Sie den Standardwert für *SCODE*.

Informationen zu Ausnahmen im Zusammenhang mit den MFC-DAO-Klassen finden Sie unter Class `CDaoException` in diesem Buch und im Artikel [Ausnahmen: Daten Bank Ausnahmen](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXDB. h

##  <a name="afxthrowdbexception"></a>Afxthrowdbexception

Mit dieser Funktion wird eine Ausnahme vom Typ `CDBException` aus Ihrem eigenen Code ausgelöst.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*nretcode*<br/>
Ein Wert vom Typ RETCODE, der den Typ des Fehlers definiert, der bewirkt hat, dass die Ausnahme ausgelöst wurde.

*PDB*<br/>
Ein Zeiger auf das `CDatabase` Objekt, das die Datenquellen Verbindung darstellt, der die Ausnahme zugeordnet ist.

*hstmt*<br/>
Ein ODBC-hstmt-handle, das das Anweisungs Handle angibt, dem die Ausnahme zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft `AfxThrowDBException` auf, wenn es einen ODBC-RETCODE aus einem Aufruf einer ODBC-API-Funktion empfängt und den RETCODE als Ausnahme Bedingung anstelle eines expectable-Fehlers interpretiert. Beispielsweise kann ein Datenzugriffs Vorgang aufgrund eines Datenträger Lese Fehlers fehlschlagen.

Informationen zu den von ODBC definierten retcodewerten finden Sie in Kapitel 8 "Abrufen von Status-und Fehlerinformationen" in der Windows SDK. Weitere Informationen über MFC-Erweiterungen für diese Codes finden Sie Unterklasse [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

##  <a name="afxabort"></a>Afxabort

Die von MFC bereitgestellte Standard Beendigungs Funktion.

```
void  AfxAbort();
```

### <a name="remarks"></a>Bemerkungen

`AfxAbort` wird von MFC-Element Funktionen intern aufgerufen, wenn ein schwerwiegender Fehler vorliegt, z. b. eine nicht abgefangene Ausnahme, die nicht behandelt werden kann. Sie können `AfxAbort` im seltenen Fall aufzurufen, wenn ein schwerwiegender Fehler auftritt, der nicht wieder hergestellt werden kann.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [catch](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** "AFX. h"

## <a name="see-also"></a>Weitere Informationen

[Makros und Globals](mfc-macros-and-globals.md)<br/>
[CException-Klasse](cexception-class.md)<br/>
[CInvalidArgException-Klasse](cinvalidargexception-class.md)
