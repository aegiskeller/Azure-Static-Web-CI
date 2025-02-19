[![Azure Static Web Apps CI/CD](https://github.com/aegiskeller/Azure-Static-Web-CI/actions/workflows/azure-static-web-apps-ashy-flower-040dfdf10.yml/badge.svg)](https://github.com/aegiskeller/Azure-Static-Web-CI/actions/workflows/azure-static-web-apps-ashy-flower-040dfdf10.yml)

# Vanilla JavaScript App

[Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview) allows you to easily build JavaScript apps in minutes. Use this repo with the [quickstart](https://docs.microsoft.com/azure/static-web-apps/getting-started?tabs=vanilla-javascript) to build and customize a new static site.

This repo is used as a starter for a _very basic_ HTML web application using no front-end frameworks.

This repo has a dev container. This means if you open it inside a [GitHub Codespace](https://github.com/features/codespaces), or using [VS Code with the remote containers extension](https://code.visualstudio.com/docs/remote/containers), it will be opened inside a container with all the dependencies already installed.

## File Transfer

get the role to transfer

az ad signed-in-user show --query id -o tsv | az role assignment create \
    --role "Storage Blob Data Contributor" \
    --assignee @- \
    --scope "/subscriptions/531a9b9c-41ed-4a91-b3fa-d7dd975c5124/resourceGroups/aegiskeller-rg/providers/Microsoft.Storage/storageAccounts/teststorageaegiskeller"

create a container for storage

az storage container create \
    --account-name teststorageaegiskeller \
    --name django \
    --auth-mode login

store the file 

az storage blob upload --account-name teststorageaegiskeller --container-name django --name myFile.txt --file myFile.txt --auth-mode login