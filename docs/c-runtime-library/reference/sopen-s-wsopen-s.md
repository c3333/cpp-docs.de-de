---
title: _sopen_s, _wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 6c3de36482c4ffdf1ef402b4059816639014eb8b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912693"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Öffnet eine Datei zur Freigabe. Diese Versionen von [_sopen und _wsopen](sopen-wsopen.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>Parameter

*PFH*<br/>
Das Dateihandle oder -1 im Fall eines Fehlers.

*Einfügen*<br/>
Dateiname

*Oflag*<br/>
Die Art der zulässigen Vorgänge.

*shflag*<br/>
Die Art der zulässigen Freigabe.

*pmode*<br/>
Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Ein Rückgabewert ungleich NULL weist auf einen Fehler hin. in diesem Fall wird **errno** auf einen der folgenden Werte festgelegt.

|errno-Wert|Bedingung|
|-|-|
| **EACCES** |  Der angegebene Pfad ist ein Verzeichnis, oder die Datei ist schreibgeschützt, aber es wurde versucht, sie zum Schreiben zu öffnen. |
| **EEXIST** |  Es wurden **_O_CREAT** -und **_O_EXCL** Flags angegeben, aber der *Dateiname* ist bereits vorhanden. |
| **Eingabe** |  Ungültiges *Oflag*-, *shflag*-oder *pmode* -Argument, oder *PFH* oder *filename* war ein NULL-Zeiger. |
| **EMFILE** | Es sind keine Dateideskriptoren mehr verfügbar. |
| **ENOENT** | Datei oder Pfad nicht gefunden. |

Wenn ein ungültiges Argument an die Funktion übergeben wird, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und **EINVAL** wird zurückgegeben.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Im Fall eines Fehlers wird-1 über *PFH* zurückgegeben (es sei denn, *PFH* ist ein NULL-Zeiger).

## <a name="remarks"></a>Hinweise

Die **_sopen_s** -Funktion öffnet die Datei, die durch *Dateiname* angegeben wird, und bereitet die Datei für das gemeinsame lesen oder schreiben vor, wie von *Oflag* und *shflag*definiert. **_wsopen_s** ist eine breit Zeichen Version von **_sopen_s**. Das *filename* -Argument für **_wsopen_s** ist eine Zeichenfolge mit breit Zeichen. **_wsopen_s** und **_sopen_s** Verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Das *Oflag* für ganzzahlige Ausdrücke wird durch Kombinieren einer oder mehrerer Manifest-Konstanten gebildet \<, die in fcntl. h> definiert sind. Wenn zwei oder mehr Konstanten das Argument *Oflag*bilden, werden Sie mit dem bitweisen OR-Operator ( **&#124;** ) kombiniert.

|*Oflag* -Konstante|Verhalten|
|-|-|
| **_O_APPEND** | Verschiebt den Dateizeiger vor jedem Schreibvorgang an das Ende der Datei. |
| **_O_BINARY** | Öffnet die Datei im Binärmodus (nicht übersetzt). (Eine Beschreibung des binären Modus finden Sie unter [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Erstellt eine Datei und öffnet sie zum Schreiben. Hat keine Auswirkung, wenn die durch *filename* angegebene Datei vorhanden ist. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Erstellt eine temporäre Datei und leert sie, wenn möglich, nicht auf die Festplatte. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Erstellt eine Datei als temporär. Die Datei wird gelöscht, wenn der letzte Dateideskriptor geschlossen wird. Das *pmode* -Argument ist erforderlich, wenn **_O_CREAT** angegeben wird. |
| **_O_CREAT** &#124;`_O_EXCL` | Gibt einen Fehlerwert zurück, wenn eine durch *filename* angegebene Datei vorhanden ist. Gilt nur bei Verwendung mit **_O_CREAT**. |
| **_O_NOINHERIT** | Verhindert die Erstellung eines freigegebenen Dateideskriptors. |
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

Zum Angeben des Datei Zugriffsmodus müssen Sie entweder **_O_RDONLY**, **_O_RDWR**oder **_O_WRONLY**angeben. Es existiert kein Standardwert für den Zugriffsmodus.

Wenn eine Datei mit **_O_WTEXT**, **_O_U8TEXT**oder **_O_U16TEXT**im Unicode-Modus geöffnet wird, übersetzen Eingabefunktionen die aus der Datei gelesenen Daten in UTF-16-Daten, die als Typ **wchar_t**gespeichert werden. Funktionen, die in eine im Unicode-Modus geöffnete Datei schreiben, erwarten Puffer, die UTF-16-Daten enthalten, die als Typ **wchar_t**gespeichert sind. Wenn eine Datei als UTF-8 kodiert ist, dann werden UTF-16-Daten beim Schreiben in UTF-8 übersetzt, und die UTF-8-kodierten Inhalte der Datei werden beim Lesen in UTF-16 übersetzt. Der Versuch, in diesem Modus eine ungerade Anzahl von Bytes in Unicode zu lesen oder zu schreiben, führt zu einem Parametervalidierungsfehler. Wenn Sie Daten lesen oder schreiben möchten, die in Ihrem Programm als UTF-8 gespeichert sind, verwenden Sie den Text- oder Binärdateienmodus anstelle eines Unicode-Modus. Sie sind für jede erforderliche Kodierungsübersetzung verantwortlich.

Wenn **_sopen_s** mit **_O_WRONLY** | **_O_APPEND** (Append-Modus) und **_O_WTEXT**, **_O_U16TEXT**oder **_O_U8TEXT**aufgerufen wird, versucht es zuerst, die Datei zum Lesen und schreiben zu öffnen, die BOM zu lesen und Sie zum Schreiben zu öffnen. Wenn das Öffnen der Datei zum Lesen und Schreiben fehlschlägt, wird die Datei nur zum Schreiben geöffnet und der Standardwert für die Unicode-Moduseinstellung verwendet.

Das Argument *shflag* ist ein konstanter Ausdruck, der aus einer der folgenden Manifest-Konstanten besteht, die in \<der Freigabe. h-> definiert sind.

|*shflag* -Konstante|Verhalten|
|-|-|
| **_SH_DENYRW** | Verweigert den Lese- und Schreibzugriff auf eine Datei. |
| **_SH_DENYWR** | Verweigert den Schreibzugriff auf eine Datei. |
| **_SH_DENYRD** | Verweigert den Lesezugriff auf eine Datei. |
| **_SH_DENYNO** | Erlaubt Lese- und Schreibzugriff. |

Das *pmode* -Argument ist immer erforderlich, im Gegensatz zu **_sopen**. Wenn Sie **_O_CREAT**angeben und die Datei nicht vorhanden ist, gibt *pmode* die Berechtigungseinstellungen der Datei an, die festgelegt werden, wenn die neue Datei zum ersten Mal geschlossen wird. Andernfalls wird *pmode* ignoriert. *pmode* ist ein ganzzahliger Ausdruck, der eine oder beide der Manifest-Konstanten **_S_IWRITE** und **_S_IREAD**enthält, die \<in der sys\status-h-> definiert sind. Wenn beide Konstanten verwendet werden, werden sie mithilfe des bitweisen OR-Operators kombiniert. Die Bedeutung von *pmode* ist wie folgt.

|*pmode*|Bedeutung|
|-|-|
| **_S_IREAD** | Nur Lesen zugelassen. |
| **_S_IWRITE** | Schreiben erlaubt. (Lässt tatsächlich Lesen und Schreiben zu.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Lesen und Schreiben erlaubt. |

Wenn keine Schreibberechtigung gewährt wird, kann die Datei nur gelesen werden. Im Windows-Betriebssystem sind alle Dateien lesbar. Es ist nicht möglich, nur Schreibberechtigungen zu vergeben. Daher sind die Modi **_S_IWRITE** und **_S_IREAD** | **_S_IWRITE** Äquivalent.

**_sopen_s** wendet die aktuelle Datei Berechtigungs Maske auf *pmode* an, bevor die Berechtigungen festgelegt werden. (Siehe [_umask](umask.md).)

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> oder \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** und **_wsopen_s** sind Microsoft-Erweiterungen. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_locking](locking.md).

## <a name="see-also"></a>Weitere Informationen

[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
