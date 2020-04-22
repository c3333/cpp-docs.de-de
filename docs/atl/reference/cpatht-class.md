---
title: CPathT-Klasse
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: c10b854ae5c2d7167a067675b1391be24b6a8122
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746595"
---
# <a name="cpatht-class"></a>CPathT-Klasse

Diese Klasse stellt einen Pfad dar.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parameter

*StringType*<br/>
Die ATL/MFC-Zeichenfolgenklasse, die für den Pfad verwendet werden soll (siehe [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Ein konstanter Zeichenfolgentyp.|
|[CPathT::PXSTR](#pxstr)|Ein Zeichenfolgentyp.|
|[CPathT::XCHAR](#xchar)|Ein Zeichentyp.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Der Konstruktor für den Pfad.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Rufen Sie diese Methode auf, um am Ende einer Zeichenfolge einen umgekehrten Schrägstrich hinzuzufügen, um die richtige Syntax für einen Pfad zu erstellen.|
|[CPathT::AddExtension](#addextension)|Rufen Sie diese Methode auf, um einem Pfad eine Dateierweiterung hinzuzufügen.|
|[CPathT::Anfügen](#append)|Rufen Sie diese Methode auf, um eine Zeichenfolge an den aktuellen Pfad anzuhängen.|
|[CPathT::BuildRoot](#buildroot)|Rufen Sie diese Methode auf, um einen Stammpfad aus einer bestimmten Laufwerknummer zu erstellen.|
|[CPathT::Canonicalize](#canonicalize)|Rufen Sie diese Methode auf, um den Pfad in kanonische Form zu konvertieren.|
|[CPathT::Kombinieren](#combine)|Rufen Sie diese Methode auf, um eine Zeichenfolge, die einen Verzeichnisnamen darstellt, und eine Zeichenfolge, die einen Dateipfadnamen darstellt, in einem Pfad zu verketten.|
|[CPathT::CommonPrefix](#commonprefix)|Rufen Sie diese Methode auf, um zu bestimmen, ob der angegebene Pfad ein gemeinsames Präfix mit dem aktuellen Pfad verwendet.|
|[CPathT::CompactPath](#compactpath)|Rufen Sie diese Methode auf, um einen Dateipfad zu abschneiden, der in eine bestimmte Pixelbreite passt, indem Pfadkomponenten durch Ellipsen ersetzt werden.|
|[CPathT::CompactPathEx](#compactpathex)|Rufen Sie diese Methode auf, um einen Dateipfad zu abschneiden, der in eine bestimmte Anzahl von Zeichen passt, indem Pfadkomponenten durch Ellipsen ersetzt werden.|
|[CPathT::FileExists](#fileexists)|Rufen Sie diese Methode auf, um zu überprüfen, ob die Datei unter diesem Pfadnamen vorhanden ist.|
|[CPathT::FindExtension](#findextension)|Rufen Sie diese Methode auf, um die Position der Dateierweiterung innerhalb des Pfads zu finden.|
|[CPathT::FindFileName](#findfilename)|Rufen Sie diese Methode auf, um die Position des Dateinamens innerhalb des Pfads zu finden.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Rufen Sie diese Methode auf, um den Pfad nach einem Laufwerkbuchstaben im Bereich von 'A' bis 'Z' zu durchsuchen und die entsprechende Laufwerksnummer zurückzugeben.|
|[CPathT::GetExtension](#getextension)|Rufen Sie diese Methode auf, um die Dateierweiterung aus dem Pfad abzurufen.|
|[CPathT::IsDirectory](#isdirectory)|Rufen Sie diese Methode auf, um zu überprüfen, ob der Pfad ein gültiges Verzeichnis ist.|
|[CPathT::IsFileSpec](#isfilespec)|Rufen Sie diese Methode auf, um einen Pfad nach Pfadtrennzeichen\\zu durchsuchen (z. B. ':' oder ' ' ). Wenn keine Pfadabgrenzungszeichen vorhanden sind, wird der Pfad als Dateispezifikationspfad betrachtet.|
|[CPathT::IsPrefix](#isprefix)|Rufen Sie diese Methode auf, um zu bestimmen, ob ein Pfad ein gültiges Präfix des Typs enthält, der von *pszPrefix*übergeben wird.|
|[CPathT::IsRelative](#isrelative)|Rufen Sie diese Methode auf, um zu bestimmen, ob der Pfad relativ ist.|
|[CPathT::IsRoot](#isroot)|Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad um einen Verzeichnisstamm handelt.|
|[CPathT::IsSameRoot](#issameroot)|Rufen Sie diese Methode auf, um zu bestimmen, ob ein anderer Pfad eine gemeinsame Stammkomponente mit dem aktuellen Pfad enthält.|
|[CPathT::IsUNC](#isunc)|Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad um einen gültigen UNC-Pfad (Universal Naming Convention) für einen Server und eine Freigabe handelt.|
|[CPathT::IsUNCServer](#isuncserver)|Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad nur um einen gültigen UNC-Pfad (Universal Naming Convention) für einen Server handelt.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Rufen Sie diese Methode auf, um zu bestimmen, ob es \\ \ sich bei dem Pfad um einen gültigen UNC-Freigabepfad (Universal Naming Convention) *handelt.*\ *share*|
|[CPathT::MakePretty](#makepretty)|Rufen Sie diese Methode auf, um einen Pfad zu allen Kleinbuchstaben zu konvertieren, um dem Pfad eine konsistente Darstellung zu verleihen.|
|[CPathT::MatchSpec](#matchspec)|Rufen Sie diese Methode auf, um den Pfad nach einer Zeichenfolge zu durchsuchen, die einen Platzhalterübereinstimmungstyp enthält.|
|[CPathT::QuoteSpaces](#quotespaces)|Rufen Sie diese Methode auf, um den Pfad in Anführungszeichen einzuschließen, wenn er Leerzeichen enthält.|
|[CPathT::RelativePathTo](#relativepathto)|Rufen Sie diese Methode auf, um einen relativen Pfad von einer Datei oder einem Ordner zu einem anderen zu erstellen.|
|[CPathT::RemoveArgs](#removeargs)|Rufen Sie diese Methode auf, um alle Befehlszeilenargumente aus dem Pfad zu entfernen.|
|[CPathT::RemoveBackslash](#removebackslash)|Rufen Sie diese Methode auf, um den nachgestellten umgekehrten Schrägstrich aus dem Pfad zu entfernen.|
|[CPathT::RemoveBlanks](#removeblanks)|Rufen Sie diese Methode auf, um alle führenden und nachfolgenden Leerzeichen aus dem Pfad zu entfernen.|
|[CPathT::RemoveExtension](#removeextension)|Rufen Sie diese Methode auf, um die Dateierweiterung aus dem Pfad zu entfernen, falls vorhanden.|
|[CPathT::RemoveFileSpec](#removefilespec)|Rufen Sie diese Methode auf, um den nachfolgenden Dateinamen und umgekehrten Schrägstrich aus dem Pfad zu entfernen, sofern er sie enthält.|
|[CPathT::RenameExtension](#renameextension)|Rufen Sie diese Methode auf, um die Dateinamenerweiterung im Pfad durch eine neue Erweiterung zu ersetzen. Wenn der Dateiname keine Erweiterung enthält, wird die Erweiterung an das Ende der Zeichenfolge angehängt.|
|[CPathT::SkipRoot](#skiproot)|Rufen Sie diese Methode auf, um einen Pfad zu analysieren, wobei der Laufwerkbuchstabe oder die UNC-Server-/Freigabepfadteile ignoriert werden.|
|[CPathT::StripPath](#strippath)|Rufen Sie diese Methode auf, um den Pfadteil eines vollqualifizierten Pfads und Dateinamens zu entfernen.|
|[CPathT::StripToRoot](#striptoroot)|Rufen Sie diese Methode auf, um alle Teile des Pfads mit Ausnahme der Stamminformationen zu entfernen.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Rufen Sie diese Methode auf, um Anführungszeichen vom Anfang und Ende eines Pfads zu entfernen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.|
|[CPathT::operator StringType &](#operator_stringtype_amp)|Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.|
|[CPathT::Operator +=](#operator_add_eq)|Dieser Operator fügt eine Zeichenfolge an den Pfad an.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Der Pfad.|

## <a name="remarks"></a>Bemerkungen

`CPath`, `CPathA`und `CPathW` sind Instanziierungen wie `CPathT` folgt definiert:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash

Rufen Sie diese Methode auf, um am Ende einer Zeichenfolge einen umgekehrten Schrägstrich hinzuzufügen, um die richtige Syntax für einen Pfad zu erstellen. Wenn der Pfad bereits einen nachgestellten umgekehrten Schrägstrich hat, wird kein umgekehrter Schrägstrich hinzugefügt.

```cpp
void AddBackslash();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT::AddExtension

Rufen Sie diese Methode auf, um einem Pfad eine Dateierweiterung hinzuzufügen.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parameter

*pszExtension*<br/>
Die hinzuzufügende Dateierweiterung.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

## <a name="cpathtappend"></a><a name="append"></a>CPathT::Anfügen

Rufen Sie diese Methode auf, um eine Zeichenfolge an den aktuellen Pfad anzuhängen.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parameter

*pszMehr*<br/>
Die anzufügende Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPathT::BuildRoot

Rufen Sie diese Methode auf, um einen Stammpfad aus einer bestimmten Laufwerknummer zu erstellen.

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parameter

*Idrive*<br/>
Die Laufwerksnummer (0 ist A:, 1 ist B:, usw.).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Canonicalize

Rufen Sie diese Methode auf, um den Pfad in kanonische Form zu konvertieren.

```cpp
void Canonicalize();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT::Kombinieren

Rufen Sie diese Methode auf, um eine Zeichenfolge, die einen Verzeichnisnamen darstellt, und eine Zeichenfolge, die einen Dateipfadnamen darstellt, in einem Pfad zu verketten.

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parameter

*pszDir*<br/>
Der Verzeichnispfad.

*pszFile*<br/>
Der Dateipfad.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix

Rufen Sie diese Methode auf, um zu bestimmen, ob der angegebene Pfad ein gemeinsames Präfix mit dem aktuellen Pfad verwendet.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parameter

*pszOther*<br/>
Der Pfad, der mit dem aktuellen zu vergleichen ist.

### <a name="return-value"></a>Rückgabewert

Gibt das allgemeine Präfix zurück.

### <a name="remarks"></a>Bemerkungen

Ein Präfix ist einer der folgenden\\\\Typen: "C: ", ".", "..", ".. \\\\". Weitere Informationen finden Sie unter [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath

Rufen Sie diese Methode auf, um einen Dateipfad zu abschneiden, der in eine bestimmte Pixelbreite passt, indem Pfadkomponenten durch Ellipsen ersetzt werden.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parameter

*Hdc*<br/>
Der Gerätekontext, der für Schriftartmetriken verwendet wird.

*nWidth*<br/>
Die Breite in Pixel, in die die Zeichenfolge passen muss.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx

Rufen Sie diese Methode auf, um einen Dateipfad zu abschneiden, der in eine bestimmte Anzahl von Zeichen passt, indem Pfadkomponenten durch Ellipsen ersetzt werden.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parameter

*nMaxChars*<br/>
Die maximale Anzahl von Zeichen, die in der neuen Zeichenfolge enthalten sein sollen, einschließlich des beendenden NULL-Zeichens.

*dwFlags*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

## <a name="cpathtcpatht"></a><a name="cpatht"></a>CPathT::CPathT

Der Konstruktor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parameter

*pszPath*<br/>
Der Zeiger auf eine Pfadzeichenfolge.

*path*<br/>
Die Pfadzeichenfolge.

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists

Rufen Sie diese Methode auf, um zu überprüfen, ob die Datei unter diesem Pfadnamen vorhanden ist.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Datei vorhanden ist, ANDERNFALLS FALSE.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPathT::FindExtension

Rufen Sie diese Methode auf, um die Position der Dateierweiterung innerhalb des Pfads zu finden.

```
int FindExtension() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Position des "." vor der Erweiterung zurück. Wenn keine Erweiterung gefunden wird, gibt -1 zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT::FindFileName

Rufen Sie diese Methode auf, um die Position des Dateinamens innerhalb des Pfads zu finden.

```
int FindFileName() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Dateinamens zurück. Wenn kein Dateiname gefunden wird, gibt -1 zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT::GetDriveNumber

Rufen Sie diese Methode auf, um den Pfad nach einem Laufwerkbuchstaben im Bereich von 'A' bis 'Z' zu durchsuchen und die entsprechende Laufwerksnummer zurückzugeben.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Laufwerksnummer als ganze Zahl von 0 bis 25 (entsprechend "A" bis "Z") zurück, wenn der Pfad einen Laufwerkbuchstaben hat, oder -1 andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT::GetExtension

Rufen Sie diese Methode auf, um die Dateierweiterung aus dem Pfad abzurufen.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Dateierweiterung zurück.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPathT::IsDirectory

Rufen Sie diese Methode auf, um zu überprüfen, ob der Pfad ein gültiges Verzeichnis ist.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null (16) zurück, wenn der Pfad ein Verzeichnis ist, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPathT::IsFileSpec

Rufen Sie diese Methode auf, um einen Pfad nach Pfadtrennzeichen\\zu durchsuchen (z. B. ':' oder ' ' ). Wenn keine Pfadabgrenzungszeichen vorhanden sind, wird der Pfad als Dateispezifikationspfad betrachtet.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn sich keine Pfadtrennzeichen innerhalb des Pfads befinden, oder FALSE, wenn Pfadtrennzeichen vorhanden sind.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT::IsPrefix

Rufen Sie diese Methode auf, um zu bestimmen, ob ein Pfad ein gültiges Präfix des Typs enthält, der von *pszPrefix*übergeben wird.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parameter

*pszPrefix*<br/>
Das Präfix, nach dem gesucht werden soll. Ein Präfix ist einer der folgenden\\\\Typen: "C: ", ".", "..", ".. \\\\".

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Pfad das Präfix enthält, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPathT::IsRelative

Rufen Sie diese Methode auf, um zu bestimmen, ob der Pfad relativ ist.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Pfad relativ ist, oder FALSE, wenn er absolut ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

## <a name="cpathtisroot"></a><a name="isroot"></a>CPathT::IsRoot

Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad um einen Verzeichnisstamm handelt.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Pfad ein Stamm ist, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPathT::IsSameRoot

Rufen Sie diese Methode auf, um zu bestimmen, ob ein anderer Pfad eine gemeinsame Stammkomponente mit dem aktuellen Pfad enthält.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parameter

*pszOther*<br/>
Der andere Pfad.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn beide Zeichenfolgen dieselbe Stammkomponente haben, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT::IsUNC

Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad um einen gültigen UNC-Pfad (Universal Naming Convention) für einen Server und eine Freigabe handelt.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn es sich bei dem Pfad um einen gültigen UNC-Pfad handelt, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT::IsUNCServer

Rufen Sie diese Methode auf, um zu bestimmen, ob es sich bei dem Pfad nur um einen gültigen UNC-Pfad (Universal Naming Convention) für einen Server handelt.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn es sich bei der Zeichenfolge um einen gültigen UNC-Pfad nur für einen Server (kein Freigabename) oder FALSE auf andere Weise handelt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT::IsUNCServerShare

Rufen Sie diese Methode auf, um zu bestimmen, ob es \\ \ sich bei dem Pfad um einen gültigen UNC-Freigabepfad (Universal Naming Convention) *handelt.*\ *share*

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn \\ \ sich der Pfad in der *Formularserverfreigabe*\ *share*befindet, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT::m_strPath

Der Pfad.

```
StringType m_strPath;
```

### <a name="remarks"></a>Bemerkungen

`StringType`ist der Vorlagenparameter für `CPathT`.

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>CPathT::MakePretty

Rufen Sie diese Methode auf, um einen Pfad zu allen Kleinbuchstaben zu konvertieren, um dem Pfad eine konsistente Darstellung zu verleihen.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Pfad konvertiert wurde, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT::MatchSpec

Rufen Sie diese Methode auf, um den Pfad nach einer Zeichenfolge zu durchsuchen, die einen Platzhalterübereinstimmungstyp enthält.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parameter

*pszSpec*<br/>
Zeiger auf eine null-terminierte Zeichenfolge mit dem Dateityp, nach dem gesucht werden soll. Um beispielsweise zu testen, ob es sich bei der Datei im aktuellen Pfad um eine DOC-Datei handelt, sollte *pszSpec* auf "*.doc" festgelegt werden.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Zeichenfolge übereinstimmt, oder FALSE andernfalls.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::Operator +=

Dieser Operator fügt eine Zeichenfolge an den Pfad an.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parameter

*pszMehr*<br/>
Die anzufügende Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt den aktualisierten Pfad zurück.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::operator const StringType&amp;

Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Zeichenfolge zurück, die den aktuellen Pfad darstellt, der von diesem Objekt verwaltet wird.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR

Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Zeichenfolge zurück, die den aktuellen Pfad darstellt, der von diesem Objekt verwaltet wird.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::operator StringType&amp;

Mit diesem Operator kann das Objekt wie eine Zeichenfolge behandelt werden.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt eine Zeichenfolge zurück, die den aktuellen Pfad darstellt, der von diesem Objekt verwaltet wird.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR

Ein konstanter Zeichenfolgentyp.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Bemerkungen

`StringType`ist der Vorlagenparameter für `CPathT`.

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR

Ein Zeichenfolgentyp.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Bemerkungen

`StringType`ist der Vorlagenparameter für `CPathT`.

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::QuoteSpaces

Rufen Sie diese Methode auf, um den Pfad in Anführungszeichen einzuschließen, wenn er Leerzeichen enthält.

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPathT::RelativePathTo

Rufen Sie diese Methode auf, um einen relativen Pfad von einer Datei oder einem Ordner zu einem anderen zu erstellen.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parameter

*pszVon*<br/>
Der Anfang des relativen Pfads.

*dwAttrVon*<br/>
Die Dateiattribute von *pszFrom*. Wenn dieser Wert FILE_ATTRIBUTE_DIRECTORY enthält, wird *pszFrom* als Verzeichnis angenommen. Andernfalls wird *pszFrom* als Datei angenommen.

*pszTo*<br/>
Der Endpunkt des relativen Pfads.

*dwAttrTo*<br/>
Die Dateiattribute von *pszTo*. Wenn dieser Wert FILE_ATTRIBUTE_DIRECTORY enthält, wird *von pszTo* als Verzeichnis angenommen. Andernfalls wird *pszTo* als Datei angenommen.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::RemoveArgs

Rufen Sie diese Methode auf, um alle Befehlszeilenargumente aus dem Pfad zu entfernen.

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash

Rufen Sie diese Methode auf, um den nachgestellten umgekehrten Schrägstrich aus dem Pfad zu entfernen.

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::RemoveBlanks

Rufen Sie diese Methode auf, um alle führenden und nachfolgenden Leerzeichen aus dem Pfad zu entfernen.

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT::RemoveExtension

Rufen Sie diese Methode auf, um die Dateierweiterung aus dem Pfad zu entfernen, falls vorhanden.

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT::RemoveFileSpec

Rufen Sie diese Methode auf, um den nachfolgenden Dateinamen und umgekehrten Schrägstrich aus dem Pfad zu entfernen, sofern er sie enthält.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::RenameExtension

Rufen Sie diese Methode auf, um die Dateinamenerweiterung im Pfad durch eine neue Erweiterung zu ersetzen. Wenn der Dateiname keine Erweiterung enthält, wird die Erweiterung an das Ende des Pfads angehängt.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parameter

*pszExtension*<br/>
Die neue Dateinamenerweiterung, der ein "."-Zeichen vorangestellt ist.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPathT::SkipRoot

Rufen Sie diese Methode auf, um einen Pfad zu analysieren, wobei der Laufwerkbuchstabe oder die UNC-Server-/Freigabepfadteile ignoriert werden.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Anfangs des Unterpfads zurück, der dem Stamm folgt (Laufwerkbuchstabe oder UNC-Server/Freigabe).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT::StripPath

Rufen Sie diese Methode auf, um den Pfadteil eines vollqualifizierten Pfads und Dateinamens zu entfernen.

```cpp
void StripPath();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPathT::StripToRoot

Rufen Sie diese Methode auf, um alle Teile des Pfads mit Ausnahme der Stamminformationen zu entfernen.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn ein gültiger Laufwerkbuchstabe im Pfad gefunden wurde, oder FALSE auf andere Weise.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT::UnquoteSpaces

Rufen Sie diese Methode auf, um Anführungszeichen vom Anfang und Ende eines Pfads zu entfernen.

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT::XCHAR

Ein Zeichentyp.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Bemerkungen

`StringType`ist der Vorlagenparameter für `CPathT`.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../atl/reference/atl-classes.md)<br/>
[CStringT-Klasse](../../atl-mfc-shared/reference/cstringt-class.md)
