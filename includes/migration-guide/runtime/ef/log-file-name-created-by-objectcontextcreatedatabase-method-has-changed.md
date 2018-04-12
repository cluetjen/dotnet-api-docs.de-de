### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="dfa61-101">Mit der ObjectContext.CreateDatabase-Methode erstellte Protokolldateiname wurde geändert, um SQL Server-Spezifikationen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="dfa61-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dfa61-102">Details</span><span class="sxs-lookup"><span data-stu-id="dfa61-102">Details</span></span>|<span data-ttu-id="dfa61-103">Wenn die <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> Methode wird aufgerufen, entweder direkt oder Code First mit dem SqlClient-Anbieter und einen AttachDBFilename-Wert in der Verbindungszeichenfolge verwenden, erstellt es eine Protokolldatei mit dem Namen filename_log.ldf statt Dateiname.ldf (wobei Dateiname ist der Name des die Datei durch den Wert von AttachDBFilename angegeben).</span><span class="sxs-lookup"><span data-stu-id="dfa61-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="dfa61-104">Diese Änderung verbessert das Debuggen, indem eine Protokolldatei bereitgestellt wird, die nach den SQL Server-Spezifikationen benannt wird.</span><span class="sxs-lookup"><span data-stu-id="dfa61-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="dfa61-105">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="dfa61-105">Suggestion</span></span>|<span data-ttu-id="dfa61-106">Wenn der Name der Protokolldatei für eine App wichtig ist, sollte die App aktualisiert werden, um das standardmäßige Dateinamenformat „_log.ldf“ zu erwarten.</span><span class="sxs-lookup"><span data-stu-id="dfa61-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="dfa61-107">Bereich</span><span class="sxs-lookup"><span data-stu-id="dfa61-107">Scope</span></span>|<span data-ttu-id="dfa61-108">Edge</span><span class="sxs-lookup"><span data-stu-id="dfa61-108">Edge</span></span>|
|<span data-ttu-id="dfa61-109">Version</span><span class="sxs-lookup"><span data-stu-id="dfa61-109">Version</span></span>|<span data-ttu-id="dfa61-110">4.5</span><span class="sxs-lookup"><span data-stu-id="dfa61-110">4.5</span></span>|
|<span data-ttu-id="dfa61-111">Typ</span><span class="sxs-lookup"><span data-stu-id="dfa61-111">Type</span></span>|<span data-ttu-id="dfa61-112">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="dfa61-112">Runtime</span></span>|
|<span data-ttu-id="dfa61-113">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="dfa61-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
