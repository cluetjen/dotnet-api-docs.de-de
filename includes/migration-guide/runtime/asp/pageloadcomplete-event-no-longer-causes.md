### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="19020-101">Page.LoadComplete Ereignis bewirkt, dass nicht mehr System.Web.UI.WebControls.EntityDataSource Steuerelement zum Aufrufen der Datenbindung</span><span class="sxs-lookup"><span data-stu-id="19020-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="19020-102">Details</span><span class="sxs-lookup"><span data-stu-id="19020-102">Details</span></span>|<span data-ttu-id="19020-103">Das <xref:System.Web.UI.Page.LoadComplete>-Ereignis führt nicht mehr dazu, dass das <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name>-Steuerelement Datenbindungen für Änderungen an Erstellungs-/Update-/Löschparametern aufruft.</span><span class="sxs-lookup"><span data-stu-id="19020-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="19020-104">Diese Änderung schließt unnötige Roundtrips zur Datenbank sowie ein Zurücksetzen der Werte von Steuerelementen aus und erzeugt Verhaltensweisen, die mit anderen Datensteuerelementen, z. B. <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> und <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name> konsistent sind.</span><span class="sxs-lookup"><span data-stu-id="19020-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>.</span></span> <span data-ttu-id="19020-105">Diese Änderung erzeugt im unwahrscheinlichen Fall, dass Anwendungen im <xref:System.Web.UI.Page.LoadComplete>-Ereignis auf Aufrufen der Datenbindung basieren, ein anderes Verhalten.</span><span class="sxs-lookup"><span data-stu-id="19020-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>|
|<span data-ttu-id="19020-106">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="19020-106">Suggestion</span></span>|<span data-ttu-id="19020-107">Wenn die Datenbindung erforderlich ist, rufen Sie sie manuell in einem Ereignis auf, das im Postback früher auftritt.</span><span class="sxs-lookup"><span data-stu-id="19020-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>|
|<span data-ttu-id="19020-108">Bereich</span><span class="sxs-lookup"><span data-stu-id="19020-108">Scope</span></span>|<span data-ttu-id="19020-109">Edge</span><span class="sxs-lookup"><span data-stu-id="19020-109">Edge</span></span>|
|<span data-ttu-id="19020-110">Version</span><span class="sxs-lookup"><span data-stu-id="19020-110">Version</span></span>|<span data-ttu-id="19020-111">4.5</span><span class="sxs-lookup"><span data-stu-id="19020-111">4.5</span></span>|
|<span data-ttu-id="19020-112">Typ</span><span class="sxs-lookup"><span data-stu-id="19020-112">Type</span></span>|<span data-ttu-id="19020-113">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="19020-113">Runtime</span></span>|
