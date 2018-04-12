 
<span data-ttu-id="e6803-101">Jedoch beim Aufrufen der **String.Format** -Methode, es ist nicht notwendig, den Fokus auf die bestimmte Überladung, die Sie aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="e6803-101">However, when calling the **String.Format** method, it is not necessary to focus on the particular overload that you want to call.</span></span> <span data-ttu-id="e6803-102">Sie können stattdessen rufen Sie die Methode mit einem Objekt, das kulturabhängige oder benutzerdefinierte Formatierung bereitstellt und ein [kombinierte Formatzeichenfolge](~/docs/standard/base-types/composite-formatting.md) , die eine oder mehrere Formatelemente enthält.</span><span class="sxs-lookup"><span data-stu-id="e6803-102">Instead, you can call the method with an object that provides culture-sensitive or custom formatting and a [composite format string](~/docs/standard/base-types/composite-formatting.md) that includes one or more format items.</span></span> <span data-ttu-id="e6803-103">Sie weisen jedes Formatelement in einen numerischen Index; der erste Index beginnt bei 0.</span><span class="sxs-lookup"><span data-stu-id="e6803-103">You assign each format item a numeric index; the first index starts at 0.</span></span> <span data-ttu-id="e6803-104">Zusätzlich zu der ursprünglichen Zeichenfolge müssen der Methodenaufruf so viele zusätzliche Argumente wie Indexwerte verfügen.</span><span class="sxs-lookup"><span data-stu-id="e6803-104">In addition to the initial string, your method call should have as many additional arguments as it has index values.</span></span> <span data-ttu-id="e6803-105">Beispielsweise sollte eine Zeichenfolge, deren Formatelemente Indizes von 0 bis 1 weisen, 2 Argumente verfügen. mit Indizes von 0 bis 5 sollte 6-Argumente aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e6803-105">For example, a string whose format items have indexes of 0 and 1 should have 2 arguments; one with indexes 0 through 5 should have 6 arguments.</span></span> <span data-ttu-id="e6803-106">Beheben der Sprachcompiler Sie dann den Methodenaufruf an eine bestimmte Überladung der der **String.Format** Methode.</span><span class="sxs-lookup"><span data-stu-id="e6803-106">Your language compiler will then resolve your method call to a particular overload of the **String.Format** method.</span></span>   

<span data-ttu-id="e6803-107">Ausführlichere Dokumentation zur Verwendung der **String.Format** -Methode finden Sie unter [Einstieg in die String.Format-Methode](#Starting) und [welche Methode aufrufen?](#FTaskList).</span><span class="sxs-lookup"><span data-stu-id="e6803-107">For more detailed documentation on using the **String.Format** method, see [Getting started with the String.Format method](#Starting) and [Which method do I call?](#FTaskList).</span></span>   