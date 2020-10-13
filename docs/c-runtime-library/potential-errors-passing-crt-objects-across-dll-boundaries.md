---
title: Potenzielle Fehler bei der Übergabe von CRT-Objekten über DLL-Grenzen
description: Eine Übersicht über mögliche Probleme, die bei der Übergabe von Microsoft C-Lauf Zeit Objekten über eine DLL-Grenze (Dynamic Link Library) auftreten können.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 2d42803b5eca7a43f122d209b7d9e2d4e45c38de
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008942"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Potenzielle Fehler bei der Übergabe von CRT-Objekten über DLL-Grenzen

Wenn Sie C-Lauf Zeit Objekte, z. b. Datei Handles, Gebiets Schemas und Umgebungsvariablen, mithilfe von Funktionsaufrufen über die DLL-Grenze in bzw. aus einer DLL übergeben, kann unerwartetes Verhalten auftreten, wenn die dll oder Dateien, die die DLL aufrufen, unterschiedliche Kopien der CRT-Bibliotheken verwenden.

Ein verwandtes Problem kann auftreten, wenn Sie Speicher zuweisen (entweder explizit mit `new` oder `malloc` oder implizit mit `strdup` , `strstreambuf::str` usw.) und dann einen Zeiger über eine DLL-Grenze übergeben, in der er freigegeben wird. Dies kann zu einer Speicherzugriffs Verletzung oder einer Heap Beschädigung führen, wenn die dll und deren Consumer unterschiedliche Kopien der CRT-Bibliotheken verwenden.

Ein weiteres Symptom dieses Problems ist ein Fehler im Ausgabefenster während des Debuggens, wie z. b. `HEAP[]: Invalid Address specified to RtlValidateHeap(#,#)`

## <a name="causes"></a>Ursachen

Jede Kopie der CRT-Bibliothek verfügt über einen eigenen Status, der von Ihrer App oder DLL im lokalen Threadspeicher gespeichert wird.

CRT-Objekte, z. b. Datei Handles, Umgebungsvariablen und Gebiets Schemas, sind nur für die Kopie der CRT in der APP oder dll gültig, in der diese Objekte zugeordnet oder festgelegt wurden. Wenn eine DLL und Ihre Clients unterschiedliche Kopien der CRT-Bibliothek verwenden, können Sie diese CRT-Objekte nicht über die DLL-Grenze hinweg übergeben und erwarten, dass Sie auf der anderen Seite ordnungsgemäß verwendet werden. Dies gilt für CRT-Versionen vor der universellen CRT in Visual Studio 2015 und höher.

Für jede mit Visual Studio 2013 oder früher erstellte Version von Visual Studio gab es eine versionsspezifische CRT-Bibliothek. Interne Implementierungsdetails der CRT, wie z. b. Datenstrukturen und Benennungs Konventionen, unterscheiden sich in jeder Version. Das dynamische Verknüpfen von Code, der für eine Version der CRT kompiliert wurde, in eine andere Version der CRT-DLL wurde nie unterstützt. Gelegentlich funktioniert Sie, aber aufgrund von Glück und nicht über das Design.

Da jede Kopie der CRT-Bibliothek über einen eigenen Heap-Manager verfügt, kann das belegen von Speicher in einer CRT-Bibliothek und das Übergeben des Zeigers über eine DLL-Grenze, die durch eine andere Kopie der CRT-Bibliothek freigegeben werden kann, zu Heap Beschädigungen führen. Wenn Sie die DLL so entwerfen, dass Sie CRT-Objekte über die DLL-Grenze hinweg übergibt, oder Arbeitsspeicher zuweist und davon ausgeht, dass Sie außerhalb der dll freigegeben werden, müssen die Clients der dll dieselbe Kopie der CRT-Bibliothek wie die DLL verwenden.

Die DLL und die DLL-Clients verwenden normalerweise nur dann die gleiche Kopie der CRT-Bibliothek, wenn beide zur Ladezeit mit der gleichen Version der CRT-DLL verknüpft sind. Da die dll-Version der universellen CRT-Bibliothek, die von Visual Studio 2015 und höher unter Windows 10 verwendet wird, jetzt eine zentral bereitgestellte Windows-Komponente (ucrtbase.dll) ist, ist Sie für apps, die mit Visual Studio 2015 und höheren Versionen erstellt wurden, identisch. Auch wenn der CRT-Code identisch ist, können Sie in einem Heap zugeordnete Arbeitsspeicher nicht an eine Komponente übergeben, die einen anderen Heap verwendet.

## <a name="example-pass-file-handle-across-dll-boundary"></a>Beispiel: übergeben des Datei Handles über eine DLL-Grenze

### <a name="description"></a>Beschreibung

Dieses Beispiel übergibt ein Dateihandle über eine DLL-Grenze.

Die dll-und exe-Dateien werden mit erstellt `/MD` , sodass Sie eine einzige Kopie der CRT gemeinsam verwenden.

Wenn Sie mit neu erstellen `/MT` , sodass die einzelnen Kopien der CRT verwendet werden, führt das Ausführen der resultierenden **test1Main.exe** zu einer Zugriffsverletzung.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example-pass-environment-variables-across-dll-boundary"></a>Beispiel: übergeben von Umgebungsvariablen über eine DLL-Grenze

### <a name="description"></a>Beschreibung

Dieses Beispiel übergibt Umgebungsvariablen über eine DLL-Grenze hinweg.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

Wenn die dll-und exe-Datei so erstellt werden, `/MD` dass nur eine Kopie der CRT verwendet wird, wird das Programm erfolgreich ausgeführt, und es wird die folgende Ausgabe erzeugt:

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Siehe auch

[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)
