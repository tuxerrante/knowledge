Import a new AKS cluster in powershell

- https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3#winget
- https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-portal?tabs=azure-powershell#connect-to-the-cluster

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
az login
Connect-AzAccount
Import-AzAksCredential -ResourceGroupName aff-experiments -Name aks-test
kubectl config list-context

choco install starship

kubectl completion powershell >> $PROFILE
Invoke-Expression (&starship init powershell) >> $PROFILE

