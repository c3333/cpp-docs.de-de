---
title: Exportieren und Importieren mithilfe von AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328598"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportieren und Importieren mithilfe von AFX_EXT_CLASS

[MFC-Erweiterungs-DLLs](extension-dlls-overview.md) verwenden die **Makro-AFX_EXT_CLASS** zum Exportieren von Klassen. Die ausführbaren Dateien, die mit der MFC-Erweiterungs-DLL verknüpft sind, verwenden das Makro zum Importieren von Klassen. Mit dem **AFX_EXT_CLASS-Makro** können dieselben Headerdateien, die zum Erstellen der MFC-Erweiterungs-DLL verwendet werden, mit den ausführbaren Dateien verwendet werden, die mit der DLL verknüpft sind.

Fügen Sie in der Headerdatei für Ihre DLL das **AFX_EXT_CLASS** Schlüsselwort der Deklaration Ihrer Klasse wie folgt hinzu:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Dieses Makro wird von `__declspec(dllexport)` MFC als `_AFXDLL` wenn `_AFXEXT` die Präprozessorsymbole definiert sind und definiert sind. Das Makro ist `__declspec(dllimport)` jedoch `_AFXDLL` definiert `_AFXEXT` als wann definiert ist und nicht definiert ist. Wenn definiert, gibt `_AFXDLL` das Präprozessorsymbol an, dass die freigegebene Version von MFC von der ausführbaren Zieldatei (entweder einer DLL oder einer Anwendung) verwendet wird. Wenn `_AFXDLL` beide `_AFXEXT` definiert sind und definiert sind, bedeutet dies, dass es sich bei der ausführbaren Zieldatei um eine MFC-Erweiterungs-DLL handelt.

Da `AFX_EXT_CLASS` beim `__declspec(dllexport)` Exportieren aus einer MFC-Erweiterungs-DLL definiert ist, können Sie ganze Klassen exportieren, ohne die ergänzten Namen für alle Symbole dieser Klasse in der .def-Datei zu platzieren.

Obwohl Sie das Erstellen einer .def-Datei und aller ergänzten Namen für die Klasse mit dieser Methode vermeiden können, ist das Erstellen einer .def-Datei effizienter, da die Namen durch Ordinal exportiert werden können. Um die .def-Dateimethode zum Exportieren zu verwenden, platzieren Sie den folgenden Code am Anfang und Am Ende der Headerdatei:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Seien Sie vorsichtig beim Exportieren von Inlinefunktionen, da sie die Möglichkeit von Versionskonflikten erzeugen können. Eine Inline-Funktion wird in den Anwendungscode erweitert. Wenn Sie die Funktion später neu schreiben, wird sie daher nur aktualisiert, wenn die Anwendung selbst neu kompiliert wird. Normalerweise können DLL-Funktionen aktualisiert werden, ohne die Anwendungen, die sie verwenden, neu zu erstellen.

## <a name="exporting-individual-members-in-a-class"></a>Exportieren einzelner Elemente in einer Klasse

Manchmal möchten Sie möglicherweise einzelne Mitglieder Ihrer Klasse exportieren. Wenn Sie z. B. eine `CDialog`-derived-Klasse exportieren, müssen Sie `DoModal` möglicherweise nur den Konstruktor und den Aufruf exportieren. Sie können `AFX_EXT_CLASS` die einzelnen Elemente verwenden, die Sie exportieren müssen.

Beispiel:

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

Da Sie nicht mehr alle Member der Klasse exportieren, kann ein zusätzliches Problem auftreten, da MFC-Makros funktionieren. Mehrere Hilfsmakros von MFC deklarieren oder definieren Tatsächlich Datenmember. Daher müssen diese Datenmember auch aus Ihrer DLL exportiert werden.

Beispielsweise wird `DECLARE_DYNAMIC` das Makro beim Erstellen einer MFC-Erweiterungs-DLL wie folgt definiert:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Die Zeile, die `AFX_DATA` mit static beginnt, deklariert ein statisches Objekt innerhalb Ihrer Klasse. Um diese Klasse korrekt zu exportieren und auf die Laufzeitinformationen aus einer ausführbaren Clientdatei zuzugreifen, müssen Sie dieses statische Objekt exportieren. Da das statische Objekt mit dem `AFX_DATA`Modifikator `AFX_DATA` deklariert `__declspec(dllexport)` wird, müssen Sie nur `__declspec(dllimport)` beim Erstellen der DLL definieren und es als beim Erstellen der ausführbaren Clientdatei definieren. Da `AFX_EXT_CLASS` dies bereits auf diese Weise definiert `AFX_DATA` ist, müssen `AFX_EXT_CLASS` Sie nur neu definieren, um mit der Klassendefinition identisch zu sein.

Beispiel:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

Da MFC immer `AFX_DATA` das Symbol für Datenelemente verwendet, die es in seinen Makros definiert, funktioniert diese Technik für alle diese Szenarien. Es funktioniert z. `DECLARE_MESSAGE_MAP`B. für .

> [!NOTE]
> Wenn Sie die gesamte Klasse und nicht die ausgewählten Member der Klasse exportieren, werden statische Datenmember automatisch exportiert.

### <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Bestimmen, welche Exportmethode verwendet werden soll](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Dekorierte Namen](reference/decorated-names.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Einfuhren](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
