---
title: Templateingestantiations-Klasse
description: Die C++ buildinsights-SDK-templateinstantiations-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2c94f8d3a4613e072c03f6dd4c846798d3d2122b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334523"
---
# <a name="templateinstantiation-class"></a>Templateingestantiations-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TemplateInstantiation`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `TemplateInstantiation`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Templatin stantiations](#template-instantiation)

### <a name="functions"></a>Functions

[Kind](#kind)
[primarytemplatesymbolkey](#primary-template-symbol-key)
[spezialisierersymbolkey](#specialization-symbol-key)

## <a name="kind"></a>Art

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Vorlageninstanziierung beschreibt.

## <a name="primary-template-symbol-key"></a>Primarytemplatesymbolkey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den spezialisierten Vorlagentyp. Dieser Bezeichner ist innerhalb eines compilerfront-End-bestanden eindeutig.

## <a name="specialization-symbol-key"></a>Spezialisierationsymbolkey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den Typ der Spezialisierung. Dieser Bezeichner ist innerhalb eines compilerfront-End-bestanden eindeutig.

## <a name="template-instantiation"></a>Templatin stantiations

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignis.

::: moniker-end
