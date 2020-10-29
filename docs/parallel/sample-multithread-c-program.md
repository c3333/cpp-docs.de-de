---
title: Beispiel für ein C-Multithreadprogramm
ms.date: 08/09/2019
ms.assetid: 4706f6cd-ff9c-4dbf-99a2-1c999b568f17
ms.openlocfilehash: 355024b995dc638b89a335983bd2e0f2cb0d96ce
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924762"
---
# <a name="sample-multithread-c-program"></a>Beispiel für ein C-Multithreadprogramm

Bounce. c ist ein Beispiel für ein Multithreadprogramm, das jedes Mal einen neuen Thread erstellt, wenn der Buchstabe oder der Buchstabe `a` `A` eingegeben wird. Jeder Thread springt einen Buchstaben mit einer anderen Farbe um den Bildschirm. Es können bis zu 32 Threads erstellt werden. Die normale Beendigung des Programms tritt auf, wenn `q` oder `Q` eingegeben wird.

## <a name="compile-and-link-a-multithread-program"></a>Kompilieren und Verknüpfen eines Multithreadprogramms

Programme werden standardmäßig als multithreadkompiliert.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>So kompilieren und verknüpfen Sie das Multithreadprogramm "Bounce. c" in der Entwicklungsumgebung

::: moniker range=">=msvc-160"

1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt** .

1. Wählen Sie im Dialogfeld **Neues Projekt erstellen** die **Konsolen-App** -Vorlage mit den Tags **C++** , **Windows** und **Console** aus. Wählen Sie zum Fortfahren **Weiter** aus.

1. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** einen Namen für das Projekt ein, z. b. "Bounce". Wählen Sie **Erstellen** , um fortzufahren.

1. Öffnen Sie im Fenster **Projektmappen-Explorer** den Ordner **Quelldateien** in Ihrem Projekt, und ändern Sie den Namen der Quelldatei, sodass Sie die Erweiterung ". c" hat.

1. Löschen Sie im Bearbeitungsfenster den vorhandenen Quellcode, und ersetzen Sie ihn durch den Beispielcode.

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** .

1. Drücken Sie **F5** , um das Programm im Debugger zu starten.

::: moniker-end

::: moniker range="<=msvc-150"

1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt** .

1. Wählen Sie im Dialogfeld **Neues Projekt** im linken Bereich **Visual C++** aus, und klicken Sie dann im mittleren Bereich auf **leeres Projekt** .

1. Geben Sie im Bearbeitungsfeld **Name** einen Namen für das Projekt ein, z. b. "Bounce". Wählen Sie **OK** aus, um das leere Projekt zu erstellen.

1. Öffnen Sie im Fenster **Projektmappen-Explorer** den Ordner **Quelldateien** in Ihrem Projekt, und fügen Sie dem Projekt die Datei mit dem C-Quellcode hinzu.

1. Erstellen Sie im Menü **Erstellen** das Projekt, indem Sie den Befehl Projekt Mappe **Erstellen** auswählen.

1. Drücken Sie **F5** , um das Programm im Debugger zu starten.

::: moniker-end

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>So kompilieren und verknüpfen Sie das Multithreadprogramm "Bounce. c" über die Befehlszeile

1. Kompilieren und verknüpfen Sie das Programm:

    ```cmd
    cl bounce.c
    ```

## <a name="example"></a>Beispiel

Kopieren Sie dieses Beispiel, und speichern Sie es in einer Quelldatei mit der Erweiterung ". c", um auf der Befehlszeile zu erstellen. Ersetzen Sie in der IDE alle durch die Vorlage erstellten Quellcodes durch dieses Beispiel:

```C
// sample_multithread_c_program.c
// compile with: /c
//
//  Bounce - Creates a new thread each time the letter 'a' is typed.
//  Each thread bounces a character of a different color around
//  the screen. All threads are terminated when the letter 'Q' is
//  entered.
//

#include <windows.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>
#include <process.h>

#define MAX_THREADS  32

// The function getrandom returns a random number between
// min and max, which must be in integer range.
#define getrandom( min, max ) (SHORT)((rand() % (int)(((max) + 1) - \
                               (min))) + (min))

int main(void);                    // Thread 1: main
void KbdFunc(void);                // Keyboard input, thread dispatch
void BounceProc(void* MyID);       // Threads 2 to n: display
void ClearScreen(void);            // Screen clear
void ShutDown(void);               // Program shutdown
void WriteTitle(int ThreadNum);    // Display title bar information

HANDLE  hConsoleOut;                 // Handle to the console
HANDLE  hRunMutex;                   // "Keep Running" mutex
HANDLE  hScreenMutex;                // "Screen update" mutex
int     ThreadNr;                    // Number of threads started
CONSOLE_SCREEN_BUFFER_INFO csbiInfo; // Console information
COORD   consoleSize;
BOOL    bTrails;

int main() // Thread One
{
    // Get display screen information & clear the screen.
    hConsoleOut = GetStdHandle(STD_OUTPUT_HANDLE);
    GetConsoleScreenBufferInfo(hConsoleOut, &csbiInfo);
    consoleSize.X = csbiInfo.srWindow.Right;
    consoleSize.Y = csbiInfo.srWindow.Bottom;
    ClearScreen();
    WriteTitle(0);

    // Create the mutexes and reset thread count.
    hScreenMutex = CreateMutexW(NULL, FALSE, NULL);  // Cleared
    hRunMutex = CreateMutexW(NULL, TRUE, NULL);      // Set
    ThreadNr = 0;
    bTrails = FALSE;

    // Start waiting for keyboard input to dispatch threads or exit.
    KbdFunc();

    // All threads done. Clean up handles.
    if (hScreenMutex) CloseHandle(hScreenMutex);
    if (hRunMutex) CloseHandle(hRunMutex);
    if (hConsoleOut) CloseHandle(hConsoleOut);
}

void ShutDown(void) // Shut down threads
{
    while (ThreadNr > 0)
    {
        // Tell thread to die and record its death.
        ReleaseMutex(hRunMutex);
        ThreadNr--;
    }

    // Clean up display when done
    WaitForSingleObject(hScreenMutex, INFINITE);
    ClearScreen();
}

void KbdFunc(void) // Dispatch and count threads.
{
    int         KeyInfo;

    do
    {
        KeyInfo = _getch();
        if (tolower(KeyInfo) == 'a' &&
            ThreadNr < MAX_THREADS)
        {
            ThreadNr++;
            _beginthread(BounceProc, 0, &ThreadNr);
            WriteTitle(ThreadNr);
        }
        if (tolower(KeyInfo) == 't')
        {
            bTrails = !bTrails;
        }
    } while (tolower(KeyInfo) != 'q');

    ShutDown();
}

void BounceProc(void* pMyID)
{
    wchar_t MyCell, OldCell;
    WORD    MyAttrib, OldAttrib = 0;
    wchar_t BlankCell = 0x20;
    COORD   Coords, Delta;
    COORD   Old = { 0,0 };
    DWORD   Dummy;
    char* MyID = (char*)pMyID;

    // Generate update increments and initial
    // display coordinates.
    srand((unsigned int)* MyID * 3);

    Coords.X = getrandom(0, consoleSize.X - 1);
    Coords.Y = getrandom(0, consoleSize.Y - 1);
    Delta.X = getrandom(-3, 3);
    Delta.Y = getrandom(-3, 3);

    // Set up character & generate color
    // attribute from thread number.
    if (*MyID > 16)
        MyCell = 0x60 + *MyID - 16; // lower case
    else
        MyCell = 0x40 + *MyID;      // upper case
    MyAttrib = *MyID & 0x0f;   // force black background

    do
    {
        // Wait for display to be available, then lock it.
        WaitForSingleObject(hScreenMutex, INFINITE);

        if (!bTrails)
        {
            // If we still occupy the old screen position, blank it out.
            ReadConsoleOutputCharacterW(hConsoleOut, &OldCell, 1,
                Old, &Dummy);
            ReadConsoleOutputAttribute(hConsoleOut, &OldAttrib, 1,
                Old, &Dummy);
            if ((OldCell == MyCell) && (OldAttrib == MyAttrib))
                WriteConsoleOutputCharacterW(hConsoleOut, &BlankCell, 1,
                    Old, &Dummy);
        }

        // Draw new character, then clear screen lock
        WriteConsoleOutputCharacterW(hConsoleOut, &MyCell, 1,
            Coords, &Dummy);
        WriteConsoleOutputAttribute(hConsoleOut, &MyAttrib, 1,
            Coords, &Dummy);
        ReleaseMutex(hScreenMutex);

        // Increment the coordinates for next placement of the block.
        Old.X = Coords.X;
        Old.Y = Coords.Y;
        Coords.X += Delta.X;
        Coords.Y += Delta.Y;

        // If we are about to go off the screen, reverse direction
        if (Coords.X < 0 || Coords.X >= consoleSize.X)
        {
            Delta.X = -Delta.X;
            Beep(400, 50);
        }
        if (Coords.Y < 0 || Coords.Y > consoleSize.Y)
        {
            Delta.Y = -Delta.Y;
            Beep(600, 50);
        }
    }
    // Repeat while RunMutex is still taken.
    while (WaitForSingleObject(hRunMutex, 75L) == WAIT_TIMEOUT);
}

void WriteTitle(int ThreadNum)
{
    enum
    {
        sizeOfNThreadMsg = 120
    };
    wchar_t    NThreadMsg[sizeOfNThreadMsg] = { L"" };

    swprintf_s(NThreadMsg, sizeOfNThreadMsg,
        L"Threads running: %02d.  Press 'A' "
        L"to start a thread, 'T' to toggle "
        L"trails, 'Q' to quit.", ThreadNum);
    SetConsoleTitleW(NThreadMsg);
}

void ClearScreen(void)
{
    DWORD    dummy = 0;
    COORD    Home = { 0, 0 };
    FillConsoleOutputCharacterW(hConsoleOut, L' ',
        consoleSize.X * consoleSize.Y,
        Home, &dummy);
}
```

## <a name="see-also"></a>Siehe auch

[Multithreading bei C und Win32](multithreading-with-c-and-win32.md)
