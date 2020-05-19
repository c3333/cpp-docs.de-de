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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328598"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportieren und Importieren mithilfe von AFX_EXT_CLASS

[MFC-Erweiterungs-DLLs](extension-dlls-overview.md) (Dynamic Link Library) verwenden das Makro **AFX_EXT_CLASS** zum Exportieren von Klassen. Die ausführbaren Dateien, die mit der MFC-Erweiterungs-DLL verknüpft sind, verwenden das Makro, um Klassen zu importieren. Mit dem Makro **AFX_EXT_CLASS** können die gleichen Headerdateien, die zum Erstellen der MFC-Erweiterungs-DLL verwendet werden, mit den ausführbaren Dateien verwendet werden, die mit der DLL verknüpft sind.

Fügen Sie in der Headerdatei für die DLL der Deklaration der Klasse das **AFX_EXT_CLASS**-Schlüsselwort wie folgt hinzu:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Dieses Makro wird von der MFC als `__declspec(dllexport)` definiert, wenn die Präprozessorsymbole `_AFXDLL` und `_AFXEXT` definiert werden. Das Makro wird jedoch als `__declspec(dllimport)` definiert, wenn `_AFXDLL` definiert und `_AFXEXT` nicht definiert ist. Im Falle einer Definition gibt das Präprozessorsymbol `_AFXDLL` an, dass die freigegebene MFC-Version von der ausführbaren Zieldatei verwendet wird (entweder eine DLL oder eine Anwendung). Wenn sowohl `_AFXDLL` als auch `_AFXEXT` definiert sind, gibt dies an, dass die ausführbare Zieldatei eine MFC-Erweiterungs-DLL ist.

Da `AFX_EXT_CLASS` beim Exportieren aus einer MFC-Erweiterungs-DLL als `__declspec(dllexport)` definiert ist, können Sie ganze Klassen exportieren, ohne die dekorierten Namen für alle Symbole dieser Klasse in der DEF-Datei abzulegen.

Obwohl Sie das Erstellen einer DEF-Datei und aller dekorierten Namen für die Klasse mit dieser Methode vermeiden können, ist das Erstellen einer DEF-Datei effizienter, da die Namen nach Ordinalzahl exportiert werden können. Fügen Sie den folgenden Code am Anfang und am Ende der Headerdatei ein, wenn Sie die DEF-Dateimethode für den Export verwenden möchten:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Beim Exportieren von Inlinefunktionen müssen Sie vorsichtig vorgehen, da diese Versionskonflikte verursachen können. Eine Inlinefunktion wird in den Anwendungscode erweitert. Wenn Sie deshalb die Funktion später neu schreiben, wird sie erst dann aktualisiert, wenn die Anwendung selbst neu kompiliert wird. (In der Regel können DLL-Funktionen ohne Neuerstellung der Anwendungen aktualisiert werden, die diese verwenden.)

## <a name="exporting-individual-members-in-a-class"></a>Exportieren einzelner Member in einer Klasse

Manchmal möchten Sie möglicherweise einzelne Member einer Klasse exportieren. Wenn Sie z. B. eine von `CDialog` abgeleitete Klasse exportieren, müssen Sie möglicherweise nur den Konstruktor und den `DoModal`-Aufruf exportieren. Sie können `AFX_EXT_CLASS` für die einzelnen Member verwenden, die Sie exportieren müssen.

Zum Beispiel:

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

Da Sie nicht mehr alle Member der Klasse exportieren, kann es aufgrund der Funktionsweise von MFC-Makros zu einem zusätzlichen Problem kommen. Mehrere MFC-Hilfsmakros deklarieren oder definieren Datenmember. Daher müssen diese Datenmember auch aus der DLL exportiert werden.

Beispielsweise wird das `DECLARE_DYNAMIC`-Makro beim Aufbau einer MFC-Erweiterungs-DLL wie folgt definiert:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Die Zeile, die mit dem statischen Element `AFX_DATA` beginnt, deklariert ein statisches Objekt in der Klasse. Wenn Sie diese Klasse ordnungsgemäß exportieren und auf die Runtimeinformationen einer ausführbaren Clientdatei zugreifen möchten, müssen Sie dieses statische Objekt exportieren. Da das statische Objekt mit dem Modifizierer `AFX_DATA` deklariert ist, müssen Sie `AFX_DATA` beim Erstellen Ihrer DLL nur als `__declspec(dllexport)` und beim Erstellen der ausführbaren Clientdatei als `__declspec(dllimport)` definieren. Da `AFX_EXT_CLASS` bereits auf diese Weise definiert ist, müssen Sie `AFX_DATA` wie `AFX_EXT_CLASS` nur um Ihre Klassendefinition herum neu definieren.

Zum Beispiel:

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

Da die MFC immer das `AFX_DATA`-Symbol für Datenelemente verwendet, die in den Makros definiert werden, funktioniert diese Technik für all diese Szenarios. Beispielsweise funktioniert es für `DECLARE_MESSAGE_MAP`.

> [!NOTE]
> Wenn Sie die gesamte Klasse anstelle ausgewählter Member der Klasse exportieren, werden statische Datenmember automatisch exportiert.

### <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Dekorierte Namen](reference/decorated-names.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
