---
title: _sopen, _wsopen
ms.date: 4/2/2020
api_name:
- _sopen
- _wsopen
- _o__sopen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsopen
- wsopen
- _sopen
- _tsopen
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
ms.openlocfilehash: 0ee788823b62d97cdc81e901a812ba25f40359e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356404"
---
# <a name="_sopen-_wsopen"></a>_sopen, _wsopen

Öffnet eine Datei zur Freigabe. Sicherere Versionen dieser Funktionen sind verfügbar: siehe [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntax

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Dateiname

*oflag*<br/>
Die Art der zulässigen Vorgänge.

*shflag*<br/>
Die Art der zulässigen Freigabe.

*Pmode*<br/>
Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Dateideskriptor für die geöffnete Datei zurück.

Wenn *filename* oder *oflag* ein **NULL-Zeiger** ist oder *wenn oflag* oder *shflag* nicht innerhalb eines gültigen Wertebereichs liegt, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen -1 zurück und setzen **errno** auf einen der folgenden Werte.

|errno-Wert|Bedingung|
|-|-|
| **EACCES** | Der angegebene Pfad ist ein Verzeichnis, oder die Datei ist schreibgeschützt, aber es wurde versucht, sie zum Schreiben zu öffnen. |
| **EEXIST** | **_O_CREAT** und **_O_EXCL-Flags** wurden angegeben, aber *der Dateiname* ist bereits vorhanden. |
| **Einval** | Ungültiges *Oflag-* oder *Shflag-Argument.* |
| **EMFILE** | Es sind keine Dateideskriptoren mehr verfügbar. |
| **ENOENT** | Datei oder Pfad nicht gefunden. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_sopen-Funktion** öffnet die durch *Dateiname* angegebene Datei und bereitet die Datei für das gemeinsame Lesen oder Schreiben vor, wie von *oflag* und *shflag*definiert. **_wsopen** ist eine breit gefächerte Version von **_sopen**; Das *Dateiname-Argument* für **_wsopen** ist eine Zeichenfolge mit großen Zeichen. **_wsopen** und **_sopen** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Der ganzzahlige Ausdruck *vonlag* wird durch Kombinieren einer oder mehrerer der \<folgenden Manifestkonstanten gebildet, die in fcntl.h> definiert sind. Wenn zwei oder mehr Konstanten das Argument *vonlag*bilden, werden sie mit dem bitweisen-ODER-Operator ( **&#124;** ) kombiniert.

|*oflag* konstante|Verhalten|
|-|-|
| **_O_APPEND** | Verschiebt den Dateizeiger vor jedem Schreibvorgang an das Ende der Datei. |
| **_O_BINARY** | Öffnet die Datei im Binärmodus (nicht übersetzt). (Eine Beschreibung des binären Modus finden Sie unter [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Erstellt eine Datei und öffnet sie zum Schreiben. Hat keine Auswirkungen, wenn die durch *Dateiname* angegebene Datei vorhanden ist. Das *pmode-Argument* ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** **&#124;** _O_SHORT_LIVED | Erstellt eine temporäre Datei und leert sie, wenn möglich, nicht auf die Festplatte. Das *pmode-Argument* ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Erstellt eine Datei als temporär. Die Datei wird gelöscht, wenn der letzte Dateideskriptor geschlossen wird. Das *pmode-Argument* ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124;`_O_EXCL` | Gibt einen Fehlerwert zurück, wenn eine durch *Dateiname* angegebene Datei vorhanden ist. Gilt nur bei Verwendung mit **_O_CREAT**. |
| **_O_NOINHERIT** | Verhindert die Erstellung eines freigegebenen Dateideskriptors. |
| **_O_RANDOM** | Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **_O_RDONLY** | Öffnet eine Datei nur zum Lesen. Kann nicht mit **_O_RDWR** oder **_O_WRONLY**angegeben werden. |
| **_O_RDWR** | Öffnet eine Datei zum Lesen und zum Schreiben. Kann nicht mit **_O_RDONLY** oder **_O_WRONLY**angegeben werden. |
| **_O_SEQUENTIAL** | Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **_O_TEXT** | Öffnet eine Datei im Textmodus (übersetzt). (Weitere Informationen finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Öffnet eine Datei und verkürzt sie auf die Länge Null. Für die Datei muss Schreibberechtigung bestehen. Kann nicht mit **_O_RDONLY**angegeben werden. **_O_TRUNC,** **die** mit _O_CREAT verwendet wird, öffnet eine vorhandene Datei oder erstellt eine Datei. **Hinweis:** Das **_O_TRUNC-Flag** zerstört den Inhalt der angegebenen Datei. |
| **_O_WRONLY** | Öffnet eine Datei nur zum Schreiben. Kann nicht mit **_O_RDONLY** oder **_O_RDWR**angegeben werden. |
| **_O_U16TEXT** | Öffnet eine Datei im Unicode-UTF-16-Modus. |
| **_O_U8TEXT** | Öffnet eine Datei im Unicode-UTF-8-Modus. |
| **_O_WTEXT** | Öffnet eine Datei im Unicode-Modus. |

Um den Dateizugriffsmodus anzugeben, müssen Sie entweder **_O_RDONLY**, **_O_RDWR**oder **_O_WRONLY**angeben. Es existiert kein Standardwert für den Zugriffsmodus.

Wenn eine Datei im Unicode-Modus mit **_O_WTEXT**, **_O_U8TEXT**oder **_O_U16TEXT**geöffnet wird, übersetzen Eingabefunktionen die aus der Datei gelesenen Daten in UTF-16-Daten, die als Typ **wchar_t**gespeichert sind. Funktionen, die in eine im Unicode-Modus geöffnete Datei schreiben, erwarten Puffer, die UTF-16-Daten enthalten, die als Typ **wchar_t**gespeichert sind. Wenn eine Datei als UTF-8 kodiert ist, dann werden UTF-16-Daten beim Schreiben in UTF-8 übersetzt, und die UTF-8-kodierten Inhalte der Datei werden beim Lesen in UTF-16 übersetzt. Der Versuch, in diesem Modus eine ungerade Anzahl von Bytes in Unicode zu lesen oder zu schreiben, führt zu einem Parametervalidierungsfehler. Wenn Sie Daten lesen oder schreiben möchten, die in Ihrem Programm als UTF-8 gespeichert sind, verwenden Sie den Text- oder Binärdateienmodus anstelle eines Unicode-Modus. Sie sind für jede erforderliche Kodierungsübersetzung verantwortlich.

Wenn **_sopen** mit **_O_WRONLY** | **_O_APPEND** (Anhängenmodus) und **_O_WTEXT**, **_O_U16TEXT**oder **_O_U8TEXT**aufgerufen wird, versucht er zunächst, die Datei zum Lesen und Schreiben zu öffnen, die Stückliste zu lesen und sie dann nur zum Schreiben wieder zu öffnen. Wenn das Öffnen der Datei zum Lesen und Schreiben fehlschlägt, wird die Datei nur zum Schreiben geöffnet und der Standardwert für die Unicode-Moduseinstellung verwendet.

Das Argument *shflag* ist ein konstanter Ausdruck, der aus einer \<der folgenden Manifestkonstanten besteht, die in share.h> definiert sind.

|*shflag* konstant|Verhalten|
|-|-|
| **_SH_DENYRW** | Verweigert den Lese- und Schreibzugriff auf eine Datei. |
| **_SH_DENYWR** | Verweigert den Schreibzugriff auf eine Datei. |
| **_SH_DENYRD** | Verweigert den Lesezugriff auf eine Datei. |
| **_SH_DENYNO** | Erlaubt Lese- und Schreibzugriff. |

Das *pmode-Argument* ist nur erforderlich, wenn **_O_CREAT** angegeben ist. Wenn die Datei nicht vorhanden ist, gibt *pmode* die Berechtigungseinstellungen der Datei an, die festgelegt werden, wenn die neue Datei zum ersten Mal geschlossen wird. Andernfalls wird *pmode* ignoriert. *pmode* ist ein ganzzahliger Ausdruck, der eine oder beide manifesten Konstanten **_S_IWRITE** und **_S_IREAD**enthält, die in \<> sys-stat.h definiert sind. Wenn beide Konstanten verwendet werden, werden sie mithilfe des bitweisen OR-Operators kombiniert. Die Bedeutung von *pmode* ist wie folgt.

|*Pmode*|Bedeutung|
|-|-|
| **_S_IREAD** | Nur Lesen zugelassen. |
| **_S_IWRITE** | Schreiben erlaubt. (Lässt tatsächlich Lesen und Schreiben zu.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Lesen und Schreiben erlaubt. |

Wenn keine Schreibberechtigung gewährt wird, kann die Datei nur gelesen werden. Im Windows-Betriebssystem sind alle Dateien lesbar. Es ist nicht möglich, nur Schreibberechtigungen zu vergeben. Daher sind die Modi **_S_IWRITE** und **_S_IREAD** | **_S_IWRITE** gleichwertig.

**_sopen** wendet die aktuelle Dateiberechtigungsmaske auf *pmode* an, bevor die Berechtigungen festgelegt werden. (Siehe [_umask](umask.md).)

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> oder \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_locking](locking.md).

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
