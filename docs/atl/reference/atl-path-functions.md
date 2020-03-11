---
title: ATL-Pfad Funktionen
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865026"
---
# <a name="atl-path-functions"></a>ATL-Pfad Funktionen

ATL stellt die atlpath-Klasse zum Bearbeiten von Pfaden in Form von [cpatht](cpatht-class.md)bereit. Diesen Code finden Sie in der Datei "atlpath. h".

### <a name="related-classes"></a>Verwandte Klassen

|||
|-|-|
|[CPathT-Klasse](cpatht-class.md)|Diese Klasse stellt einen Pfad dar.|

### <a name="related-typedefs"></a>Verwandte Typedefs

|||
|-|-|
|`CPath`|Eine Spezialisierung von [cpatht](cpatht-class.md) mithilfe von `CString`.|
|`CPathA`|Eine Spezialisierung von [cpatht](cpatht-class.md) mithilfe von `CStringA`.|
|`CPathW`|Eine Spezialisierung von [cpatht](cpatht-class.md) mithilfe von `CStringW`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[Atlpath:: addbackschräg Strich](#addbackslash)|Diese Funktion ist ein überladener Wrapper für [pathaddbackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[Atlpath:: AddExtension](#addextension)|Diese Funktion ist ein überladener Wrapper für [pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[Atlpath:: Append](#append)|Diese Funktion ist ein überladener Wrapper für [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[Atlpath:: Buildroot](#buildroot)|Diese Funktion ist ein überladener Wrapper für [pathbuildroot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[Atlpath:: Canonicalize](#canonicalize)|Diese Funktion ist ein überladener Wrapper für [pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[Atlpath:: Combine](#combine)|Diese Funktion ist ein überladener Wrapper für [pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[Atlpath:: commonprefix](#commonprefix)|Diese Funktion ist ein überladener Wrapper für [pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[Atlpath:: compactpath](#compactpath)|Diese Funktion ist ein überladener Wrapper für [pathcompactpath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[Atlpath:: compactpathex](#compactpathex)|Diese Funktion ist ein überladener Wrapper für [pathcompactpathex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[Atlpath:: fileexistiert](#fileexists)|Diese Funktion ist ein überladener Wrapper für [pathfilevorhanden](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[Atlpath:: findextension](#findextension)|Diese Funktion ist ein überladener Wrapper für [pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[Atlpath:: findfilename](#findfilename)|Diese Funktion ist ein überladener Wrapper für [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[Atlpath:: getdrivenzuber](#getdrivenumber)|Diese Funktion ist ein überladener Wrapper für [pathgetdrivenumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[Atlpath:: IsDirectory](#isdirectory)|Diese Funktion ist ein überladener Wrapper für [pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[Atlpath:: isfilespec](#isfilespec)|Diese Funktion ist ein überladener Wrapper für [pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[Atlpath:: istreufix](#isprefix)|Diese Funktion ist ein überladener Wrapper für " [pthistreufix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)".|
|[Atlpath:: IsRelative](#isrelative)|Diese Funktion ist ein überladener Wrapper für [pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[Atlpath:: IsRoot](#isroot)|Diese Funktion ist ein überladener Wrapper für [pathisroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[Atlpath:: issameroot](#issameroot)|Diese Funktion ist ein überladener Wrapper für " [pthissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)".|
|[Atlpath:: IsUnc](#isunc)|Diese Funktion ist ein überladener Wrapper für [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[Atlpath:: isuncserver](#isuncserver)|Diese Funktion ist ein überladener Wrapper für [pathisuncserver](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[Atlpath:: isuncservershare](#isuncservershare)|Diese Funktion ist ein überladener Wrapper für [pathisuncservershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[Atlpath:: makepretty](#makepretty)|Diese Funktion ist ein überladener Wrapper für [pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[Atlpath:: matchspec](#matchspec)|Diese Funktion ist ein überladener Wrapper für [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[Atlpath:: quotespaces](#quotespaces)|Diese Funktion ist ein überladener Wrapper für [pathquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[Atlpath:: RelativePathTo](#relativepathto)|Diese Funktion ist ein überladener Wrapper für [pathrelativepathto](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[Atlpath:: removeargs](#removeargs)|Diese Funktion ist ein überladener Wrapper für " [pthremuveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)".|
|[Atlpath:: removebackschräg Strich](#removebackslash)|Diese Funktion ist ein überladener Wrapper für " [pthremuvebackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)".|
|[Atlpath:: removeblank](#removeblanks)|Diese Funktion ist ein überladener Wrapper für " [pthremuveblank](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)".|
|[Atlpath:: removeextension](#removeextension)|Diese Funktion ist ein überladener Wrapper für " [pthremuveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)".|
|[Atlpath:: removefilespec](#removefilespec)|Diese Funktion ist ein überladener Wrapper für " [pthremuvefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)".|
|[Atlpath:: renameextension](#renameextension)|Diese Funktion ist ein überladener Wrapper für [pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[Atlpath:: skiproot](#skiproot)|Diese Funktion ist ein überladener Wrapper für [pathskiproot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[Atlpath:: strippath](#strippath)|Diese Funktion ist ein überladener Wrapper für [pathstrippath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[Atlpath:: striptor](#striptoroot)|Diese Funktion ist ein überladener Wrapper für [pathstriptoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[Atlpath:: unquotespaces](#unquotespaces)|Diese Funktion ist ein überladener Wrapper für [pathunquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlpath. h

## <a name="addbackslash"></a>Atlpath:: addbackschräg Strich

Diese Funktion ist ein überladener Wrapper für [pathaddbackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Syntax

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathaddbackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) .

## <a name="addextension"></a>Atlpath:: AddExtension

Diese Funktion ist ein überladener Wrapper für [pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Syntax

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) .

## <a name="append"></a>Atlpath:: Append

Diese Funktion ist ein überladener Wrapper für [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Syntax

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) .

## <a name="buildroot"></a>Atlpath:: Buildroot

Diese Funktion ist ein überladener Wrapper für [pathbuildroot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Syntax

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathbuildroot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) .

## <a name="canonicalize"></a>Atlpath:: Canonicalize

Diese Funktion ist ein überladener Wrapper für [pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Syntax

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) .

## <a name="combine"></a>Atlpath:: Combine

Diese Funktion ist ein überladener Wrapper für [pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

### <a name="syntax"></a>Syntax

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter pathcombine.

## <a name="commonprefix"></a>Atlpath:: commonprefix

Diese Funktion ist ein überladener Wrapper für [pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

### <a name="syntax"></a>Syntax

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) .

## <a name="compactpath"></a>Atlpath:: compactpath

Diese Funktion ist ein überladener Wrapper für [pathcompactpath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

### <a name="syntax"></a>Syntax

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathcompactpath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) .

## <a name="compactpathex"></a>Atlpath:: compactpathex

Diese Funktion ist ein überladener Wrapper für [pathcompactpathex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

### <a name="syntax"></a>Syntax

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathcompactpathex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) .

## <a name="fileexists"></a>Atlpath:: fileexistiert

Diese Funktion ist ein überladener Wrapper für [pathfilevorhanden](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Syntax

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathfilevorhanden](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) .

## <a name="findextension"></a>Atlpath:: findextension

Diese Funktion ist ein überladener Wrapper für [pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Syntax

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) .

## <a name="findfilename"></a>Atlpath:: findfilename

Diese Funktion ist ein überladener Wrapper für [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Syntax

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) .

## <a name="getdrivenumber"></a>Atlpath:: getdrivenzuber

Diese Funktion ist ein überladener Wrapper für [pathgetdrivenumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Syntax

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathgetdrivenumschlag](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) .

## <a name="isdirectory"></a>Atlpath:: IsDirectory

Diese Funktion ist ein überladener Wrapper für [pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter pathisdirectory.

## <a name="isfilespec"></a>Atlpath:: isfilespec

Diese Funktion ist ein überladener Wrapper für [pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) .

## <a name="isprefix"></a>Atlpath:: istreufix

Diese Funktion ist ein überladener Wrapper für " [pthistreufix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)".

### <a name="syntax"></a>Syntax

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthistreufix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) ".

## <a name="isrelative"></a>Atlpath:: IsRelative

Diese Funktion ist ein überladener Wrapper für [pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Syntax

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) .

## <a name="isroot"></a>Atlpath:: IsRoot

Diese Funktion ist ein überladener Wrapper für [pathisroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathisroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) .

## <a name="issameroot"></a>Atlpath:: issameroot

Diese Funktion ist ein überladener Wrapper für " [pthissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)".

### <a name="syntax"></a>Syntax

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) ".

## <a name="isunc"></a>Atlpath:: IsUnc

Diese Funktion ist ein überladener Wrapper für [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) .

## <a name="isuncserver"></a>Atlpath:: isuncserver

Diese Funktion ist ein überladener Wrapper für [pathisuncserver](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathisuncserver](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) .

## <a name="isuncservershare"></a>Atlpath:: isuncservershare

Diese Funktion ist ein überladener Wrapper für [pathisuncservershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathisuncservershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) .

## <a name="makepretty"></a>Atlpath:: makepretty

Diese Funktion ist ein überladener Wrapper für [pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Syntax

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) .

## <a name="matchspec"></a>Atlpath:: matchspec

Diese Funktion ist ein überladener Wrapper für [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Syntax

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) .

## <a name="quotespaces"></a>Atlpath:: quotespaces

Diese Funktion ist ein überladener Wrapper für [pathquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Syntax

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) .

## <a name="relativepathto"></a>Atlpath:: RelativePathTo

Diese Funktion ist ein überladener Wrapper für [pathrelativepathto](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

### <a name="syntax"></a>Syntax

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden [Sie unter pathrelativepathto](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) .

## <a name="removeargs"></a>Atlpath:: removeargs

Diese Funktion ist ein überladener Wrapper für " [pthremuveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)".

### <a name="syntax"></a>Syntax

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthremuveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) ".

## <a name="removebackslash"></a>Atlpath:: removebackschräg Strich

Diese Funktion ist ein überladener Wrapper für " [pthremuvebackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)".

### <a name="syntax"></a>Syntax

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Ausführliche Informationen finden Sie unter " [pthremuvebackschräg Strich](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) ".

## <a name="removeblanks"></a>Atlpath:: removeblank

Diese Funktion ist ein überladener Wrapper für " [pthremuveblank](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)".

### <a name="syntax"></a>Syntax

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthremuveblank](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) ".

## <a name="removeextension"></a>Atlpath:: removeextension

Diese Funktion ist ein überladener Wrapper für " [pthremuveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)".

### <a name="syntax"></a>Syntax

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthremuveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) ".

## <a name="removefilespec"></a>Atlpath:: removefilespec

Diese Funktion ist ein überladener Wrapper für " [pthremuvefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)".

### <a name="syntax"></a>Syntax

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [pthremuvefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) ".

## <a name="renameextension"></a>Atlpath:: renameextension

Diese Funktion ist ein überladener Wrapper für [pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Syntax

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) .

## <a name="skiproot"></a>Atlpath:: skiproot

Diese Funktion ist ein überladener Wrapper für [pathskiproot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Syntax

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathskiproot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) .

## <a name="strippath"></a>Atlpath:: strippath

Diese Funktion ist ein überladener Wrapper für [pathstrippath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Syntax

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathstrippath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) .

## <a name="striptoroot"></a>Atlpath:: striptor

Diese Funktion ist ein überladener Wrapper für [pathstriptoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Syntax

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathstriptor oot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) .

## <a name="unquotespaces"></a>Atlpath:: unquotespaces

Diese Funktion ist ein überladener Wrapper für [pathunquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Syntax

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [pathunquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) .
