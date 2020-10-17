---
title: Implementieren eines Fensters mit CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 7ce1a2ec08e49e047aee5248bda0094d9e392614
ms.sourcegitcommit: ced5ff1431ffbd25b20d106901955532723bd188
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92135514"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementieren eines Fensters mit CWindowImpl

Zum Implementieren eines Fensters leiten Sie eine Klasse von ab `CWindowImpl` . Deklarieren Sie in der abgeleiteten Klasse eine Meldungs Zuordnung und die nachrichtenhandlerfunktionen. Sie können Ihre Klasse jetzt auf drei verschiedene Arten verwenden:

- [Erstellen eines Fensters auf der Grundlage einer neuen Windows-Klasse](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Übergeordnete Klasse einer vorhandenen Windows-Klasse](#_atl_superclassing_an_existing_windows_class)

- [Unterklasse eines vorhandenen Fensters](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Erstellen eines Fensters auf der Grundlage einer neuen Windows-Klasse

`CWindowImpl` enthält das [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) Makro, um Windows-Klassen Informationen zu deklarieren. Dieses Makro implementiert die- `GetWndClassInfo` Funktion, die [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) verwendet, um die Informationen einer neuen Windows-Klasse zu definieren. Wenn `CWindowImpl::Create` aufgerufen wird, wird diese Windows-Klasse registriert und ein neues Fenster erstellt.

> [!NOTE]
> `CWindowImpl` übergibt NULL an das `DECLARE_WND_CLASS` Makro. Dies bedeutet, dass ATL einen Windows-Klassennamen generiert. Um einen eigenen Namen anzugeben, übergeben Sie eine Zeichenfolge an DECLARE_WND_CLASS in der von `CWindowImpl` abgeleiteten Klasse.

## <a name="example-implement-a-window"></a>Beispiel: Implementieren eines Fensters

Im folgenden finden Sie ein Beispiel für eine Klasse, die ein Fenster implementiert, das auf einer neuen Windows-Klasse basiert:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Erstellen Sie zum Erstellen eines Fensters eine Instanz von, `CMyWindow` und rufen Sie dann die- `Create` Methode auf.

> [!NOTE]
> Um die standardmäßigen Windows-Klassen Informationen zu überschreiben, implementieren Sie die- `GetWndClassInfo` Methode in der abgeleiteten Klasse, indem Sie die Elemente `CWndClassInfo` auf die entsprechenden Werte festlegen.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a> Übergeordnete Klassen für eine vorhandene Windows-Klasse

Mit dem [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) -Makro können Sie ein Fenster erstellen, das eine vorhandene Windows-Klasse überlagert. Geben Sie dieses Makro in der von `CWindowImpl` abgeleiteten Klasse an. Wie jedes andere ATL-Fenster werden Nachrichten von einer Meldungs Zuordnung verarbeitet.

Wenn Sie DECLARE_WND_SUPERCLASS verwenden, wird eine neue Windows-Klasse registriert. Diese neue Klasse ist identisch mit der von Ihnen angegebenen vorhandenen Klasse, ersetzt jedoch die Fenster Prozedur durch `CWindowImpl::WindowProc` (oder durch die Funktion, die diese Methode überschreibt).

## <a name="example-superclass-the-edit-class"></a>Beispiel: übergeordnete Klasse der Edit-Klasse

Im folgenden finden Sie ein Beispiel für eine Klasse, die die Klasse "Standard Edit" überlagert:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Um das übergeordnete Bearbeitungsfenster zu erstellen, erstellen Sie eine Instanz von, `CMyEdit` und rufen Sie dann die- `Create` Methode auf.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a> Unterklassen für ein vorhandenes Fenster

Um ein vorhandenes Fenster zu unterteilen, leiten Sie eine Klasse von ab, `CWindowImpl` und deklarieren Sie eine Meldungs Zuordnung, wie in den beiden vorherigen Fällen. Beachten Sie jedoch, dass Sie keine Informationen zu Windows-Klassen angeben, da Sie ein bereits vorhandenes Fenster Unterklassen.

Statt `Create` aufzurufen, rufen `SubclassWindow` Sie auf, und übergeben Sie das Handle an das vorhandene Fenster, das Sie Unterklasse verwenden möchten. Sobald das Fenster untergeordnet ist, wird `CWindowImpl::WindowProc` (oder die Funktion, die diese Methode überschreibt) zum Weiterleiten von Nachrichten an die Meldungs Zuordnung verwendet. Um ein untergeordnetes Fenster vom-Objekt zu trennen, müssen Sie den Befehl `UnsubclassWindow` . Die ursprüngliche Fenster Prozedur des Fensters wird dann wieder hergestellt.

## <a name="see-also"></a>Siehe auch

[Implementieren eines Fensters](../atl/implementing-a-window.md)
