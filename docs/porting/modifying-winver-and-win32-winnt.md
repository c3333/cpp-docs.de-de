---
title: Aktualisieren von WINVER und _WIN32_WINNT
description: Wann und wie aktualisieren Sie Winver-und _WIN32_WINNT Makros in aktualisierten Visual Studio C++-Projekten.
ms.date: 06/19/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: a0faed612517bf26cd89473e1aef248fb9e7b33e
ms.sourcegitcommit: 493fd8747f832e1facb9a76c437a25a5c9fb55f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141053"
---
# <a name="update-winver-and-_win32_winnt"></a>Aktualisieren von WINVER und _WIN32_WINNT

Wenn Sie die Windows SDK verwenden, können Sie angeben, auf welchen Versionen von Windows der Code ausgeführt werden kann. Die Präprozessormakros **winver** und **_WIN32_WINNT** geben die minimale Betriebssystemversion an, die der Code unterstützt. Visual Studio und die Microsoft C++-Compilerunterstützung für Windows 7 SP1 und höher. Ältere Toolsets umfassen Unterstützung für Windows XP SP2, Windows Server 2003 SP1, Vista und Windows Server 2008. Windows 95, Windows 98, Windows Me, Windows NT und Windows 2000 werden nicht unterstützt.

Wenn Sie ein älteres Projekt aktualisieren, müssen Sie möglicherweise Ihre **winver** -oder **_WIN32_WINNT** -Makros aktualisieren. Wenn Ihnen Werte für eine nicht unterstützte Version von Windows zugewiesen sind, werden möglicherweise Kompilierungsfehler im Zusammenhang mit diesen Makros angezeigt.

## <a name="remarks"></a>Hinweise

Fügen Sie die folgenden Zeilen hinzu, um die Makros in einer Header Datei (z. b. in " *targetver. h*", die in einigen Projektvorlagen für Windows enthalten ist) zu ändern.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Die Makros im Beispiel sind so festgelegt, dass Sie auf jede Version des Windows 10-Betriebssystems abzielen. Die möglichen Werte sind in der Windows-Header Datei *sdkddkver. h*aufgeführt, mit der Makros für die einzelnen Hauptversionen von Windows definiert werden. Wenn Sie Ihre Anwendung zur Unterstützung einer früheren Windows-Plattform erstellen möchten, schließen Sie " *winsdkver. h*" ein. Legen Sie dann die **winver** -und **_WIN32_WINNT** Makros auf die älteste unterstützte Plattform fest, bevor Sie " *sdkddkver. h*" einschließen. Im folgenden finden Sie die Zeilen aus der Windows 10 SDK-Version von *sdkddkver. h* , die die Werte für die einzelnen Hauptversionen von Windows codieren:

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

Für einen differenzierteren Ansatz bei der Versionsverwaltung können Sie die ntddi-Versions Konstanten in " *sdkddkver. h*" verwenden. Im folgenden finden Sie einige der Makros, die von " *sdkddkver. h* " in der Windows 10 SDK-Version 10.0.18362.0 definiert werden:

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

Die **osver**-, **spver**-und **Subver** -Makros können im Code verwendet werden, um die bedingte Kompilierung für verschiedene Ebenen der API-Unterstützung zu steuern.

Möglicherweise werden nicht alle diese Versionen von Windows in der Datei " *sdkddkver. h* " aufgeführt, die Sie sich ansehen. Dies bedeutet, dass Sie wahrscheinlich eine ältere Version des Windows SDK verwenden. Standardmäßig verwenden neue Windows-Projekte in Visual Studio das Windows 10-SDK.

> [!NOTE]
> Es ist nicht gewährleistet, dass die Werte auf jeden Fall funktionieren, wenn Sie interne MFC-Header in die Anwendung aufnehmen.

Dieses Makro kann auch mithilfe der `/D`-Compileroption definiert werden. Weitere Informationen finden Sie unter [/D (Präprozessordefinitionen)](../build/reference/d-preprocessor-definitions.md).

Weitere Informationen zur Bedeutung dieser Makros finden Sie unter [Verwenden der Windows-Header](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Weitere Informationen

[Änderungsverlauf von Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
