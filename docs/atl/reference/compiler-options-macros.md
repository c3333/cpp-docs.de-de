---
title: CompilerOptions-Makros
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
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423207"
---
# <a name="compiler-options-macros"></a>CompilerOptions-Makros

Diese Makros steuern bestimmte Compilerfeatures.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Ein Symbol, das Fehler in Projekten ermöglicht, die aus früheren Versionen von ATL konvertiert wurden.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Legen Sie fest, ob ein oder mehrere ihrer Objekte das Apartment Threading verwenden.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Macht bestimmte `CString` Konstruktoren explizit und verhindert unbeabsichtigte Konvertierungen.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definieren Sie dieses Makro, um die C++ standardkonforme Syntax zu verwenden, die den C4867-Compilerfehler generiert, wenn eine nicht standardmäßige Syntax verwendet wird, um einen Zeiger auf eine Element Funktion zu initialisieren.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Legen Sie fest, ob eines oder mehrere der Objekte ein kostenloses oder neutrales Threading verwenden.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Ein Symbol, das angibt, dass das Projekt über Objekte verfügt, die als "frei" oder "neutral" gekennzeichnet sind. Stattdessen sollte das Makro [_ATL_FREE_THREADED](#_atl_free_threaded) verwendet werden.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Ein Symbol, das die Standardverwendung von Namespace als ATL verhindert.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Ein Symbol, das verhindert, dass com-bezogener Code mit dem Projekt kompiliert wird.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Ein Symbol, das verhindert, dass der vtable-Zeiger im Konstruktor und debugtor der Klasse initialisiert wird.|
|[ATL_NOINLINE](#atl_noinline)|Ein Symbol, das angibt, dass eine Funktion nicht Inline sein sollte.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Legen Sie fest, ob alle Objekte das einzelne Threading Modell verwenden.|

##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Ein Symbol, das Fehler in Projekten ermöglicht, die aus früheren Versionen von ATL konvertiert wurden.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Hinweise

Vor Visual C++ .NET 2002 hat ATL viele Warnungen deaktiviert und deaktiviert, sodass Sie im Benutzercode nicht angezeigt werden. Dies gilt insbesondere in folgenden Fällen:

- C4127 bedingter Ausdruck ist konstant

- C4786 ' Identifier ': der Bezeichner wurde in den Debuginformationen auf ' Number '-Zeichen gekürzt.

- C4201 nicht dem Standard entsprechende Erweiterung: namenlose Struktur/Union

- C4103 "Dateiname": verwendet #pragma Paket zum Ändern der Ausrichtung

- C4291 ' Deklaration ': Es wurde kein entsprechender Operator gelöscht gefunden. der Arbeitsspeicher wird nicht freigegeben, wenn die Initialisierung eine Ausnahme auslöst.

- C4268 ' Identifier ': ' Konstante ' statische/globale Daten, die mit dem vom Compiler generierten Standardkonstruktor initialisiert wurden, füllen das Objekt mit Nullen

- C4702 nicht erreichbarer Code

In Projekten, die aus früheren Versionen konvertiert wurden, werden diese Warnungen weiterhin von den Bibliotheks Headern deaktiviert.

Dieses Verhalten kann geändert werden, indem Sie der Datei " *PCH. h* " die folgende Zeile hinzufügen (*stdafx. h* in Visual Studio 2017 und früher).

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Wenn diese `#define` hinzugefügt wird, sind die ATL-Header darauf bedacht, den Zustand dieser Warnungen beizubehalten, damit Sie nicht global deaktiviert werden (oder wenn der Benutzer einzelne Warnungen explizit deaktiviert, ohne Sie zu aktivieren).

In neuen Projekten ist diese `#define` in " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher) standardmäßig festgelegt.

##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Legen Sie fest, ob ein oder mehrere ihrer Objekte das Apartment Threading verwenden.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Hinweise

Gibt Apartment Threading an. Weitere Informationen finden Sie unter [angeben des Threading Modells des Projekts](../../atl/specifying-the-threading-model-for-a-project-atl.md) für andere Threading Optionen und [Optionen, ATL-Assistent für einfache Objekte](../../atl/reference/options-atl-simple-object-wizard.md) für eine Beschreibung der Threading Modelle, die für ein ATL-Objekt verfügbar sind.

##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Macht bestimmte `CString` Konstruktoren explizit und verhindert unbeabsichtigte Konvertierungen.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Hinweise

Wenn dieser Konstruktor definiert ist, werden alle CString-Konstruktoren, die einen einzelnen Parameter annehmen, mit dem expliziten Schlüsselwort kompiliert, das implizite Konvertierungen von Eingabe Argumenten verhindert. Dies bedeutet beispielsweise, dass beim Versuch, eine char *-Zeichenfolge als CString-Konstruktorargument zu verwenden, ein Compilerfehler ausgegeben wird, wenn _UNICODE definiert ist. Verwenden Sie dieses Makro in Situationen, in denen implizite Konvertierungen zwischen schmalen und breiten Zeichen folgen Typen verhindert werden müssen.

Wenn Sie das _T-Makro für alle Konstruktorzeichenfolgen-Argumente verwenden, können Sie _ATL_CSTRING_EXPLICIT_CONSTRUCTORS definieren und Kompilierungsfehler vermeiden, unabhängig davon, ob _UNICODE definiert ist.

##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Definieren Sie dieses Makro, um die Verwendung von ANSI C++ -Standard kompatiblen Syntax für Zeiger auf Element Funktionen zu erzwingen. Die Verwendung dieses Makros bewirkt, dass der C4867-Compilerfehler generiert wird, wenn eine nicht standardmäßige Syntax verwendet wird, um einen Zeiger auf eine Element Funktion zu initialisieren.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Hinweise

Die ATL-und MFC-Bibliotheken wurden geändert, damit Sie C++ mit der verbesserten Standard C++ Konformität von Microsoft-Compiler übereinstimmen. Gemäß dem ANSI C++ -Standard sollte die Syntax eines Zeigers auf eine Klassenmember-Funktion `&CMyClass::MyFunc`werden.

Wenn [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) nicht definiert ist (Standardfall), deaktiviert ATL/MFC den C4867-Fehler in Makro Zuordnungen (insbesondere Meldungs Zuordnungen), sodass der Code, der in früheren Versionen erstellt wurde, weiterhin wie zuvor erstellt werden kann. Wenn Sie **_ATL_ENABLE_PTM_WARNING**definieren, sollte der Code Standard C++ konform sein.

Das nicht standardmäßige Formular ist jedoch veraltet. Sie müssen vorhandenen Code in C++ eine standardmäßige kompatible Syntax verschieben. Beispielsweise folgender Code:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Änderung erforderlich in:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Fügen Sie für Karten Makros das kaufmännische und-Zeichen "&" hinzu. Sie sollten das Zeichen im Code nicht erneut hinzufügen.

##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Legen Sie fest, ob eines oder mehrere der Objekte ein kostenloses oder neutrales Threading verwenden.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Hinweise

Gibt das kostenlose Threading an. Ein kostenloses Threading entspricht einem Multithread-Apartment Modell. Weitere Informationen finden Sie unter [angeben des Threading Modells des Projekts](../../atl/specifying-the-threading-model-for-a-project-atl.md) für andere Threading Optionen und [Optionen, ATL-Assistent für einfache Objekte](../../atl/reference/options-atl-simple-object-wizard.md) für eine Beschreibung der Threading Modelle, die für ein ATL-Objekt verfügbar sind.

##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Ein Symbol, das angibt, dass das Projekt über Objekte verfügt, die als "frei" oder "neutral" gekennzeichnet sind.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Hinweise

Wenn dieses Symbol definiert ist, ruft ATL Code ab, der den Zugriff auf globale Daten ordnungsgemäß synchronisiert. Neuer Code sollte stattdessen das äquivalente Makro [_ATL_FREE_THREADED](#_atl_free_threaded) verwenden.

##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Ein Symbol, das die Standardverwendung von Namespace als ATL verhindert.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Hinweise

Wenn dieses Symbol nicht definiert ist, wird von "atlbase. h" standardmäßig die **Verwendung der Namespace-ATL** durchgeführt. Dies kann zu Namenskonflikten führen. Um dies zu verhindern, definieren Sie dieses Symbol.

##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Ein Symbol, das verhindert, dass com-bezogener Code mit dem Projekt kompiliert wird.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>ATL_NO_VTABLE

Ein Symbol, das verhindert, dass der vtable-Zeiger im Konstruktor und debugtor der Klasse initialisiert wird.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Hinweise

Wenn der vtable-Zeiger nicht im Konstruktor und debugtor der Klasse initialisiert werden kann, kann der Linker die Vtable und alle Funktionen entfernen, auf die er verweist. Wird zu **__declspec (novtable)** erweitert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>ATL_NOINLINE

Ein Symbol, das angibt, dass eine Funktion nicht Inline sein sollte.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parameter

*MyFunction*<br/>
Die Funktion, die nicht Inline sein soll.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Symbol, wenn Sie sicherstellen möchten, dass eine Funktion nicht vom Compiler Inline geschaltet wird, obwohl Sie als Inline deklariert werden muss, damit Sie in eine Header Datei eingefügt werden kann. Wird zu **__declspec (noinline)** erweitert.

##  <a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Hiermit wird definiert, ob alle Objekte das einzelne Threading Modell verwenden.

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Hinweise

Gibt an, dass das Objekt immer im primären com-Thread ausgeführt wird. Weitere Informationen finden Sie unter [angeben des Threading Modells des Projekts](../../atl/specifying-the-threading-model-for-a-project-atl.md) für andere Threading Optionen und [Optionen, ATL-Assistent für einfache Objekte](../../atl/reference/options-atl-simple-object-wizard.md) für eine Beschreibung der Threading Modelle, die für ein ATL-Objekt verfügbar sind.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
