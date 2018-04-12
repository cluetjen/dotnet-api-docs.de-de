### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="30036-101">Neue (mehrdeutige) Dispatcher.Invoke Überladungen konnte zu verschiedenen Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="30036-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30036-102">Details</span><span class="sxs-lookup"><span data-stu-id="30036-102">Details</span></span>|<span data-ttu-id="30036-103">.NET Framework 4.5 fügt neue Überladungen zum <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , enthalten einen Parameter vom Typ <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="30036-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="30036-104">Vorhandener Code neu kompiliert, lösen Compiler möglicherweise Aufrufe an Dispatcher.Invoke-Methoden, die über eine <xref:System.Delegate> Parameter als Aufrufe an Dispatcher.Invoke Methoden mit einem <xref:System.Action> Parameter.</span><span class="sxs-lookup"><span data-stu-id="30036-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="30036-105">Ein Aufruf an eine Überladung Dispatcher.Invoke mit einer <xref:System.Delegate> Parameter wird als ein Aufruf an eine Überladung Dispatcher.Invoke mit aufgelöst ein <xref:System.Action> Parameter, die folgenden Unterschiede im Verhalten auftreten:</span><span class="sxs-lookup"><span data-stu-id="30036-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span><ul><li><span data-ttu-id="30036-106">Tritt eine Ausnahme auf, werden die <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter>- und <xref:System.Windows.Threading.Dispatcher.UnhandledException>-Ereignisse nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="30036-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="30036-107">Stattdessen werden Ausnahmen durch das <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name>-Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="30036-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name> event.</span></span></li><li><span data-ttu-id="30036-108">Bis der Vorgang abgeschlossen ist, werden Aufrufe an einige Member, z. B. <xref:System.Windows.Threading.DispatcherOperation.Result>, blockiert.</span><span class="sxs-lookup"><span data-stu-id="30036-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span></li></ul>|
|<span data-ttu-id="30036-109">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="30036-109">Suggestion</span></span>|<span data-ttu-id="30036-110">Um Unklarheiten zu vermeiden (und mögliche Abweichungen bei der Ausnahmebehandlung oder bei blockierendem Verhalten), kann Code, der „Dispatcher.Invoke“ aufruft, ein leeres Objekt [] als zweiten Parameter an den Invoke-Aufruf übergeben, um sicherzustellen, dass nach der .NET 4.0-Methodenüberladung aufgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="30036-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET 4.0 method overload.</span></span>|
|<span data-ttu-id="30036-111">Bereich</span><span class="sxs-lookup"><span data-stu-id="30036-111">Scope</span></span>|<span data-ttu-id="30036-112">Gering</span><span class="sxs-lookup"><span data-stu-id="30036-112">Minor</span></span>|
|<span data-ttu-id="30036-113">Version</span><span class="sxs-lookup"><span data-stu-id="30036-113">Version</span></span>|<span data-ttu-id="30036-114">4.5</span><span class="sxs-lookup"><span data-stu-id="30036-114">4.5</span></span>|
|<span data-ttu-id="30036-115">Typ</span><span class="sxs-lookup"><span data-stu-id="30036-115">Type</span></span>|<span data-ttu-id="30036-116">Neuzuweisung</span><span class="sxs-lookup"><span data-stu-id="30036-116">Retargeting</span></span>|
|<span data-ttu-id="30036-117">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="30036-117">Affected APIs</span></span>|<ul><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li></ul>|
