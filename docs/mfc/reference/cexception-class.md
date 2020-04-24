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
ms.openlocfilehash: 93901f6f92ee79bd893b2ec0d1e341e77749d951
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753179"
---
# <a name="cexception-class"></a>CException-Klasse

Die Basisklasse für alle Ausnahmen in der Microsoft Foundation Class-Bibliothek.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CException::CException](#cexception)|Erstellt ein `CException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CException::Delete](#delete)|Löscht ein `CException` Objekt.|
|[CException::ReportError](#reporterror)|Meldet eine Fehlermeldung in einem Meldungsfeld an den Benutzer.|

## <a name="remarks"></a>Bemerkungen

Da `CException` es sich um eine `CException` abstrakte Basisklasse handelt, können Sie keine Objekte direkt erstellen. Sie müssen Objekte abgeleiteter Klassen erstellen. Wenn Sie eine eigene `CException`-style-Klasse erstellen müssen, verwenden Sie eine der oben aufgeführten abgeleiteten Klassen als Modell. Stellen Sie sicher, dass `IMPLEMENT_DYNAMIC`Ihre abgeleitete Klasse auch verwendet.

Die abgeleiteten Klassen und ihre Beschreibungen sind unten aufgeführt:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Eine Basisklasse für ressourcenkritische MFC-Ausnahmen|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Ungültige Argumentausnahmebedingung|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Außerspeicher-Ausnahme|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Anforderung eines nicht unterstützten Vorgangs|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Archivspezifische Ausnahme|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Dateispezifische Ausnahme|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows-Ressource nicht gefunden oder nicht verunstetzbar|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE-Ausnahme|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Datenbankausnahme (d. h. Ausnahmebedingungen für MFC-Datenbankklassen basierend auf Open Database Connectivity)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE-Dispatch-Ausnahme (Automatisierung)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Ausnahme, die angibt, dass eine Ressource nicht gefunden wurde|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Ausnahme für Datenzugriffsobjekt (d. h. Ausnahmebedingungen für DAO-Klassen)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Internetausnahme (d. h. Ausnahmebedingungen für Internetklassen).|

Diese Ausnahmen sind für die Verwendung mit den Makros [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch)und [end_catch](exception-processing.md#end_catch) vorgesehen. Weitere Informationen zu Ausnahmen finden Sie unter [Ausnahmeverarbeitung](exception-processing.md)oder im Artikel [Exception Handling (MFC)](../exception-handling-in-mfc.md).

Um eine bestimmte Ausnahme abzufangen, verwenden Sie die entsprechende abgeleitete Klasse. Um alle Arten von Ausnahmen `CException`abzufangen, verwenden Sie , und verwenden `CException`Sie dann [CObject::IsKindOf,](cobject-class.md#iskindof) um zwischen -abgeleiteten Klassen zu unterscheiden. Beachten `CObject::IsKindOf` Sie, dass dies nur für Klassen funktioniert, die mit dem [IMPLEMENT_DYNAMIC-Makro](run-time-object-model-services.md#implement_dynamic) deklariert sind, um die Vorteile der dynamischen Typprüfung zu nutzen. Jede `CException`-abgeleitete Klasse, die `IMPLEMENT_DYNAMIC` Sie erstellen, sollte auch das Makro verwenden.

Sie können Details zu Ausnahmen an den Benutzer melden, indem Sie [GetErrorMessage](cfileexception-class.md#geterrormessage) `CException`oder [ReportError](#reporterror)aufrufen, zwei Memberfunktionen, die mit einer der abgeleiteten Klassen von funktionieren.

Wenn eine Ausnahme von einem der Makros abgefangen wird, wird das `CException` Objekt automatisch gelöscht. löschen Sie es nicht selbst. Wenn eine Ausnahme mithilfe **catch** eines catch-Schlüsselworts abgefangen wird, wird sie nicht automatisch gelöscht. Weitere Informationen zum Löschen eines Exeption-Objekts finden Sie im Artikel [Exception Handling (MFC).](../exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](cobject-class.md)

`CException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException::CException

Diese Memberfunktion erstellt `CException` ein Objekt.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*b_AutoDelete*<br/>
Geben Sie TRUE an, wenn der Speicher für das `CException` Objekt auf dem Heap zugewiesen wurde. Dies führt `CException` dazu, dass `Delete` das Objekt gelöscht wird, wenn die Memberfunktion aufgerufen wird, um die Ausnahme zu löschen. Geben Sie `CException` FALSE an, wenn sich das Objekt auf dem Stapel befindet oder ein globales Objekt ist. In diesem Fall `CException` wird das Objekt `Delete` nicht gelöscht, wenn die Memberfunktion aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Normalerweise müssten Sie diesen Konstruktor normalerweise nie direkt aufrufen. Eine Funktion, die eine Ausnahme auslöst, sollte eine Instanz einer `CException`-derived-Klasse erstellen und ihren Konstruktor aufrufen, oder sie sollte eine der MFC-Throw-Funktionen verwenden, z. B. [AfxThrowFileException](exception-processing.md#afxthrowfileexception), um einen vordefinierten Typ auszulösen. Diese Dokumentation wird nur der Vollständigkeit zur Verfügung gestellt.

## <a name="cexceptiondelete"></a><a name="delete"></a>CException::Delete

Diese Funktion überprüft, `CException` ob das Objekt auf dem Heap erstellt wurde, und wenn ja, ruft sie den **delete-Operator** für das Objekt auf.

```cpp
void Delete();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `CException` beim Löschen `Delete` eines Objekts die Memberfunktion, um die Ausnahme zu löschen. Verwenden Sie den **delete-Operator** `CException` nicht direkt, da es sich bei dem Objekt möglicherweise um ein globales Objekt handelt oder auf dem Stapel erstellt wurde.

Sie können angeben, ob das Objekt gelöscht werden soll, wenn das Objekt erstellt wird. Weitere Informationen finden Sie unter [CException::CException](#cexception).

Sie müssen nur `Delete` anrufen, wenn Sie den C++-Catch-Mechanismus **try**- **catch** verwenden. Wenn Sie die MFC-Makros **TRY** und **CATCH**verwenden, rufen diese Makros diese Funktion automatisch auf.

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError

Rufen Sie diese Memberfunktion auf, um Fehlertext in einem Meldungsfeld an den Benutzer zu melden.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Parameter

*nType*<br/>
Gibt den Stil des Meldungsfelds an. Wenden Sie eine beliebige Kombination der [Meldungsfeldstile](styles-used-by-mfc.md#message-box-styles) auf das Feld an. Wenn Sie diesen Parameter nicht angeben, ist der Standardwert MB_OK.

*nMessageID*<br/>
Gibt die Ressourcen-ID (Zeichenfolgentabelleneintrag) einer Meldung an, die angezeigt werden soll, wenn das Ausnahmeobjekt keine Fehlermeldung aufweist. Wenn 0, wird die Meldung "Keine Fehlermeldung ist verfügbar" angezeigt.

### <a name="return-value"></a>Rückgabewert

Ein `AfxMessageBox` Wert; andernfalls 0, wenn nicht genügend Arbeitsspeicher vorhanden ist, um das Meldungsfeld anzuzeigen. Siehe [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) für die möglichen Rückgabewerte.

### <a name="example"></a>Beispiel

Hier ist ein Beispiel `CException::ReportError`für die Verwendung von . Ein weiteres Beispiel finden Sie im Beispiel für [CATCH](exception-processing.md#catch).

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
[Hierarchiediagramm](../hierarchy-chart.md)<br/>
[Ausnahmeverarbeitung](exception-processing.md)<br/>
[Wie kann ich: Erstellen Sie meine eigenen benutzerdefinierten Ausnahmeklassen](https://go.microsoft.com/fwlink/p/?linkid=128045)
