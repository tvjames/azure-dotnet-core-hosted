# Hosting on Azure Web Services

[![Build Status](https://thomasvjames.visualstudio.com/azure-dotnet-core-hosted-example/_apis/build/status/azure-dotnet-core-hosted-example-CI?branchName=master)](https://thomasvjames.visualstudio.com/azure-dotnet-core-hosted-example/_build/latest?definitionId=2&branchName=master)

* Install the azure cli on macOS [azure-cli]
  * `brew update && brew install azure-cli`
  * `az login`

* Create an asp.net core mvc application
  * `mkdir -p src/ExampleMvcSite`
  * `cd src/ExampleMvcSite`
  * `dotnet new webapp`
  * `cd ..`
  * `dotnet new sln --name AzureHosted`
  * `dotnet sln AzureHosted.sln add ExampleMvcSite/`
  * `dotnet build`

* Configure Azure hosting using the free tier [getting-started]
  * Find free tier regions: `az appservice list-locations --sku F1 --linux-workers-enabled` or `az appservice list-locations --sku F1`
  * Resource Group: `azure-dotnet-core-hosted-example`
  * App Service Plan: `azure-dotnet-core-hosted-example-app-plan`
  * `az group create --name azure-dotnet-core-hosted-example --location "Australia East"`
  * `az appservice plan create --name azure-dotnet-core-hosted-example-app-plan --resource-group azure-dotnet-core-hosted-example --sku F1`
  * `az webapp create --resource-group azure-dotnet-core-hosted-example --plan azure-dotnet-core-hosted-example-app-plan --name azure-dotnet-core-hosted-example`

* Azure DevOps (CI/CD)
  * Configure Azure Pipeline


[azure-cli]: https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest 
[dotnet-sdk-22]: https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.106-macos-x64-installer
[dotnet-sdk-21]: https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.1.603-macos-x64-installer
[getting-started]: https://docs.microsoft.com/en-us/azure/app-service/containers/quickstart-dotnetcore
[app-service-plans]: https://azure.microsoft.com/en-au/pricing/details/app-service/windows/
