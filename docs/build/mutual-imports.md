---
title: Gegenseitige Importe
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295672"
---
# <a name="mutual-imports"></a>Gegenseitige Importe

Beim Exportieren oder Importieren in eine andere ausführbare Datei kommt es zu Problemen, wenn es sich um gegenseitige Importe (oder Ringimporte) handelt. Ein Beispiel hierfür wäre, dass zwei DLLs Symbole aus der jeweils anderen DLL importieren, ähnlich wie bei gegenseitig rekursiven Funktionen.

Das Problem beim gegenseitigen Importieren von ausführbaren Dateien (in der Regel DLLs) besteht darin, dass keine der beiden Dateien erstellt werden kann, ohne dass zuerst die andere erstellt wird. Jeder der Buildprozesse erfordert als Eingabe eine Importbibliothek, die vom jeweils anderen Buildprozess erstellt wird.

Die Lösung besteht darin, das Hilfsprogramm LIB mit der Option /DEF zu verwenden, wodurch eine Importbibliothek erstellt wird, aber keine ausführbare Datei. Mit diesem Hilfsprogramm können Sie alle benötigten Importbibliotheken erstellen, unabhängig davon, wie viele DLLs beteiligt sind und wie kompliziert die Abhängigkeiten sind.

Die allgemeine Lösung für den Umgang mit gegenseitigen Importen ist folgende:

1. Verwenden Sie die einzelnen DLLs nacheinander. (Jede Reihenfolge ist möglich, auch wenn manche besser geeignet sind als andere.) Wenn alle benötigten Importbibliotheken vorhanden und aktuell sind, führen Sie LINK aus, um die ausführbare Datei (DLL) zu erstellen. Hierdurch wird eine Importbibliothek erstellt. Führen Sie ansonsten LIB aus, um eine Importbibliothek zu erstellen.

   Beim Ausführen von LIB mit der Option /DEF wird eine zusätzliche Datei mit der Erweiterung „.exp“ erstellt. Die EXP-Datei muss später zum Erstellen der ausführbaren Datei verwendet werden.

1. Wenn Sie mit LINK oder LIB alle Importbibliotheken erstellt haben, wechseln Sie zurück, und führen Sie LINK aus, um alle ausführbaren Dateien zu erstellen, die im vorherigen Schritt noch nicht erstellt wurden. Beachten Sie, dass die entsprechende EXP-Datei in der LINK-Zeile angegeben werden muss.

   Wenn Sie das Hilfsprogramm LIB bereits ausgeführt haben, um eine Importbibliothek für DLL1 zu erzeugen, hat LIB die Datei „DLL1.exp“ bereits ebenfalls erstellt. Sie müssen die Datei „DLL1.exp“ als Eingabe für LINK verwenden, wenn Sie „DLL1.dll“ erstellen.

Die folgende Abbildung zeigt eine Lösung für zwei sich gegenseitig importierende DLLs, DLL1 und DLL2. Schritt 1 ist das Ausführen von LIB mit der Option /DEF für DLL1. In Schritt 1 werden „DLL1.lib“, eine Importbibliothek, und „DLL1.exp“ erstellt. In Schritt 2 wird die Importbibliothek verwendet, um DLL2 zu erstellen, wobei wiederum eine Importbibliothek für die Symbole von DLL2 erstellt wird. In Schritt 3 wird DLL1 erstellt, wobei „DLL1.exp“ und „DLL2.lib“ als Eingabe verwendet werden. Beachten Sie, dass für DLL2 keine EXP-Datei erforderlich ist, da LIB nicht zum Erstellen der Importbibliothek von DLL2 verwendet wurde.

![Verwenden von gegenseitigen Importen zum Verknüpfen von zwei DLLs](media/vc37yj1.gif "Verwenden von gegenseitigen Importen zum Verknüpfen von zwei DLLs")<br/>
Verknüpfen von zwei DLLs mit gegenseitigen Importen

## <a name="limitations-of-_afxext"></a>Einschränkungen für _AFXEXT

Sie können das Präprozessorsymbol `_AFXEXT` für Ihre MFC-Erweiterungs-DLLs verwenden, solange Sie nicht über mehrere Ebenen von MFC-Erweiterungs-DLLs verfügen. Wenn Sie über MFC-Erweiterungs-DLLs verfügen, die Klassen aus Ihren eigenen MFC-Erweiterungs-DLLs aufrufen oder davon abgeleitet sind, und diese wiederum von den MFC-Klassen abgeleitet sind, müssen Sie ein eigenes Präprozessorsymbol verwenden, um Mehrdeutigkeit zu vermeiden.

Das Problem besteht darin, dass Sie in Win32 alle Daten explizit als **__declspec(dllexport)** deklarieren müssen, wenn sie aus einer DLL exportiert werden sollen, und als **__declspec(dllimport)** , wenn sie aus einer DLL importiert werden sollen. Wenn Sie `_AFXEXT` definieren, stellen die MFC-Header sicher, dass **AFX_EXT_CLASS** ordnungsgemäß definiert ist.

Wenn Sie über mehrere Ebenen verfügen, ist ein Symbol, z. B. **AFX_EXT_CLASS**, nicht ausreichend, da eine MFC-Erweiterungs-DLL möglicherweise neue Klassen exportiert und andere Klassen aus einer anderen MFC-Erweiterungs-DLL importiert. Dieses Problem können Sie beheben, indem Sie ein spezielles Präprozessorsymbol verwenden, das angibt, ob Sie die DLL erstellen oder verwenden. Stellen Sie sich beispielsweise zwei MFC-Erweiterungs-DLLs vor: „A.dll“ und „B.dll“. Diese exportieren jeweils einige Klassen in „A.h“ bzw. „B.h“. „B.dll“ verwendet die Klassen aus „A.dll“. Die Headerdateien würden in etwa wie folgt aussehen:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

Wenn „A.dll“ erstellt wird, wird `/D A_IMPL` verwendet, und wenn „B.dll“ erstellt wird, wird `/D B_IMPL` verwendet. Wenn Sie für jede DLL eigene Symbole verwenden, wird beim Erstellen von „B.dll“ `CExampleB` exportiert und `CExampleA` importiert. Die Klasse `CExampleA` wird exportiert, wenn „A.dll“ erstellt wird, und importiert, wenn sie von „B.dll“ (oder einem anderen Client) verwendet wird.

Ebenen können so nicht verwendet werden, wenn die integrierten **AFX_EXT_CLASS**- und `_AFXEXT`-Präprozessorsymbole verwendet werden. Mit dem oben beschriebenen Verfahren wird dieses Problem auf eine Weise gelöst, die dem Mechanismus ähnelt, den MFC selbst bei der Erstellung von Active Technology-, Datenbank- und Netzwerk-MFC-Erweiterungs-DLLs verwendet.

## <a name="not-exporting-the-entire-class"></a>Exportieren von Teilen einer Klasse

Wenn Sie nicht die gesamte Klasse exportieren, müssen Sie sicherstellen, dass die von den MFC-Makros erstellten erforderlichen Datenelemente ordnungsgemäß exportiert werden. Dies können Sie erreichen, indem Sie `AFX_DATA` neu als das Makro der jeweiligen Klasse definieren. Dies sollten Sie immer tun, wenn Sie nicht die gesamte Klasse exportieren.

Zum Beispiel:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL](exporting-from-a-dll.md)

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von „AFX_EXT_CLASS“](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Das Hilfsprogramm LIB und die Option /DEF](reference/lib-reference.md)

## <a name="see-also"></a>Siehe auch

[Importieren und Exportieren](importing-and-exporting.md)
