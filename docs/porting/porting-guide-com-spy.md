---
title: 'Leitfaden zum Portieren: COM Spy'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: f4fece07b9ea4541d8bf21dd81fd659b44f39718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368459"
---
# <a name="porting-guide-com-spy"></a>Leitfaden zum Portieren: COM Spy

Dieses Thema ist das zweite aus einer Reihe von Artikeln, in denen der Upgradevorgang für ältere C++-Projekte in Visual Studio auf die aktuellste Visual Studio-Version vorgestellt wird. Der Beispielcode in diesem Thema wurde zuletzt mit Visual Studio 2005 kompiliert.

## <a name="comspy"></a>COMSpy

COMSpy ist ein Programm, das die Aktivität von Serviced Components auf einem Computer überwacht und protokolliert. Serviced Components sind COM+-Komponenten, die auf einem System ausgeführt werden und von Computern im selben Netzwerk verwendet werden können. Sie werden durch die Funktion „Komponentendienste“ in der Windows-Systemsteuerung verwaltet.

### <a name="step-1-converting-the-project-file"></a>Schritt 1: Konvertieren der Projektdatei

Die Projektdatei lässt sich problemlos konvertieren und erstellt einen Migrationsbericht. Einige Einträge in dem Bericht geben Hinweise auf Probleme, die eventuell beseitigt werden müssen. Im Folgenden eines der gemeldeten Probleme. Beachten Sie, dass Fehlermeldungen in diesem Thema zur besseren Lesbarkeit manchmal gekürzt werden; z. B. werden die vollständigen Pfade teilweise entfernt.

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

Eines der häufigen Probleme beim Aktualisieren von Projekten besteht darin, dass die **Linker OutputFile-Einstellung** im Dialogfeld Projekteigenschaften möglicherweise überprüft werden muss. Bei Projekten vor Visual Studio 2010 ist OutputFile eine Einstellung, die dem Assistenten für die automatische Konvertierung Probleme bereitet, wenn sie nicht auf einen Standardwert festgelegt ist. In diesem Fall wurden die Pfade für die Ausgabedateien auf den nicht standardmäßigen Ordner XP32_DEBUG festgelegt. Weitere Informationen zu diesem Fehler finden Sie in diesem [Blogbeitrag](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) zum Visual Studio 2010-Projektupgrade, einem Upgrade, bei dem der wichtige Wechsel von vcbuild zu msbuild erfolgte. Gemäß den Informationen in diesem Blogbeitrag lautet der Standardwert für die **OutputFile**-Einstellung beim Erstellen eines neuen Projekts `$(OutDir)$(TargetName)$(TargetExt)`, doch wird dieser Wert nicht bei der Konvertierung festgelegt, da die Überprüfung der Richtigkeit für konvertierte Projekte nicht möglich ist. Wir prüfen nun trotzdem, ob dies für OutputFile möglich ist.  Es funktioniert und wir können den Vorgang fortsetzen. Wenn es keinen bestimmten Grund für die Verwendung eines nicht dem Standard entsprechenden Ausgabeordners gibt, wird die Verwendung des standardmäßigen Speicherorts empfohlen. In diesem Fall haben wir als Ausgabespeicherort während der Portierung und des Upgrades den nicht standardmäßigen Speicherort belassen. `$(OutDir)` wird in der **Debuggen**-Konfiguration in den XP32_DEBUG-Ordner und in der **Release**-Konfiguration in den ReleaseU-Ordner aufgelöst.

### <a name="step-2-getting-it-to-build"></a>Schritt 2: Erstellen des Projekts

Beim Erstellen des portierten Projekts treten eine Reihe von Fehlern und Warnungen auf.

`ComSpyCtl` wird aufgrund des folgenden Fehlers nicht kompiliert:

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

Die Fehlermeldung verweist auf die `Save`-Methode in der `IPersistStreamInitImpl`-Klasse in „atlcom.h“.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Das Problem besteht darin, dass eine Konvertierung, die von einer älteren Version des Compilers akzeptiert wurde, nicht mehr gültig ist. Um dem C++-Standard zu entsprechen, wird zuvor zulässiger Code nicht mehr zugelassen. In diesem Fall ist es nicht sicher, einen nicht konstanten Zeiger an eine Funktion zu übergeben, die einen konstanten Zeiger erwartet.  Die Lösung besteht darin, die Deklaration von `IPersistStreamInit_Save` in der `CComSpy`-Klasse zu suchen und den const-Modifizierer dem dritten Parameter hinzuzufügen.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

Eine ähnliche Änderung ist in `IPersistStreamInit_Load` erforderlich.

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

Der nächste Fehler befasst sich mit der Registrierung.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

Dieser Postbuild-Registrierungsbefehl wird nicht mehr benötigt. Stattdessen entfernen wir einfach den benutzerdefinierten Buildbefehl und geben in den **Linker-Einstellungen** an, um die Ausgabe zu registrieren.

### <a name="dealing-with-warnings"></a>Umgang mit Warnungen

Das Projekt erzeugt die folgende Linkerwarnung.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

Die Verwendung der Compileroption `/SAFESEH` ist im Modus „Debuggen“ nicht sinnvoll. Hier ist `/EDITANDCONTINUE` nützlich. Die Lösung besteht also darin, `/SAFESEH` ausschließlich für **Debuggen**-Konfigurationen zu deaktivieren. Dazu wird das Eigenschaftendialogfeld des Projekts geöffnet, das den Fehler auslöst, und zuerst die **Konfiguration** auf **Debuggen** (**Debug Unicode** (Unicode debuggen)) festgelegt. Danach wird im Linkerabschnitt **Erweitert** die Eigenschaft **Image weist sichere Ausnahmehandler auf** auf **Nein** zurückgesetzt (`/SAFESEH:NO`).

Der Compiler warnt davor, dass `PROP_ENTRY_EX` veraltet ist. Die Eigenschaft ist nicht sicher, weswegen empfohlen wird, sie durch `PROP_ENTRY_TYPE_EX` zu ersetzen.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Entsprechend wird der Code in ccomspy.h geändert und COM-Typen nach Bedarf hinzugefügt.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Wir kommen nun zu den letzten Warnmeldungen, die ebenfalls durch strengere Überprüfungen der Compilerkonformität ausgelöst werden.

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

Warnung C4018 stammt aus dem folgenden Code:

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Das Problem besteht darin, dass `i` als `UINT` und `lCount` als **long** deklariert ist, wodurch es zum Konflikt zwischen „signed“ und „unsigned“ kommt. Es wäre unpraktisch, den Typ von `lCount` in `UINT` zu ändern, da dieser seinen Wert aus `IMtsEventInfo::get_Count` erhält, der den Typ **long** verwendet und sich nicht im Benutzercode befindet. Daher wird eine Umwandlung zu dem Code hinzugefügt. Eine Besetzung im C-Stil würde für eine numerische Besetzung wie diese tun, aber **static_cast** ist der empfohlene Stil.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Diese Warnungen betreffen Fälle, in denen eine Variable in einer Funktion deklariert wurde, die einen Parameter mit dem gleichen Namen aufweist, was zu möglicherweise irreführendem Code führt. Dies wurde durch Änderung der Namen der lokalen Variablen behoben.

### <a name="step-3-testing-and-debugging"></a>Schritt 3: Testen und Debuggen

Die App wurde getestet, indem zuerst die verschiedenen Menüs und Befehle ausgeführt wurden und dann die Anwendung geschlossen wurde. Das einzige Problem war eine Debugassertion beim Schließen der Anwendung. Das Problem wurde im Destruktor für `CWindowImpl` angezeigt. Hierbei handelt es sich um eine Basisklasse des `CSpyCon`-Objekts, der wichtigsten COM-Komponente der Anwendung. Der Assertionsfehler ist im folgenden Code in atlwin.h aufgetreten.

```cpp
virtual ~CWindowImplRoot()
{
     #ifdef _DEBUG
     if(m_hWnd != NULL)// should be cleared in WindowProc
     {
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));
          ATLASSERT(FALSE);
     }
     #endif //_DEBUG
}
```

Normalerweise wird `hWnd` in der `WindowProc`-Funktion auf null (0) festgelegt. Dieser Vorgang wurde jedoch nicht ausgeführt, da statt der `WindowProc`-Standardfunktion ein benutzerdefinierter Handler für die Windows-Meldung (WM_SYSCOMMAND) aufgerufen wurde, der das Fenster schließt. Der benutzerdefinierte Handler hat `hWnd` nicht auf null (0) festgelegt. Ein Blick auf ähnlichen Code in der `CWnd`-Klasse von MFC zeigt, dass beim Entfernen eines Fensters `OnNcDestroy` aufgerufen wird. Gemäß den Empfehlungen in der Dokumentation zu MFC sollte beim Überschreiben von `CWnd::OnNcDestroy``NcDestroy` der Basisklasse aufgerufen werden, um sicherzustellen, dass die richtigen Bereinigungen durchgeführt werden. Dazu gehört auch das Trennen des Fensterhandles vom Fenster, oder anders ausgedrückt das Festlegen von `hWnd` auf null (0). Diese Bestätigung kann auch in der ursprünglichen Version des Beispiels ausgelöst worden sein, da der gleiche Assertionscode auch in der alten Version von atlwin.h vorhanden war.

Um die Funktionalität der App zu testen, haben wir eine **serviced Component** mit der ATL-Projektvorlage erstellt und com+-Unterstützung im ATL-Projektassistenten hinzugefügt. Wenn Sie noch nicht mit gewarteten Komponenten gearbeitet haben, ist es nicht schwierig, eine zu erstellen und eine registrierte und im Netzwerk verfügbare Komponente für andere Apps zu verwenden. Mit der COM Spy-App kann die Aktivität von Serviced Components zu Diagnosezwecken überwacht werden.

Dann wurde eine Klasse hinzugefügt, „ATL Object“ (ATL-Objekt) ausgewählt und als Objektname `Dog` angegeben. In dog.h und dog.cpp wurde dann die Implementierung hinzugefügt.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Als Nächstes haben wir es erstellt und registriert (Sie müssen Visual Studio als Administrator ausführen) und es mithilfe der **Anwendung "Serviced Component"** in der Windows-Systemsteuerung aktiviert. Es wurde ein C#-Windows Forms-Projekt erstellt, eine Schaltfläche aus der Toolbox in das Formular gezogen und durch Doppelklick ein Click-Ereignishandler erstellt. Zum Instanziieren der `Dog`-Komponente wurde folgender Code hinzugefügt.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

Dieser Code wurde ohne Probleme ausgeführt. Nach dem Ausführen und der Konfigurierung von COM Spy zur Überwachung der `Dog`-Komponente werden zahlreiche Daten zur Aktivität angezeigt.

## <a name="see-also"></a>Siehe auch

[Portieren und Aktualisieren: Beispiele und Fallstudien](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Nächstes Beispiel: Spy++](../porting/porting-guide-spy-increment.md)<br/>
[Vorheriges Beispiel: MFC Scribble](../porting/porting-guide-mfc-scribble.md)
