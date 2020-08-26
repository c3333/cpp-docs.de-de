---
title: CException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: e27802e05c832d28d848d9eb1235d6ef5980b306
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841557"
---
# <a name="cexception-class"></a>CException-Klasse

Die Basisklasse für alle Ausnahmen in der Microsoft Foundation Class-Bibliothek.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CException:: CException](#cexception)|Erstellt ein `CException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CException::D Elete](#delete)|Löscht ein- `CException` Objekt.|
|[CException:: Report Terror](#reporterror)|Meldet dem Benutzer eine Fehlermeldung in einem Meldungs Feld.|

## <a name="remarks"></a>Bemerkungen

Da `CException` eine abstrakte Basisklasse ist, können Sie `CException` Objekte nicht direkt erstellen. Sie müssen Objekte abgeleiteter Klassen erstellen. Wenn Sie eine eigene Klasse erstellen müssen `CException` , verwenden Sie eine der oben aufgeführten abgeleiteten Klassen als Modell. Stellen Sie sicher, dass auch von der abgeleiteten Klasse verwendet wird `IMPLEMENT_DYNAMIC` .

Die abgeleiteten Klassen und ihre Beschreibungen sind unten aufgeführt:

|Name|Beschreibung|
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Eine Basisklasse für Ressourcen kritische MFC-Ausnahmen|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Ungültige Argument Ausnahme Bedingung|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Ausnahme wegen nicht genügend Arbeitsspeichers|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Anforderung für einen nicht unterstützten Vorgang|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Archiv spezifische Ausnahme|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Datei spezifische Ausnahme|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows-Ressource nicht gefunden oder nicht erstellbar|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE-Ausnahme|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Daten Bank Ausnahme (d. h. Ausnahmebedingungen, die für MFC-Datenbankklassen basierend auf Open Database Connectivity auftreten)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE Dispatch-Ausnahme (Automation)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Eine Ausnahme, die angibt, dass eine Ressource nicht gefunden wurde.|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Ausnahme für das Datenzugriffs Objekt (d. h. Ausnahmebedingungen, die für DAO-Klassen entstehen)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Internet Ausnahme (d. h. Ausnahmebedingungen, die für Internet Klassen entstehen).|

Diese Ausnahmen sind für die Verwendung mit den Makros [throw](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [AND_CATCH](exception-processing.md#and_catch)und [END_CATCH](exception-processing.md#end_catch) vorgesehen. Weitere Informationen zu Ausnahmen finden Sie unter [Ausnahme Verarbeitung](exception-processing.md)oder im Artikel [Ausnahmebehandlung (MFC)](../exception-handling-in-mfc.md).

Um eine bestimmte Ausnahme abzufangen, verwenden Sie die entsprechende abgeleitete Klasse. Zum Abfangen aller Typen von Ausnahmen verwenden Sie `CException` , und verwenden Sie dann [CObject:: IsKindOf](cobject-class.md#iskindof) , um zwischen `CException` abgeleitete Klassen zu unterscheiden. Beachten Sie, dass `CObject::IsKindOf` nur für mit dem [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) -Makro deklarierte Klassen funktioniert, um die Verwendung dynamischer Typüberprüfungen zu nutzen. Eine von `CException` Ihnen erstellte von abgeleitete Klasse sollte auch das- `IMPLEMENT_DYNAMIC` Makro verwenden.

Sie können Details zu Ausnahmen an den Benutzer melden, indem Sie [getErrorMessage](cfileexception-class.md#geterrormessage) oder Report [Terror](#reporterror)aufrufen, zwei Member-Funktionen, die mit einer der `CException` abgeleiteten Klassen funktionieren.

Wenn eine Ausnahme von einem der Makros abgefangen wird, wird das `CException` Objekt automatisch gelöscht. löschen Sie es nicht selbst. Wenn eine Ausnahme mithilfe eines **`catch`** Schlüssel Worts abgefangen wird, wird Sie nicht automatisch gelöscht. Weitere Informationen zum Zeitpunkt, zu dem ein Verarbeitungs-Objekt gelöscht werden soll, finden Sie im Artikel [Ausnahmebehandlung (MFC)](../exception-handling-in-mfc.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cexceptioncexception"></a><a name="cexception"></a> CException:: CException

Diese Member-Funktion erstellt ein- `CException` Objekt.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*b_AutoDelete*<br/>
Geben Sie true an, wenn der Speicher für das `CException` Objekt auf dem Heap zugeordnet wurde. Dadurch wird das `CException` Objekt gelöscht, wenn die Member- `Delete` Funktion aufgerufen wird, um die Ausnahme zu löschen. Geben Sie false an, wenn `CException` sich das Objekt im Stapel befindet oder wenn es sich um ein globales Objekt handelt. In diesem Fall wird das `CException` Objekt nicht gelöscht, wenn die `Delete` Member-Funktion aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor muss normalerweise niemals direkt aufgerufen werden. Eine Funktion, die eine Ausnahme auslöst, sollte eine Instanz einer von `CException` abgeleiteten Klasse erstellen und deren Konstruktor aufzurufen, oder Sie sollte eine der MFC-Throw-Funktionen, wie z. b. [afxthrowfileexception](exception-processing.md#afxthrowfileexception), verwenden, um einen vordefinierten Typ auszulösen. Diese Dokumentation wird nur aus Gründen der Vollständigkeit bereitgestellt.

## <a name="cexceptiondelete"></a><a name="delete"></a> CException::D Elete

Diese Funktion überprüft, ob das `CException` Objekt auf dem Heap erstellt wurde. wenn dies der Fall ist, wird der- **`delete`** Operator für das-Objekt aufgerufen.

```cpp
void Delete();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie beim Löschen eines- `CException` Objekts die- `Delete` Member-Funktion, um die Ausnahme zu löschen. Verwenden Sie den- **`delete`** Operator nicht direkt, da es sich `CException` bei dem Objekt möglicherweise um ein globales Objekt handelt oder es im Stapel erstellt wurde.

Sie können angeben, ob das Objekt gelöscht werden soll, wenn das Objekt erstellt wird. Weitere Informationen finden Sie unter [CException:: CException](#cexception).

Sie müssen nur dann anrufen, `Delete` Wenn Sie den C++- **`try`** -  **`catch`** Mechanismus verwenden. Wenn Sie die MFC-Makros **try** und **catch**verwenden, wird diese Funktion automatisch von diesen Makros aufgerufen.

### <a name="example"></a>Beispiel

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

## <a name="cexceptionreporterror"></a><a name="reporterror"></a> CException:: Report Terror

Mit dieser Member-Funktion können Sie dem Benutzerfehler Text in einem Meldungs Feld melden.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt den Stil des Meldungs Felds an. Wenden Sie eine beliebige Kombination der [Nachrichtenfeld Stile](styles-used-by-mfc.md#message-box-styles) auf das Feld an. Wenn Sie diesen Parameter nicht angeben, wird der Standardwert MB_OK.

*nmessageid*<br/>
Gibt die Ressourcen-ID (Zeichen folgen-Tabelleneintrag) einer Meldung an, die angezeigt werden soll, wenn das Ausnahme Objekt keine Fehlermeldung enthält. Wenn der Wert 0 ist, wird die Meldung "Es ist keine Fehlermeldung verfügbar" angezeigt.

### <a name="return-value"></a>Rückgabewert

Ein- `AfxMessageBox` Wert, andernfalls 0, wenn nicht genügend Arbeitsspeicher vorhanden ist, um das Meldungs Feld anzuzeigen. Die möglichen Rückgabewerte finden Sie unter [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) .

### <a name="example"></a>Beispiel

Im folgenden finden Sie ein Beispiel für die Verwendung von `CException::ReportError` . Ein weiteres Beispiel finden Sie im Beispiel für [catch](exception-processing.md#catch).

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](cobject-class.md)<br/>
[Hierarchie Diagramm](../hierarchy-chart.md)<br/>
[Ausnahme Verarbeitung](exception-processing.md)<br/>
[Gewusst wie: Erstellen von eigenen benutzerdefinierten Ausnahme Klassen](https://go.microsoft.com/fwlink/p/?linkid=128045)
