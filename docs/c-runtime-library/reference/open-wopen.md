---
title: _open, _wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: 4ce6e9aebe5d058143ad737f9c9db5bb68b30b1f
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150724"
---
# <a name="_open-_wopen"></a>_open, _wopen

Öffnet eine Datei. Diese Funktionen sind veraltet, da sichere Versionen verfügbar sind; siehe [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntax

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>Parameter

*filename*<br/>
Dateiname

*Oflag*<br/>
Die Art der zulässigen Vorgänge.

*pmode*<br/>
Berechtigungsmodus.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Dateideskriptor für die geöffnete Datei zurück. Der Rückgabewert-1 gibt einen Fehler an. in diesem Fall wird **errno** auf einen der folgenden Werte festgelegt.

|errno-Wert|Bedingung|
|-|-|
| **EACCES** | Versuch, eine schreibgeschützte Datei zum Schreiben zu öffnen, der Freigabemodus der Datei lässt die angegebenen Vorgänge nicht zu, oder der vorgegebene Pfad ist ein Verzeichnis. |
| **EEXIST** | **_O_CREAT** und **_O_EXCL** Flags angegeben, aber der *Dateiname* ist bereits vorhanden. |
| **EINVAL** | Ungültiges *Oflag* -oder *pmode* -Argument. |
| **EMFILE** | Es sind keine weiteren Dateideskriptoren verfügbar (zu viele Dateien sind geöffnet). |
| **ENOENT** | Datei oder Pfad nicht gefunden. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_open** -Funktion öffnet die durch *Dateiname* angegebene Datei und bereitet Sie für das Lesen oder schreiben vor, wie von *Oflag*angegeben. **_wopen** ist eine breit Zeichen Version von **_open**. Das *filename* -Argument für **_wopen** ist eine Zeichenfolge mit breit Zeichen. **_wopen** und **_open** Verhalten sich andernfalls identisch.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*Oflag* ist ein ganzzahliger Ausdruck, der aus einer oder mehreren der folgenden Manifest-Konstanten oder Konstanten Kombinationen gebildet wird, die in \<fcntl. h-> definiert sind.

|*Oflag* -Konstante|Verhalten|
|-|-|
| **_O_APPEND** | Verschiebt den Dateizeiger vor jedem Schreibvorgang an das Ende der Datei. |
| **_O_BINARY** | Öffnet die Datei im Binärmodus (nicht übersetzt). (Eine Beschreibung des binären Modus finden Sie unter [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Erstellt eine Datei und öffnet sie zum Schreiben. Hat keine Auswirkung, wenn die durch *filename* angegebene Datei vorhanden ist. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Erstellt eine Datei als temporär und schreibt sie, wenn möglich, nicht auf den Datenträger. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Erstellt eine temporäre Datei. Die Datei wird gelöscht, wenn der letzte Dateideskriptor geschlossen wird. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; `_O_EXCL` | Gibt einen Fehlerwert zurück, wenn eine durch *filename* angegebene Datei vorhanden ist. Gilt nur bei Verwendung mit **_O_CREAT**. |
| **_O_NOINHERIT** | Verhindert die Erstellung eines gemeinsam verwendeten Dateideskriptors. |
| **_O_RANDOM** | Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **_O_RDONLY** | Öffnet eine Datei nur zum Lesen. Kann nicht mit **_O_RDWR** oder **_O_WRONLY**angegeben werden. |
| **_O_RDWR** | Öffnet eine Datei zum Lesen und zum Schreiben. Kann nicht mit **_O_RDONLY** oder **_O_WRONLY**angegeben werden. |
| **_O_SEQUENTIAL** | Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **_O_TEXT** | Öffnet eine Datei im Textmodus (übersetzt). (Weitere Informationen finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Öffnet eine Datei und verkürzt sie auf die Länge Null. Für die Datei muss Schreibberechtigung bestehen. Kann nicht mit **_O_RDONLY**angegeben werden. **_O_TRUNC** , die mit **_O_CREAT** verwendet werden, öffnet eine vorhandene Datei oder erstellt eine Datei. **Hinweis:** Das **_O_TRUNC** -Flag zerstört den Inhalt der angegebenen Datei. |
| **_O_WRONLY** | Öffnet eine Datei nur zum Schreiben. Kann nicht mit **_O_RDONLY** oder **_O_RDWR**angegeben werden. |
| **_O_U16TEXT** | Öffnet eine Datei im Unicode-UTF-16-Modus. |
| **_O_U8TEXT** | Öffnet eine Datei im Unicode-UTF-8-Modus. |
| **_O_WTEXT** | Öffnet eine Datei im Unicode-Modus. |

Zum Angeben des Datei Zugriffsmodus müssen Sie entweder **_O_RDONLY**, **_O_RDWR**oder **_O_WRONLY**angeben. Es gibt keinen Standardwert für den Zugriffsmodus.

Wenn **_O_WTEXT** verwendet wird, um eine Datei zum Lesen zu öffnen, liest **_open** den Anfang der Datei und überprüft, ob eine Byte Reihenfolge-Marke (BOM) angezeigt wird. Wenn eine BOM vorhanden ist, wird die Datei je nach BOM als UTF-8 oder UTF-16LE behandelt. Wenn keine BOM vorhanden ist, wird die Datei als ANSI behandelt. Wenn eine Datei mit **_O_WTEXT**zum Schreiben geöffnet wird, wird UTF-16 verwendet. Unabhängig von früheren Einstellungen oder Byte Reihenfolge Markierungen wird die Datei immer als UTF-8 geöffnet, wenn **_O_U8TEXT** verwendet wird. Wenn **_O_U16TEXT** verwendet wird, wird die Datei immer als UTF-16 geöffnet.

Wenn eine Datei mit **_O_WTEXT**, **_O_U8TEXT**oder **_O_U16TEXT**im Unicode-Modus geöffnet wird, übersetzen Eingabefunktionen die aus der Datei gelesenen Daten in UTF-16-Daten, die als Typ **wchar_t**gespeichert werden. Funktionen, die in eine im Unicode-Modus geöffnete Datei schreiben, erwarten Puffer, die UTF-16-Daten enthalten, die als Typ **wchar_t**gespeichert sind. Wenn eine Datei als UTF-8 kodiert ist, dann werden UTF-16-Daten beim Schreiben in UTF-8 übersetzt, und die UTF-8-kodierten Inhalte der Datei werden beim Lesen in UTF-16 übersetzt. Der Versuch, eine ungerade Anzahl von Bytes im Unicode-Modus zu lesen oder zu schreiben, führt zu einem Parametervalidierungsfehler. Wenn Sie Daten lesen oder schreiben möchten, die in Ihrem Programm als UTF-8 gespeichert sind, verwenden Sie den Text- oder Binärdateienmodus anstelle eines Unicode-Modus. Sie sind für jede erforderliche Kodierungsübersetzung verantwortlich.

Wenn **_open** mit **_O_WRONLY** |  **_O_APPEND** (Append-Modus) und **_O_WTEXT**, **_O_U16TEXT**oder **_O_U8TEXT**aufgerufen wird, versucht es zuerst, die Datei zum Lesen und schreiben zu öffnen, die BOM zu lesen und Sie zum Schreiben zu öffnen. Wenn das Öffnen der Datei zum Lesen und Schreiben fehlschlägt, wird die Datei nur zum Schreiben geöffnet und der Standardwert für die Unicode-Moduseinstellung verwendet.

Wenn zwei oder mehr Manifest-Konstanten verwendet werden, um das *Oflag* -Argument zu bilden, werden die Konstanten mit dem bitweisen or- **&#124;** Operator () kombiniert. Eine Darstellung des Binär- und Textmodus finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Das *pmode* -Argument ist nur erforderlich, wenn **_O_CREAT** angegeben wird. Wenn die Datei bereits vorhanden ist, wird *pmode* ignoriert. Andernfalls gibt *pmode* die Datei Berechtigungseinstellungen an, die festgelegt werden, wenn die neue Datei zum ersten Mal geschlossen wird. **_open** wendet die aktuelle Datei Berechtigungs Maske auf *pmode* an, bevor die Berechtigungen festgelegt werden. (Weitere Informationen finden Sie unter [_umask](umask.md).) *pmode* ist ein ganzzahliger Ausdruck, der eine oder beide der folgenden Manifest-Konstanten enthält, die in \<sys\status-h-> definiert sind.

|*pmode*|Bedeutung|
|-|-|
| **_S_IREAD** | Nur Lesen zugelassen. |
| **_S_IWRITE** | Schreiben zugelassen. (Lässt tatsächlich Lesen und Schreiben zu.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Lesen und Schreiben erlaubt. |

Wenn beide Konstanten angegeben werden, werden Sie mit dem bitweisen OR-Operator ( **&#124;** ) verknüpft. In Windows sind alle Dateien lesbar, eine schreibgeschützte Berechtigung ist nicht verfügbar. Daher sind die Modi **_S_IWRITE** und **_S_IREAD** |  **_S_IWRITE** Äquivalent.

Wenn ein anderer Wert als eine Kombination aus **_S_IREAD** und **_S_IWRITE** für *pmode*angegeben wird – auch wenn er einen gültigen *pmode* -Wert in einem anderen Betriebssystem angeben würde – oder wenn ein anderer Wert als die zulässigen *Oflag* -Werte angegeben wird, generiert die Funktion eine-Assertion im Debugmodus und ruft den Handler für ungültige Parameter auf, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück und legt **errno** auf **EINVAL**fest.

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen**|\<io.h> oder \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_open** und **_wopen** sind Microsoft-Erweiterungen. Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen der [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Output

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Weitere Informationen

[E/A auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
