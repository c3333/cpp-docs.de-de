---
title: Zuordnungen für generischen Text in tchar.h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361345"
---
# <a name="generic-text-mappings-in-tcharh"></a>Zuordnungen für generischen Text in tchar.h

Um den Transport von Code für die internationale Verwendung zu vereinfachen, stellt die Microsoft-Laufzeitbibliothek Microsoft-spezifische generische Textzuordnungen für viele Datentypen, Routinen und andere Objekte bereit. Sie können diese Zuordnungen, die in tchar.h definiert sind, verwenden, um generischen Code zu schreiben, der für Single-Byte-, Multibyte- oder Unicode-Zeichensätze kompiliert werden kann, abhängig von einer Manifestkonstante, die Sie mithilfe einer `#define` Anweisung definieren. Generische Textzuordnungen sind Microsoft-Erweiterungen, die nicht mit ANSI kompatibel sind.

Mithilfe von tchar.h können Sie Single-Byte-, Multibyte-Zeichensatz( MBCS) und Unicode-Anwendungen aus denselben Quellen erstellen. tchar.h definiert Makros (die das `_tcs`Präfix haben), die mit den `str`richtigen `_mbs`Präprozessordefinitionen gegebenenfalls zu , oder `wcs` Funktionen zugeordnet werden. Definieren Sie zur Erstellung von MBCS das `_MBCS`-Symbol. Um Unicode zu erstellen, definieren Sie das Symbol `_UNICODE`. Um eine Einzelbyte-Anwendung zu erstellen, geben Sie nichts an (Standardeinstellung). Standardmäßig wird `_UNICODE` für MFC-Anwendungen definiert.

Der `_TCHAR` Datentyp wird bedingt in tchar.h definiert. Wenn das `_UNICODE` Symbol für Ihren `_TCHAR` Build definiert ist, wird es als **wchar_t**definiert. Andernfalls wird es bei Single-Byte- und MBCS-Builds als **char**definiert. (**wchar_t**, der grundlegende Unicode-Datentyp mit einem Unicode-Breitzeichentyp, ist das 16-Bit-Gegenstück zu einem 8-Bit-signierten **Zeichen**.) Verwenden Sie für `_tcs` internationale Anwendungen die Funktionsfamilie, die in Einheiten und nicht in `_TCHAR` Bytes ausgeführt wird. Beispielsweise `_tcsncpy` werden `n` `_TCHARs`Kopien `n` , nicht Bytes.

Da für einige Funktionen zur Zeichenfolgenbehandlung bei Einzelbyte-Zeichensätzen (SBCS) `char*`-Parameter (mit Vorzeichen) erforderlich sind, wird bei der Definition von `_MBCS` eine Compiler-Warnung ausgegeben, die auf einen Typenkonflikt hinweist. Es gibt drei Möglichkeiten, diese Warnung zu vermeiden:

1. Verwenden Sie die typsichere Inline-Funktion thunks in tchar.h. Dies ist das Standardverhalten.

1. Verwenden Sie die direkten Makros in `_MB_MAP_DIRECT` tchar.h, indem Sie in der Befehlszeile definieren. In diesem Fall müssen Sie die Typübereinstimmung manuell sicherstellen. Dies ist die schnellste Methode; sie ist jedoch nicht typsicher.

1. Verwenden Sie die typsichere statisch verknüpfte Bibliotheksfunktion thunks in tchar.h. Definieren Sie hierzu in der Befehlszeile die Konstante `_NO_INLINING`. Dies ist die langsamste Methode; sie bietet jedoch auch die größte Typsicherheit.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Präprozessordirektiven zum Zuordnen von generischem Text

|#define|Kompilierte Version|Beispiel|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (Breitzeichen)|`_tcsrev` wird `_wcsrev` zugeordnet.|
|`_MBCS`|Mehrbytezeichen|`_tcsrev` wird `_mbsrev` zugeordnet.|
|Keine (bei der Standardeinstellung ist weder `_UNICODE` noch `_MBCS` definiert)|SBCS (ASCII)|`_tcsrev` wird `strrev` zugeordnet.|

Beispielsweise wird die `_tcsrev`generic-text-Funktion , die in tchar.h definiert ist, zugeordnet, `_mbsrev` wenn Sie in Ihrem Programm definiert `_MBCS` haben oder `_wcsrev` wenn Sie definiert `_UNICODE`haben. Andernfalls wird `_tcsrev``strrev` zugeordnet. Andere Datentypzuordnungen werden in tchar.h für `_TCHAR` Programmierfreundlichkeit bereitgestellt, ist aber am nützlichsten.

### <a name="generic-text-data-type-mappings"></a>Generische Textzuordnungen von Datentypen

|Generischer Text<br /> Datentypname|_UNICODE &<br /> _MBCS nicht definiert|_MBCS<br /> Definiert|_UNICODE<br /> Definiert|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**Wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**char mit Vorzeichen**|**char mit Vorzeichen**|**Wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**Wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**Wchar_t**|
|`_T` oder `_TEXT`|Ohne Auswirkung (wird vom Präprozessor entfernt)|Ohne Auswirkung (wird vom Präprozessor entfernt)|`L`(konvertiert das folgende Zeichen oder die folgende Zeichenfolge in sein Unicode-Pendant)|

Eine Liste der generischen Textzuordnungen von Routinen, Variablen und anderen Objekten finden Sie unter [Generic-Text Mappings](../c-runtime-library/generic-text-mappings.md) in der Laufzeitbibliotheksreferenz.

> [!NOTE]
> Verwenden Sie die `str`-Funktionsreihe nicht mit Unicode-Zeichenfolgen, da diese wahrscheinlich eingebettete NULL-Bytes enthalten. Ebenso sollten Sie die `wcs`-Funktionsreihe nicht mit Zeichenfolgen vom Typ MBCS (oder SBCS) verwenden.

Aus den folgenden Codefragmenten geht hervor, wie `_TCHAR` und `_tcsrev` für die Zuordnung zu den MBCS-, Unicode- und SBCS-Modellen verwendet werden.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Wenn `_MBCS` definiert wurde, ordnet der Präprozessor diesem Code folgenden Ausschnitt zu:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Wenn `_UNICODE` definiert wurde, ordnet der Präprozessor diesem Code folgenden Ausschnitt zu:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Wenn `_MBCS` weder noch `_UNICODE` nicht definiert wurde, ordnet der Präprozessor das Fragment dem ASCII-Code mit einem Byte wie folgt zu:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Folglich können Sie eine einzige Quellcodedatei so schreiben, verwalten und kompilieren, dass sie mit Routinen ausgeführt wird, die jeweils speziell auf einen der drei Zeichensätze ausgerichtet sind.

## <a name="see-also"></a>Siehe auch

[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[Verwenden von TCHAR. H Datentypen mit _MBCS Code](../text/using-tchar-h-data-types-with-mbcs-code.md)
