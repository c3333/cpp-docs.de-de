---
title: Zuordnungen für generischen Text in Tchar. h
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
ms.openlocfilehash: c317e7d67cc3d086dacbe0f24b0103d389afefda
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217297"
---
# <a name="generic-text-mappings-in-tcharh"></a>Zuordnungen für generischen Text in Tchar. h

Um den Code für die internationale Verwendung zu vereinfachen, stellt die Microsoft-Lauf Zeit Bibliothek Microsoft-spezifische Zuordnungen für generischen Text für viele Datentypen, Routinen und andere Objekte bereit. Sie können diese Zuordnungen verwenden, die in Tchar. h definiert sind, um generischen Code zu schreiben, der für Einzel Byte-, Multibyte-oder Unicode-Zeichensätze kompiliert werden kann, abhängig von einer Manifest-Konstante, die Sie mithilfe einer- `#define` Anweisung definieren. Generische Textzuordnungen sind Microsoft-Erweiterungen, die nicht mit ANSI kompatibel sind.

Mithilfe von Tchar. h können Sie Einzel Byte-, Multibyte-Zeichensatz (MBCS) und Unicode-Anwendungen aus denselben Quellen erstellen. Tchar. h definiert Makros (mit dem Präfix `_tcs` ), die mit den richtigen Präprozessordefinitionen den,-oder-Funktionen entsprechend zugeordnet werden `str` `_mbs` `wcs` . Definieren Sie zur Erstellung von MBCS das `_MBCS`-Symbol. Definieren Sie zum Erstellen von Unicode das Symbol `_UNICODE` . Um eine Einzelbyte-Anwendung zu erstellen, geben Sie nichts an (Standardeinstellung). Standardmäßig wird `_UNICODE` für MFC-Anwendungen definiert.

Der- `_TCHAR` Datentyp wird in Tchar. h bedingt definiert. Wenn das Symbol `_UNICODE` für den Build definiert ist, `_TCHAR` wird als definiert **`wchar_t`** . andernfalls wird es für Single-Byte-und MBCS-Builds als definiert **`char`** . ( **`wchar_t`** , der grundlegende Unicode-breit Zeichen Datentyp, ist der 16-Bit-Gegenstück zu einem 8-Bit-Wert **`signed char`** .) Verwenden Sie für internationale Anwendungen die- `_tcs` Funktions Familie, die in `_TCHAR` Einheiten und nicht in Bytes betrieben wird. Beispielsweise `_tcsncpy` kopiert `n` `_TCHARs` , nicht `n` Bytes.

Da einige SBCS-Funktionen (Single Byte Character Set, SBCS) für die Zeichen folgen Behandlung Parameter (signiert) akzeptieren **`char*`** , ist ein Typ nicht mit Compilerwarnungen identisch, wenn `_MBCS` definiert wird. Es gibt drei Möglichkeiten, diese Warnung zu vermeiden:

1. Verwenden Sie die typsicheren Inline Funktions-thunas in Tchar. h. Dies ist das Standardverhalten.

1. Verwenden Sie die direkten Makros in Tchar. h, indem Sie in `_MB_MAP_DIRECT` der Befehlszeile definieren. In diesem Fall müssen Sie die Typübereinstimmung manuell sicherstellen. Dies ist die schnellste Methode; sie ist jedoch nicht typsicher.

1. Verwenden Sie die typsicheren statisch verknüpften Bibliotheksfunktionen in Tchar. h. Definieren Sie hierzu in der Befehlszeile die Konstante `_NO_INLINING`. Dies ist die langsamste Methode; sie bietet jedoch auch die größte Typsicherheit.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Präprozessordirektiven zum Zuordnen von generischem Text

|#define|Kompilierte Version|Beispiel|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (Breitzeichen)|`_tcsrev` ist `_wcsrev` zugeordnet.|
|`_MBCS`|Mehrbytezeichen|`_tcsrev` ist `_mbsrev` zugeordnet.|
|Keine (bei der Standardeinstellung ist weder `_UNICODE` noch `_MBCS` definiert)|SBCS (ASCII)|`_tcsrev` ist `strrev` zugeordnet.|

Die `_tcsrev` in Tchar. h definierte generische Textfunktion wird beispielsweise zugeordnet, `_mbsrev` Wenn Sie `_MBCS` in Ihrem Programm definiert haben, oder, `_wcsrev` Wenn Sie definiert haben `_UNICODE` . Andernfalls wird `_tcsrev``strrev` zugeordnet. Andere Datentyp Zuordnungen werden in Tchar. h zur einfacheren Programmierung bereitgestellt, sind jedoch `_TCHAR` die nützlichsten.

### <a name="generic-text-data-type-mappings"></a>Generische Textzuordnungen von Datentypen

|Generischer Text<br /> Datentypname|_UNICODE &<br /> _MBCS nicht definiert|_MBCS<br /> Definiert|_UNICODE<br /> Definiert|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`unsigned int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` oder `_TEXT`|Ohne Auswirkung (wird vom Präprozessor entfernt)|Ohne Auswirkung (wird vom Präprozessor entfernt)|`L`(konvertiert das folgende Zeichen oder die Zeichenfolge in seine Unicode-Entsprechung)|

Eine Liste der generischen Text Zuordnungen von Routinen, Variablen und anderen Objekten finden Sie unter [generische Text](../c-runtime-library/generic-text-mappings.md) Zuordnungen in der Lauf Zeit Bibliotheks Referenz.

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

Wenn weder `_MBCS` noch `_UNICODE` definiert wurden, ordnet der Präprozessor das Fragment wie folgt dem Single-Byte-ASCII-Code zu:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Folglich können Sie eine einzige Quellcodedatei so schreiben, verwalten und kompilieren, dass sie mit Routinen ausgeführt wird, die jeweils speziell auf einen der drei Zeichensätze ausgerichtet sind.

## <a name="see-also"></a>Weitere Informationen

[Text und Zeichen folgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[Verwenden von Tchar. H-Datentypen mit _MBCS-Code](../text/using-tchar-h-data-types-with-mbcs-code.md)
