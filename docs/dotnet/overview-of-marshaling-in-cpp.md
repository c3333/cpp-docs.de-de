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
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372012"
---
# <a name="overview-of-marshaling-in-ccli"></a>Überblick über Das Marshalling in C++/CLI

Im gemischten Modus müssen Sie die Daten zwischen nativen und verwalteten Typen manchmal marshallen. Die *Marshalling-Bibliothek* hilft Ihnen, Daten auf einfache Weise zu marshallen und zu konvertieren.  Die Marshallingbibliothek besteht aus einer `marshal_context` Reihe von Funktionen und einer Klasse, die Dasiziels für allgemeine Typen ausführen. Die Bibliothek ist in diesen Headern im **Include/msclr-Verzeichnis** für Ihre Visual Studio-Edition definiert:

|Header|BESCHREIBUNG|
|---------------|-----------------|
|marshal.h|`marshal_context`Klassen- und kontextfreie Marshalling-Funktionen|
|marshal_atl.h| Funktionen zum Marshallen von ATL-Typen|
|marshal_cppstd.h|Funktionen zum Marshalling von Standard-C++-Typen|
|marshal_windows.h|Funktionen zum Marshallen von Windows-Typen|

Der Standardpfad für **msclr-Ordner** ist ungefähr so, je nachdem, welche Edition Sie haben und die Buildnummer:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Sie können die Marshallingbibliothek mit oder ohne [marshal_context Klasse](../dotnet/marshal-context-class.md)verwenden. Einige Konvertierungen erfordern einen Kontext. Andere Konvertierungen können mit der [marshal_as-Funktion](../dotnet/marshal-as.md) implementiert werden. Die folgende Tabelle enthält eine Liste der aktuell unterstützten Konvertierungen und Informationen dazu, ob sie einen Kontext benötigen und welche Marschalldatei Sie hinzufügen müssen:

|Von Typ|in Typ|Marschallmethode|Includedatei|
|---------------|-------------|--------------------|------------------|
|System::String^|const char\*|marshal_context|marshal.h|
|const char\*|System::String^|marshal_as|marshal.h|
|Char\*|System::String^|marshal_as|marshal.h|
|System::String^|const wchar_t\*|marshal_context|marshal.h|
|const wchar_t\*|System::String^|marshal_as|marshal.h|
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
|System::String^|CStringT->\<|marshal_as|marshal_atl.h|
|CStringT->\<|System::String^|marshal_as|marshal_atl.h|
|System::String^|CStringT<wchar_t>|marshal_as|marshal_atl.h|
|CStringT<wchar_t>|System::String^|marshal_as|marshal_atl.h|
|System::String^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String^|marshal_as|marshal_atl.h|

Marshalling erfordert nur einen Kontext, wenn Sie von verwalteten in systemeigene Datentypen marshallen und der systemeigene Typ, den Sie konvertieren, keinen Destruktor zur automatischen Bereinigung besitzt. Der Marshallingkontext zerstört den zugeordneten nativen Datentyp in seinem Destruktor. Daher sind Konvertierungen, die einen Kontext erfordern, nur gültig, bis der Kontext gelöscht wird. Um alle gemarshallten Werte zu speichern, müssen Sie die Werte in Ihre eigenen Variablen kopieren.

> [!NOTE]
> Wenn Sie `NULL` in die Zeichenfolge eingebettet haben, ist das Ergebnis des Marshallens der Zeichenfolge nicht garantiert. Durch eine eingebettete `NULL` kann die Zeichenfolge abgeschnitten oder beibehalten werden.

Dieses Beispiel zeigt, wie das Verzeichnis "msclr" einer Includeheaderdeklaration hinzugefügt wird:

`#include "msclr\marshal_cppstd.h"`

Die Marshallingbibliothek ist erweiterbar, sodass Sie eigene Marshallingtypen hinzufügen können. Weitere Informationen zum Erweitern der Marshallingbibliothek finden Sie unter [Gewusst wie: Erweitern der Marshallingbibliothek](../dotnet/how-to-extend-the-marshaling-library.md).

## <a name="see-also"></a>Siehe auch

[C++-Supportbibliothek](../dotnet/cpp-support-library.md)<br/>
[Gewusst wie: Erweitern der Marshallingbibliothek](../dotnet/how-to-extend-the-marshaling-library.md)
