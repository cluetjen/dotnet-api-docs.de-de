### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="c41c1-101">Einschränken von gleichzeitigen Anforderungen pro Sitzung</span><span class="sxs-lookup"><span data-stu-id="c41c1-101">Throttle concurrent requests per session</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c41c1-102">Details</span><span class="sxs-lookup"><span data-stu-id="c41c1-102">Details</span></span>|<span data-ttu-id="c41c1-103">In .NET Framework 4.6.2 und früher, führt ASP.NET Anforderungen mit der gleichen Sessionid sequenziell aus, und ASP.NET stellt immer die Sessionid mithilfe von Cookies standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="c41c1-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="c41c1-104">Wenn eine Seite lange Antworten ausgeführt wird, wird sie serverleistung erheblich beeinträchtigt, einfach durch Drücken von F5 im Browser.</span><span class="sxs-lookup"><span data-stu-id="c41c1-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing F5 on the browser.</span></span> <span data-ttu-id="c41c1-105">Die Lösung haben wir einen Zähler, um die in der Warteschlange Anforderungen nachzuverfolgen und die Anforderungen zu beenden, wenn sie einen bestimmten Grenzwert überschreiten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c41c1-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="c41c1-106">Der Standardwert ist 50.</span><span class="sxs-lookup"><span data-stu-id="c41c1-106">The default value is 50.</span></span> <span data-ttu-id="c41c1-107">Wenn der Grenzwert erreicht ist, wird eine Warnung im Ereignisprotokoll Protokoll- und eine HTTP 500-Antwort im IIS-Protokoll aufgezeichnet werden möglicherweise protokolliert.</span><span class="sxs-lookup"><span data-stu-id="c41c1-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>|
|<span data-ttu-id="c41c1-108">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="c41c1-108">Suggestion</span></span>|<span data-ttu-id="c41c1-109">Um das alte Verhalten wiederherzustellen, können Sie Ihrer web.config-Datei die folgende Einstellung hinzufügen, um sich gegen das neue Verhalten zu entscheiden.</span><span class="sxs-lookup"><span data-stu-id="c41c1-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span><pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="c41c1-110">Bereich</span><span class="sxs-lookup"><span data-stu-id="c41c1-110">Scope</span></span>|<span data-ttu-id="c41c1-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c41c1-111">Edge</span></span>|
|<span data-ttu-id="c41c1-112">Version</span><span class="sxs-lookup"><span data-stu-id="c41c1-112">Version</span></span>|<span data-ttu-id="c41c1-113">4.7</span><span class="sxs-lookup"><span data-stu-id="c41c1-113">4.7</span></span>|
|<span data-ttu-id="c41c1-114">Typ</span><span class="sxs-lookup"><span data-stu-id="c41c1-114">Type</span></span>|<span data-ttu-id="c41c1-115">Neuzuweisung</span><span class="sxs-lookup"><span data-stu-id="c41c1-115">Retargeting</span></span>|
