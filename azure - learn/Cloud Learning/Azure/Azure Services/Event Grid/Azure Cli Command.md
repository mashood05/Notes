$resourceGroup = az group list --query '[0].name' --output tsv
$location = az resource list --query '[0].location' --output tsv
$namespace = az eventhubs namespace list --resource-group $resourceGroup --query '[0].name' --output tsv 
$hubId = az eventhubs eventhub list --resource-group $resourceGroup --namespace-name $namespace --query '[0].id' --output tsv


#create event grid topic and subscription

$topicname = “topic-09152020”
az eventgrid topic create --name $topicname -l $location -g $resourceGroup
$topicId = az eventgrid topic list --query ‘[0].id’ --output tsv
$ehSubName = “es09152020”
az eventgrid event-subscription create --name $ehSubName --source-resource-id $topicId --endpoint $hubId --endpoint-type eventhub
$eventID = Get-Random 99999
$eventDate = Get-Date -Format s

$htbody = @{
 id= $eventID
 eventType="recordInserted"
 subject="myapp/guitars/gibson"
 eventTime= $eventDate
 data= @{
 make="Gibson"
 model="Les Paul"
 }
 dataVersion="1.0"
}

$body = "["+(ConvertTo-Json $htbody)+"]"