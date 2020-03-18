---
title: /GS (Puffer-Sicherheitsüberprüfung)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 92d296e8079a9ecd8d366c46bbdad8b2ee5dc313
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439565"
---
# <a name="gs-buffer-security-check"></a>/GS (Puffer-Sicherheitsüberprüfung)

Erkennt einige Pufferüberläufe, welche die Rückgabeadresse einer Funktion, eine Ausnahmehandleradresse oder bestimmte Typen von Parametern überschreiben. Einen Pufferüberlauf zu verursachen ist eine von Hackern verwendete Technik, um Code auszunutzen, der keine Puffergrößeneinschränkungen erzwingt.

## <a name="syntax"></a>Syntax

```
/GS[-]
```

## <a name="remarks"></a>Bemerkungen

**/GS** ist standardmäßig aktiviert. Verwenden Sie **/GS-** , wenn Sie erwarten, dass für Ihre Anwendung keine Sicherheitsrisiko verfügbar ist. Weitere Informationen zum Unterdrücken der Pufferüberlauf Erkennung finden Sie unter [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Sicherheitsüberprüfungen

Bei Funktionen, die vom Compiler als überlaufgefährdet und problematisch eingestuft werden, reserviert der Compiler vor der Rückgabeadresse Speicherplatz auf dem Stapel. Bei einem Funktions Eintrag wird der zugewiesene Speicherplatz mit einem *Sicherheits Cookie* geladen, das einmal beim Laden des Moduls berechnet wird. Bei Funktionsende und beim Entladen von Rahmen auf 64-Bit-Betriebssystemen wird dann eine Hilfsfunktion aufgerufen, die sicherstellt, dass sich der Wert des Cookies nicht geändert hat. Ein abweichender Wert gibt an, dass der Stapel möglicherweise überschrieben wurde. Ein abweichender Wert führt dazu, dass der Prozess beendet wird.

## <a name="gs-buffers"></a>GS-Puffer

Eine Pufferüberlauf-Sicherheitsüberprüfung wird in einem *GS-Puffer*ausgeführt. Ein GS-Puffer kann einer der Folgenden sein:

- Ein Array, das größer als 4 Bytes ist und über mehr als zwei Elemente sowie einen Elementtyp verfügt, der kein Zeigertyp ist.

- Eine Datenstruktur, die größer als 8 Bytes ist und keine Zeiger enthält.

- Ein mit der [_alloca](../../c-runtime-library/reference/alloca.md) -Funktion zugewiesener Puffer.

- Eine beliebige Klasse oder Struktur, die einen GS-Puffer enthält.

Beispielsweise werden GS-Puffer durch die folgenden Anweisungen deklariert.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

Die folgenden Anweisungen deklarieren jedoch keine GS-Puffer. Die ersten beiden Deklarationen enthalten Elemente des Zeigertyps. Die dritte und vierte Anweisung deklariert Arrays, deren Größe zu klein ist. Die fünfte Anweisung deklariert eine Struktur, deren Größe auf einer x86-Plattform nicht mehr als 8 Bytes beträgt.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>Initialisieren des Sicherheitscookies

Die **/GS** -Compileroption erfordert, dass das Sicherheits Cookie initialisiert wird, bevor eine Funktion, die das Cookie verwendet, ausgeführt wird. Das Sicherheits Cookie muss sofort beim Eintrag für eine exe-oder dll-Assembly initialisiert werden. Dies erfolgt automatisch, wenn Sie die standardmäßigen vcruntime-Einstiegspunkte verwenden: MainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup oder _DllMainCRTStartup. Wenn Sie einen alternativen Einstiegspunkt verwenden, müssen Sie das Sicherheits Cookie manuell initialisieren, indem Sie [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)aufrufen.

## <a name="what-is-protected"></a>Geschützte Informationen

Die **/GS** -Compileroption schützt die folgenden Elemente:

- Die Rückgabeadresse eines Funktionsaufrufs.

- Die Adresse eines Ausnahmehandlers für eine Funktion.

- Anfällige Funktionsparameter.

Auf allen Plattformen versucht **/GS** , Pufferüberläufe in der Rückgabeadresse zu erkennen. Auf Plattformen wie x86 und x64 mit Aufrufkonventionen, durch welche die Rücksprungadresse eines Funktionsaufrufes auf dem Stapel gespeichert wird, lassen sich Pufferüberläufe leichter ausnutzen.

Wird auf x86-Systemen ein Ausnahme-Handler verwendet, fügt der Compiler ein Sicherheitscookie ein, um die Adresse des Ausnahmehandlers zu schützen. Dieses Cookie wird beim Entladen von Rahmen überprüft.

**/GS** schützt *anfällige Parameter* , die an eine Funktion übermittelt werden. Ein verwundbarer Parameter ist ein Zeiger, ein C++-Verweis oder eine C-Struktur (C++-POD-Typ), die einen Zeiger oder einen GS-Puffer enthält.

Ein verwundbarer Parameter wird vor dem Cookie und den lokalen Variablen zugeordnet. Durch einen Pufferüberlauf kann dieser Parameter überschrieben werden. Und der in der Funktion enthaltene Code, der diesen Parameter verwendet, könnte einen Angriff verursachen, bevor der Rücksprung aus der Funktion erfolgt und die Sicherheitsprüfung ausgeführt wird. Um diese Gefahr zu minimieren, erstellt der Compiler während des Funktionsprologs eine Kopie der verwundbaren Parameter und legt diese unterhalb des Speicherbereichs ab, in dem sich sämtliche Puffer befinden.

Der Compiler erstellt keine Kopien verwundbarer Parameter, wenn folgende Bedingungen erfüllt sind:

- Funktionen enthalten keinen GS-Puffer.

- Optimierungen ([/O-Optionen](o-options-optimize-code.md)) sind nicht aktiviert.

- Funktionen verfügen über eine variable Argumentliste (...).

- Funktionen, die mit [Naked](../../cpp/naked-cpp.md)markiert sind.

- Funktionen enthalten Inlineassemblycode in der ersten Anweisung.

- Ein Parameter wird nur auf eine Art und Weise verwendet, die im Falle eines Pufferüberlaufs höchstwahrscheinlich nicht ausgenutzt werden kann.

## <a name="what-is-not-protected"></a>Nicht geschützte Informationen

Die **/GS** -Compileroption schützt nicht vor allen Sicherheitsangriffen mit Pufferüberlauf. Wenn ein Objekt beispielsweise einen Puffer und eine vtable enthält, könnte der Pufferüberlauf die vtable beschädigen.

Selbst wenn Sie **/GS**verwenden, versuchen Sie immer, sicheren Code zu schreiben, der keine Pufferüberläufe aufweist.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>So legen Sie diese Compileroption in Visual Studio fest

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

   Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie im Dialogfeld **Eigenschaften Seiten** auf den Ordner **CC++ /** .

1. Klicken Sie auf die Eigenschaften Seite **Code Generierung** .

1. Ändern Sie die Eigenschaft **Puffer Sicherheitsüberprüfung** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein Pufferüberlauf stattfinden. Dadurch versagt die Anwendung zur Laufzeit.

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
