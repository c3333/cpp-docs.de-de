---
title: 'Ressourcencompiler: Fehler RW2003'
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: 60e813fff46ebc015f281dfed99d2916ca0eb4bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190611"
---
# <a name="resource-compiler-error-rw2003"></a>Ressourcencompiler: Fehler RW2003

Generierungs Fehler

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. **Fehler: die Ressourcen Datei der Bitmapdatei ist nicht im 3,00-Format.**

   Bitmaps mit dem Windows-Version 2.x-Format können nicht in Ressourcendateien der Version 3.x verwendet werden. Die Bitmap muss neu gezeichnet oder in das 3. x-Format konvertiert werden.

1. **Fehler: altes DIB in Ressourcen Name. Übergeben von SDKPAINT**

   Eine geräteunabhängige Bitmap (DIB) in der angegebenen Ressource ist nicht mit dem Windows 3,0-Format kompatibel. Die Bitmap muss neu gezeichnet oder in das 3. x-Format konvertiert werden.

1. **Fehler: Ressourcen Datei Ressource-Name ist nicht im 3,00-Format.**

   Ein Symbol oder ein Cursor in der angegebenen Ressource hat ein Format aus einer früheren Version von Windows verwendet. Das Symbol oder der Cursor muss neu gezeichnet oder in das 3. x-Format konvertiert werden.

1. **Unbekanntes DIB-Header Format**

   Der Bitmap-Header ist keine BITMAPCOREHEADER-oder BITMAPINFOHEADER-Struktur.

1. **Symbol Informationen können nicht initialisiert werden.**

   Dieser Fehler tritt nur in Visual C++auf. Die wahrscheinlichste Ursache ist, dass Sie zu viele geöffnete Dateien haben oder nicht in den Datendateien, die für die Visualisierung C++ erforderlich sind, um die Symbole in das Skript zu importieren. Visual C++ versucht, diese Dateien in dem Verzeichnis zu erstellen, das von der **tmp** -Umgebungsvariablen oder dem aktuellen Verzeichnis angegeben wird, wenn kein Wert angegeben ist.

1. **Symbol Informationen können nicht gespeichert werden.**

   Dieser Fehler tritt nur in Visual C++auf. Die wahrscheinlichste Ursache ist, dass Sie zu viele geöffnete Dateien haben, oder Sie können die Datendateien, die für Visual C++ erforderlich sind, um die Symbole in das Skript zu importieren, nicht schließen oder in diese schreiben. Visual C++ versucht, diese Dateien in dem Verzeichnis zu verwenden, das von der **tmp** -Umgebungsvariablen oder dem aktuellen Verzeichnis angegeben wird, wenn kein Wert angegeben ist.

1. **Die Ressourcen Datei der Bitmapdatei ist nicht im 2,03-Format.**

   Für eine Bitmap wurde ein Format einer früheren Version als Version 2.03 verwendet. Die Bitmap muss neu gezeichnet oder in das Format für Version 3.00 oder eine höhere Version konvertiert werden.

1. **Ressource zu groß**

   Für Windows 3,1 darf eine Ressource etwa 65000 Bytes nicht überschreiten. Wenn Ihre Ressource funktioniert, können Sie Sie nicht mit Visual C++ oder dem Befehlszeilen-Ressourcen Compiler kompilieren. Dieser Grenzwert gilt nicht für Cursor, Symbole, Bitmaps oder andere dateibasierte Ressourcen.

1. **Die Ressourcen Datei weist nicht das 3,00-Format auf.**

   Ein Cursor oder Symbol hat ein Format vor Version 3,00 verwendet. Die Ressource muss mit dem Format für Version 3,00 oder höher konvertiert oder neu gezeichnet werden.

1. **Die temporäre Datei kann nicht geöffnet werden.**

   Der Ressourcencompiler/Visual C++ konnte eine temporäre Datei nicht öffnen. Die wahrscheinlichste Ursache ist, dass Sie nicht über Schreibberechtigungen für das Verzeichnis verfügen oder dass das Verzeichnis nicht vorhanden ist. Der Ressourcencompiler/Visual C++ versucht, diese Dateien im von der **TMP** -Umgebungsvariablen angegebenen Verzeichnis bzw. im aktuellen Verzeichnis zu verwenden, wenn kein Verzeichnis angegeben ist.
