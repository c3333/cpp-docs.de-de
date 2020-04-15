---
title: Compileroptionen Makros
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331625"
---
# <a name="compiler-options-macros"></a>Compileroptionen Makros

Diese Makros steuern bestimmte Compilerfeatures.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Ein Symbol, das Fehler in Projekten ermöglicht, die aus früheren Versionen von ATL konvertiert wurden.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Legen Sie fest, ob eines oder mehrere Ihrer Objekte das Einfädeln von Wohnungen verwenden.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Macht `CString` bestimmte Konstruktoren explizit und verhindert unbeabsichtigte Konvertierungen.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definieren Sie dieses Makro, um die C++-Standardsyntax zu verwenden, die den C4867-Compilerfehler generiert, wenn eine nicht standardmäßige Syntax verwendet wird, um einen Zeiger auf eine Memberfunktion zu initialisieren.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Legen Sie fest, ob eines oder mehrere Ihrer Objekte freies oder neutrales Gewindeverwenden verwenden.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Ein Symbol, das angibt, dass das Projekt Objekte enthält, die als beide, Frei oder Neutral markiert sind. Stattdessen [sollte](#_atl_free_threaded) das _ATL_FREE_THREADED verwendet werden.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Ein Symbol, das die standardmäßige Verwendung von Namespace als ATL verhindert.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Ein Symbol, das verhindert, dass COM-bezogener Code mit Ihrem Projekt kompiliert wird.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Ein Symbol, das verhindert, dass der vtable-Zeiger im Konstruktor und Destruktor der Klasse initialisiert wird.|
|[ATL_NOINLINE](#atl_noinline)|Ein Symbol, das angibt, dass eine Funktion nicht eingefüttert werden soll.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Legen Sie fest, ob alle Objekte das einzelne Threadingmodell verwenden.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Ein Symbol, das Fehler in Projekten ermöglicht, die aus früheren Versionen von ATL konvertiert wurden.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Bemerkungen

Vor Visual C++ .NET 2002 hat ATL viele Warnungen deaktiviert und deaktiviert, sodass sie nie im Benutzercode angezeigt wurden. Dies gilt insbesondere in folgenden Fällen:

- Der bedingte Ausdruck C4127 ist konstant.

- C4786 'Bezeichner' : Bezeichner wurde in den Debuginformationen auf 'Number'-Zeichen abgeschnitten

- C4201 nicht standardmäßige Erweiterung verwendet : namenlose Struktur/Union

- C4103 'Dateiname' : verwendet #pragma-Pack, um die Ausrichtung zu ändern

- C4291 'Deklaration': kein übereinstimmender Operatorlöschen gefunden; Speicher wird nicht freigegeben, wenn die Initialisierung eine Ausnahme auslöst

- C4268 'Bezeichner' : 'const' statische/globale Daten initialisiert mit Compiler-generiertem Standardkonstruktor füllt das Objekt mit Nullen

- C4702 nicht erreichbarer Code

In Projekten, die aus früheren Versionen konvertiert wurden, werden diese Warnungen weiterhin von den Bibliotheksheadern deaktiviert.

Durch Hinzufügen der folgenden Zeile zur Datei *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) vor dem Einschließen von Bibliotheksheadern kann dieses Verhalten geändert werden.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Wenn `#define` dies hinzugefügt wird, achten die ATL-Header darauf, den Status dieser Warnungen beizubehalten, damit sie nicht global deaktiviert werden (oder wenn der Benutzer einzelne Warnungen explizit deaktiviert, um sie nicht zu aktivieren).

Neue Projekte `#define` haben diesen Satz standardmäßig in *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) festgelegt.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Legen Sie fest, ob eines oder mehrere Ihrer Objekte das Einfädeln von Wohnungen verwenden.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Bemerkungen

Gibt das Einfädeln der Wohnung an. Eine Beschreibung der für ein ATL-Objekt verfügbaren Threadingmodelle finden Sie unter [Angeben des Threadingmodells](../../atl/specifying-the-threading-model-for-a-project-atl.md) des Projekts für andere Threadingoptionen und [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Macht `CString` bestimmte Konstruktoren explizit und verhindert unbeabsichtigte Konvertierungen.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Bemerkungen

Wenn dieser Konstruktor definiert ist, werden alle CString-Konstruktoren, die einen einzelnen Parameter annehmen, mit dem expliziten Schlüsselwort kompiliert, wodurch implizite Konvertierungen von Eingabeargumenten verhindert werden. Dies bedeutet z. B., dass bei der Definition _UNICODE, wenn Sie versuchen, eine char*-Zeichenfolge als CString-Konstruktorargument zu verwenden, ein Compilerfehler resultieren. Verwenden Sie dieses Makro in Situationen, in denen Sie implizite Konvertierungen zwischen schmalen und breiten Zeichenfolgentypen verhindern müssen.

Wenn Sie das _T-Makro für alle Konstruktorzeichenfolgenargumente verwenden, können Sie _ATL_CSTRING_EXPLICIT_CONSTRUCTORS definieren und Kompilierungsfehler vermeiden, unabhängig davon, ob _UNICODE definiert ist.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Definieren Sie dieses Makro, um die Verwendung der ANSI C++-Standardsyntax für Zeiger auf Memberfunktionen zu erzwingen. Die Verwendung dieses Makros bewirkt, dass der C4867-Compilerfehler generiert wird, wenn eine nicht standardmäßige Syntax verwendet wird, um einen Zeiger auf eine Memberfunktion zu initialisieren.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Bemerkungen

Die ATL- und MFC-Bibliotheken wurden entsprechend der verbesserten C++-Standard-C++-Konformität des Microsoft C++-Compilers geändert. Gemäß dem ANSI C++-Standard sollte die Syntax eines Zeigers `&CMyClass::MyFunc`auf eine Klassenmemberfunktion .

Wenn [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) nicht definiert ist (Standardfall), deaktiviert ATL/MFC den C4867-Fehler in Makrozuordnungen (insbesondere Nachrichtenzuordnungen), sodass Code, der in früheren Versionen erstellt wurde, weiterhin wie zuvor erstellt werden kann. Wenn Sie **_ATL_ENABLE_PTM_WARNING**definieren, sollte ihr Code C++-Standard kompatibel sein.

Das nicht standardmäßige Formular ist jedoch veraltet. Sie müssen vorhandenen Code in die C++-Standardsyntax verschieben. Beispielsweise folgender Code:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Änderung erforderlich in:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Fügen Sie für Kartenmakros das bildende und & Zeichen hinzu. Sie sollten das Zeichen nicht erneut in Ihren Code hinzufügen.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Legen Sie fest, ob eines oder mehrere Ihrer Objekte freies oder neutrales Gewindeverwenden verwenden.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Bemerkungen

Gibt das kostenlose Threading an. Kostenloses Einfädeln entspricht einem Multithread-Apartmentmodell. Eine Beschreibung der für ein ATL-Objekt verfügbaren Threadingmodelle finden Sie unter [Angeben des Threadingmodells](../../atl/specifying-the-threading-model-for-a-project-atl.md) des Projekts für andere Threadingoptionen und [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Ein Symbol, das angibt, dass das Projekt Objekte enthält, die als beide, Frei oder Neutral markiert sind.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Bemerkungen

Wenn dieses Symbol definiert ist, ruft ATL Code ein, der den Zugriff auf globale Daten korrekt synchronisiert. Neuer Code sollte stattdessen das entsprechende Makro [_ATL_FREE_THREADED](#_atl_free_threaded) verwenden.

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Ein Symbol, das die standardmäßige Verwendung von Namespace als ATL verhindert.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Bemerkungen

Wenn dieses Symbol nicht definiert ist, wird einschließlich atlbase.h standardmäßig **mit Namespace ATL** ausgeführt, was zu Namenskonflikten führen kann. Um dies zu verhindern, definieren Sie dieses Symbol.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Ein Symbol, das verhindert, dass COM-bezogener Code mit Ihrem Projekt kompiliert wird.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Ein Symbol, das verhindert, dass der vtable-Zeiger im Konstruktor und Destruktor der Klasse initialisiert wird.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Bemerkungen

Wenn verhindert wird, dass der vtable-Zeiger im Konstruktor und Destruktor der Klasse initialisiert wird, kann der Linker die vtable und alle Funktionen, auf die er verweist, eliminieren. Erweitert auf **__declspec(novtable)**.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Ein Symbol, das angibt, dass eine Funktion nicht eingefüttert werden soll.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parameter

*Myfunction*<br/>
Die Funktion, die nicht einstrichen sollte.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Symbol, wenn Sie sicherstellen möchten, dass eine Funktion nicht vom Compiler inline wird, obwohl sie als Inline deklariert werden muss, damit sie in einer Headerdatei platziert werden kann. Erweitert auf **__declspec(noinline)**.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Definieren, ob alle Objekte das einzelne Threadingmodell verwenden

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Bemerkungen

Gibt an, dass das Objekt immer im primären COM-Thread ausgeführt wird. Eine Beschreibung der für ein ATL-Objekt verfügbaren Threadingmodelle finden Sie unter [Angeben des Threadingmodells](../../atl/specifying-the-threading-model-for-a-project-atl.md) des Projekts für andere Threadingoptionen und [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
