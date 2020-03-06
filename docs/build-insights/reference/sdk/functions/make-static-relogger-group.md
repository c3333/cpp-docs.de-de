---
title: Makestatikreloggergroup
description: Die C++ Funktionsreferenz für das Build Insights SDK makestatikreloggergroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334385"
---
# <a name="makestaticreloggergroup"></a>Makestatikreloggergroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeStaticReloggerGroup`-Funktion wird verwendet, um eine statische der reloggersitzung-Gruppe zu erstellen, die an Funktionen wie z. b. [relog](relog.md)übergeben werden kann. Mitglieder einer der reloggersitzung-Gruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablauf Verfolgung verarbeitet wurden.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parameter

*Treloggerptrs* -\
Dieser Parameter wird immer abgeleitet.

*reloggers*\
Ein Parameter Paket von [irelogger](../other-types/irelogger-class.md) -Zeigern, das in der statischen der reloggersitzung-Gruppe enthalten ist. Diese Zeiger können RAW, `std::unique_ptr`oder `std::shared_ptr`sein. [Ianalyzer](../other-types/ianalyzer-class.md) -Zeiger werden aufgrund einer Vererbungs Beziehung auch als `IRelogger` Zeiger betrachtet.

### <a name="return-value"></a>Rückgabewert

Eine statische der reloggersitzung-Gruppe. Verwenden Sie das Schlüsselwort " **Auto** ", um den Rückgabewert aufzuzeichnen.

## <a name="remarks"></a>Bemerkungen

Anders als dynamische der reloggersitzung-Gruppen müssen die Mitglieder einer statischen der reloggersitzung-Gruppe zum Zeitpunkt der Kompilierung bekannt sein. Darüber hinaus enthält eine statische der reloggersitzung-Gruppe [irelogger](../other-types/irelogger-class.md) -Zeiger, die kein polymorphes Verhalten aufweisen. Wenn eine statische der reloggersitzung-Gruppe verwendet wird, um eine ETW-Ablauf Verfolgung (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows) zu analysieren, werden Aufrufe der `IRelogger`-Schnittstelle immer in das Objekt aufgelöst, auf das das Gruppenelement der reloggersitzung Dieser Verlust von Flexibilität bietet die Möglichkeit, schnellere Ereignis Verarbeitungszeiten zu verursachen. Wenn die Mitglieder einer der reloggersitzung-Gruppe zum Zeitpunkt der Kompilierung nicht bekannt sein können oder wenn Sie polymorphe Verhalten auf den `IRelogger` Zeigern benötigen, sollten Sie die Verwendung einer dynamischen der reloggersitzung-Gruppe in Erwägung gezogen. Sie können eine dynamische der reloggersitzung-Gruppe verwenden, indem Sie stattdessen [makedynamicreloggergroup](make-dynamic-relogger-group.md) aufrufen.

::: moniker-end
