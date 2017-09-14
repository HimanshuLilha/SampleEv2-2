
//Initial rollout will setup the V1.0.0.0 version of the Contacts API App.

// storage query string for contacts-app-v1.0.0.0 ---- expiry set to dec/31/2020
?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=jYyuFzaRMgYd1PJ91%2FXGvWrK2weh%2BM4RYcjCrLqaOAw%3D

//storage location for contacts-app-v1.0.0.0 ---- expiry set to dec/31/2020
//https://admbuildstore.blob.core.windows.net/contacts-app-1-0-0-0?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=jYyuFzaRMgYd1PJ91%2FXGvWrK2weh%2BM4RYcjCrLqaOAw%3D

//set up the servicegroup root
$sgrootv1="C:\code\Repos\MyFirstProject\deploy-v1"

//run new-azureserviceRollout 
New-AzureServiceRollout -ServiceGroupRoot $sgrootv1 -RolloutSpec rolloutspec_multi-region.json -RolloutInfra Prod -WaitToComplete

// rollout V1 from Azure Storage: 
New-AzureServiceRollout -FromCloudStorage -ArtifactSourceType AzureStorage -CredentialSource Api -CredentialType AzureStorageSASUri -Credential @{"value"='https://admbuildstore.blob.core.windows.net/contacts-app-1-0-0-0?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=jYyuFzaRMgYd1PJ91%2FXGvWrK2weh%2BM4RYcjCrLqaOAw%3D'} -ServiceGroupRoot deploy-v1 -RolloutSpec rolloutspec_multi-region.json -RolloutInfra Prod -WaitToComplete

// demo: visual
// open portal. 
// click on resource groups
//select contacts-app-HR
// open web page. 
// show version and API information.


//Update v2.0.0.0 rollout will setup the V2.0.0.0 version of the Contacts API App.

// storage query string for contacts-app-v2.0.0.0 ---- expiry set to dec/31/2020
?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=UhwhdAHjJsbX7WX2u7qcv%2FGKiUCnvoLG0sNrP7rkIJs%3D

//storage location for contacts-app-v2.0.0.0 ---- expiry set to dec/31/2020
https://admbuildstore.blob.core.windows.net/contacts-app-2-0-0-0?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=UhwhdAHjJsbX7WX2u7qcv%2FGKiUCnvoLG0sNrP7rkIJs%3D

//set up the servicegroup root
$sgroot="C:\code\Repos\MyFirstProject\deploy-v2"
//run new-azureserviceRollout 
New-AzureServiceRollout -ServiceGroupRoot $sgroot -RolloutSpec rolloutspec_multi-region.json -RolloutInfra Prod -WaitToComplete

New-AzureServiceRollout -FromCloudStorage -ArtifactSourceType AzureStorage -CredentialSource Api -CredentialType AzureStorageSASUri -Credential @{"value"='https://admbuildstore.blob.core.windows.net/contacts-app-2-0-0-0?st=2017-05-08T22%3A59%3A00Z&se=2020-12-31T23%3A59%3A00Z&sp=rl&sv=2016-05-31&sr=c&sig=UhwhdAHjJsbX7WX2u7qcv%2FGKiUCnvoLG0sNrP7rkIJs%3D'} -ServiceGroupRoot deploy-v2 -RolloutSpec rolloutspec_multi-region.json -RolloutInfra Prod -WaitToComplete
