---
title: Übersicht über das Marshalling in C++
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 937fbdf4b3ed09344e69a8f1eb731565c36794ae
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544435"
---
# <a name="overview-of-marshaling-in-ccli"></a>Übersicht über das Marshalling in C++/CLI

Im gemischten Modus müssen Sie die Daten zwischen nativen und verwalteten Typen manchmal marshallen. Die *Marshallingbibliothek* hilft Ihnen, Daten auf einfache Weise zu Mars Hallen und zu konvertieren.  Die Marshallingbibliothek besteht aus einer Reihe von Funktionen und einer `marshal_context` Klasse, die das Marshalling für allgemeine Typen durchführen. Die Bibliothek ist in diesen Headern im Verzeichnis **include/msclr** für Ihre Visual Studio-Edition definiert:

|Header|Beschreibung|
|---------------|-----------------|
|marshal.h|`marshal_context`-Klasse und kontextfreie Marshallingfunktionen|
|marshal_atl.h| Funktionen für das Mars Hallen von ATL-Typen|
|marshal_cppstd.h|Funktionen für das Mars Hallen von C++ Standardtypen|
|marshal_windows.h|Funktionen für das Mars Hallen von Windows-Typen|

Der Standardpfad für den Ordner " **msclr** " ist abhängig von der verwendeten Edition und der Buildnummer wie folgt:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Sie können die Marshallingbibliothek mit oder ohne [Marshal_context Klasse](../dotnet/marshal-context-class.md)verwenden. Einige Konvertierungen erfordern einen Kontext. Andere Konvertierungen können mit der [marshal_as](../dotnet/marshal-as.md) -Funktion implementiert werden. Die folgende Tabelle enthält eine Liste der aktuell unterstützten Konvertierungen und Informationen dazu, ob sie einen Kontext benötigen und welche Marschalldatei Sie hinzufügen müssen:

|Von Typ|in Typ|Marschallmethode|Includedatei|
|---------------|-------------|--------------------|------------------|
|System::String^|Konstante char-\*|marshal_context|marshal.h|
|Konstante char-\*|System::String^|marshal_as|marshal.h|
|char-\*|System::String^|marshal_as|marshal.h|
|System::String^|Konstante wchar_t\*|marshal_context|marshal.h|
|Konstante wchar_t \*|System::String^|marshal_as|marshal.h|
|wchar_t \*|System::String^|marshal_as|marshal.h|
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|
|System::String^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System::String^|marshal_as|marshal.h|
|System::String^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::String^|marshal_as|marshal_windows.h|
|System::String^|std::string|marshal_as|marshal_cppstd.h|
|std::string|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|CStringT\<Char >|marshal_as|marshal_atl.h|
|CStringT\<Char >|System::String^|marshal_as|marshal_atl.h|
|System::String^|CStringT < wchar_t >|marshal_as|marshal_atl.h|
|CStringT < wchar_t >|System::String^|marshal_as|marshal_atl.h|
|System::String^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String^|marshal_as|marshal_atl.h|

Marshalling erfordert nur einen Kontext, wenn Sie von verwalteten in systemeigene Datentypen marshallen und der systemeigene Typ, den Sie konvertieren, keinen Destruktor zur automatischen Bereinigung besitzt. Der Marshallingkontext zerstört den zugeordneten nativen Datentyp in seinem Destruktor. Daher sind Konvertierungen, die einen Kontext erfordern, nur gültig, bis der Kontext gelöscht wird. Um alle gemarshallten Werte zu speichern, müssen Sie die Werte in Ihre eigenen Variablen kopieren.

> [!NOTE]
>  Wenn Sie `NULL` in die Zeichenfolge eingebettet haben, ist das Ergebnis des Marshallens der Zeichenfolge nicht garantiert. Durch eine eingebettete `NULL` kann die Zeichenfolge abgeschnitten oder beibehalten werden.

Dieses Beispiel zeigt, wie das Verzeichnis "msclr" einer Includeheaderdeklaration hinzugefügt wird:

`#include "msclr\marshal_cppstd.h"`

Die Marshallingbibliothek ist erweiterbar, sodass Sie eigene Marshallingtypen hinzufügen können. Weitere Informationen zum Erweitern der Marshallingbibliothek finden Sie unter Gewusst [wie: Erweitern der](../dotnet/how-to-extend-the-marshaling-library.md)Marshallingbibliothek.

## <a name="see-also"></a>Siehe auch

[C++-Standardbibliothek](../dotnet/cpp-support-library.md)<br/>
[Vorgehensweise: Erweitern der Marshallingbibliothek](../dotnet/how-to-extend-the-marshaling-library.md)
