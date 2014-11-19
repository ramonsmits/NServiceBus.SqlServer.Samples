
1. Make sure LocalDB is enabled on your machine. It is configured to use `(localdb)\MSSQLLocalDB` which is 'SQL Server 2014 Express LocalDB' but the same works with previous version to. Just perform a search and replace on that data source.

2. A persistant storage MUST be configured when running without the debuggger. Running via the debugger uses the in memory provider for the following features.
* sagas
* timeouts
* subscriptions
* outbox
* gatewaydeduplication

3. Makre sure the NServiceBus performance counters are initialized. Either by
** [using the installer](http://particular.net/downloads) or
** [Via PS by executing Install-NServiceBusPerformanceCounter](http://docs.particular.net/nservicebus/managing-nservicebus-using-powershell)


4. Databases are not created by the SQL transport. Only the queue tables are created during installation. The sample has a database per host :

Creation

	CREATE DATABASE [VideoStore.ContentManagement]
	CREATE DATABASE [VideoStore.Operations]
	CREATE DATABASE [VideoStore.Sales]
	CREATE DATABASE [VideoStore.CustomerRelations]
	CREATE DATABASE [VideoStore.ECommerce]

Drop 

	DROP DATABASE [VideoStore.ContentManagement]
	DROP DATABASE [VideoStore.Operations]
	DROP DATABASE [VideoStore.Sales]
	DROP DATABASE [VideoStore.CustomerRelations]
	DROP DATABASE [VideoStore.ECommerce]



