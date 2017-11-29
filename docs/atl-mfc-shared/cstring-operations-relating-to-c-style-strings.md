---
title: "CString Operations Relating to C-Style Strings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "casting CString objects"
  - "CString objects, Grundlegende Vorgänge"
  - "C-style strings"
  - "MFC [C++], string handling class"
  - "NULL-Werte, Null-terminated string conversion"
  - "standard run-time library string functions"
  - "string arguments"
  - "Zeichenfolgenkonvertierung [C++], C-style strings"
  - "Zeichenfolgenfunktionen"
  - "Zeichenfolgen [C++], class CString"
  - "Zeichenfolgen [C++], in C"
  - "Zeichenfolgen [C++], string operations"
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CString Operations Relating to C-Style Strings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ein [CString](../atl-mfc-shared/using-cstring.md)\-Objekt enthält Zeichenfolgendaten.  `CString` übernimmt den Satz an [Methoden und Operatoren](../atl-mfc-shared/reference/cstringt-class.md), die in der Klassenvorlage [CStringT](../atl-mfc-shared/reference/cstringt-class.md) für die Nutzung mit Zeichenfolgendaten definiert wurden.  \(`CString` ist eine `typedef`, die `CStringT` spezialisiert, damit sie mit den Zeichendaten genutzt werden kann, die `CString` unterstützt.\)  
  
 `CString` speichert keine Zeichendaten intern als auf NULL abschließende Zeichenfolge im C\-Format.  Stattdessen zeichnet `CString` die Länge der Zeichendaten auf, sodass die Daten und der benötigte Speicherplatz besser überwacht werden können.  
  
 `CString` akzeptiert Zeichenfolgen im C\-Format und bietet Methoden, um auf Zeichendaten als eine Zeichenfolge im C\-Format zuzugreifen.  Dieses Thema enthält die folgenden Abschnitte, in denen Sie erfahren, wie Sie ein `CString`\-Objekt als auf NULL abschließende Zeichenfolge im C\-Format verwenden können.  
  
-   [Konvertieren in auf NULL abschließende Zeichenfolgen im C\-Format](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
-   [Arbeiten mit standardmäßigen Funktionen für Laufzeitbibliothek\-Zeichenfolgen](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
-   [Direktes Ändern von CString\-Inhalten](#_core_modifying_cstring_contents_directly)  
  
-   [Verwenden von CString\-Objekten mit variablen Argumentsfunktionen](#_core_using_cstring_objects_with_variable_argument_functions)  
  
-   [Angeben von formalen CString\-Parametern](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> Verwenden von CString als eine auf NULL abschließende Zeichenfolge im C\-Format  
 Um ein `CString`\-Objekt als Zeichenfolge im C\-Format zu verwenden, wandeln Sie das Objekt in `LPCTSTR` um.  Im folgenden Beispiel gibt `CString` einen Zeiger auf eine schreibgeschützte auf NULL abschließende Zeichenfolge im C\-Format zurück.  Die `strcpy`\-Funktion fügt eine Kopie der Zeichenfolge im C\-Format in der Variablen `myString` ein.  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);  
  
```  
  
 Sie können `CString`\-Methoden, z. B. `SetAt`, verwenden, um einzelne Zeichen im Zeichenfolgenobjekt zu ändern.  Der `LPCTSTR`\-Zeiger ist jedoch nur temporär und wird ungültig, wenn Änderungen an `CString` vorgenommen werden.  `CString` kann auch den gültigen Bereich verlassen und automatisch gelöscht werden.  Wir empfehlen nach jeder Nutzung einen aktuellen `LPCTSTR`\-Zeiger eines `CString`\-Objekts abzurufen.  
  
 Gelegentlich benötigen Sie eine Kopie der `CString`\-Daten, um direkte Änderungen vorzunehmen.  Verwenden Sie die sicherere Funktion `strcpy_s` \(oder die Unicode\/MBCS\-portable Funktion `_tcscpy_s`\), um das `CString`\-Objekt in einen eigenen Puffer zu kopieren.  Dort können die Zeichen sicher geändert werden, wie im folgenden Beispiel gezeigt.  
  
 [!CODE [NVC_ATLMFC_Utilities#189](../CodeSnippet/VS_Snippets_Cpp/NVC_ATLMFC_Utilities#189)]  
  
> [!NOTE]
>  Das dritte Argument für `strcpy_s` \(oder das Unicode\/MBCS\-portable `_tcscpy_s`\) ist entweder `const``wchar_t*` \(Unicode\) oder `const``char*` \(ANSI\).  Das oben stehende Beispiel übergibt einen `CString` für dieses Argument.  Der C\+\+\-Compiler wendet automatisch die Konvertierungsfunktion an, die für die `CString`\-Klasse definiert wurde, mit der ein `CString` in einen `LPCTSTR` konvertiert wird.  Die Fähigkeit, Umwandlungsvorgänge von einem Typ in einen anderen zu definieren, ist eine der nützlichsten Funktionen von C\+\+.  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Arbeiten mit standardmäßigen Funktionen für Laufzeitbibliothek\-Zeichenfolgen  
 Sie sollten eine `CString`\-Methode finden können, um einen beliebigen Zeichenfolgenvorgang durchzuführen, für den Sie die standardmäßigen Funktionen fürC\-Laufzeit\-Bibliothekszeichenfolgen wie `strcmp` \(oder das Unicode\/MBCS\-portable `_tcscmp`\) in Betracht ziehen könnten.  
  
 Wenn Sie die C\-Laufzeit\-Zeichenfolgenfunktionen verwenden müssen, können Sie die im folgenden Abschnitt beschriebenen Techniken verwenden: \_core\_using\_cstring\_as\_a\_c.2d.style\_null.2d.terminated\_string.  Sie können das `CString`\-Objekt in einen entsprechenden Zeichenfolgenpuffer im C\-Format kopieren, die Vorgänge durchführen und dann die resultierende Zeichenfolge im C\-Format wieder einem `CString`\-Objekt zuweisen.  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> Direktes Ändern von CString\-Inhalten  
 In den meisten Situationen sollten Sie `CString`\-Memberfunktionen verwenden, um die Inhalte eines `CString`\-Objekts zu ändern oder um den `CString` in eine Zeichenfolge im C\-Format zu konvertieren.  
  
 Es gibt einige Situationen, in denen es sinnvoll ist, die `CString`\-Inhalte direkt zu ändern, z. B. wenn Sie mit Betriebssystemfunktionen arbeiten, die einen Zeichenpuffer benötigen.  
  
 Die `GetBuffer`\- und `ReleaseBuffer`\-Methoden bieten Zugriff auf den internen Zeichenpuffer eines `CString`\-Objekts, sodass Sie es direkt ändern können.  Die folgenden Schritte zeigen Ihnen, wie Sie diese Funktionen zu diesem Zweck verwenden können.  
  
#### So verwenden Sie GetBuffer und ReleaseBuffer für den Zugriff auf den internen Zeichenpuffer eines CString\-Objekts  
  
1.  Rufen Sie `GetBuffer` für ein `CString`\-Objekt auf, und geben Sie die Länge des benötigten Puffers an.  
  
2.  Verwenden Sie den von `GetBuffer` zurückgegebenen Zeiger, um Zeichen direkt in das `CString`\-Objekt zu schreiben.  
  
3.  Rufen Sie `ReleaseBuffer` für das `CString`\-Objekt auf, um alle internen `CString`\-Statusinformationen, z. B. die Länge der Zeichenfolge, zu aktualisieren.  Nachdem Sie die Inhalte eines `CString`\-Objekts direkt geändert haben, müssen Sie `ReleaseBuffer` aufrufen, bevor Sie eine andere `CString`\-Memberfunktion aufrufen.  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> Verwenden von CString\-Objekten mit variablen Argumentsfunktionen  
 Einige C\-Funktionen haben eine variable Anzahl an Argumenten.  Ein bedeutsames Beispiel ist `printf_s`.  Aufgrund der Art und Weise, in der diese Funktion deklariert wird, kann der Compiler sich nicht über den Typ der Argumente sicher sein, und er kann nicht bestimmen, welcher Konvertierungsvorgang für jedes Argument durchgeführt werden muss.  Daher ist es sehr wichtig, dass Sie eine explizite Typumwandlung verwenden, wenn Sie ein `CString`\-Objekt an eine Funktion übergeben, die eine variable Anzahl an Argumenten haben kann.  
  
 Um ein `CString`\-Objekt in einer variablen Argumentsfunktion zu verwenden, wandeln Sie `CString` explizit in eine `LPCTSTR`\-Zeichenfolge um, wie im folgenden Beispiel gezeigt.  
  
 [!CODE [NVC_ATLMFC_Utilities#190](../CodeSnippet/VS_Snippets_Cpp/NVC_ATLMFC_Utilities#190)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> Angeben von formalen CString\-Parametern  
 Bei den meisten Funktionen, die ein Zeichenfolgenargument benötigen, ist es am besten, den formalen Parameter im Funktionsprototypen als einen `const`\-Zeiger auf ein Zeichen \(`LPCTSTR`\) anstelle eines `CString` anzugeben.  Wenn ein formaler Parameter als `const`\-Zeiger auf ein Zeichen angegeben wird, können Sie entweder einen Zeiger auf ein `TCHAR`\-Array, eine Literalzeichenfolge \[`"hi there"`\], oder ein `CString`\-Objekt übergeben.  Das `CString`\-Objekt wird automatisch in `LPCTSTR` konvertiert.  Überall dort, wo Sie einen `LPCTSTR` verwenden können, können Sie auch ein `CString`\-Objekt verwenden.  
  
 Sie können auch einen formalen Parameter als einen Konstantenzeichenfolgenverweis angeben \(z. B. `const``CString&`\), wenn das Argument nicht geändert wird.  Legen Sie den `const`\-Modifizierer ab, wenn die Zeichenfolge mit der Funktion geändert wird.  Wenn ein standardmäßiger NULL\-Wert gewünscht ist, initialisieren Sie es mit der NULL\-Zeichenfolge \[`""`\], wie nachfolgend beschrieben:  
  
 [!CODE [NVC_ATLMFC_Utilities#191](../CodeSnippet/VS_Snippets_Cpp/NVC_ATLMFC_Utilities#191)]  
  
 Bei den meisten Funktionsergebnissen können Sie einfach ein `CString`\-Objekt nach Wert zurückgeben.  
  
## Siehe auch  
 [Zeichenfolgen](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString Argument Passing](../atl-mfc-shared/cstring-argument-passing.md)