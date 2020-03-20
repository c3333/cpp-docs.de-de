---
title: Konvertieren von Projekten im gemischten Modus in reine Intermediate Language
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 05ece23e6d79fc399085099deebcde0aa4a92c64
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544735"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Konvertieren von Projekten im gemischten Modus in reine Zwischensprache

Alle Visual C++ CLR-Projekte sind standardmäßig mit den C-Laufzeitbibliotheken verknüpft. Folglich werden diese Projekte als Anwendungen im gemischten Modus klassifiziert, da Sie nativen Code mit Code kombinieren, der die Common Language Runtime (verwalteter Code) als Ziel hat. Wenn Sie kompiliert werden, werden Sie in Intermediate Language (IL) kompiliert, auch bekannt als MSIL (Microsoft Intermediate Language).

> [!IMPORTANT]
> Visual Studio 2015 ist veraltet, und Visual Studio 2017 unterstützt die Erstellung von **/clr: pure** oder **/clr: Safe** -Code für CLR-Anwendungen nicht mehr. Wenn Sie reine oder sichere Assemblys benötigen, empfiehlt es sich, die C#Anwendung in zu übersetzen.

Wenn Sie eine frühere Version des Microsoft C++ -compilertoolsets verwenden, das **/clr: pure** oder **/clr: Safe**unterstützt, können Sie diesen Vorgang verwenden, um Ihren Code in pure MSIL zu konvertieren:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>So konvertieren Sie Ihre Anwendung im gemischten Modus in eine reine zwischen Sprache

1. Entfernen Sie Verknüpfungen zu den [C-Laufzeitbibliotheken](../c-runtime-library/crt-library-features.md) (CRT):

   1. Ändern Sie in der CPP-Datei, die den Einstiegspunkt der Anwendung definiert, den Einstiegspunkt in `Main()`. Die Verwendung von `Main()` gibt an, dass das Projekt nicht mit der CRT verknüpft ist.

   2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü die Option Eigenschaften aus, um die **Eigenschaften** Seiten für die Anwendung zu öffnen.

   3. Wählen Sie auf der Eigenschaften Seite **Advanced** Project für den **Linker**den **Einstiegspunkt** aus, und geben Sie dann **Main** in dieses Feld ein.

   4. Wählen Sie für Konsolen Anwendungen auf der Eigenschaften Seite **System** Projekt für den **Linker**das Feld **Subsystem** aus, und ändern Sie dieses in **Console (/Subsystem: Console)** .

      > [!NOTE]
      > Sie müssen diese Eigenschaft nicht für Windows Forms Anwendungen festlegen, da das **Subsystem** -Feld standardmäßig auf **Windows (/Subsystem: Windows)** festgelegt ist.

   5. Kommentieren Sie in *stdafx. h*alle `#include`-Anweisungen aus. Beispielsweise in Konsolen Anwendungen:

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       \- oder -

       Beispielsweise in Windows Forms Anwendungen:

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Kommentieren Sie für Windows Forms Anwendungen in Form1. cpp die `#include`-Anweisung aus, die auf Windows. h verweist. Beispiel:

      ```cpp
      // #include <windows.h>
      ```

2. Fügen Sie " *stdafx. h*" den folgenden Code hinzu:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Entfernen Sie alle nicht verwalteten Typen:

   Ersetzen Sie bei Bedarf nicht verwaltete Typen durch Verweise auf Strukturen aus dem [System](/dotnet/api/system) -Namespace. Allgemeine verwaltete Typen sind in der folgenden Tabelle aufgeführt:

   |Struktur|Beschreibung|
   |---------------|-----------------|
   |[Boolescher Wert](/dotnet/api/system.boolean)|Stellt einen booleschen Wert dar.|
   |[Byte](/dotnet/api/system.byte)|Stellt eine 8-Bit-Ganzzahl ohne Vorzeichen dar.|
   |[Char](/dotnet/api/system.char)|Stellt ein Unicode-Zeichen dar.|
   |[DateTime](/dotnet/api/system.datetime)|Stellt einen Zeitpunkt dar, der üblicherweise als Datum und Uhrzeit ausgedrückt wird.|
   |[Decimal](/dotnet/api/system.decimal)|Stellt eine Dezimalzahl dar.|
   |[Double](/dotnet/api/system.double)|Stellt eine Gleitkommazahl mit doppelter Genauigkeit dar.|
   |[Guid](/dotnet/api/system.guid)|Stellt einen Globally Unique Identifier (GUID) dar.|
   |[Int16](/dotnet/api/system.int16)|Stellt eine 16-Bit-Ganzzahl mit Vorzeichen dar.|
   |[Int32](/dotnet/api/system.int32)|Stellt eine 32-Bit-Ganzzahl mit Vorzeichen dar.|
   |[Int64](/dotnet/api/system.int64)|Stellt eine 64-Bit-Ganzzahl mit Vorzeichen dar.|
   |[IntPtr](/dotnet/api/system.intptr)|Ein plattformspezifischer Typ zum Darstellen eines Zeigers oder Handles.|
   |[SByte](/dotnet/api/system.byte)|Stellt eine 8-Bit-Ganzzahl mit Vorzeichen dar.|
   |[Single](/dotnet/api/system.single)|Stellt eine Gleitkommazahl mit einfacher Genauigkeit dar.|
   |[TimeSpan](/dotnet/api/system.timespan)|Stellt ein Zeitintervall dar.|
   |[UInt16](/dotnet/api/system.uint16)|Stellt eine 16-Bit-Ganzzahl ohne Vorzeichen dar.|
   |[UInt32](/dotnet/api/system.uint32)|Stellt eine 32-Bit-Ganzzahl ohne Vorzeichen dar.|
   |[UInt64](/dotnet/api/system.uint64)|Stellt eine 64-Bit-Ganzzahl ohne Vorzeichen dar.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Ein plattformspezifischer Typ zum Darstellen eines Zeigers oder Handles.|
   |[Blutung](/dotnet/api/system.void)|Gibt eine Methode an, die keinen Wert zurückgibt. Das heißt, die Methode weist den void-Rückgabetyp auf.|