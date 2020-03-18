---
title: Stream-E/A
ms.date: 11/04/2016
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: 0fc49d4cd26593cb02a2ff05c3205cc630ef848c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444620"
---
# <a name="stream-io"></a>Stream-E/A

Diese Funktionen verarbeiten die Daten in verschiedenen Größen und Formate, angefangen bei einzelnen Zeichen bis hin zu großen Datenstrukturen. Darüber hinaus verwenden sie Pufferung, wodurch die Leistung verbessert werden kann. Die Standardgröße eines Streamingpuffers beträgt 4 KB. Diese Routinen wirken sich nur auf Puffer aus, die von den Routinen der Laufzeitbibliothek erstellt wurden. Sie haben keine Auswirkungen auf die vom Betriebssystem erstellten Puffer.

## <a name="stream-io-routines"></a>Stream-E/A-Routinen

|Routine|Zweck|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|Fehlerindikator für Stream löschen|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|Stream schließen|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Alle offenen Streams außer **stdin**, **stdout** und **stderr** schließen.|
|[_fdopen, wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Stream dem Dateideskriptor der geöffneten Datei zuordnen|
|[feof](../c-runtime-library/reference/feof.md)|Test für das Dateiende (End-of-File) im Stream|
|[ferror](../c-runtime-library/reference/ferror.md)|Test für Fehler im Stream|
|[fflush](../c-runtime-library/reference/fflush.md)|Stream in den Puffer oder in das Speichergerät leeren|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Zeichen aus dem Stream lesen (Funktionsversionen von **getc** und **getwc**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Zeichen aus **stdin** lesen (Funktionsversionen von **getchar** und **getwchar**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Positionsindikator des Streams abrufen|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Zeichenfolge aus dem Stream lesen|
|[_fileno](../c-runtime-library/reference/fileno.md)|Dateideskriptor abrufen, der dem Stream zugeordnet ist|
|[_flushall](../c-runtime-library/reference/flushall.md)|Alle Streams in den Puffer oder das Speichergerät leeren|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Stream öffnen|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Formatierte Daten in Stream schreiben|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Ein Zeichen in einen Stream schreiben (Funktionsversionen von **putc** und **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Ein Zeichen in **stdout** schreiben (Funktionsversionen von **putchar** und **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Zeichenfolge in Stream schreiben|
|[fread](../c-runtime-library/reference/fread.md)|Nicht formatierte Daten aus Stream lesen|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|**FILE**-Streamzeiger erneut einer neuen Datei oder einem neuen Gerät zuweisen|
|[fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Formatierte Daten aus Stream lesen|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Dateiposition an angegebenen Speicherort verschieben|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Positionsindikator des Streams festslegen|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Stream mit Dateifreigabe öffnen|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Aktuelle Dateiposition abrufen|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Nicht formatierte Datenelemente in Stream schreiben|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Zeichen aus dem Stream lesen (Makroversionen von **fgetc** und **fgetwc**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Zeichen aus **stdin** lesen (Makroversionen von **fgetchar** und **fgetwchar**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Gibt die Anzahl der Dateien an, die auf der E/A-Ebene des Streams gleichzeitig geöffnet sein können.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Zeile aus **stdin** lesen|
|[_getw](../c-runtime-library/reference/getw.md)|Binäres **int** aus dem Stream lesen|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Formatierte Daten in **stdout** schreiben|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Zeichen in einen Stream schreiben (Makroversionen von **fputc** und **fputwc**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Zeichen in **stdout** schreiben (Makroversionen von **fputchar** und **fputwchar**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Zeile in Stream schreiben|
|[_putw](../c-runtime-library/reference/putw.md)|Binäres **int** in den Stream schreiben|
|[rewind](../c-runtime-library/reference/rewind.md)|Dateiposition an den Anfang des Streams verschieben|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Von **tmpfile** erstellte temporäre Dateien entfernen|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Formatierte Daten aus **stdin** lesen|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Streampufferung steuern|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Maximale Anzahl der Dateien festlegen, die auf der E/A-Ebene des Streams gleichzeitig geöffnet sein können.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Streampufferung und Puffergröße steuern|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Formatierte Daten der angegebenen Länge in Zeichenfolge schreiben|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Lesen von formatierten Daten einer angegebenen Länge aus dem Standardeingabestream.|
|[sprintf, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Formatierte Daten in Zeichenfolge schreiben|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Formatierte Daten aus Stream lesen|
|[_tempnam, _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Temporären Dateinamen im angegebenen Verzeichnis generieren|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|Temporäre Datei erstellen|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Temporären Dateinamen generieren|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Zeichen zurück in den Stream verschieben|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Formatierte Daten in die Konsole schreiben|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Formatierte Daten in Stream schreiben|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Formatierte Daten in **stdout** schreiben|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Formatierte Daten der angegebenen Länge in Puffer schreiben|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Formatierte Daten in Puffer schreiben|

Wenn ein Programm mit der Ausführung beginnt, öffnet der Startcode automatisch mehrere Streams: Standardeingabe (auf die von **stdin** verwiesen wird), Standardausgabe (auf die von **stdout** verwiesen wird) und Standardfehler (auf den von **stderr** verwiesen wird). Diese Streams werden standardmäßig an die Konsole (Tastatur und Bildschirm) weitergeleitet. Verwenden Sie **freopen**, um **stdin**, **stdout** oder **stderr** an eine Datenträgerdatei oder ein Gerät umzuleiten.

Dateien, die mit den Streamroutinen geöffnet werden, werden standardmäßig gepuffert. Die Funktionen **stdout** und **stderr** werden geleert, wenn sie voll sind, oder wenn Sie nach jedem Bibliotheksaufruf in ein Zeichengerät schreiben. Wenn ein Programm nicht normal beendet wird, werden Ausgabepuffer möglicherweise nicht geleert, sodass es zu einem Verlust von Daten kommt. Verwenden Sie **fflush** oder **_flushall**, um sicherzustellen, dass der mit einer angegebenen Datei verknüpfte Puffer oder alle geöffneten Puffer in das Betriebssystem geleert werden, das die Daten zwischenspeichern kann, bevor sie auf den Datenträger geschrieben werden. Durch das Commit an den Datenträger wird sichergestellt, dass der Inhalt des geleerten Puffers bei einem Systemfehler nicht verloren geht.

Es gibt zwei Möglichkeiten, ein Commit des Pufferinhalts auf den Datenträger durchführen:

- Stellen Sie eine Verknüpfung mit der Datei „COMMODE.OBJ“ her, um eine globale Commitkennzeichnung festzulegen. Die Standardeinstellung des globalen Flags ist **n** (dies steht für „no-commit“).

- Legen Sie das Modusflag mit **fopen** oder **_fdopen** auf **c** fest.

Jede Datei, die ausdrücklich entweder mit dem **c**- oder dem **n**-Flag geöffnet wird, weist unabhängig vom Zustand des globalen Flags für ein Commit/No-Commit das für das Flag spezifische Verhalten auf.

Wenn Ihre Anwendung einen Stream nicht explizit schließt, wird der Stream beim Beenden des Programms automatisch geschlossen. Sie solltne einen Stream nach dem Beenden des Programms jedoch schließen, da die Anzahl der Streams, die gleichzeitig geöffnet sein können, begrenzt ist. Weitere Informationen zu dieser Begrenzung finden Sie unter [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) .

Die Eingabe kann nur dann direkt auf die Ausgabe folgen, wenn zwischenzeitlich ein Aufruf von **fflush** oder einer dateipositionierenden Funktion (**fseek**, **fsetpos** oder **rewind**) erfolgt. Die Ausgabe kann ohne einen zwischenzeitlichen Aufruf einer dateipositionierenden Funktion auf die Eingabe folgen, wenn der Eingabevorgang auf das Ende der Datei trifft.

## <a name="see-also"></a>Weitere Informationen

[Eingabe und Ausgabe](../c-runtime-library/input-and-output.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
