---
title: ATL-Pfadfunktionen
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
ms.openlocfilehash: f3d8fa63e7fd20f8a0d6759fee8417b3fbc29486
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319218"
---
# <a name="atl-path-functions"></a>ATL-Pfadfunktionen

ATL stellt die ATLPath-Klasse zum Bearbeiten von Pfaden in Form von [CPathT](cpatht-class.md)bereit. Dieser Code finden Sie in atlpath.h.

### <a name="related-classes"></a>Verwandte Klassen

|||
|-|-|
|[CPathT-Klasse](cpatht-class.md)|Diese Klasse stellt einen Pfad dar.|

### <a name="related-typedefs"></a>Verwandte Typedefs

|||
|-|-|
|`CPath`|Eine Spezialisierung von [CPathT](cpatht-class.md) mit `CString`.|
|`CPathA`|Eine Spezialisierung von [CPathT](cpatht-class.md) mit `CStringA`.|
|`CPathW`|Eine Spezialisierung von [CPathT](cpatht-class.md) mit `CStringW`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Diese Funktion ist ein überladener Wrapper für [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Diese Funktion ist ein überladener Wrapper für [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Append](#append)|Diese Funktion ist ein überladener Wrapper für [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::BuildRoot](#buildroot)|Diese Funktion ist ein überladener Wrapper für [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Canonicalize](#canonicalize)|Diese Funktion ist ein überladener Wrapper für [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Combine](#combine)|Diese Funktion ist ein überladener Wrapper für [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Diese Funktion ist ein überladener Wrapper für [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Diese Funktion ist ein überladener Wrapper für [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Diese Funktion ist ein überladener Wrapper für [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Diese Funktion ist ein überladener Wrapper für [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Diese Funktion ist ein überladener Wrapper für [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Diese Funktion ist ein überladener Wrapper für [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Diese Funktion ist ein überladener Wrapper für [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Diese Funktion ist ein überladener Wrapper für [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Diese Funktion ist ein überladener Wrapper für [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Diese Funktion ist ein überladener Wrapper für [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::IsRelative](#isrelative)|Diese Funktion ist ein überladener Wrapper für [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::IsRoot](#isroot)|Diese Funktion ist ein überladener Wrapper für [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Diese Funktion ist ein überladener Wrapper für [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Diese Funktion ist ein überladener Wrapper für [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Diese Funktion ist ein überladener Wrapper für [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Diese Funktion ist ein überladener Wrapper für [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Diese Funktion ist ein überladener Wrapper für [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Diese Funktion ist ein überladener Wrapper für [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::QuoteSpaces](#quotespaces)|Diese Funktion ist ein überladener Wrapper für [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Diese Funktion ist ein überladener Wrapper für [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Diese Funktion ist ein überladener Wrapper für [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Diese Funktion ist ein überladener Wrapper für [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Diese Funktion ist ein überladener Wrapper für [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Diese Funktion ist ein überladener Wrapper für [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Diese Funktion ist ein überladener Wrapper für [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::RenameExtension](#renameextension)|Diese Funktion ist ein überladener Wrapper für [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Diese Funktion ist ein überladener Wrapper für [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Diese Funktion ist ein überladener Wrapper für [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Diese Funktion ist ein überladener Wrapper für [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Diese Funktion ist ein überladener Wrapper für [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlpath.h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath::AddBackSlash

Diese Funktion ist ein überladener Wrapper für [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Syntax

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAddBackslash.](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath::AddExtension

Diese Funktion ist ein überladener Wrapper für [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Syntax

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAddExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)

## <a name="atlpathappend"></a><a name="append"></a>ATLPath::Anfügen

Diese Funktion ist ein überladener Wrapper für [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Syntax

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathAppend.](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath::BuildRoot

Diese Funktion ist ein überladener Wrapper für [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Syntax

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathBuildRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath::Canonicalize

Diese Funktion ist ein überladener Wrapper für [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Syntax

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathCanonicalize.](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath::Kombinieren

Diese Funktion ist ein überladener Wrapper für [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

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

Weitere Informationen finden Sie unter PathCombine.

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath::CommonPrefix

Diese Funktion ist ein überladener Wrapper für [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

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

Weitere Informationen finden Sie unter [PathCommonPrefix.](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath::CompactPath

Diese Funktion ist ein überladener Wrapper für [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

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

Weitere Informationen finden Sie unter [PathCompactPath.](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath::CompactPathEx

Diese Funktion ist ein überladener Wrapper für [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

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

Weitere Informationen finden Sie unter [PathCompactPathEx.](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath::FileExists

Diese Funktion ist ein überladener Wrapper für [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Syntax

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFileExists.](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath::FindExtension

Diese Funktion ist ein überladener Wrapper für [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Syntax

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFindExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath::FindFileName

Diese Funktion ist ein überladener Wrapper für [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Syntax

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathFindFileName.](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath::GetDriveNumber

Diese Funktion ist ein überladener Wrapper für [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Syntax

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathGetDriveNumber.](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath::IsDirectory

Diese Funktion ist ein überladener Wrapper für [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter PathIsDirectory.

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath::IsFileSpec

Diese Funktion ist ein überladener Wrapper für [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath::IsPrefix

Diese Funktion ist ein überladener Wrapper für [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsPrefix.](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath::IsRelative

Diese Funktion ist ein überladener Wrapper für [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Syntax

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsRelative.](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath::IsRoot

Diese Funktion ist ein überladener Wrapper für [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath::IsSameRoot

Diese Funktion ist ein überladener Wrapper für [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsSameRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath::IsUNC

Diese Funktion ist ein überladener Wrapper für [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNC.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath::IsUNCServer

Diese Funktion ist ein überladener Wrapper für [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNCServer.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath::IsUNCServerShare

Diese Funktion ist ein überladener Wrapper für [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Syntax

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathIsUNCServerShare.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath::MakePretty

Diese Funktion ist ein überladener Wrapper für [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Syntax

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathMakePretty.](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath::MatchSpec

Diese Funktion ist ein überladener Wrapper für [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Syntax

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathMatchSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath::QuoteSpaces

Diese Funktion ist ein überladener Wrapper für [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Syntax

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathQuoteSpaces.](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath::RelativePathTo

Diese Funktion ist ein überladener Wrapper für [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

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

Weitere Informationen finden Sie unter [PathRelativePathTo.](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath::RemoveArgs

Diese Funktion ist ein überladener Wrapper für [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Syntax

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveArgs.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath::RemoveBackslash

Diese Funktion ist ein überladener Wrapper für [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Syntax

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveBackslash.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath::RemoveBlanks

Diese Funktion ist ein überladener Wrapper für [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Syntax

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveBlanks.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath::RemoveExtension

Diese Funktion ist ein überladener Wrapper für [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Syntax

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath::RemoveFileSpec

Diese Funktion ist ein überladener Wrapper für [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Syntax

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRemoveFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath::RenameExtension

Diese Funktion ist ein überladener Wrapper für [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Syntax

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathRenameExtension.](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath::SkipRoot

Diese Funktion ist ein überladener Wrapper für [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Syntax

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathSkipRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath::StripPath

Diese Funktion ist ein überladener Wrapper für [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Syntax

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathStripPath.](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath::StripToRoot

Diese Funktion ist ein überladener Wrapper für [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Syntax

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathStripToRoot.](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath::UnquoteSpaces

Diese Funktion ist ein überladener Wrapper für [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Syntax

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [PathUnquoteSpaces.](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)
