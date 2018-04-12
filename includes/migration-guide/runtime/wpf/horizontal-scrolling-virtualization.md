### <a name="horizontal-scrolling-and-virtualization"></a><span data-ttu-id="8f599-101">Horizontaler Bildlauf und Virtualisierung</span><span class="sxs-lookup"><span data-stu-id="8f599-101">Horizontal scrolling and virtualization</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8f599-102">Details</span><span class="sxs-lookup"><span data-stu-id="8f599-102">Details</span></span>|<span data-ttu-id="8f599-103">Diese Änderung gilt für eine <xref:System.Windows.Controls.ItemsControl?displayProperty=name> eigene Virtualisierung in Richtung auf die wichtigsten Durchführen eines Bildlaufs Richtung orthogonale ausführt (chief Beispiel ist <xref:System.Windows.Controls.DataGrid?displayProperty=name> mit EnableColumnVirtualization =&quot;"true"&quot;).</span><span class="sxs-lookup"><span data-stu-id="8f599-103">This change applies to an <xref:System.Windows.Controls.ItemsControl?displayProperty=name> that does its own virtualization in the direction orthogonal to the main scrolling direction (the chief example is <xref:System.Windows.Controls.DataGrid?displayProperty=name> with EnableColumnVirtualization=&quot;True&quot;).</span></span>  <span data-ttu-id="8f599-104">Das Ergebnis bestimmter Vorgänge für horizontalen Bildlauf wurde geändert, um Ergebnisse zu erzeugen, die eine intuitivere und mehr analog zu den Ergebnissen vergleichbare vertikale Vorgänge sind. Vorgängen zählen &quot;Bildlauf hier&quot; und &quot;Rechte Kante&quot;, um die Namen aus dem Menü erhalten, indem Sie mit der rechten Maustaste einer horizontalen Bildlaufleiste verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f599-104">The outcome of certain horizontal scrolling operations has been changed to produce results that are more intuitive and more analogous to the results of comparable vertical operations.The operations include &quot;Scroll Here&quot; and &quot;Right Edge&quot;, to use the names from the menu obtained by right-clicking a horizontal scrollbar.</span></span>  <span data-ttu-id="8f599-105">Beide Optionen zu berechnen, ein Kandidat Offset und rufen <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>. Nach dem Bildlauf zu der neuen Offset, das Konzept von &quot;hier&quot; oder &quot;Rand&quot; möglicherweise geändert haben, da neu Deduplizierung virtualisierten Inhalt den Wert des geänderten <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>. Vor .net 4.6.2, den Offset Candidate vom Vorgang Scroll einfach verwendet, obwohl er möglicherweise nicht &quot;hier&quot; oder an der &quot;Rand&quot; mehr.</span><span class="sxs-lookup"><span data-stu-id="8f599-105">Both of these compute a candidate offset and call <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.After scrolling to the new offset, the notion of &quot;here&quot; or &quot;right edge&quot; may have changed because newly de-virtualized content has changed the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.Prior to .Net 4.6.2, the scroll operation simply uses the candidate offset, even though it may not be &quot;here&quot; or at the &quot;right edge&quot; any more.</span></span>  <span data-ttu-id="8f599-106">Dies führt zu Auswirkungen wie &quot;verarbeit&quot; Scroll Ziehpunkt, bewährte anhand eines Beispiels veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="8f599-106">This results in effects like &quot;bouncing&quot; the scroll thumb, best illustrated by example.</span></span> <span data-ttu-id="8f599-107">Nehmen Sie an einer <xref:System.Windows.Controls.DataGrid?displayProperty=name> hat ExtentWidth = 1000 und Breite = 200.</span><span class="sxs-lookup"><span data-stu-id="8f599-107">Suppose a <xref:System.Windows.Controls.DataGrid?displayProperty=name> has ExtentWidth=1000 and Width=200.</span></span>  <span data-ttu-id="8f599-108">Eine einen Bildlauf zum &quot;Rechte Kante&quot; verwendet Candidate offset 1000 200 = 800.</span><span class="sxs-lookup"><span data-stu-id="8f599-108">A scroll to &quot;Right Edge&quot; uses candidate offset 1000 - 200 = 800.</span></span>  <span data-ttu-id="8f599-109">Beim Durchführen eines Bildlaufs, Offset, werden neue Spalten de-virtualisiert; Angenommen, sie sind sehr breit, sodass die <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> auf 2000 geändert.</span><span class="sxs-lookup"><span data-stu-id="8f599-109">While scrolling to that offset, new columns are de- virtualized; let's suppose they are very wide, so that the <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> changes to 2000.</span></span>  <span data-ttu-id="8f599-110">Das Scroll endet mit HorizontalOffset = 800 und Ziehpunkt &quot;abprallt&quot; wieder in der Mitte der Bildlaufleiste - genau an 800/2000 = 40 %. Die Änderung wird an einen neuen Kandidaten Offset neu berechnet, wenn diese Situation tritt ein, und wiederholen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="8f599-110">The scroll ends with HorizontalOffset=800, and the thumb &quot;bounces&quot; back to near the middle of the scrollbar - precisely at 800/2000 = 40%.The change is to recompute a new candidate offset when this situation occurs, and try again.</span></span> <span data-ttu-id="8f599-111">(Dies ist wie vertikaler Bildlauf bereits funktioniert.) Die Änderung erzeugt eine vorhersagbare und intuitive Erfahrung für den Endbenutzer, aber es könnte auch jeder app, die abhängig von den exakten Wert des beeinträchtigen <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> nach eine horizontalen Bildlauf, ob vom Endbenutzer oder durch ein expliziter Aufruf von aufgerufen <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.</span><span class="sxs-lookup"><span data-stu-id="8f599-111">(This is how vertical scrolling works already.)The change produces a more predictable and intuitive experience for the end user, but it could also affect any app that depends on the exact value of <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> after a horizontal scroll, whether invoked by the end user or by an explicit call to <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.</span></span>|
|<span data-ttu-id="8f599-112">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="8f599-112">Suggestion</span></span>|<span data-ttu-id="8f599-113">Eine app, die für einen vorhergesagten Wert verwendet <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> sollte geändert werden, um den tatsächlichen Wert abzurufen (und den Wert der <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) nach jeder horizontalen Bildlaufleiste, die sich ändern, könnte <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> aufgrund Deduplizierung Virtualisierung.</span><span class="sxs-lookup"><span data-stu-id="8f599-113">An app that uses a predicted value for <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> should be changed to fetch the actual value (and the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) after any horizontal scroll that could change <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> due to de-virtualization.</span></span>|
|<span data-ttu-id="8f599-114">Bereich</span><span class="sxs-lookup"><span data-stu-id="8f599-114">Scope</span></span>|<span data-ttu-id="8f599-115">Gering</span><span class="sxs-lookup"><span data-stu-id="8f599-115">Minor</span></span>|
|<span data-ttu-id="8f599-116">Version</span><span class="sxs-lookup"><span data-stu-id="8f599-116">Version</span></span>|<span data-ttu-id="8f599-117">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8f599-117">4.6.2</span></span>|
|<span data-ttu-id="8f599-118">Typ</span><span class="sxs-lookup"><span data-stu-id="8f599-118">Type</span></span>|<span data-ttu-id="8f599-119">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="8f599-119">Runtime</span></span>|
|<span data-ttu-id="8f599-120">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="8f599-120">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
